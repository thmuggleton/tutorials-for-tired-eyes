---
layout: default
category: git
position_in_category: 2
---
## {{ page.category }}: {{ page.title }}

While learning `git`, I would recommend creating a new, empty directory in
which to create a new `git` repository.  We will work with dummy files that we
have created along the way to demonstrate necessary concepts and commands.
This way, if you make any mistakes, you will only lose the dummy files that we
have created, rather than anything important.

### Creating a git repository

In order to create a `git` repository, you just need to navigate to the
top-level directory of your project and execute `git init`.  For our purposes,
we will create a `tmp` directory inside our home directory, create a directory
inside that called `git-first-steps`, and then create a `git` repository inside
`git-first-steps`:
```
username@localhost$ cd
username@localhost$ mkdir -p tmp/git-first-steps
username@localhost$ cd tmp/git-first-steps
username@localhost$ git init
Initialized empty Git repository in /home/username/tmp/git-first-steps/.git/
```

You now have a `git` repository.  If you execute `ls -a`, you will see that
`git init` has created a hidden directory called `.git`.  This is where `git`
stores all of the files necessary to maintain the revision history of your
repository.
```
username@localhost$ ls -a
.  ..  .git
```

### Creating some files

Now that you have a `git` repository, you can track changes to the files in
your repository.  First, we will need some files.  We can create these using
the `echo` command and output redirection.  The `echo` command prints whatever
you type to the standard output stream, which is usually displayed on your
terminal screen.  Output redirection is a shell feature which allows you to
take the output from a command and write it to a file, rather than writing it
to your terminal screen.  You use the "`>`" operator to redirect the standard
output stream to a file:
```
username@localhost$ echo hello
hello
username@localhost$ echo hello > greetings.txt
username@localhost$ ls
greetings.txt
```

NB: if for whatever reason you have decided to ignore the advice to create a
new directory for the purpose of practising `git` commands, note that **"`>`"
will overwrite files with the same name without warning**, so be careful with
it.

### Committing changes

Now that we have a file, we would like to put it safely in our repository so
that we can recover this version of it at any given point in the future.
Putting files, or changes to files, into a `git` repository is a 2-step
process.  Firstly, you need to "stage" the files.  Once you have staged the
files, you can then "commit" them to the repository.  I will leave further
discussion of the reason for this 2-step process until later; you can still
achieve something useful without knowing the reason behind it.  For the moment,
we will just accept that this is how `git` works.

To stage files, you use the `git add` command.  This command provides various
mechanisms for staging files, but, to avoid confusion, for the moment we will
limit ourselves to two of them.  The first is to supply the path to the file as
an argument to `git add`:
```
username@localhost$ git add greetings.txt
```

However, if you have multiple files to stage, this can become arduous.  The
simplest way around this is to use a "`.`", which stages all uncommitted
changes:
```
username@localhost$ echo pear > fruit.txt
username@localhost$ echo carrot > vegetables.txt
username@localhost$ git add .
```

Now that we have staged our files, we can commit them using the `git commit`
command.  Again, this command provides various options, but for the moment we
will stick to the simplest mechanism for committing.  To do this, we use the
`-m` option to provide a message describing the changes that we are committing
to the repository.  The first commit in a `git` repository usually has the
message "Initial commit", but it can be anything you want:
```
username@localhost$ git commit -m 'Add greeting and some tasty fruit and vegetables.'
```

Note that when using `-m`, the commit message has to be quoted so that the
shell does not split it on whitespace.

### Viewing the revision history

Now we have a way to track changes to our files.  If you want to view all of
the changes that have been committed to the repository, you use the `git log`
command.  This will either dump the commit log to your terminal screen or, if
it is long enough, it will open it using `less`.  If you are not familiar with
`less`, there is a brief introduction to it on the [Getting
Help](../../basics/getting-help) page in the Basics section.
```
username@localhost$ git log
```

Without any options, `git log` will display the date, author and message, among
a few other things, for each commit.  That crazy string of numbers and letters
after the word "commit" is a base-16 representation of the **commit hash**,
which is used to uniquely identify the commit.  If you don't know what
"base-16" means, don't worry about it; the important thing is that the commit
hash is a unique identifier that can be used to refer to a specific commit.
This will come in useful later on when learning about recovering previous
versions of your files, among other things.

### Summary

So far, we have learned how to:
- create a new local `git` repository using `git init`
- stage files and changes using `git add`
- commit staged files and changes using `git commit`
- view the revision history using `git log`

Depending on what you want to do with `git`, you are now in a good position to
learn about:
- more sophisticated updates to your repository using `git status`, `git diff`
  and the other options available for `git add` and `git commit`
- recovering previous versions of your files using `git revert` and `git
  checkout`
- trying out ideas using `git branch`
- sharing or backing up your repository using `git remote`, `git push` and `git
  pull`

