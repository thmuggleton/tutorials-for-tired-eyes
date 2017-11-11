---
layout: default
category: vim
position_in_category: 1
---
## {{ page.category }}: {{ page.title }}

This section introduces `Vim`.  While it assumes no prior knowledge of `Vim`,
it does assume basic knowledge of using the command line.  If you have not used
the command line before, there is an introduction to it in the [Basics
section](../../basics/introduction).

### What is Vim?

`Vim` is a modal command-line text editor.  It is worth breaking down this
definition into its constituent parts:
* A text editor is a computer program used to edit text files; amazing, but
  true.  It is worth noting that text editors are different from word
  processors in that they generally do not provide any in-built capability to
  add formatting.
* A command-line text editor is a text editor which can run within the context
  of a terminal window, and thus does not require a full GUI environment to
  function.
* In order to maximise the utility of a standard keyboard, Vim has multiple
  'modes', hence why it is called a 'modal text editor' (more on this later).

### Who might want to use Vim?

Before giving the reasons that you might want to use `Vim`, it is important to
note that `Vim` has a pretty steep learning curve.  This means that, in order
to learn `Vim`, you will need to invest time that might be better spent on
other things.  This is not an attempt to put you off; it is far from
impossible to learn `Vim` and also quite rewarding, but it will require some
effort, so just make sure that there is a valid reason to learn it before you
invest the necessary time.  With that said, who might want to use `Vim`?

Firstly, because `Vim` is a command-line editor, it is an excellent tool for
those working with headless servers or computers that do not have a GUI
environment installed, such as system administrators.  Furthermore, if you are
working a lot on the command-line, e.g. as a programmer, using a command-line
editor can mean that there is less context switching compared to using a GUI
editor.

Secondly, `Vim` has built-in support, such as syntax highlighting, for many
programming languages.  This makes it suitable for programmers.

Finally, the modal editing capabilities of `Vim` mean that proficient users can
build up reasonable speed at editing text.  This can make it an attractive
prospect for anyone wanting to be able to edit text files quickly.

### Why would you use Vim over other text editors?

There are many competing text editors available, which can result in rather
futile arguments over which one is 'best'.  In particular, users of
[`Emacs`](https://en.wikipedia.org/wiki/Emacs) and users of `Vim` are
well-known within certain circles for having heated debates.

I have little interest in engaging in these arguments; ultimately, I think that
you should use whatever works for you.  However, I hope that by giving the
reasons that I decided to learn `Vim`, it will inform others trying to decide
whether they want to invest the necessary time in learning it.

I learned `Vim` because:
* `Vim` is (almost) universally available;
  * `Vim` is part of the POSIX standard, and so a version of it is installed on
    almost all Unix and Unix-like systems.  As a programmer, I work on the
    command-line a lot and wanted to feel comfortable with the available tools.
    Since `Vim` is generally always installed on Unix and Unix-like systems,
    knowing `Vim` would mean that I would always have a text editor that I
    could use, whether developing locally, using virtual machines, or logging
    into headless servers.
* `Vim` is open-source software;
  * For many reasons, including those outlined in
    [the philosophy of the Free Software Foundation](https://www.gnu.org/philosophy/philosophy.html),
    I always use open-source software whenever I can.
* Using a mouse slows you down;
  * A mouse is great for usability, but using a keyboard can be much faster.
    `Vim` has the necessary capabilities to make editing text potentially very
    fast.
* I was concerned about ['Emacs pinky'](https://en.wikipedia.org/wiki/Emacs#Emacs_pinky);
  * Another reason to use a keyboard rather than a mouse is that it can help
    avoid RSI if you are working with computers for lengthy periods of time.
    As a modal editor, `Vim` allows you to mostly keep your fingers on the
    'home row' of keys and avoid too much stretching that can, over time, hurt
    your hands.  `Emacs` makes extensive use of meta-keys, such as CTRL, ALT
    and SHIFT, which can result in 'Emacs pinky'.  I wanted to avoid that, so I
    decided to learn `Vim` instead.

### Where should you start?

Installations of `Vim` usually come with `vimtutor`, an interactive
walk-through of how to use `Vim`.  This can be a very useful way to start
learning about and, importantly, practice making use of `Vim`.  To start up
`vimtutor`, just execute it from the command line:
```
$ vimtutor
```
