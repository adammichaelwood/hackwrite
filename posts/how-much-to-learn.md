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
 - Lack of fear or anxiety, and the confidence to use Google or Stack Overflow to solve problems

It's great to know more, of course. Tools like `grep` can help you search code bases; understanding `awk` and other tools can help you with data munging and cleaning up text. Having some facility with bash scripting can help you automate various aspects of your job, making you happier and more productive.

But knowing these simple things --- and especially being confident in your ability to Google and figure stuff out --- will make everything else easier.

If you work in big enterprise organizations, you may also need to learn the Windows/DOS-prompt version of all this. (But, then, you'll also likely be using an integrated enterprise toolchain as well, so it might not matter.)

### Basic Web Dev

Having an understanding of how the web works in general and how browsers turn HTML, CSS, and JavaScript into a rendered page is really helpful. You don't need to get bogged down in all the frontend JS framework insanity --- focus on web fundamentals and core concepts.

 - I have found understanding how the web is/was "supposed" to work (that is, as a web of *documents*, [identified by URIs](https://www.w3.org/Provider/Style/URI.html), and transferred via HTTP) helps me conceptualize content organization better. It also helps me understand why so many things about web development are non-trivial.
 - Knowing (and caring) about "textual" HTML (all the inline elements) and their semantic meaning is helpful.
 - Knowing what makes for good (valid, clean) HTML, and understanding proper separation of concerns helps me evaluate the quality of my tooling and prevents future redesign and reorganization headaches.
 - Understanding 
 - Basic facility with CSS (LESS, SASS) gives me the ability to
 -

### plaintext, code editors


### git



### Python



## Domain Knowledge

### Languages

 - Java
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
