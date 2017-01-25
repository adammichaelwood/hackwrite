<!--
.. title: File Names
.. slug: file-names
.. date: 2017-01-20 06:31:12 UTC-08:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
-->

> There are only two hard things in Computer Science: cache invalidation and naming things.  
> -- Phil Karlton

> I cannot help you with cache invalidation.  
> -- Adam Michael Wood

I recently saw a question about file names in the [Episcopal Communicators Facebook Group](https://www.facebook.com/groups/episcopalcommunicators/):

![Question about file names.](/img/filename-question.png)

> This is a question about filenames for websites.
>
> When we first developed our website, our consultant told me that when we put a file on there, it's important to give the file a date and a unique and descriptive name.
>
> While that works for some files, it doesn't for others. It caused me to end up with a lot of old files on my website.
>
> What I changed was that I stopped changing file names. So instead of mileage_rates_2016.pdf, I just call it mileage_rates.pdf. That way every link is correct, everywhere on the site.
>
> However, when we link to outside websites, like the wider church's site, we end up with obsolete links. Case in point: the Manual of Business Methods:
>
> We had full_manual_updated_09-30-2013.pdf.
>
> And now the link is full_manual_updated_012815_0.pdf
>
> Is there any need to give dates to files like this? It's important for the organization to archive old versions, but is there any need to have unique names so that websites like ours end up with older versions?

I summed a few file name best practices, but... I have *a lot* to say about this topic. File naming is one of those weird little things I have irrationally strong feelings about, and the ubiquity of bad file naming practices is a constant source of rage in my life.

<!-- TEASER_END -->

Also, people tend to just dash off a few rules about file names, without talking much about the underlying reasons. So I thought I would spend some time exploring how to think about file names.


## What is a file?

Our experience of using computers is mostly [a](http://www.sciencedirect.com/science/article/pii/S1570868308000463) [series](https://bytebaker.com/2008/12/04/metaphors-in-computer-science/) [of](http://www.cs.utexas.edu/users/EWD/ewd10xx/EWD1036.PDF) [metaphors](http://cargocollective.com/jamesfearon/Metaphors-Abstractions-Humans-and-Computers) for how we interact with physical objects. File is one of those metaphors --- we imagine a fistful of paper or a glossy photo print. When we send or receive a file, we imagine this physical object moving around. Even when we acknowledge that transferring files is really just copying them, we typically imagine analog photocopy machines. Then, sometimes, we imagine we're getting the *real computer answer* when we are told or acknowledge that a file is "a string of ones and zeroes," which isn't really accurate either.

We actually mean several different things with the word **file**.

Most of the time we mean the abstracted contents of the file. This works the same way we usually talk about a **book**. This summer, [my parish](http://www.allsoulsparish.org/) is trying to everyone to read the same book. That doesn't mean we are all literally going to hold the same physical object; it means we're all going to read (or listen to) the same words.

We usually mean **file** this way when we talk about revising or editing a file. If someone tells you they just *finished writing a book* and is now working with an editor, we don't say that the editor is now going to write a new book. Likewise, if someone emails you a file, and you edit it and email it back, you don't say, "attached is a new file, based on the one you sent me." You just say, "I've revised the file." (Sidenote: This is a terrible practice. Don't email revisions.)

We might mean a couple other (closely related) things when we say *file*:

 - The actual binary representation as it is stored on a disk. (The "ones and zeroes," manifested in a particular physical location.)
 - The abstract numerical value of the data. That is, the information that is loaded in memory, sent over the internet, and decoded by a program. There are many individual copies of this value when a file is in use or in transit.

Most of us don't really think about either of these meanings. We sometimes imagine we mean the first, when we talk about which "folder" a file is in. But [that is an abstraction](http://www.bilskiblog.com/blog/2013/09/the-processof-developing-software-typically-involves-the-use-of-abstractions-of-concrete-concepts-to-describe-the-operationsp.html). As a user, you don't deal with a file at the level of its physical storage.

As to the numerical value of the data itself, the only time I can think of where this is relevant to users is when comparing [file checksum hashes](https://en.wikipedia.org/wiki/Checksum). And how often do you do that?

I bring up these other underlying meanings of *file* because its important to think about which reality we are naming when we name a file. Everyone seems to know that we aren't naming a specific physical manifestation of data on a disk. But, contrary to those who think `_revised_Nov_2016` belongs in a file name, we also aren't naming the particular content at any given time. If we were, the proper name would be the checksum hash, and it would change every time you added or deleted a single character.

What we are naming and thinking about when we name and think about files is the underlying content --- its meaning to us.  Therefore the name should be meaningful to us *at precisely that level of abstraction*.

This means the file name is not a place for commentary like `revised`. It does not need a creation date or other metadata.

If it is important to track changes to a file over time, then it should be under version control. If the *creation date* is important an important thing for everyone to know, then it should be under version control. If those things aren't important, then there should be no need to put things like `revised` or `2016_11_03` into a file name.

## Uniqueness, File Names, and URIs/URLs

Arbitrary uniqueness tags like timestamps, `_(1)`, or ` -- copy` are not needed in file names, and are generally a sign of poor organization or poor thinking.  If they are not descriptions of the underlying, Platonic reality of the content, they shouldn't be in the file name.

If you have two documents with the same name in a single directory, and its *not* just because of bad version control, you need more explicit names, or more granular directories. Dating them is not going to help you remember later which one is which.

If you are thinking a file needs a name with uniqueness tags in order to ensure universal uniqueness, the information in that file would probably be better distributed as a web document (an HTML page) with a Uniform Resource Identifier (URI or informally, URL) that is guaranteed to be globally unique and [unchanging](https://www.w3.org/Provider/Style/URI.html), not to mention easier to read and universally accessible.

## When Dates Belong

File names should reflect the underlying Platonic reality of the content. Therefore, dates make sense if the content itself is related to a date. Blog posts, news items, photos, meeting notes, invoices, and a whole host of other types of documents should include date stamps in the title because the content is related to a particular date. Of course, it is the date of the content that matters, not the creation date of the file --- meeting notes should be dated to match the date of the meeting, not three days later when you typed them up.

Typically, if you have dates in a file name, you will end up with many files that have similar names differentiated only by the date. It makes sense to want to sort these easily by the date, so you need to name them in a way that makes that possible. Put the dates at the beginning or the end (pick one consistently) and use `YYYY-MM-DD` format. Use leading zeroes for single-digit days and months.

## Technical Concerns

File names are used in a wide variety of contexts, only some of which you will be able to predict at the time of naming a file. File names should work everywhere, for every user, every time. Therefore, a whole host of technical restrictions should be followed *even if you think they won't matter*. For example, some file systems have trouble with special (non-ASCII) characters in file names, and also URIs can only contain ASCII characters. Even if your system handles them just fine, you shouldn't presume that everyone else who might need to view or work with the file can do so easily. Spaces cause problems for file names when they become a part of a URI --- they get translated into the hard-to-read `%20` encoding. Since you don't know that a file will never be distributed via the web, avoiding spaces is a good idea. (Also, people who do their computing at a terminal or command line are extremely annoyed at file names with spaces.)

Mixed-case (upper and lower) can cause problems for naive search implementations, and also play havoc with uniqueness checks. So it makes sense to uniformly use lowercase. Underscores are [bad word separators](https://blog.codinghorror.com/of-spaces-underscores-and-dashes/), so use hyphens (dashes) instead. Unix, Linux, and Mac file systems, and URLs, all use slashes ( `/` ) as a path separator, and Windows/DOS uses the backwards slash ( `\` ), so avoid both of those characters. Single and double quote marks are extremely problematic in a number of contexts. Finally, dots typically have special meanings in file names. Only use them if you specifically know how. (Really, avoiding all punctuation is best.)

(NOTE: Underscores, like dots, are used in particular situations with meaning. That is fine. But if you don't have a reason to use them *that you understand*, don't use them.)

## File Name Guidelines {#file-name-guidelinesn}

Here's the compiled list of file name rules.

 - File names should only have a date if it is intrinsic to the content. Your 2017 budget should have "2017" in the title. Meeting minutes should have meeting date in the title.
 - Files that are not time or date specific shouldn't have the date in the title. If you have a photo release form, a resume, your novel, or a PO request document, the creation date is probably irrelevant.
 - Except for news and blog posts (and similar itmes), *creation date* is usually irrelevant. Your 2017 budget should NOT specify in the file name that it was created in 2016.
 - Dates, if needed, should be either at the beginning or the end of the name, depending largely on how heaps of files will likely be organized and sorted.
 - Dates should be YYYY or YYYY-MM or YYYY-MM-DD. Always include leading zeros (`-2016-01-04`). Do not run the date together (`20170119`).
 - Version history should **not ever** be inserted into the file name. Use version control, not multiple renamed copies of files.
 - Global uniqueness is not a function of file names, but of URIs. A file name only has to be unique to its context, which should normally be a directory related to a particular project.
 - No spaces.
 - Dashes, not underscores.
 - No special characters. File names should only use characters in the ASCII character set.
 - No slashes, no commas, no dots, no single quote marks, no double quote marks, no back-ticks, no pipes... really no punctuation of any kind.

Here's a shareable picture to help.

![File name guide](/img/file-name-guides.png)
