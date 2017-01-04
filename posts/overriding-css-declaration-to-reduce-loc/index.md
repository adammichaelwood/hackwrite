<!--
.. title: Overriding CSS/LESS Declaration to Reduce One LOC
.. slug: overriding-css-declaration-to-reduce-loc
.. date: 2017-01-04 05:50:39 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

While working on the theme for [this site](http://hackwrite.com), I was referencing [Markdown CSS](http://mrcoles.com/demo/markdown-css/), which makes HTML look like Markdown. (h/t [@ericholscher](https://twitter.com/ericholscher))

I [ran across an interesting (let's call it a) pattern](https://github.com/mrcoles/markdown-css/blob/master/markdown.less).

```less
h2:before,
h3:before,
h4:before,
h5:before,
h6:before {
    content: "## ";
    display: inline;
}
h3:before {
    content: "### ";
}
h4:before {
    content: "#### ";
}
h5:before {
    content: "##### ";
}
h6:before {
    content: "###### ";
}

```

The `content` for all five subheadings is first set to `## `, and then re-defined individually.

This saves, as far as I can figure out, one line of code. (Well, two lines if you count the closing curly brace.)

```less
h2:before,
h3:before,
h4:before,
h5:before,
h6:before {
    display: inline;
}
h2:before {
    content: "## ";
}
h3:before {
    content: "### ";
}
h4:before {
    content: "#### ";
}
h5:before {
    content: "##### ";
}
h6:before {
    content: "###### ";
}

```
The second way --- one extra line of verbosity --- strikes me as more readable, easier to understand immediately.

But the first way isn't _really_ obscure, just a touch clever. It doesn't impede readability so much as provide a little brain hiccup. If I weren't writing about it, it would have cost me nothing more than a brief moment.

Which makes me wonder. We generally place a premium on code readability. "Don't be clever" is common --- and good --- advice. But if code is poetry (or, at least, art), maybe these little flourishes --- when they don't impede readability, really --- add to the beauty of the code.
