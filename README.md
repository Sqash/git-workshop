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

We're going to do this starting locally, working with some common and useful
git commands to do so, and then create an online home for your repository to
send it to. Finally, we're going to send it 'upstream' (to a non-local
repository) to Github so you can look at in all its glory.

#### Step 1: Initialize your repository

In the terminal, navigate to where you want to store the directory that will
house your repository.

Once in that directory create a new directory (probably with `mkdir`) called
`first-git-repo`. Enter the new directory.

Run the command `git init`. It will initialize your repository by creating a
new directory named `.git` which you can view with `ls -la` in Bash. There's no
data or files that git is tracking yet though (or any at all really), so onto
Step 2!

#### Step 1.5: Set the settings!

New Git repositories have a few settings you need to tell it about explicitly
unless you've already done so for Git globally. We're going to set them up
globally for your computer. Just run these commands, trust me.

- `git config --global user.email "<your Github email>"`
- `git config --global user.name "<your name>"`
- `git config --global push.default simple`

#### Step 2: Make a file for Git to Track

Create a new file in the directory called `README.md`. Add some text to the
file such as "This is my first repository! Yay me!", then save it.

This file will eventually be used as the introductory blurb for your
repository (Github automatically uses `README.md` if it's in the top
directory). If you're familiar with Markdown files, it supports all standard
Markdown syntax as well as some Git specific additions. Having one is a good
standard for you Git repos.

#### Step 3: Get Git to track the file

If you use `git status` you'll notice that the file you added isn't yet tracked
by Git. We're going to change that.

If you enter `git add README.md` (auto-complete might help you there) git will
add the file you just made to the Staging Area. This means that the next commit
you make with include the file's changes in the snapshot.

Try entering `git status` again to see the difference. It's a really helpful
command to use before you commit to make sure you're committing all the right
things.

#### Step 4: Commit your new file

Time to save changes. Run `git commit -m "Initial commit"`. The `-m` option
just specifies the commit message to use on the command line instead of it
opening the default editor and you **really** don't want that. It can be
changed though, don't worry, but we cover that in the Intermediate section. For
this tutorial just use the `-m` option when you commit.

Remember, **all commits have to have messages** and those messages are **very
helpful**.

Now let's look at our commit! Run `git log`. You should see an output that has
a big hash value (that's the commit's hash), your name and email address, and
time, and the message you wrote. When you make more commits this will turn into
a scrollable list. You'll love `git log` when you're working on a repo with
hundreds or thousands of commits you didn't make!

#### Step 5: Add some good Git default files

Almost all git repos should have a `.gitignore` file and a `.gitattributes`
file, so we're going to make them (even though they won't do much).

Create an empty file called `.gitignore` in the directory, then use `git add
.gitignore` to add it to the staging area.

Create a file called `.gitattributes` in the directory and add the line "\*
text=auto" to it. Save it, and use `git add .gitattributes` to add it to the
staging area as well.

Additionally, if you wanted, you could add a `LICENSE` file to the repo. This
isn't really important here, but for code projects could be incredibly
important. We're going to skip it, but Github has some really good information
on it if you're curious.

Use `git status` to make sure both the files we made are in the Staging Area
and then use `git commit -m "Added git config files"` to save those changes
too.

If you're curious, check out `git log` again to see how it changes.

#### Step 6: Make an online home

Go back to Github in your web browser and navigate to your profile (clicking
your icon in the top right should do it). Click the "Repositories" tab.

On the right side there should be a button that says "New". Click that one too!

In the repository name section type in `first-git-repo` or whatever you called
that directory your repo is in on your computer. It doesn't *have* to be the
same but it really helps to keep things organized.

Enter a description if you like, make sure the "Public" radio button is
selected, and make sure that you don't change the options below. You'll note
that the things we've already made, Github can do for you. In the future it's
usually quite handy but that wouldn't be any fun here at all.

Once you've verified the settings as above, click "Create Repository". It'll
have a bunch of instructions (it always does this) for reference. Just ignore
them because we're doing those things right now!

What you *should* do is copy the HTTPS link at the top (it's easier than SSH).

#### Step 7: Add the online repository as a Remote

In Git, a remote is a reference to an upstream repository. We want to add the
online repository we just created as a remote.

Run `git remote add origin <the link you copied>`. What this does is tells Git
to add the link you copied as a remote to its storage and call it "origin" for
future reference. You could call it other stuff, but "origin" is pretty
standard for the main online home of your repos.

#### Step 8: Copy your repo upstream!

Now that you have the online remote, time to use it! Run the command `git push
-u origin master`. It will ask you for your Github username and password and
that's important, so that no one can make changes from your computer without
your credentials. Enter them and it should complete no problem.

What the command did was take all of the commits you have in your repo that the
online one doesn't have (all of them) and sends them to it. The `-u` option
tells git that you want your current repository branch to be linked to the one
on the "origin" remote called "master" (the branch you're currently on is called
"master" as well. It's another default thing). You only need to use the `-u`
option once for a remote/branch combination, so in future pushes you can just
run `git push` and it should work automatically.

#### Step 9: Go and look at your handy-work!

Go back to your browser (you might have to refresh the repository page), and
look at all the files you made! They're the same (and that's the point)!

Good job!

### Further reading.

You've got your first ever repository up? **Awesome!** It wasn't as hard as you
thought it would be, right? Good on you for getting started on a rad and
important skill for a programmer!

Now, if you want to learn more (and you should), there's lots more for you. You
can either get going right away on next section of this workshop or you can do
some reading and playing!

I recommend at least browsing, but probably just full on reading these
resources (not in any particular order):

- [Pro Git](https://git-scm.com/book/en/v2), a book by Scott Chacon and Ben
  Straub, published by Apress. It's available for free at this link online and
  if you *really* want to know how Git works then this book is awesome.
- [Atlassian Git Tutorials](https://www.atlassian.com/git/), a collection of
  really useful tips, techniques, etc. for using Git to your full advantage.
- [Git Branching Game](http://pcottle.github.io/learnGitBranching/)

I've gone through all of the above resources and attribute much of my skill
with Git to them; the rest to practice.

Additionally, if you ever need to know what a git command does but don't
remember the exact options, in your terminal `man git-<name-of-command>`. If
you're not familiar with man pages, they're the internal manual of terminal
commands and are super useful.

## Intermediate Start Here

//TODO
