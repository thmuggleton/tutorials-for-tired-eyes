---
layout: default
category: basics
position_in_category: 4
---
## {{ page.title }}

When you first get started with the command line, the prospect of remembering
the correct format and all of the options for the various commands can seem
overwhelming.  Thankfully, there are various mechanisms available to get help
from within a terminal session.  Once you know how to access these, it makes
working on the command line a lot less daunting.

### Manual pages

The installation of many commands includes a manual, which is often an
invaluable source of information; manual pages include a description of the
command, detail the available options and what they do, and give any other
information, such as example usage, that the author deems useful.  These can be
accessed by supplying the name of a command as an argument to the `man`
command.  However, in order to get the most from them, it is necessary to learn
a little about a paging program called `less`, which is used to view manual
pages.

Once you have opened a manual page (or any text file) with `less`, you navigate
the file and issue other commands to `less` using the keyboard.  Here is a list
of keys that is hopefully enough to get you started:
- `q` quits `less` and returns you to the command prompt;
- The up and down arrows can be used to scroll up and down;
- `f` and `b` move forward and backward, respectively, by a page at a time;
- `g` goes to the beginning of the file, and `G` goes to the end;
- Search by pressing `/`, entering some text, then pressing `ENTER`;
- After you have searched for a term, press `n` to find the next occurrence,
  and `N` to go back to the previous occurrence;
- `h` displays help for `less`

If you want to learn more about `less`, you can read its manual page by
entering the following at a command prompt:
```
username@localhost$ man less
```

All of the commands covered so far in this introduction to the command line
have manual pages, with the exception of `cd`.  `cd` is a 'built-in' command
provided by the shell, so does not have its own manual page.  However, if you
are using `bash`, the default shell on Mac OS X and many GNU/Linux
distributions, entering `man cd` at the command prompt will helpfully open the
manual page for all of the built-ins provided by `bash`.  From there you can
search for `cd` and find the help specific to `cd`.

### Using the \-\-help option

Unfortunately, some commands do not have manual pages.  However, you can
sometimes still get help for these commands by supplying a `--help` option.
This should summarise what the command does and explain any options that are
available.

The output after supplying `--help` is sometimes opened with `less`, but is
often dumped straight to the output of your terminal.  I generally find it
useful to "pipe" this output, using the `|` operator, into less so that it can
be paged through more easily.  Pipes take the output of one command and supply
it as input to another command, e.g.
```
username@localhost$ some-command --help | less
```
This takes the output produced by supplying the `--help` option to
`some-command` and provides it as input to `less`.

You can read more about pipes [here](http://www.linfo.org/pipe.html).
