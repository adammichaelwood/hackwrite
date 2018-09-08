<!--
.. title: Emacs for Technical Writing
.. slug: emacs-for-technical-writing
.. date: 2017-08-22 08:29:08 UTC-07:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
-->

I've been thinking about switching to Emacs for a long time. I had a sense that it would fit my personality, and that the ability to automate tasks and customize the environment would boost productivity. But it always seemed a bit out of reach. I thought I would probably need to take several weeks to really learn it, and I never seem to have that kind of time.

But I recently made the switch, and am now using Emacs as my primary editor and terminal.

This is my fourth editor. When I first started writing code and using plaintext for prose, I used Notepad++. When I had enough of an idea about what I wanted in an editor, I switched to Sublime. Then about a year or so ago I switched to Atom because it is Free and Open, and provided a very similar experience to Sublime.

But Emacs was always there, in the back of my mind. Finally, two things shifted the balance for me:

 - better reStructured text support in Emacs (specificially, proper syntax highlighting)
 - the dawning realization of Atom's (well, Electron's) performance problems

There are a couple Atom plugins for highlighting ReST, but neither one works right 100% of the time. I would write some oddball directive and all of the sudden half the document was grey or red. Then I'd open a new `.rst` doc and try the samwe thing and it would be fine. Or portions simply wouldn't highlight at all. I found it maddening. I thought about learning enough about the Atom plugin development and syntax highlighting to try to fix the problem myself, but that seemed like a bad use of my time and learning bandwidth.

Looking around for editors with good ReST support, I found Emacs listed. I use ReST and Sphinx every day now, and I'm currently on my fourth Sphinx-using writing gig. *Okay... I guess I'll finally take the time.*

## Benefits of Emacs

I've quickly discovered that Emacs is:

 - not *that hard* to get going with
 - enormously helpful

Here are a few of the benefits I have noticed in just the first couple weeks, while barely scratching the surface.

### Less Pain

I have moderate-to-severe pain in my back, around my right shoulder blade. This seems to be largely caused by my constant trackpadding. Moving to a keyboard-centric interface has greatly reduced my pain. (I suspect that if I switch to a split keyboard and maybe get a foot pedal I can make more progress on this front. I also think I should take the time to learn to type properly.)

It is, of course, possible to use a keyboard to navigate in Atom and most other editors. I could have installed Emacs keybinding for Atom. But it was too easy not too. Emacs served a forcing function because mouse navigating simply isn't possible. (I am even running Emacs in my terminal, rather than as a standalone app, so I can't even mouse on the menu.)

### Less Distraction

You can run a shell inside Emacs. Since I can switch from the file I'm working on to the shell inside the same window, I don't need to swipe over to another screen. This 