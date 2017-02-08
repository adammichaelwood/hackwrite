<!--
.. title: Verbiage
.. slug: verbiage
.. date: 2017-02-08 08:26:57 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

I hate the word _verbiage_.

First, we need to deal with the fact that it is the *wrong word*. Most of the time, when people say *verbiage*, they really mean *verbage* --- that is, the wording. *Verbiage*, properly, means excessive wordiness, not the specifics of word choice.

But this isn't what I hate about it. I would hate it just as much if it meant precisely what every one uses it to mean. My problem is with the idea itself. I hate what people are saying when they say *verbiage*.

Every time I have ever heard the word *verbiage*, the person has been talking about *the precise way that something is worded*. The context is always about improving something.

 - *Can you make this more clear by fixing up the verbiage?*
 - *After you get the first draft of the design done, ask Adam to help you clean up the verbiage.*
 - *Maybe we can change the verbiage on this form to make it more user friendly.*

Without fail, a request to *work on the verbiage* is symptomatic of a deeply flawed design and engineering process. We got to this point because people were [decorating, not designing](http://hackwrite.com/posts/designing-vs-decorating/), and now we are going to try to get out of it by changing the words the user sees.

This causes more problems, of course.

The reason the words aren't clear and precise in the UI is that the mental model developed by the engineering team is either confused or just plain wrong. In order to make the application easy to use, our Verbiage Specialist has to overlay a new mental model --- often, the one that should have been used in the first place. This new mental model, and the collection of verbages that go with it, will be imprecise and incomplete because the Verbiage Engineering Team can't tell the developers to restructure the database and rename all the application's variables. The result is that the UI becomes temporarily easier to use, but at the cost of taking on additional Verbiage Debt. Somewhere deep in an internal wiki or Confluence page is a OVM (Object-Verbiage Mapper) glossary telling you that `dev:event_property => user:"Device Status"`. But nobody reads internal wiki pages, so the problem just gets worse.

You cannot fix an application by redecorating the UI. Fixing the *verbiage* is just redecorating + technical debt. If you find yourself *fixing up the verbiage*, the problems are much deeper.

So how do you avoid Verbiage Debt?

Stop treating writers as Verbiage Technicians and think of them as Verbiage Architects. (I'm sure there's a [good word for this](http://www.uxbooth.com/articles/what-is-ux-writing/) already.) Your Verbiage Team, along with your Pictures of Things Engineers, need to be involved **from the beginning** with the design of your application, and they need to be fully-fledged members of the engineering team --- not hired hands, consultants, helpers, or otherwise after-the-facters.

Building software has more to do with creating mental models than it does with writing code. Humans create mental models in language and pictures.

Your language and pictures people are as important as your coders.
