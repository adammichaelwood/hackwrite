<!--
.. title: Intersection of Non-Empty Sets in Python
.. slug: intersection-of-non-empty-sets-in-python
.. date: 2017-04-15 07:48:40 UTC-07:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

Suppose you generate several sets on the fly, and you want to find the elements that are in all the sets. That's easy, it's the intersection of sets.

```python
# One syntax option
result = set_one & set_two & set_three

# Another option
result = set.intersection(set_one, set_two, set_three)
```

But let's suppose that one or more of your sets is empty. The intersection of any set and an empty set is an empty set. But, that's not what you want. (Well, it wasn't what I wanted, anyway.)

Suppose you want the intersection of all non-empty sets.

## List comprehension

If the sets are in a list, you can remove the empties. Then unpack the list into the `set.intersection()` function.

```python

list_of_sets = [set_one, set_two, set_three]

# Empty sets evaluate to false,
# so will be excluded from list comp.
non_empties = [x for x in list_of_sets if x]

solution_set = set.intersection(*non_empties)
```

The asterisk before `non_empties` unpacks the list into a series of positional arguments. This is needed because `set.intersection()` takes an arbitrary number of sets, not an iterable full of sets. (It's the same asterisk as in `*args` in function definitions.)

(Note: You *could* use a filter instead of a list comprehension, but [Guido thinks a list comprehension is better](http://www.artima.com/weblogs/viewpost.jsp?thread=98196). I agree.)

### With iterable unpacking (tuple unpacking)

In my case, I was generating the sets in my code, and the solution set always contained only one item. And I wanted the item, not a set with the item. So...

```python

# initialize an empty list
list_of_sets = []

# each time I create a set,
# append set to list when it is created,
# instead of naming them individually
list_of_sets.append( thing_that_generates_a_set() )

# drop the empties, find the intersection
# and unpack the remaining single element
solution, = set.intersection(*[x for x in list_of_sets if x])

```

The comma after `solution` turns the assignment into a tuple unpacking. If you unpack a collection of one, you get the single item.

By the way, if you end up with more than one item in your collection, and only want the first item, you can do:

```
first_item, *_ = some_collection
```

The `*` indicates a variable number of positional arguments (it's the same asterisk as in `*args` and in passing the list to `set.intersection()` above), and the underscore is used as a convention for "not using this stuff."

```
# you could have done this instead

first_item, *stuff_i_will_not_care_about = some_collection
```

I'll be using that `*_` below, in the actual code.


## Why would you ever do this?

### The generalized problem

From a pool of items, there are three attributes to select for. Specifying any two of them should produce one and only one result.

### More specifically...

Musical intervals.

A musical interval has:

 - a quality (Major, Minor, Perfect, Augment, or Diminished)
 - a number (Unison (1), Second (2), Third (3) ... Octave (8))
 - a distance of half_steps (for example, a major third is 4 half steps)

If you know any two of these, you can select the correct one.

## Some actual code


```python

class Interval():

  #####################################
  # ... all sorts of things removed ...
  #####################################


  instances = set()
  # all instances of Interval


  @classmethod
  def get_intervals(cls, *, quality=None, number=None, half_steps=None):
      """Return a set of intervals."""

      candidate_sets = []

      candidate_sets.append({x for x in cls.instances if x.quality == quality})

      candidate_sets.append({x for x in cls.instances if x.number == number})

      candidate_sets.append({x for x in cls.instances if x.half_steps == half_steps})

      candidate_sets = [x for x in candidate_sets if len(x) > 0]

      return set.intersection(*candidate_sets)

  @classmethod
  def get_interval(cls, quality=None, number=None, half_steps=None):
      """ Return a single interval."""

      try:
          interval, = cls.get_intervals(quality=quality, number=number, half_steps=half_steps)

      ## if there was not one and only one result
      except ValueError:

          # only select by half_steps
          candidates = [x for x in cls.instances if half_steps == x.half_steps]

          # select the first one,
          # based on quality priority:
          # Perfect, Major, Minor, Dim, Aug
          interval, *_ = sorted(candidates, key=lambda x: x.quality.priority)

        return interval

```

In [the actual code](https://github.com/OphisMusic/ophis), there's a bunch of other things going on, but this is the general idea.

## Another approach

For my specific use case, another approach is simply to not create a set for the unspecified attribute.

```python

if quality is not None:
    candidate_sets.append({x for x in cls.instances if x.quality == quality})

if number is not None:
    candidate_sets.append({x for x in cls.instances if x.number == number})

if half_steps is not None:
    candidate_sets.append({x for x in cls.instances if x.half_steps == half_steps})
```

In my working code, I actually do both. This allows for a potentially meaningful result even if something is specified incorrectly. I could have decided to let bad input cause explicit failure, but I **think** I'd rather not in this case.

## So... what's the point?

This post looks like a tutorial on list comprehension. Or maybe set operations. But really this post is about problem solving while writing code.

The code solution to this problem is really easy... but *only if you've figured out the problem you need to solve*.

I started with the following problem:

> Find the intersection of all non-empty sets, from an arbitrary pool of sets, not knowing which ones would be empty.

So I started Googling variations on that theme. But there aren't any "intersection of just the good sets" functions. Then I tried to start writing a question for Stack Overflow, and as soon as I had written the title, I knew the answer.

> Starting with a collection of sets, drop the empty sets and find the intersection of the remaining sets.

As soon as I broke my one problem into two steps, the problem was immediately solved:

1. Create a new collection without the empties. (List comp.)
2. Find the intersection of *that* list.

At the same moment I realized these steps, it also become clear that the original group of sets should be a collection, not just several unrelated objects.

So, the moral of the story is...

If you can't find the solution to your specific problem, restate your problem as a series of steps.
