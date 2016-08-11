# How to *git* things done.

So the first step to starting any new project is to create a folder to hold our
code. I recommend having a folder to store all of your projects in, since I run
mostly on a Linux system I put this folder in my $HOME directory. The Windows
equivalent is `C:\Users\<Your Username>\`, but you can put it wherever you want
don't let some random dude on the internet run your life!

Once you have a projects folder create a folder for our application code, I'm
going to call mine `super_todo`. You can name yours whatever you like!

Now we need to open the terminal in that folder, I won't go into detail how to do
that here but if you're on Windows you'll need to use Git Bash which you installed
in the very beginning of this book.

Once you're in that folder `super_todo $` run the command `git init`.

## What is Git?

Git is a source code management system, you might be asking yourself what that
really means and that's ok I'm going to explain it.

Imagine if you will that you're working on a team with a bunch of other programmers
how do you know who changed what code when? More importantly how do you make sure
that bad code doesn't get into production or if it does how do you roll back?
With the way we've been doing things there would be no traceability or way to
revert our scripts back to a previous state, Git gives us that power.

Git is one of those tools that so simple it's complicated, at a basic level
all git does is track and manage changes to files, that's it. So let's define 
some terms so we are speaking the same language:

- **Repo** - a git repo is any folder which as a subfolder called `.git` it's generally
the top level folder where your source code is stored, after you ran `git init`
if you run `ls -a` you will see that git created a `.git` folder.

- **Branch** - a "branch" of the repo is an isolated copy of the repo, you can make
changes in this branch without affecting other branches, git will let you switch
between branches and even merge the branches so the changes can be combined.

- **Remote** - a location (usually a URL) that has another copy of your repo, a very
common remote is Github, Github will store a remote copy of your repo and allows
you to do some management of your repo via a nice GUI. This is pretty important
because it keeps your code "accident proof" since you now have an offsite backup

- **Pull** - This means to pull the changes from a remote repo into your local repo.
 
- **Push** - is the inverse of pull, this means to push the changes from your local
repo to a remote repo
 
- **Checkout** - This means to "switch" to a given branch
 
- **Merge Conflict** - This happens when git can't automatically figure out how to "smush"
two branches together, so it will throw a merge conflict and you have to go in and
manually specify how you want the file to look. If you follow best practices you
will mostly avoid this but they aren't scary or hard to deal with despite what
the internet would have you believe.

Now that's a lot to take in and some of it still won't make sense to you because
it's hard to understand without seeing it in action. So with that said let's start
our project.

## Your first commit.

After initializing 
