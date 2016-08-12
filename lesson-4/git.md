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

Once you're in your terminal in that folder:

````
super_todo $ git init
```

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

After initializing your local repo you'll want to add a file, the first file
that I like to make is the README, the README is a text file that gives users
and other developers an intro to your project. Our is going to be pretty simple:

README.md:
```
# Super Todo
------------
An awesome CLI tool to let you manage your todo list. Organize your life like 
it's 1999!
```

The above syntax is called markdown and if you're not familiar with it, Github
has a great resource for it [here](https://guides.github.com/features/mastering-markdown/) 
so I won't spend too much time on it.

Now that we have our first file let's run a command we will use a lot as we learn
git, `git status`

```
super_todo $ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	README.md

nothing added to commit but untracked files present (use "git add" to track)
super_todo $
```

The basic git workflow goes like this:

1. Make a change
2. Stage the change
3. Commit the change
4. Repeat above until done for the day.
5. Push your changes to the remote.

So now we have made a change by creating the README.md and you can see from
our status command that we have an **Untracked file** this means that git
won't keep track of any further changes until the file is committed. But to
commit it we need to first stage it. We do that by using the git add command
as shown in the status output 
`(use "git add <file>..." to include in what will be committed)`

```
super_todo $ git add README.md
super_todo $
```

It may look like nothing happened but if we run `git status` again:

```
super_todo $ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   README.md

super_todo $
```

You will see that we now have a **change to be committed**, git status also
shows us how to unstage a file, this isn't relevant here since we meant to do
that but it's nice to know git will show you how to undo a mistake.

So to commit our file we run git commit. Before we do that however we'll need
to configure git and tell it some info about ourselves:

```
super_todo $ git config --global user.name "Mathew Robinson"
super_todo $ git config --global user.email "youremail@example.com"
super_todo $ 
```

Substitute your information as appropriate, this is so git knows who the commit
author is. Another option you should look at settings is 
[core.editor](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#Basic-Client-Configuration)
I'll let you read the documentation yourself since you should get in the habit,
but I'll assume you know what it means and have set it going forward.

Now we can finally commit our change:

```
super_todo $ git commit
```

This will open the text editor specified by your core.editor option or by $EDITOR
if on a Unix system, you will be prompted to write a commit message; this is
so you can describe what you changed. For this change we will simply type `added
a readme`. Then save and quit your editor and you will see:

```
[master (root-commit) 9b4cec3] added a readme
 1 file changed, 4 insertions(+)
 create mode 100644 README.md
super_todo $
```

If that all happened then your doing fine, if you note we have just completed
step 3. of our basic git workflow, to save you some scrolling I'll copy it here:

1. Make a change
2. Stage the change
3. Commit the change
4. Repeat above until done for the day.
5. Push your changes to the remote.

Now we move on to step 4. which says to repeat above until done for the day.
For the sake of this chapter let's say we are done already so we can complete
our git basics. For these next commands you will need a remote repository, there
are multiple free providers but I recommend [Github](https://github.com/) since
it's easy to use and has a lot of documentation.

First create your remote repo, if you're using Github and have signed up for an
account the documentation is [here](https://help.github.com/articles/create-a-repo/)
A couple of things to note, in that documentation it advises you to initialize with
a README, don't do that since we've already created one ourselves, and if you want
to save money I advised choosing a public repo, and if you don't want to save money
I still recommend choosing a public repo.

Once you have your new repo you can get the **Clone URL** by clicking the green
button and copying the URL it gives you. Once you have that run this command
replace my URL with yours:

```
super_todo $ git remote add origin https://github.com/chasinglogic/super_todo
```

What this does and creates a remote named `origin` which points at the URL you
give it, so in my case `origin` points at `https://github.com/chasinglogic/super_todo`
origin is a special name for a remote, when you clone a repo it's automatically set
for you. If you want to see all of your remotes and their names you can run
`git remote -v`

Alright we can finally push our code up to our remote. Run the following command:

```
super_todo $ git push -u origin master
Counting objects: 3, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 315 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/chasinglogic/super_todo
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
super_todo $
```

If you check your repo in your web browser you will now see your code! Don't
worry I know this chapter seems very dense and laborious but this workflow
eventually becomes much quicker and even second nature.

Let's actually write some Python now! For real this time!
