<!--
.. title: How much to learn?
.. slug: how-much-to-learn
.. date: 2017-01-11 05:56:51 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

I recently wrote that you don't need to attain a high-level of coding skill for learning to code to be useful. A technical writer can see substantial ROI from just learning [enough to be dangerous](http://hackwrite.com/posts/enough-to-be-dangerous/).

Which raises (not begs!) the question: How much *is* enough? What topics should tech writers know? And how well should we know them?

To start answering that question, I'd like to expand what we mean by "learn to code" or "knowing how to code." Let's expand that to "developer skills" in general. Too much focus on *coding* overlooks the other highly useful things that developers know and do that tech writers can benefit from.

Further, we need to distinguish between two (overlapping) sets of developer skills:

 - skills that you may directly use as a tech writer
 - skills that help you understand the technology you write about

For example, I use Python a lot as a writer. I can hack together little scripts to help me automate things. This blog is built on Nikola, and I use Sphinx a lot for building documentation --- both built in Python, and I have just enough Python skill to debug problems and add very minor functionality when needed. But I've never written documentation about something written in Python.

On the other hand, I have never once written a line of Java. I hardly know anything about the language, its ecosystem, or common tooling. But I've stared at enough of it that *in context* I can usually dumb out the sorts of things a tech writer might need to know about a web API written in Java.

Endless discussion board and subreddit questions about "what language should I learn" usually ignore this distinction. But it's a good idea to separate dev skills which are actually a subset of tech writer skills, and dev skills which are actually domain-knowledge about your subject matter.

## Tech Writing Dev Skills

These are the skills that I have found most useful day to day. Additionally, these skills have made me much more employable. Since I started focusing on these skills and highlighting them in my resume, I get a lot more phone calls and interviews.

I know a lot of really good tech writers don't have these particular skills, but to me --- the following are *essential skills*.


### Comfortable at the Terminal

