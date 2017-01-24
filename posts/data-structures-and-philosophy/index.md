<!--
.. title: Data Structures and Philosophy
.. slug: data-structures-and-philosophy
.. date: 2017-01-06 07:26:34 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

Sometimes bad programming is just bad programming: people write sloppy code, people don't know how things are supposed to work, people forget that binary math is weird sometimes.

But often, bad programming is a result of bad philosophy - a fundamental misunderstanding of how meaning is made, or thought works, or how the world is structured. Sometimes the fault is a little less radical, tied to ignorance of some domain-specific facts, but often it's just plain bad philosophy.

<!-- TEASER_END -->

And nowhere is bad philosophy more on display than in poorly designed data models. Most [database 'antipatterns'](http://www.amazon.com/gp/product/B00A376BB2/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00A376BB2&linkCode=as2&tag=musforsun-20) are philosophical in nature.

This is, I think, not well understood by the majority of programmers and project managers. Even most engineers (read: technicians) who do things the right way can't always explain the philosophical underpinnings of the right way. This situation is analogous to high school students who know how to use the quadratic formula, but have no idea why it's meaningful. But while most of those bored teenagers move blissfully away from mathematics without doing anyone any serious harm, programmers without a sense of good philosophy (along with plenty of [theology and geometry](http://www.amazon.com/gp/product/0517122707/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0517122707&linkCode=as2&tag=musforsun-20)) move from project to project, wreaking havoc on database after database without any understanding of why things keep breaking. This situation is, of course, compounded by project managers, executives, and [pointy-haired bosses](http://www.amazon.com/gp/product/B007O8101E/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B007O8101E&linkCode=as2&tag=musforsun-20) of all stripes who don't rise to the level of software technician, and so don't even know what the right way is, let alone understand why there has to be a right way in the first place.

## The Canonical Example: How Old Are You?

I assume you are aware that the correct piece of information to store about a person is not their age, but their birthday. Other than the fact that this is painfully obvious to anyone who thinks about it for more than a moment, what might we offer as a philosophical explanation of the right way, and how can we understand why so many people take the wrong path?

If we are forced to "show our work," there are at least two routes by which one can arrive at the "store birthdays, not ages."

### Understanding of Human Thought

The more obvious, and slightly less interesting, of the two routes involves an understanding of what a person does when asked the question, "How old are you?" or "How old is Socrates?"

(Socrates is, of course, either the interviewee's child or pet.)

Typically, we do not walk around with the answer to this question readily available. Rather, we quickly calculate it:

"Let's see, I was born in 1982 and... what year is it? Oh right, so I'm... 34, I guess? Yeah - 34. I'll be 35 in July."

By working backwards from "how do I figure it out" we can arrive at "how should it be known."

### God's Knowledge: Thomistic Data Structures

We can do the inverse, work forwards from the more fundamental question --- how is a thing known?

Your database is supposed to know everything, and always be right. But facts change. How can this be handled?!

Medieval philosophers had a similar, but much more fundamental question:
God knows everything, and is always right. Facts change. **But God cannot change.** How can God know about things if God doesn't change, but things do?

> **Whether the knowledge of God is variable?**
>
> Objection 1:  
> It seems that the knowledge of God is variable. For knowledge is related to what is knowable. But whatever imports relation to the creature is applied to God from time, and varies according to the variation of creatures. Therefore the knowledge of God is variable according to the variation of creatures.
>
> --- [Thomas Aquinas, Summa Theologica, Pars Prima - Question 14, Article 15](http://home.newadvent.org/summa/1014.htm#article15)

This might seem silly, but it was a big deal at the time: If God's knowledge is variable, than God is variable. But God *is not* variable --- God is Simple, and One. The whole edifice of belief might crumble if we imagine a God who just changes willy-nilly. (Not unlike a computer system that crashes from too many logical contradictions and inconsistencies.)

Moreover, like the issue of storing birthdays or ages, the question only seems silly now because an answer was provided which is so obvious and clear that once you have grokked it, you will wonder why you didn't think of it yourself.

(The following is Aquinas' reply to a later objection, but it is particularly relevant here.)

> The ancient Nominalists said that it was the same thing to say "Christ is born" and "will be born" and "was born"; because the same thing is signified by these three--viz. the nativity of Christ. Therefore it follows, they said, that whatever God knew, He knows; because now He knows that Christ is born, which means the same thing as that Christ will be born. This opinion, however, is false; both because the diversity in the parts of a sentence causes a diversity of enunciations; and because it would follow that a proposition which is true once would be always true; which is contrary to what the Philosopher lays down (Categor. iii) when he says that this sentence, "Socrates sits," is true when he is sitting, and false when he rises up. Therefore, it must be conceded that this proposition is not true, "Whatever God knew He knows," if referred to enunciable propositions. But because of this, it does not follow that the knowledge of God is variable. For as it is without variation in the divine knowledge that God knows one and the same thing sometime to be, and sometime not to be, so it is without variation in the divine knowledge that God knows an enunciable proposition is sometime true, and sometime false. The knowledge of God, however, would be variable if He knew enunciable things by way of enunciation, by composition and division, as occurs in our intellect. Hence our knowledge varies either as regards truth and falsity, for example, if when either as regards truth and falsity, for example, if when a thing suffers change we retained the same opinion about it; or as regards diverse opinions, as if we first thought that anyone was sitting, and afterwards thought that he was not sitting; neither of which can be in God.

Aquinas is explaining that some thing which is only true at a point in time is not known by God by way of the kind of knowledge expressed in present-tense statements, like "Socrates is sitting."

This is precisely analogous to our database, where enunciating the individual facts "today I am 34; tomorrow I will be 35" is not proper to the way a database knows things.

### Data Persistence vs. Application Layer

Here, I think we have an analogy to the separation of concerns between a *Single Source of Truth* database and the application layer. The database doesn't "know" things by way of enunciation --- it simply knows things. It is up to the (human?) logic of the application layer to enunciate that knowledge for human consumption.

### Imperfect Analogies

Of course this is an imperfect analogy, since `INSERT` and `DELETE` exist. (That is, the contents of the database change.)

So our database is in no way omniscient (unless you work for Google), but there is a benefit to patterning knowledge using the highest form of rational thinking possible. With the birthday example, we can look to a Divine Precedent for our data model.

(One can be an atheist or agnostic and still benefit from this analogy by asking the question as a hypothetical: How *would* an omniscient, unmoving God know things.)

As a side note --- having this Divine Precedent probably explains my aesthetic revulsion at [NoSQL's propensity to float data integrity concerns into the application layer](http://blog.mlab.com/2012/08/why-is-mongodb-wildly-popular/#comment-353). (I'm not sure if this means that NoSQL people are Godless heathens or just [process theologians](https://en.wikipedia.org/wiki/Process_theology).)

### Models of Knowledge

The point is that philosophy, or at least philosophical thinking, can inform system design. The application of epistemology (how we know things) should be of particular interest to the design of knowledge systems.

A simple example is choice of database. Instead of following the New Hotness (or the "I've always done it this way"), what if we had an epistemological approach to selecting a particular database engine? What if, before asking "how this should information be stored?" we asked "How is this knowledge known?"

Sometime, the knowledge will be known in an Aristotelian (or Medieval Scholastic) way, in which case traditional SQL (or [something even more on the nose](http://www.sciencedirect.com/science/article/pii/S0747717189800306)) might be the right approach. Other times, we'll have to look to human reason. Other times, some other way of knowing and organizing the world. (So maybe those Mongo people are on to *something*...)
