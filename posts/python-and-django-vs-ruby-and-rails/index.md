<!--
.. title: Python and Django vs. Ruby and Rails
.. slug: python-and-django-vs-ruby-and-rails
.. date: 2016-02-10 15:22:39 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

_tl;dr - Python._

I can't even begin to count how many forum posts and deleted Stack Overflow questions there are boiling down to some version of _Python vs. Ruby_ or, more specifically, _Django vs. Rails_. Google (as of right now) has [NINE POINT EIGHT MILLION](https://en.wiktionary.org/wiki/buttload) results for ["Python vs. Ruby"](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#safe=off&q=python+vs.+ruby), which is basically insane.

Unfortunately many of the articles and posts answering the question don't actually answer it. They provide some generalizations about each, talk about some of the differences, and say that it's up to you.

__Have an opinion, you soulless producers of Search Engine fodder!__

I have recently spent a bunch of time trying to answer this question as I attempt to transition out of the wasteland of PHP and WordPress. I have a particular app I'm trying to build, and it is just the sort of content-driven, database-backed, CRUD app that both Ruby on Rails and Django are perfectly suited for. (And that WordPress <del>idiots</del> evangelists would claim would be just perfect as a custom plugin, except that's a _terrible idea_.)

So here is the definitive answer...

Use Python, and Django, if you care about any of the following:

 - Schema design
 - Data analytics
 - Programming best practices
 - Learning how to actually program
 - Database integrity

Also, use Python, and (if needed) Django, if you are working in any of the following domains:

 - Math
 - Science
 - Music
 - Signal Processing
 - AI
 - Analytics (which is really math)
 - Statistics (more math)
 - Academia (most likely math)
 - Engineering
 - Remotely serious gaming
 - Security
 - Networking

Use Ruby if you want to use Rails. And use Rails if you care about:

 - Getting a <del>stupid</del> <ins>clever</ins> social media app MVP up and running as soon as possible

<span title="Actually it is.">This isn't really a judgement on the quality of either language.</span> <span title="But I will anyway.">I am not in a position to say which language is intrinsically better suited for either task.</span> (And neither are most of the people blogging on this subject.)

What matters in either case is the community of people who have gravitated to each language and (therefore) what kinds of tools are available for each. Also, the focus of the two disparate communities has impacted the design of Django and Rails in different ways.

So, who uses Python? Nerds, mostly. Sciencey people. Math people. People who care about data. People who know three or four or a dozen other programming languages. People who prefer PostgreSQL to MongoDB, because they care about things like data integrity. People who actually understand what polymorphism is. People who want to teach computers to write music or recognize handwriting.

Because these are the kind of people who have gotten into Python, the tools exist in Python to do that kind of work. And because those tools exist, more and more of those kinds of people have gravitated to the language, generating a positive feedback loop and a network effect of geeky awesomeness.

And who uses Ruby? People who want to get rich building the next Twitter.

Compare the contents of Python's [package index](https://pypi.python.org/pypi?%3Aaction=browse) against the [Ruby gems library](https://rubygems.org/gems).

<span title="Yes it is.">This is not a moral judgement.</span> I would love to get rich building the next Twitter. But since a deep understanding of either language, either platform, can be a ticket to a lucrative career, I think it makes more sense to focus on a language and community that has more interesting possibilities. (And it's not like you _can't_ build the next Twitter on Django.)

These differences in focus and culture manifest in non-trivial differences between Django and Rails. One difference in particular sealed the deal for me in selecting Django (and, by extension, Python) for my next project, even though I was already leaning in that direction.

I am working on a library-catalog-like index of church music --- everything from Gregorian Chant to Christian Pop, including tons of information about liturgy (rituals), history, legislation and a hundred other things you wouldn't understand unless you really cared about church music. The corpus is unbelievable large and just wrapping one's head around how the data should be organized is difficult.

One tiny, nearly non-trivial example of one of the data modeling problems: A hymn consists of a tune and a text. A tune can have multiple harmonizations, but it is possible that one is "canonical." Texts might be paired with different tunes over time (for example, there are at least [two](https://www.youtube.com/watch?v=MTPyKwqUUgc) [different](https://www.youtube.com/watch?v=Lj2fwME46GM) well-known tunes for the Christmas Hymn _O Little Town of Bethlehem_.) And the tunes often end up paired to different texts over time. Sometimes these pairings are "canonical" or widely recognized, while other times they are one-off pairings that appear only in a single book or hymnal. And sometimes a tune and text simply cannot be separated, because they were written together and form a singular unit. And sometimes that happens, but someone else still comes behind and writes a new tune for the text.

Another issue... authors of texts and tunes. Most texts are written by individual people. But some are written by groups, like a worship committee or church council. Others are traditional or anonymous. Some are attributed to a particular person, but he or she probably didn't actually write it. Some attributions are apocryphal, others are doubtful but possible, some fraudulent or spurious, and so on.

And the possibilities for relationships between authors and texts, is the same as for composers and tunes --- so <span title="Yes, it should be.">shouldn't that be abstracted?</span> And therefore <span title="Yes, again.">shouldn't tunes and texts (and books and arrangements and sermons and pamphlets) be abstracted to something like `Works`</span>? And since people and groups can both be contributors, <span title="Still yes.">shouldn't they be abstracted into something like `Entities`</span>?

Trying to capture all of these different relationships, and the meta-data under the relationships (_What type of tune-text pairing?_ _What degree of certainty does an attribution have?_) is a big undertaking. To get it right, I need a pretty high degree of control over the database schema.

That _could_ mean writing SQL from scratch and using a framework that doesn't have a built-in abstraction layer, which would be great if I wanted to go completely insane.

Or it _could_ mean basically hacking Ruby on Rails, relying on a [poorly supported plugin](https://github.com/hzamani/acts_as_relation) or [reading way too much](https://dan.chak.org/enterprise-rails/chapter-10-multiple-table-inheritance/) to accomplish multi-table inheritance.

Or I could just use Django, which [natively and simply supports multi-table inheritance](https://docs.djangoproject.com/en/1.9/topics/db/models/#multi-table-inheritance), and provides pretty real polymorphism with a [well-documented, actively developed plugin](https://django-polymorphic.readthedocs.org/en/latest/quickstart.html).

(And if you want to jump all over me about performance issues with concrete inheritance and left joins, _fuck off_. I will take a data model that reflects reality over cargo-cult performance superstitions any day. Besides, I'm not building 911 dispatch or a global e-commerce site. I'm indexing hymnals for church musicians.)

This one example --- how each framework deals with model inheritance --- is indicative of a larger trend I found when trying to mockup various pieces of my system in both platforms: Django gives you more control over the data model. There's still an abstraction layer, but it was written by people who care about schema --- not people who are trying to hide it from you. Since I care about data models also (maybe you don't), this is a killer feature.

It doesn't hurt that if I want to do anything remotely interesting with all the music data I plan to <del>[steal](http://scrapy.org/)</del> <ins>collect</ins>, I'll want to do that sort of thing in Python.

Analyze all the hymn tunes written in 17th century Germany in order to programatically create new tunes in the same style?

Yeah, I could totally do that in Ruby.

So... bottom line: If you are learning to code because you want to be an entrepreneur, <span title="Or, better yet, hire a developer.">learn Ruby on Rails</span>. If you are learning to code because you want to do unique and interesting things as a developer, learn Python.