Tech writers should be *comfortable* at a Unix (GNU/Linux, Mac) Bash terminal.

 - Basic facility with navigation and file manipulation commands (`cd`, `mkdir`, `rm`, `mv`)
 - General understanding of how commands work --- enough to quickly learn and use other tools you may need (`git`, `curl`, etc.)
 - Know how to open, edit, and close a file with `vi` (you don't have to *really know* Vim or use it for authoring; just know enough to be able to edit files on unfamiliar machines --- `vi` is everywhere)
 - Basic facility with Bash scripting --- just enough that if you find yourself typing the same sequence of commands over and over, you know how turn that into a simple script
 - Lack of fear or anxiety, and the confidence to use Google or Stack Overflow to solve problems

It's great to know more, of course. Tools like `grep` can help you search code bases; understanding `awk` and other tools can help you with data munging and cleaning up text.

But knowing these simple things --- and especially being confident in your ability to Google and figure stuff out --- will make everything else easier.

If you work in big enterprise organizations, you may also need to learn the Windows/DOS-prompt version of all this. (But, then, you'll also likely be using an integrated enterprise toolchain as well, so it might not matter.)

### Basic Web Dev

Having an understanding of how the web works in general and how browsers turn HTML, CSS, and JavaScript into a rendered page is really helpful. You don't need to get bogged down in all the [frontend JS framework insanity](https://hackernoon.com/how-it-feels-to-learn-javascript-in-2016-d3a717dd577f#.uwcjmcwnt) --- focus on web fundamentals and core concepts.

 - I have found understanding how the web is/was "supposed" to work (that is, as a web of *documents*, [identified by URIs](https://www.w3.org/Provider/Style/URI.html), and transferred via HTTP) helps me conceptualize content organization better. It also helps me understand why so many things about web development are non-trivial.
 - Knowing (and caring) about "textual" HTML (all the inline elements) and their semantic meaning is helpful.
 - Knowing what makes for good (valid, clean) HTML, and understanding proper separation of concerns helps me evaluate the quality of my tooling and prevents future redesign and reorganization headaches.
 - Those last three items --- and a general focus on web standards --- [give you a big head start in understanding web accessibility needs](https://twitter.com/sarah_edo/status/780780145086988289) which too few tech writers care about, but we all should.
 - Basic facility with CSS (LESS, SASS) gives me the ability to solve my own design problems. (For example, styling help text to mimic the UI being written about.)

### plaintext, code editors

 - Being comfortable away from WYSIWYG editors and word processors is a requirement for most of the other tools I use.
 - Fluency in [Markdown](http://kirkstrobeck.github.io/whatismarkdown.com/) has become nearly mandatory, since developers really like it and [Github supports it by default](https://guides.github.com/features/mastering-markdown/).
 - [reStructured Text](http://docutils.sourceforge.net/rst.html) is a [better tool than Markdown for documentation](http://ericholscher.com/blog/2016/mar/15/dont-use-markdown-for-technical-docs/). It really helps to know rST and [Sphinx](http://www.sphinx-doc.org/en/1.5.1/), which is a static site generator designed for documentation. Like many static site generators, Sphinx is mostly run from the command line (another reason for you to get comfortable at a terminal).

If you're going to be writing Markdown, rSt, or another plain text format, you'll need to find an editor you like. I use [Atom](http://atom.io) myself, but [Sublime Text](https://www.sublimetext.com/3), [Notepad++](https://notepad-plus-plus.org/), and [Vim](https://en.wikipedia.org/wiki/Vim_(text_editor) are also popular among writers. (And there are many others.)

One of the great things about plaintext formats is that, instead of everyone being forced to use the same software (Word or Framemaker, for example), everyone can use their own preferred editor. Developers have been able to do this for a long time, and now writers can enjoy the freedom to customize their workspace as they see fit.

### git and Github

Git is a distributed version control system. Even though [no one really understands it](https://xkcd.com/1597/), it's become standard for many developers and development teams. If you're going to [treat docs like code](http://justwriteclick.com/2015/05/19/treat-docs-like-code-doc-bugs-and-issues/) (which you should), some basic git skills are really helpful.

 - basic git commands: `add`, `commit`, `pull`, `push`, `merge`, `clone`
 - general understanding of the distributed model, remotes, and common work flow with Github (fork, clone down, edit, commit, push, pull request)
 - how to use Github pages and Jekyll (Developers tend to like these, so more and more startups are using them for docs --- if you're the first writer to show up, you be dealing with existing Jekyll docs written by the developers.)

Git is complicated, and can [cause particular problems for writers](http://hackwrite.com/posts/github-pages-problem/). Perhaps the most important skill in git is the ability to keep calm, Google your problem, and knowing when to ask for help before you make things worse.


### Python

This is my favorite developer skill because it is *actually coding*, and makes me feel (I think?) like a real developer.

It is really helpful to be able to write local scripts to automate your own tasks as a writer, and --- if you're treating docs like code --- for automating the building, testing, and deployment of your docs. You could do this sort of thing in several languages (Perl, Ruby, Bash, JavaScript), but Python is probably the best choice. It's easy to learn, you can do a lot with it early on, and the [PyPi](https://pypi.python.org/pypi) ecosystem provides pretty much every tool you are likely to need for basic scripting and automating purposes. In a number of fields (science, math, engineering, digital humanities) it has become the default language for non-developers writing code to get things done.

(I recommend [Automating the Boring Stuff](http://amzn.to/2jV13iW) as a good intro to Python and what you can accomplish with it.)

## Domain Knowledge

Every tech writer needs to know different things in order to understand the technology they are writing about. So, the following is highly conditional and probably not that helpful for tech writers already deep into a particular field. But this might be a decent overview for people trying to get into the field or make a change.

### Languages

It's always hard to 

 - Java --- Java is ubiquitous in large enterprise organizations (and startups founded by people who used to work for them).
 - JavaScript
 - Objective C / Swift
 - Whatever they are doing where you work...

### System

 - Architecture
 - How things talk to each other

### Process

 - Agile
 - TDD, BDD, etc...
 - Devops, deployment, CI
