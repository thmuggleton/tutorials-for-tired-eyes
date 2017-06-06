---
layout: default
category: basics
position_in_category: 2
---
## {{ page.title }}

The first thing that you will need to do to get started with the command line
is to open a program called a **terminal emulator**.  The easiest way to do
this, and which will work on many operating systems, is to first open the
desktop search feature for your operating system and then type "terminal":
- if you are using a GNU/Linux distribution, hit the [Super (Windows)
  key](https://en.wikipedia.org/wiki/Super_key_(keyboard_button)), type
  "terminal", then press `ENTER`.
- if you are using Mac OS X, type `CMD-SPACE` to open
  [Spotlight](https://en.wikipedia.org/wiki/Spotlight_(software)), type
  "terminal", then press `ENTER`.

If you are still struggling to open a terminal emulator application, try
searching online for "open terminal" and the name of your operating system.

You should now have a command prompt which looks something like this:
```
username@localhost$
```
To execute a command, you type it in and then press `ENTER`; see below for some
commands to get you started.

### Navigation

An important concept when working on the command line is the **working
directory**.  A directory is another name for a folder, and you can think of
the working directory as the folder that you are looking at, much as you would
do with a graphical file manager.  The working directory gives the context for
the commands that you run.

To find out what your current working directory is, you use `pwd`, which stands
for "print working directory" (Nb. "print" here just means output to the
screen, not send something to a physical printer).  Try it yourself by typing
the following, then pressing `ENTER`:
```
pwd
```
At this point, if you are using GNU/Linux, you should see something like this:
```
username@localhost$ pwd
/home/username
```
For Mac OS X users, you will probably see `/Users/username` instead.  Either
way, this directory is referred to as your **home directory**.

To find out what the current working directory contains, execute:
```
ls
```
You should now see something like:
```
username@localhost$ ls
Desktop  Documents  Downloads  Music  Pictures
```
`ls` is short for "list" and allows you to list the contents of the current
working directory.  In conjunction with `pwd`, this is very useful to orient
yourself when using the command line.

Now that you know where you are, it might be useful to move around.  For this
you can use `cd`, which stands for "change directory".  To change to the
`Documents` directory, execute:
```
cd Documents
```
This an example of using a "relative path" to specify the directory which will
become your new working directory.  This requires that there is a directory
called `Documents` inside your current working directory.  If you were not in
your home directory but still wanted to change to the `Documents` directory,
you could execute something like:
```
cd /home/username/Documents
```
This is an absolute path, which you can tell because it starts with a forward
slash.  The leading `/` is also known as the **root directory**.

Two useful shorthands related to paths are `.` and `..`.  These refer to the
current working directory and the **parent directory** respectively.  The
parent directory is the directory which contains the current working directory.
This might be easier to understand with an example:
```
username@localhost$ pwd
/home/username/Documents
username@localhost$ cd ..
username@localhost$ pwd
/home/username
```
Thus, you can see that if my current working directory is
`/home/username/Documents`, the parent directory is `/home/username`.

One final shorthand that is useful to know is `~`.  This is used in place of
your home directory, i.e. `/home/username` on GNU/Linux or `/Users/username` on
Mac OS X:
```
username@localhost$ cd ~/Pictures
username@localhost$ pwd
/home/username/Pictures
```
However, it is worth noting that some programs do not recognise `~`, so if you
experience errors, you may need to specify the full absolute path.

### Tab completion

A useful trick to introduce at this point is tab completion.  This allows you
to auto-complete based on context.  To try this, first go back to your home
directory by executing `cd` without specifying a path:
```
cd
```
Now type "cd Doc" and press the `TAB` key.  You should now see that "Documents"
has been automatically completed for you.

For this to work, the possible completion needs to be unambiguous.  If there
are multiple possible completions, you can see what they are by pressing `TAB`
a second time.  To try this, from your home directory type "cd D" and press
`TAB` twice.  You should now see something like this:
```
username@localhost$ cd D
Desktop  Documents  Downloads
```
Tab completion also works for commands.  However, this will only really be
useful once you are using commands which are longer than a few characters.
