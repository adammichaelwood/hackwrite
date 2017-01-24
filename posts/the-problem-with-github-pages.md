<!--
.. title: The Problem with Github Pages
.. slug: github-pages-problem
.. date: 2017-01-10 05:50:37 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

I love Github Pages. I run this blog, my [personal blog](http://adammichaelwood.com), and my [music and liturgy blog](http://progressivesolemnity.org) on it. I used it to host [documentation for my most recent tech writing gig](http://docs.botcentral.ai).

For a single writer with moderate or better technical skills looking for a simple hosting solution, it's amazing. But, I've recently realized there's a problem with it that makes it ill-suited for multiple collaborators working on complicated documentation. (Or even, as I discovered, a single writer on more than one machine.)

<!-- TEASER_END -->

Let's review how Github pages works. You designate a particular branch or directory of a branch as the Github pages source. The source can either be an unbuilt Jekyll site source, plain markdown files, or a fully built static HTML (+CSS +JS) site. If it's plain markdown or Jekyll, Github builds and deploys for you. If it's a built HTML site, Github just serves those files.

If you let Github build your site automatically from Jekyll or plain markdown files, everything works great. The Open Source collaboration model applies as well to content as it does to code. Better, perhaps, because adding or modifying content doesn't cause conflicts and run-time errors. But if you need to run a build yourself --- because you're using another generator like [Sphinx](http://www.sphinx-doc.org/en/1.5.1/), [Nikola](https://getnikola.com/), or [Mkdocs](http://www.mkdocs.org/) --- or because you have some [Jekyll plugins](https://jekyllrb.com/docs/plugins/) that aren't supported in Github --- you'll have problems once you add a second writer.

Suppose Addison and Bahati are two writers each working on their own piece of content in a Sphinx repo. This repo is set up to serve Github pages from a `/docs/` directory that they are supposed to build to. For the sake of simplicity, let's pretend nothing they do would conflict, even a little bit. They both fork, clone down, and get to work.

In the course of their work, they have each built locally a handful of times and made one or two commits. Now, the end of the day, they are both ready to do a PR. Addison pulls down from upstream (like ya do), runs the build, commits, pushes, and PRs. Addison also has commit privileges, and goes ahead and accepts the PR right away. No problem.

A few minutes later, Bahati --- whose work doesn't conflict, even a little bit --- finishes up and is ready to do the same. Bahati starts by pulling down from upstream (like ya do) and gets a merge conflict.

![Screen shot of merge conflict error message.](/img/git-merge-conflict.png)

Since Bahati [understands git about as well as the average developer](https://xkcd.com/1597/), this is a problem.

![Merge tool not configured](/img/merge-tool-not-configured.png)

What went wrong?

The problem is that a built HTML site --- whether it's Jekyll or Sphinx or anything else --- has cross references on every page to nearly every other page. Tables of contents, menus, internal links. This is the case on "regular" sites and blogs, but is even more true with technical documentation, where there might be an entire sitemap on the side bar of every page.

This means that even though Addison and Bahati each only added a single file, and their work didn't conflict (even a little bit), there is no way to merge back together their built output.

And here's the problem with Github pages for complex documentation (that is, anything that needs to be built outside GH). **Output shouldn't be version controlled, only source files should be version controlled.**

## Solving the Problem

The worst solution, which might work for a very small team, is to use the `gh-pages` branch and workflow that attempts to ensure all builds to `gh-pages` happen in a very fast pull-build-push cycle. With a little scripting, a little luck, and lot of commit privileges, this will work. However, the more complicated the documentation is, the longer the pull-build-push process takes. Combined with a large team, the potential for conflicts grows.

The right solution is don't use Github pages. Don't attempt to keep built output files in version control. Keep your source files in git/Github, and setup a tool(chain) that builds, deploys, and hosts your documentation from Github to some other place. The other place could be [Read the Docs](https://readthedocs.org/), an [AWS server](https://aws.amazon.com/s3/), a [content delivery network](https://www.keycdn.com/support/static-site-hosting-with-a-cdn/), or pretty much anything. (But it probably should be Read the Docs. Just sayin'.)

## When to use Github Pages (and when not to)

Github pages is great if you have uncomplicated needs that are well served by a Jekyll site that is built automatically. (So... personal blogs.) Lots of people are using Jekyll for documentation, but [that isn't a good idea, really](http://ericholscher.com/blog/2016/mar/15/dont-use-markdown-for-technical-docs/).

You can also get away with hosting locally-built static sites on Github pages if you are the only author. (So... personal blogs.) This site, for example, is built locally from [Nikola](https://getnikola.com/) and hosted on Github pages. But even then, you can run into problems. I was switching back and forth between two computers and ran into difficulty.

![git error: updates rejected](/img/updates-rejected.png)

(Those other error messages above were also my own. 100% real.)

For anything more complicated --- developer or user documentation written by more than one person --- you should be using a tool like [Sphinx](http://www.sphinx-doc.org/en/1.5.1/), using git and Github for source control, and publishing from there to [some place designed for that sort of thing](https://readthedocs.org/).  
