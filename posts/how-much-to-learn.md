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

### Plaintext and Code Editors

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

#### Other Helpful Languages

Python is not the only good utility language for this sort of work. Bash is also very helpful, as I mentioned earlier. It's also not hard to learn, so the ROI is pretty high.

##### What about Ruby or JavaScript?

Ruby is the language behind Jekyll, the most popular static site generator and also Ruby on Rails, the most popular rapid web application development framework. [Ruby definitely has facility as a local utility language](https://smthngsmwhr.wordpress.com/2013/01/01/gentle-introduction-to-routine-tasks-automation-with-ruby/), but I don't know anyone who uses it that way who isn't also a Ruby developer generally. I'm trying to focus on dev skills for non-devs.

JavaScript (or, more specifically, Node.js) can also be used for this kind of work, but there is a much shorter history of it, so the tools are not as settled. If you already know JS well, then by all means use it. But if you're looking for a local utility language to learn, I wouldn't start here.


##### What about Perl?

Perl used to hold the place Python has assumed, as the "standard" utility and scripting language. I'm not sure there's a lot of need for tech writers to know it (I don't), but I'd feel remiss not mentioning it.

## Domain Knowledge

Every tech writer needs to know different things in order to understand the technology they are writing about. So, the following is highly conditional and probably not that helpful for tech writers already deep into a particular field.

This is intended as a general overview for people trying to get into the field or make a change.

### Languages

I'm really of the opinion that for most tech writers --- even those writing developer docs --- the amount of target-language skill required is low, and can be acquired for most languages in a week or so.

Once you've acquired basic programming skill in one language, *most* other languages are relatively similar. You need a quick primer on the syntax, how typical things are done (loops, conditionals, function definitions, etc.), and anything unusual or weird about the language. Anything else you need to know you can probably Google or ask someone when you encounter. ("What's this `lambda` thing?")

That being said, there are a handful of languages that are especially helpful. If you're interested in expanding your knowledge of languages (and you've already got a good handle on Python) you might look into these.

 - Java --- Java is ubiquitous in large enterprise organizations (and startups founded by people who used to work for them). Though [Python and JavaScript have both surpassed Java on some measures of popularity](https://github.com/emmanuel-keller/github-language-statistics/blob/master/README.md), there are still [way more tech writer job openings for people who know Java](https://www.indeed.com/jobtrends/q-%22technical-writer%22-java-q-%22technical-writer%22-javascript-q-%22technical-writer%22-C++-q-%22technical-writer%22-python.html) than other languages. No doubt this is because big enterprise software companies using Java are more likely to hire a technical writer than smaller companies that might use "cooler" languages.
    - Another reason to learn Java in particular is that it is the native language for Android apps. There's a lot of work available documenting mobile SDKs for cloud-based utilities. Knowing (at least a bit of) Java is a requirement for that.
    - If you're interested in mobile SDK work, also get familiar with Objective C and Swift, which are both used for iOS development. Someone with decent facility in those three languages could carve out a nice niche working on mobile developer docs.
 - JavaScript is just freaking everywhere. Every web application that is complicated enough to need a tech writer is going to have at least some JavaScript. That doesn't mean you have to know it to work on it, but it can't hurt. (And having it on your resume implicitly tells hiring managers that you understand web technology.)

I could go on and on --- this language is popular in this industry, that language gets a lot of use for this other kind of work. That probably wouldn't be helpful.

If you're writing developer docs for a library, SDK, or language API, the most important language to know (if you need to know one at all) is whatever language they are using to build the thing you are currently documenting. Trying to learn languages in the abstract, in case you might need them as a tech writer, is probably not the best use of your time.

If you just want to have a better sense of programming in general, work on Python because you'll find it useful as a tool in its own right. If you have your heart set on a particular area or specialization (mobile, web, machine learning, etc.) find out what languages and technologies are popular there.

### Systems and Architecture

Perhaps more important than understanding in particular language is understanding how systems work and communicate with each other. As always, my view is particular, but --- I've had dozens of interviews over the last year and nearly all of them required a basic understanding of Service Oriented Architecture (whether or not they called it that) and RESTful web APIs.

It seems that a large percentage of people hiring tech writers need them to understand how the modern web works, how web and mobile applications communicate with servers, and how multiple system components connect to each other and to third party systems.

## These are not the only skills

It's important to remember that developer skills (or technical skills more broadly) are not the only skills needed for technical writers. We also need to be good writers and teachers. Project management skills are also extremely helpful. And don't forget marketing copywriting --- someone is eventually going to ask you to do that if they haven't already.
