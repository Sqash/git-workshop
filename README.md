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

So you're ready to Git gud? Awesome. This section of the workshop/tutorial
assumes you've used Git before, used it for more than the one project above,
and that you've probably messed up a project or two with it before as well.

Fret not! We're here to give you new and powerful tools and knowledge to extend
your skills to a level you feel proud of.

Additionally, this section will be a lot more conceptual than the n00b section;
fair warning.

On to the fun part.

### 1. Sweet git commands and command options

These are the useful ones for every day. We'll get to the big scary ones later.

#### `git log`

"Ooooohhh how boring," you say sarcastically. Not even, mate. You want to check
my git log? It brings all the boys to the yard.

Seriously though: `git log --graph --oneline --decorate` is amazing to look at
and perfect for almost everything. Try it in a repo with [seriously whack
history](https://github.com/CarletonComputerScienceSociety/ccss-docs) in
comparison with your regular old `git log`; and yes I can post that because
most of it was my <strike>lazy</strike> fault when deadlines were too tight.
Now it's too late and a great example.

If you want that to be even better I've got 2 words for you: "Git" "Aliases".
They're a thing, if you didn't know. For that one above as an example, open up
the file `~/.gitconfig` and add:

```
[alias]
  <alias-name> = log --graph --oneline --decorate
```

Then anywhere you can use git you can use `git <alias-name>` and it does that
pretty business.

Also, use the `--all` option to view literally all of the history (not just
stuff on the branch you're on right now) and --stat to list file changes (not a
diff, just the +/-).

Lastly, you can use `git log` similarly to `git diff` if you want to track the
changes in a file or tree over time. `git log --follow -p -- <file/tree-ish>`.

#### Change that damn editor

Have you ever used the default commit editor with git? Have you been using `-m`
ever since? Fear no more, there is a moderate solution.

One line commit messages are frequently not enough so `-m` is out of the
question. Thankfully you can take your favorite *ever* text editor and make it
the one Git outsources to. I use vim, personally. To change Git's default to
your favorite (even gedit, Lord forbid) open `~/.gitconfig` again and add the
section:

```
[core]
  editor = <command>
```

Where `<command>` is the terminal command you would use to open that text
editor.

You're welcome.

#### Checkout options

Arguably (by me) one of the most useful commands ever, it has lots of cool
options.

Using `git branch <new branch>`, `git checkout <new branch>`? Don't. Use `git
checkout -b <new branch>`, it's both in one!

`git checkout <branch> -- <file/pathspec>` grabs the version of a file from a
different branch right into your working directory. You can the work with it,
see if it behaves right, reset it, commit it there, whatever you want. It's
just handy sometimes.

#### Stashing

Awesome feature not many people use. `git stash` removes but saves all your
working branch changes so you can pull that change you forgot about when you're
working on a branch you **shouldn't have been working on**.

`git stash list` shows you all the saved stashes, `git stash apply` puts them
back for you (with an optional selection on which one. Default is most recent),
and `git stash drop` deletes all those saved stashes.

#### Fetch and why it's good

Again, people are working on branches they probably shouldn't have. Using `git
fetch` lets you get the changes from your remotes without putting them places
that are going to break things right way (like `git pull` would).

Still messed up, but at least you've got some breathing/thinking room.

#### Tags

Git tags are awesome. They let you semantically leave markers in your repo
about where important things happened. **Generally**, this is for version tags
on `master`, but you can also use them to mark things like "I did the
potentially breaking build change things starting riiiiight here." for a
potential need for reverts or something. You can also remove them when you're
done with them.

`git tag <tag name>` to add one to your current commit. `git tag -l` to list
tags that exist. `git tag -d <tag name>` to remove it.

**Important point**: tags are NOT pushed to a remote repository. This is pretty
awesome as a default. If you DO want to push your tags though, you can use `git
push <remote> <tag name>` for a single tag or you can use `git push <remote>
--tags` to send it **all** of the tags your repo has.

### 2. Collaboration Tactics

#### Working Cooperatively

The **most** important part of working with Git with other people is to make
sure you're all following the same practices, rules, strategies, etc. This is
seriously the Golden Rule of collaboration.

Other than that, I highly recommend you determine one person (or a specific
team, if relevant) to perform all of the branch merges/feature conflicts for
your project. This will help ensure the sanity of your commit tree.

#### Branching

There are a wide variety of expert and enterprise scale schemes for total
repository management. They are waaay too complex for me to cover here but you
can find a bunch through Google quite easily. What we're going to cover here is
the basic dos and don'ts of using branches while collaborating.

**DON'T**:
  - Commit directly to a public branch.
  - Merge/Rebase onto a public branch without checking changes upstream first.
  - Merge gross looking history from a private branch to a public one
    - Clean it up first (`commit --amend` or `rebase -i`)

**DO:**
  - Branch often. Every unrelated element of dev should have it's own branch
    for its own non-merged lifetime.
  - Only work on branches that are local to your machine.
  - Make sure you follow the group standard for merging.

It all seems obvious probably, but it's really important. If you forget one of
these things then it goes to hell pretty damn quick.

#### Rebase vs Merge

So we'll look more into `git rebase` in a bit, but basically when moving a
group of commits from one branch to another you've only got two options:

- `git merge`, probably what you're familiar with
- `git rebase`, something you've probably heard about

The big difference in the long run the difference is just how it makes you
project commit tree look in the end. If you want it to be linear then you need
to use `git rebase` and if you want to have the branches clear with specific
commits for merges then you'll need to use `git merge`.

There's no real right or wrong way to organize your git commit history from
that standpoint. It's more about preference and readability, so make the
decision with your group and then go with it.

More on rebasing in a bit.

### 3. More (Advanced?) Commands

#### Cherry-Pick

Basically, it copies a specific commit (or series of commits), to a new place
in the repo as a **new** commit (or series of commits). You can use this for
things like getting a specific change from something experimental into a
feature. I'm sure there's other good uses for it as well.

Just remember that `git cherry-pick` creates a new commit. It's a copy of
another commit, not a reference to that commit. If you use it poorly it can
muddle up your history with duplicate commits.

#### The Difference Between Reset and Revert

You've probably used `git reset` to unstage changes in the repo and maybe even
done something along the lines of deleting commits you decided were not useful.
However, if you've **ever** used `git reset` to delete commits that are on a
public branch you've done a **really bad thing**. Then you probably had to use
`git push --force` and everyone else's history is now full of problems and it's
all your fault.

This is the point of `git revert`! It, instead of essentially deleting commits,
produces a commit that is the inverse of the ones you listed. It produces an
undo that you can share and won't screw up everyone else! If you have changes
in your repo that are public that need to be undone, this is the command you
need.

`git reset` for private commits, `git revert` for public commits.

#### Rebasing

To many, this is a scary Git command. I'm going to try and reduce the mystery
and tell you of some good tricks and uses for it. At the same time, for your
first few tries with `git rebase` I recommend using it on a test repo of some
sort, just in case.

What `git rebase` does, is takes the *base* commit of the series of commits you
specify (the first one) and puts it (and the commits after it) somewhere else
in your repo.

It is also useful in that you can edit and/or change the commits in the branch
section you're moving as you move it.

**Note:** Like `git cherry-pick` this command makes **new** commits that are
copies of the ones specified. Unlike `git cherry-pick` it also deletes the
original commits. **Only use this command on non-public branches**.

Usually, it's smart to use `git rebase` with the `-i` flag, meaning
"interactive". This will open the editor (that you should've changed from the
default one) and allow you to specify the changes to make while moving the
branch before all of the operations happen.

When you use `git rebase -i` it will bring up an editor with a list of commits
in the form of

```
pick <hash1> <message1>
pick <hash2> <message2>
pick <hash3> <message3>
```

These represent all commits that will be rebased in order of commit from top
(least recent) to the bottom (most recent). There are a number of things that
you can change to determine how these commits are rebased. All of the changes
you make should be by changing the word "pick" to another option **OR** by
deleting a line entirely (which means the commit and its changes will be
discarded completely) **OR** by reordering the lines (changing what order the
changes are committed in).

The options that may go in the place of "pick" are:

- `pick` -- take the commit as is.
- `edit` -- pause at this commit so you can change the commit before it
  happens. Useful for things like splitting a commit into more atomic commits.
- `squash` -- merge the changes in this commit into the previous commit. Amend
  the commit message (default to the concatenation of the messages).
- `fixup` -- merge the changes in this commit into the previous commit. Take
  the first commit's message as the message.
- `reword` -- keep the commit but change the message.

**If you get a conflict, error, or rebase stops part way for an edit**, don't
worry! Fix up the conflict, make your edits, whatever, then use `git rebase
--continue` and rebase will continue on it's merry automatic way.

If you ever get into a jam and want to undo the rebase part way, `git rebase
--abort` and it should undo the whole thing for you!

Rebasing is **really** useful for cleaning up your private branch history
before merging it into a public branch for consumption. You can make up your
commit history to look like you're a coding genius! Doooo it. It makes the repo
much nicer to look at in the long run. Change those commits into the commits
you know they could've been! Just make sure you do it only if the branch is
still **private**.

### Further Reading and Practice

Most of the commits in this repo are trivial and for demonstration so that you
can explore them, move them, look at the branching, etc. It's designed to be a
nice playground to test these things you've learned. Start looking around with
`git log --graph --oneline --decorate --all` to find things to play with!

Also, the [Further Reading](#further-reading) in the N00b section is good for
everyone. You'll always learn something new and helpful!

I hope that you've gained some helpful and fun new skills and tools, so
practice practice practice and you'll Git gud in no time at all!

