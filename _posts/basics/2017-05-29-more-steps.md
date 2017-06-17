---
layout: default
category: basics
position_in_category: 3
---
## {{ page.title }}

In [First Steps](../first-steps), we learned how to find out what the current
working directory is with `pwd`, list the contents of a directory with `ls`,
and move between directories with `cd`.  With this in hand, you can now start
doing some more interesting things with files.

### Arguments, shells and spaces

However, first you need to understand two more important command line concepts:
**arguments** and **shells**.

We have already used arguments when changing directories; the path that we
specified was the "argument" that we gave to the `cd` command.  It is worth
knowing that arguments can also be referred to as "parameters"; although there
is a slight technical distinction, the two terms are often used
interchangeably.

The simplest description of a shell is that it is a program which passes your
commands and their arguments to the operating system.  When you use the command
line, you use a shell to make things easier, such as the tab-completion
mentioned in [First Steps](../first-steps), and so that you do not have to deal
with direct, lower-level interactions with the operating system.  This is
basically all that you need to know about shells at this stage, but fuller
descriptions can be found [here](https://kb.iu.edu/d/agvf) and
[here](https://en.wikipedia.org/wiki/Unix_shell) if you are curious.

At this point, it may seem that I am introducing unnecessary technical jargon
for no reason.  However, understanding arguments and how your shell parses them
is crucial to avoiding potentially destructive mistakes when working with files
on the command line.  This is because whitespace characters, such as tabs and
spaces, constitute argument delimiters.  This means that if a filename has a
space in it, passing it to a command without special treatment will not work as
expected, since the shell will split the filename on the space and pass it to
the command as two separate arguments.

In order to get around this, it is necessary to "quote" anything that you do
not want the shell to split using whitespace.  There are various nuances to
quoting when using the shell (see footnote 1 below), but suffice to say for
the moment that you can avoid splitting on whitespace with any of the following
methods:
```
cd "My Documents"
cd 'My Documents'
cd My\ Documents
```
All three of the above are functionally equivalent.  However, without these
quoting mechanisms, i.e. `cd My Documents`, the shell would pass `My` and
`Documents` as two separate arguments and you would likely get an error.  This
can have more serious consequences when working with files, as you will see
when learning about the `rm` command below.

### Options

There is one final thing that is necessary to explain before moving on to
commands that actually do something, which is **options**.  Options are passed
to commands in a similar way to arguments.  However, while arguments generally
specify what the command should act upon, options alter the behaviour of the
command.  Consequently, options are, by convention, differentiated from
arguments through the use of single or double dashes preceding the option.

There are various examples of options being used below, but to illustrate them
here, we can use our old friend `ls`.  By passing the `-l` option to `ls`, you
can get a 'long' listing, e.g.
```
username@localhost$ ls -l
-rw-r--r--. 1 username group 3661 May 30 20:38 my-file.txt
-rw-r--r--. 1 username group 2343 May 30 20:45 file-2.txt
```
Some of the output may not mean very much at this stage, but you have now seen
an option being used.

### Creating directories

Creating directories using the command line is fairly simple; you just use the
`mkdir` command:
```
username@localhost$ pwd
/home/username/Pictures
username@localhost$ ls
landscape.png  portrait.jpg
username@localhost$ mkdir art
username@localhost$ ls
art  landscape.png  portrait.jpg
```

### Copying files

To copy a file using the command line, you can use `cp`:
```
username@localhost$ pwd
/home/username/Documents
username@localhost$ ls
fruit.txt  vegetables.jpg
username@localhost$ cp fruit.txt more-fruit.txt
username@localhost$ ls
fruit.txt  more-fruit.txt  vegetables.jpg
```
This works fine for individual files, but when you try to copy a directory like
this, you will get an error:
```
username@localhost$ pwd
/home/username
username@localhost$ cp Documents More-Documents
cp: omitting directory 'Documents'
```
In order to successfully copy a whole directory, you need to specify the `-r`
option.  This stands for 'recursive', but unless you have studied computer
science this probably doesn't mean very much.  For the moment it might be
easiest to just memorise it.
```
username@localhost$ cp -r Documents More-Documents
username@localhost$ ls
Desktop  Documents  Downloads  More-Documents Music  Pictures
```
An alternative tool that you can use for copying files and directories is
`rsync`.  A significant use-case for `rsync` is to copy files from your local
system to a remote system, i.e. a computer that you are accessing over a
network, but it can also be used to copy files locally.  Although `rsync` is
slightly more complicated than `cp`, it provides a number of features that are
useful for creating local backups, such as file integrity checks to avoid data
corruption and, optionally, retaining timestamps.

`rsync` has a number of options, but for simple usage you can get away with
just knowing one or two.  The `-a` option, which stands for 'archive', is a
useful shorthand for a number of different options which basically preserve all
of the attributes, e.g. modification time, associated with the original files
in the copies.  `-a` also applies the `-r` option, which behaves in the same
way as the `-r` option for `cp`.
```
username@localhost$ rsync -a Documents More-Documents
username@localhost$ ls
Desktop  Documents  Downloads  More-Documents Music  Pictures
```
The other option for `rsync` that you might find helpful is the `-v` option,
which stands for 'verbose'.  This just increases the amount of information that
`rsync` outputs while it is running to show, e.g., which files and directories
it has copied.

### Moving and renaming files

To move a file using the command line, you can use the `mv` command:
```
username@localhost$ pwd
/home/username/Documents
username@localhost$ ls
fruit.txt  more-fruit.txt  vegetables.jpg
username@localhost$ mv vegetables.jpg ../Pictures/
username@localhost$ ls
fruit.txt  more-fruit.txt
username@localhost$ ls ../Pictures/
art  landscape.png  portrait.jpg  vegetables.jpg
```
Here, I have moved `vegetables.jpg` from `~/Documents` to `~/Pictures`.  This
might seem straightforward, but there are a few subtleties with `mv` that are
important to note.

Firstly, if you move a file to a location where a file of the same name already
exists, you will overwrite the other file.

Secondly, if you want to rename a file, then you simply move it within the same
directory.

To demonstrate these two points, observe the following:
```
username@localhost$ ls
fruit.txt  more-fruit.txt  vegetables.txt
username@localhost$ mv vegetables.txt more-fruit.txt
username@localhost$ ls
fruit.txt  more-fruit.txt
```
This may look like I have deleted `vegetables.txt`, but what I have actually
done is renamed `vegetables.txt` to `more-fruit.txt`, in the process deleting
the original file called `more-fruit.txt`.

You can move and rename directories similarly to how you rename files, i.e. by
moving them to a different location with `mv`, or 'moving' them within the same
parent directory to rename them.

### Deleting files

To delete files using the command line, you can use the `rm` command.  Note
that, by default, **`rm` will not prompt you before deleting files and deletes
them immediately**, without an intermediary step like the Windows Recycle Bin:
```
username@localhost$ ls
fruit.txt  more-fruit.txt
username@localhost$ rm more-fruit.txt
username@localhost$ ls
fruit.txt
```
It is especially important to be mindful of shell quoting when using `rm`.
Consider the following example:
```
username@localhost$ ls
My Words.txt  Words.txt
username@localhost$ rm My Words.txt
rm: cannot remove 'My': No such file or directory
username@localhost$ ls
My Words.txt
```
As you can possibly deduce from the error message, `rm` tried to delete two
files 'My' and 'Words.txt'.  It successfully deleted 'Words.txt', but this is
probably not what we wanted.  This is because, as described earlier, the shell
splits arguments on whitespace before passing them to the command.  To get the
intended effect, we would need to do something like the following:
```
username@localhost$ ls
My Words.txt  Words.txt
username@localhost$ rm "My Words.txt"
username@localhost$ ls
Words.txt
```
Like `cp`, `rm` without any options will only work for individual files.  In
order to delete directories, you can use the `-r` option with `rm`.  However,
be very careful with this because **`rm -r` will delete the whole directory and
any files and sub-directories that it contains**:
```
username@localhost$ pwd
/home/username/Pictures
username@localhost$ ls
art  landscape.png  portrait.jpg
username@localhost$ rm -r art
username@localhost$ ls
landscape.png  portrait.jpg
```
If you need to delete files securely, i.e. overwrite their contents on disk so
that they are much harder to recover, you can use `shred` on GNU/Linux or `srm`
if you are using Mac OS X.  `srm` behaves similarly to `rm`, but `shred`
requires the `-u` option to delete files after overwriting them.  Note that
these tools come with various caveats about their effectiveness under different
circumstances.  Further discussion of secure deletion is outside the scope of
this brief tutorial but you can find out more about these tools by reading the
relevant manual pages (see the next section on [Getting Help](../getting-help)
to learn more about manual pages).

### Footnotes
1 If you are feeling really adventurous, this is a very good
explanation of shell quoting:
[http://www.grymoire.com/Unix/Quote.html](http://www.grymoire.com/Unix/Quote.html).
However, I wouldn't necessarily recommend getting into that level of detail
just yet.
