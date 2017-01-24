<!--
.. title: Simple Input Validation and Exception Handling in Python
.. slug: simple-input-validation-handling-python
.. date: 2017-01-02 06:33:49 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

If you are doing a simple terminal script in Python, and you need to validate some user-supplied input, you can put the assignment and validation in a `try` block inside a `while` loop.

<!-- TEASER_END -->

```python

while: # variable not assigned
    try:
        # input, assignment, validation
    except:
        continue

```

If the assignment or validation fails, the loop repeats and the user has another opportunity to enter input. (You could even add a message to `except` if you wanted to.)

This came up for me in [a little script I wrote](https://gist.github.com/adammichaelwood/6f2e02c4156c6cc27020ce179d2e8638) to [semi-automate a task](https://www.reddit.com/r/learnpython/comments/56r94z/what_python_program_have_you_created_to_make_your/d8m0hy6/?context=3). I needed to rate the quality of something I was looking at, and I was going for speed: Glance at the item, make a snap quality judgment, type a number.

But, of course, sometimes I typed the number incorrectly, hitting a letter instead of a number. This screwed things up latter, when I tried to order all my items by quality rating.

So, I cast the input to an integer inside the `try` block, and used the `while` loop to repeat until the `quality` rating was assigned.

```python
while 'quality' not in lnk:
    try:
        lnk['quality'] = int(input("Quality (0-9): "))
    except:
        continue
```

This approach could be expanded for more complicated types of validation, and messages to the user could be added. I just wanted a quick way to deal with my fat fingers.
