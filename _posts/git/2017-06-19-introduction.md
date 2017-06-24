---
layout: default
category: git
position_in_category: 1
---
## {{ page.category }}: {{ page.title }}

This section introduces `git`.  While it assumes no prior knowledge of `git`,
it does assume basic knowledge of using the command line.  If you have not used
the command line before, there is an introduction to it in the [Basics
section](../../basics/introduction).

### What is git?

In essence, `git` is a distributed version control system.  However, if you
already know what that means, you probably don't need me to tell you what `git`
is.  There are basically two parts to that description, so I will endeavour to
explain them both.

A **version control system** is a way to manage files that are frequently, or
even constantly, changed and revised.  This is particularly useful if you have
numerous people making changes, potentially at the same time, to these files.
Having a way to track changes and revert to previous versions is often key to
ensuring the quality of the eventual output.

Such systems have become central to software projects, which are generally
worked on collaboratively and whose source code is being updated continuously.
However, they are potentially useful in any endeavour in which files go through
a number of revisions before being finalised, especially if multiple people
contribute.

Many older version control systems are based on the idea of a central server
which stores all of the files, the revision history, and provides access
controls.  If you want to make use of these systems, you need to constantly
interact with the server to get the benefits of the revision history.

`git` is different in that, while you often do have a central server that can
do all of these things, you can equally, and easily, leverage all of its
version control capabilities purely on your own computer.  This is because
`git` is **distributed**; every `git` repository stores all of the version
history and can function completely independently of any others.  However,
`git` also provides the ability to synchronise the contents of related
repositories by allowing you to "push" changes to, or "pull" changes from,
"remote" repositories, i.e. those on other computers accessed via a network.

This may seem slightly confusing, but hopefully an example of how this is often
set up in practice will help.

Imagine that you have created a `git` repository on your computer.  You then
make changes to a number of different files, and commit these revisions to your
repository.  You now have a way to access different versions of your files on
your own computer.

You now want a backup of your repository, so you push it up to a central
server.  There are now 2 copies of the repository, one on your own computer and
one on the central server.  Both of these repositories store the full version
history of the files and can function independently of each other, but are
linked by a common version history.

Now you want to work on your files together with a friend.  If you grant access
to the central server, your friend can pull down their own copy of the
repository from the central server.  There are now 3 independent copies of the
repository.

Your friend now makes some changes to the repository on their computer.  They
can then push these changes up to the repository on the central server.  Your
friend's repository and the one on the central server now have the same version
history, but yours is different because it does not include the changes that
your friend made.

You can continue to use your repository as you did originally, when yours was
the only copy of the repository.  If you make further changes and do not push
these up to the repository on the central server, then your repository will
diverge further from the other two.  However, if at any point you want the
changes that your friend made, you can pull these into the repository on your
computer from the remote repository on the central server.

There are some terms that have been used here without much explanation, which
has been deliberately left until fuller treatment can be given to the relevant
topics.  However, the preceding paragraphs are hopefully sufficient to give a
basic idea of what `git` is.

### Who might want to use git?

`git` is particularly popular with software engineers.  However, it will be
useful to anyone working with files that go through multiple revisions, such as
essays or reports.  Investing a little time in learning `git` will provide you
with a much better way of managing multiple versions of files than trying to do
this manually.

However, an important caveat is that you need to be willing to invest
sufficient time to learn `git` to avoid making mistakes, because you could end
up losing your work, wasting a lot of time, and/or getting extremely
frustrated.  Thankfully, for simple version control you can get by with a few
commands and a (simplified) mental model of how it works.

### Why would you use git?

`git` is an extremely powerful version control system, and with sufficient
understanding it can meet the needs of many different projects, use cases and
ways of working.  As a distributed version control system, `git` also has a
significant advantage over older version control systems such as Subversion in
that you can enjoy many of its features by just installing it on your own
computer; you do not need to setup a remote server as is the case with
Subversion.

On the other hand, it is worth mentioning that some people seem to find `git`
quite confusing and not very intuitive.  I do not necessarily share this
opinion, and will try my best to explain things in a way that is
comprehensible.  Further, I will deliberately leave out details that are not
necessary for simple use cases (there are other excellent resources available
if you want to dig deeper).  However, it feels important to acknowledge
potential difficulties in getting to grips with `git` at this point.

For those already using a different version control system, such as Subversion,
`git` might provide a number of improvements.  For example, the branching model
used by `git` is much faster and has significantly less overhead than that
employed by Subversion.  Thus, once you understand it, `git` is a much more
flexible tool for a number of use cases.  The distributed nature of `git` also
builds in significant redundancy compared to a centralised version control
system, which could contribute to disaster recovery and improve the resilience
of your source control system.

### Where should you start?

If `git` sounds like something that could be useful to you, the first thing to
do is install it.  `git` is [free
software](https://www.fsf.org/about/what-is-free-software) and is widely
available for GNU/Linux distributions as well as Unix-based and Windows
operating systems.  You can find instructions for how to install `git` on
various platforms
[here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

However, the caveat on the [home page](../../) that this website is geared
towards GNU/Linux and Unix-based operating systems still applies.  Thus, if you
are using Windows, resources other than this website might provide you with
more reliable information on the specifics of using `git` from the command
line on Windows.

Once you have installed `git`, the [First Steps](../first-steps) page explains
the basics of using `git`.
