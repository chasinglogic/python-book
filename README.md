<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#to-parseltongue-in-6-lessons">1. # 0 to Parseltongue in 6 lessons</a></li>
<li><a href="#a-quick-four-word.">2. A quick four word.</a></li>
<li><a href="#a-foreword.">3. A foreword.</a></li>
<li><a href="#getting-started">4. # Getting Started</a></li>
<li><a href="#choose-your-weapon.">5. Choose your weapon.</a>
<ul>
<li><a href="#text-editor">5.1. Text Editor</a></li>
<li><a href="#python-interpreter">5.2. Python Interpreter</a></li>
<li><a href="#pip-and-virtualenv">5.3. Pip and Virtualenv</a></li>
<li><a href="#git-scm">5.4. Git SCM</a></li>
<li><a href="#coding-style-guide">5.5. Coding Style Guide</a></li>
</ul>
</li>
</ul>
</div>
</div>

<a id="to-parseltongue-in-6-lessons"></a>

# # 0 to Parseltongue in 6 lessons


<a id="a-quick-four-word."></a>

# A quick four word.

This is a book.


<a id="a-foreword."></a>

# A foreword.

This book is made to get you from knowing nothing about programming to
having a grasp on the basics and where to go from there in the shortest
amount of time possible. However, this means that the book moves at a
very quick pace and it expects you to be doing all of the homework,
typing all of the examples, and applying what you learn as you learn it.
For example when we go over if statements write your own script that's
not in the book that you come up with to test your knowledge. Debugging
is the only real way to learn programming and you have to be self
motivated to get anything from this book.


<a id="getting-started"></a>

# # Getting Started


<a id="choose-your-weapon."></a>

# Choose your weapon.


<a id="text-editor"></a>

## Text Editor

The choice of text editor is one of the most hotly debated and least
important topics in programming. For this course you will, however, need
to pick one. Personally I use [Vim](http://www.vim.org/) but I would
warn you that Vim is software that is a bit archaic and some find
complicated to use when compared to modern software. If you're looking
for a more modern editor that is an easy jumping off point I would
recommend [Atom](https://atom.io). Or if you want an
[IDE](https://en.wikipedia.org/wiki/Integrated\_development\_environment)
there is a free version of
[PyCharm](https://www.jetbrains.com/pycharm/) (an IDE is an Integrated
Development Environment, basically it has some nice tooling for python
code.)

Ultimately the choice is not that big of a deal. Pick from the list
above or find your own, there is abundance of options available and you
can always switch later. (I know I've switched multiple times!)


<a id="python-interpreter"></a>

## Python Interpreter

We will talk more about what the interpreter is and what it does later,
but for now you need to get it installed. For these lessons we will be
using CPython which is the official interpreter found at
<https://www.python.org/> download Version 3.

Note for Linux Users: If you're on a Linux Distro (woot woot) you can
use your package manager. Most major distros provide Python v3.X via a
package named python3, otherwise consult your distro's documentation.

Note for Mac Users: If you're running Mac OS X and you have
[homebrew](https://brew.sh) installed you can install python 3 via

	brew install python3


<a id="pip-and-virtualenv"></a>

## Pip and Virtualenv

These are tools we will uselater however they are pretty excellent to
have now. Pip should already be installed when you install CPython so
just upgrade it:

Mac OS X / Linux:

	pip install -U pip

Windows:

	python -m pip install -U pip


<a id="git-scm"></a>

## Git SCM

Git is a Source Code Management tool and we'll start using it at Lesson
4 so you might as well install it now.

*For Linux users* once again it's in all the standard repos so install
it using your distro package manager.

*For Mac users* git comes with xcode install xcode from the Mac App
Store and you should be good to go

*For Windows users* you can download the installer
[here](https://git-scm.com/download/win) you can just accept all the
defaults.


<a id="coding-style-guide"></a>

## Coding Style Guide

We will be coding according to the
[PEP8 Style Guide](https://www.python.org/dev/peps/pep-0008/) However
you don't really need to worry about that yet just type the examples the
way I do and you'll be fine.

Additionally we will be using the
[80 Column-rule](https://www.emacswiki.org/emacs/EightyColumnRule)
though pretty loosely.

You should turn on "Wrapping at preferred length" for whichever text
editor you chose.

And finally, the golden rule, TYPE EVERY LINE OF CODE IN THESE LESSONS.
SERIOUSLY. TYPE IT OUT. DONT COPY AND PASTE. AND DO YOUR HOMEWORK.

I've intentionally made the code samples as concise as possible, so make
sure you take the time to type them out, it will help you learn even if
you think it won't and each lesson is written assuming that you take the
time to FULLY understand the lesson prior.

Alright let's get started!
