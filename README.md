# Git Workshop

A skill-building workshop by Sam Whiteley

Most recently hosted live on September 16th, 2015 for members of the
[CCSS](http://ccss.carleton.ca)

## Overview

### For N00bs (and intermediates who have not done these things):

1. Install git.
    - [Windows Download](https://git-scm.com/download/win)
    - Ubuntu Linux: in terminal run `sudo apt-get install git`
    - [Mac OS Download](https://git-scm.com/download/mac)

2. Create a [Github](https://github.com) account.

3. Vocabulary tiem!

4. Make a new repository to get the hang of the basics.
    - Work with the basics: Complete the task list!

5. Further reading.

[**Start**](#n00b-start-here)

### For intermediates

1. Your new favorite commands and options
    - log options (and making aliases)
    - changing your commit editor
    - cherrypick
    - reset vs revert
    - stash
    - rebase (-i)
    - checkout (-b, -- [file ...])
    - fetch
    - tag

2. Practice these commands with the git-workshop repository!

3. Tactics for good collaboration
    - branching
    - rebase vs merge
    - picking a leader
    - Making sure everyone is doing the same thing

[**Start**](#intermediate-start-here)

## N00b Start Here

### Install git.

If you're totally new to the command line, then a Git GUI may be a lot more
comfortable for you to use. Windows, Mac, and Linux have GUI applications that
leverage git for you. I give you this warning: **using a GUI for your own
comfort will severly limit the power that git can yield to you for the
excellent management of your own projects**. I highly recommend learning git in
the terminal from the get go.

#### Windows

[Windows Download](https://git-scm.com/download/win)

When using the installer GUI you will be asked a number of questions you likely
don't know the answer to. For this tutorial, ensure you have it install 'Git
Bash'. This is a Bash terminal emulator for windows so that you may use the
same commands on Windows with git as you would for Linux or Mac.

#### Ubuntu

In terminal run `sudo apt-get install git`

#### Mac OS

[Mac OS Download](https://git-scm.com/download/mac)

### Create a Github account.

[Github Homepage](https://github.com)

I highly recommend you use your main email account and real name, things you
will be comfortable and proud of putting on your resume. The reason for this is
that as a programmer/developer your Github account is akin to an artist's
portfolio. You should have a link to this account on your resume/CV, LinkedIn,
etc. once it's got one or two things in it.

If you thereafter add your Carleton email to the account (do it afterwards, not
in this tutorial), you can get a student account on Github. This allows you to
have *private* repositories which can be exceptionally useful during group
assignments.

[Github Student info](https://education.github.com/pack)

### New Vocabulary

#### Repository

A set of files and directories that are tracked by git and therefore are under
source control. Source control is the entire point!

The commands related the most to repositories are `git init` and `git clone`
which create a new repository in your current directory and copy a repository
from somewhere else into your current directory respectively.

#### Commit

A snapshot of the current state of your repository. It saves the state of all
files that you're tracking with the repository so that you can go back to it
later (and you'll want to).

The command related the most to commits is `git commit`! It creates a commit
for you out of the files in your staging area. Also there's `git log` which
shows you the list of previous commits.

#### Working Directory

A set of files from a specific commit in a repository. You can change them,
look at them, get rid of them, and even add totally new ones. It's a little
complicated on the inside, but basically its just the regular old filesystem
you're used to. You can do all the same stuff!

The commands most related to the Working Directory are:

- `git stash`. It hides all of your changes until you want them back. Sometimes
  this is necessary!
- `git branch` shows you what branch your working on and which ones you have.
- `git checkout` allows you to change your working directory to a different
  commit.

#### Staging Area

Tell git what's important. This is where you put files that you've changed that
you want to tell git to save the changes of. When you make a commit in your
repo, git takes all of the files in the staging area and records the changes
you made and saves that. It assumes all other files didn't (even if you did!)
and this is a **good** thing.

There's all sorts of staging area commands!

- `git add` adds a new file or changed file to the staging area
- `git rm` deletes a file from your repository **AND** tells git that you
  deleted it (you can get it back now)
- `git status` tells you what is going on with your Staging Area right now

#### Branches

Branches are **really** handy references to different sections of your
repository. With branches you can do things like experiment without touching
the code that you are sure already works, work on stuff at the same time as
other members of your group without having everything smooshed together, and
lots more!

`git branch`, `git checkout`, and `git remote` are all relevant commands to
branches but we won't get too deep into them at this level.

### Make a Repo!

Okay! Now that you know a little bit about the terms we're going to use and
have the software to work with git, we're going to dive in head first! It's
time to make your (probably) first ever repository. Once we've done that, we're
going to put it up on Github for you to look at online!

*Tasks*

### Further reading.

You've got your first ever repository up? **Awesome!** It wasn't as hard as you
thought it would be, right? Good on you for getting started on a rad and
important skill for a programmer!

Now, if you want to learn more (and you should), there's lots more for you. You
can either get going right away on next section of this workshop or you can do
some reading and playing!

I recommend at least browsing, but probably just full on reading these
resources:

- [Pro Git](https://git-scm.com/book/en/v2), a book by Scott Chacon and Ben
  Straub, published by Apress. It's available for free at this link online and
  if you *really* want to know how Git works then this book is awesome.
- [Atlassian Git Tutorials](https://www.atlassian.com/git/), a collection of
  really useful tips, techniques, etc. for using Git to your full advantage.
- [Git Branching Game](http://pcottle.github.io/learnGitBranching/)

Additionally, if you ever need to know what a git command does but don't
remember the exact options, in your terminal `man git-<name-of-command>`. If
you're not familiar with man pages, they're the internal manual of terminal
commands and are super useful.

## Intermediate Start Here

//TODO
