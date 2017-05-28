<!--
.. title: Registering Functions Against Object Methods in Python
.. slug: registering-functions-against-object-methods-in-python
.. date: 2017-05-25 13:07:32 UTC-07:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

My big side project right now is a [music theory library in Python, called Ophis](https://github.com/OphisMusic/ophis). Among many other concerns, I'm trying to make the API as natural and easy to use as possible. This often means finding ways of creating objects other than `ClassName(args)`.

Ophis has the classes `Chroma` and `Pitch`. A chroma is a note name without an octave (the *idea* of C), while a pitch is a chroma with a specified octave (middle C).

The problem with this is that the conventional way of referring to a pitch would then be:

```python

ophis.Pitch(ophis.C, 0)

```

You can see, Ophis has already initialized all the note names (chromae) you would need. We *could* do that with pitches...

```python
C0 = Pitch(C, 0)
C1 = Pitch(C, 1)

# later, in user code...

ophis.C1
```

...but I think we all know the problem with that. It requires initializing several hundred pitch objects that may never be used. Most songs don't use every note. And every physical note has multiple names because of enharmonic spelling (F♯ == G♭).

So, what if the API looked like this?

```python

ophis.C(1)
```

That's cool. Pretty easy to do, too.

```python

class Chroma:

  #
  #
  #

  def __call__(self, octave):
    return Pitch(self, octave)
```

## What if we went deeper?

Once you realize this is a good idea, the next thing you realize is.... what about chords?

```python

ophis.Chord(ophis.C, Major)
```

Well, that looks pretty similar, doesn't it?

So, um... okay...

```python

class Chroma:

    #
    #
    #

    def __call__(self, x):
        try:
          return Pitch(self, x)
        except TypeError:
          return Chord(self, x)
```

There are problems with this.

 - Definitions for Pitch and Chord are in modules that get loaded after Chroma. This doesn't create any errors (because the function isn't run on load), but still feels wrong.
 - It is brittle. If I change the name of `Pitch` or `Chord`, I have to go back and change it here. The tightly-wound nature of music terminology means I have long-since given up the idea of *loose coupling*, but I'm trying to make these types of dependencies only go up the conceptual ladder, not back down it.
 - What if I want to add more things to this method? Eventually I'm going to end up creating a series of type checks.

When I was working through this, I didn't see any way around a series of type checks, but I thought I could solve the first two problems with some creative coding.

I decided I could register functions into a `dict`, stored on the class. The keys for the dict would be types, and the values would be the functions to run when `__call__` is called with that particular type as an argument. These functions could be registered at the point when the type that the function is supposed to return is created.

Something like...

```python

class Chroma:

    #
    #
    #

    _callable_funcs = dict()

    def __call__(self, x, x_type=None):

        if callable(x):
            self.__class__._callable_funcs[x_type] = x
        else:
            return self.__class__._callable_funcs[type(x)](self, x)


# This code has not been tested.
```

I got (a version of) this to work, and I was feeling pretty darn proud of myself for thinking of this solution, and implementing it.

Then I had this feeling like this was all very familiar. Maybe I had read about this type of thing?

I quickly discovered three things:

 - I had read about precisely this in [*Fluent Python* by Luciano Ramalho](http://amzn.to/2ruo2td). (This is a great book for intermediate Python programmers.)
 - This pattern is called *single dispatch*.
 - It is already [implemented in the standard library](https://docs.python.org/3/library/functools.html#functools.singledispatch).

Unfortunately, I have two problems:

 - The `@singledispatch` decorator only looks at the first argument of a function call. The first argument of a method call is always `self`. So, out of the box, this dosn't work for instance methods.
 - `@singledispatch` was [added in v3.4](https://www.python.org/dev/peps/pep-0443/), making it still a little newish. Since I'm writing a utility library for others to use, and not my own application, it seems unwise to rely on something that everyone might not have.

But, now I can do two things:

 - See if anyone has already figured out a way to apply `@singledispatch` to a method. ([Someone has](https://stackoverflow.com/questions/24601722/how-can-i-use-functools-singledispatch-with-instance-methods).)
 - Potentially re-implement `@singledispatch` myself, for backwards compatibility.

Right...


```python

# oph_utils.py

try:
    from functools import singledispatch
except:
    # A re-implementation of @singledispatch
    # has been left as an exercise for the reader
    # because I haven't done one yet.

def method_dispatch(func):
    """
    An extension of functools.singledispatch,
    which looks at the argument after self.
    """
    dispatcher = singledispatch(func)
    def wrapper(*args, **kw):
        return dispatcher.dispatch(args[1].__class__)(*args, **kw)
    wrapper.register = dispatcher.register
    update_wrapper(wrapper, func)
    return wrapper

# chroma.py

class Chroma():

    #
    #
    #


    @oph_utils.method_dispatch
    def __call__(self, x):
        return self

# pitch.py


import chroma as ch

class Pitch:

    def __init__(self, chroma, octave=0):
          self.chroma = chroma
          self.octave = int(octave)


ch.Chroma.__call__.register(int, Pitch)


# In user code:

ophis.C(0) == ophis.Pitch(ophis.C, 0)
# True

```

And finally, to encourage this usage...

```python

class Pitch:

    #
    #
    #


    __repr__(self):
        return "".join([
            self.chroma.__repr__()], "(",
            self.octave.__repr__()], ")"
            ])


# At a terminal...

>>> ophis.Pitch(ophis.C, 0)
C(0)

```

Feels Pythonic, yes?

## Further Reading

 - [Fluent Python, by Luciano Ramalho](http://amzn.to/2rLvDTO)
 - [PEP 443 -- Single-dispatch generic functions](https://www.python.org/dev/peps/pep-0443/)
 - [Python 3.4 single dispatch, a step into generic functions](https://julien.danjou.info/blog/2013/python-3.4-single-dispatch-generic-function) (Also a music-related example.)
