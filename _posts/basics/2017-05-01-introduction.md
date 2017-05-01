---
layout: default
category: basics
position_in_category: 1
---
## {{ page.title }}

This section introduces command line basics, and assumes no prior knowledge of
using the command line.  If you have used the command line before, you might
want to skip past this basic introduction.

Please note that although Windows does have a command-line, and some of the
commands mentioned here work on Windows, this website is aimed at GNU/Linux
distributions and operating systems based on Unix, such as FreeBSD and Mac OS
X.  Unfortunately, I have never really taken enough interest in the Windows
command line to offer anything useful in this regard.

### What is the command line?

These days, most people who use computers use Graphical User Interfaces (GUIs),
even if they are not familiar with this term.  In essence, a GUI allows you
to control a computer and its applications by clicking or tapping on icons
using a mouse or a touchscreen.

By contrast, when using a command line interface (CLI), you control the
computer and its applications by typing in commands.  For historical reasons,
what you type these commands into is often referred to as a 'terminal'.

### Who might want to use the command line?

If you are a system administrator or a software engineer, then you are probably
(hopefully) already making significant use of the command line.  However,
learning the command line will benefit anyone who uses a computer.  What's
more, although there is a huge amount that you can learn about the command line
and associated tools, the basics of it are really not very difficult.  Learning
to use the command line will hopefully remove a lot of the mystery and help you
feel more in control of your computer.

If you are reading this, you presumably already have some interest in learning
more about the command line.  However, if you still need convincing, read the
next section for some thoughts about why you might want to invest the necessary
time.

### Why would you use the command line?

While GUIs make computers much more approachable and usable for many people,
they often do this at the expense of functionality.  The reason for this is
that you can often express much more complex instructions when typing commands
than you can by clicking on icons.

For example, say you have 100 images in a folder and want to move any that have
the word 'penguin' in the filename into a new subfolder called 'Lovely-birds'.
If there are more than about 5 of these files, and they are not grouped
together by any available sorting, this would be rather arduous using a GUI.
On the command line, you would just issue this command:

```
$ mkdir Lovely-birds && mv *penguin* Lovely-birds/
```

You might counter that, by the time you have typed all of that in, you might as
well have just done it using a GUI.  If you thought that, firstly let me say
that I am glad that you are not taking everything written here to be true
simply because some random person wrote it down.  However, there are at least
two things that are worth considering in this regard:

- Firstly, command line interfaces have been around for a long time and you
  will learn that, over time, software developers have come up with various,
  often ingenious, ways to make working on the command line faster and easier.

- Secondly, this is a simple and fairly contrived example to illustrate a
  point; the real power of the command line will become apparent quite quickly
  once you start using it.

Finally, there are some tools for which GUIs have not been developed.  By
getting comfortable with the command line, these tools become accessible to
you, and through this, you open up a number of useful possibilities.

### Where should you start?

I have provided some basic guides to the command line that are available via
the links on the right-hand side.  These are hopefully enough to get you
started.
