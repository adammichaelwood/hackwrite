<!--
.. title: The Real Reason I Love Static Site Generators
.. slug: real-reason-i-love-static-site-generators
.. date: 2017-01-25 06:07:37 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

There's a lot to like about [static site generators](https://www.staticgen.com/) like [Jekyll](http://jekyllrb.com/), [Nikola](https://getnikola.com/), and [Sphinx](http://www.sphinx-doc.org/).

 - Hosting is much simpler, and can usually be done for free.
 - Static sites are inherently more secure than dynamic ones.
 - Very fast page load times.
 - Authoring in a code editor that I have control over.
 - Markdown and reStructured Text are both faster to type than HTML or rich content in a WYSIWYG editor.
 - Version control.
 - The ability to manage the build and deploy process like code.

There are probably more benefits I'm not thinking of at the moment. When I first started using Jekyll, my main motivation was wanting to simplify hosting and exert control over authoring. I discovered the other benefits along the way, and they have really changed my professional life.

But I've realized there's one thing that has come to matter the most to me:

**Static sites revive and make real the notion of a document on the web.**

In database-backed CMSes, the pretty URL is a noble lie. Content is smeared around in a database and accessed through `?id=1234` parameters or internal query mechanisms. This is fine, and really the only way to handle massive amounts of content.

But the web was built to serve documents, not database results. In an age where content-as-data is on such hyperdrive that people think a [single-page app blog system](http://sennajs.com/examples/blog/) is a reasonable idea, it is calming to use a technology that works the way the web was always supposed to work.

And this has as much to do with the mental model as with the technology. (Maybe more.) The individual documents that make up a static site are handled *as documents* before being processed to HTML. If I want to change the content on some blog post, I edit a file on my local computer. I don't have to log in and use an application. It is transparent, and there's a direct relationship between a single file in my source and a single URI on my site. Now it feels like the URI actually identifies a *resource*, and is not just a cleverly-disguised search pattern.

I understand why we moved past the web of documents. But if you're producing documents, maybe it's the right model.
