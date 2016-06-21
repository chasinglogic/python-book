# Choose your weapon.

### Text Editor The choice of text editor is one of the most hotly debated and
least important topics in programming. For this course you will, however, need
to pick one. Personally I use [[https://www.gnu.org/software/emacs/][Emacs]]
with the [[https://github.com/syl20bnr/spacemacs][Spacemacs]] package, but I
would warn you that Emacs is software that is a bit archaic and some find
complicated to use when used to modern software. If you're looking for a more
modern editor that is an easy jumping off point I would recommend
[[https://atom.io][Atom]]. If you want an
[[https://en.wikipedia.org/wiki/Integrated_development_environment][IDE]] there
is a free version of [[https://www.jetbrains.com/pycharm/][PyCharm]]

Ultimately the choice is not that big of a deal. Pick from the list above or
find your own, there is abundance of options available and you can always switch
later. (I know I've switched multiple times!)

### Python Interpreter We will talk more about what the interpreter is and what
it does later, but for now you need to get it installed. For these lessons we
will be using CPython which is the official interpreter found at
https://www.python.org/ download Version 3. 

Note for Linux Users: If you're on a Linux Distro (woot woot) you can use your
package manager. Most major distros provide Python v3.X via a package named
python3, otherwise consult your distro's documentation.

Note for Mac Users: If you're running Mac OS X and you have
[homebrew](https://brew.sh) installed you can install python 3 via

```bash 
brew install python3 
``` 

### Pip and Virtualenv 
These are tools we will uselater however they are pretty excellent to have now. 
Pip should already be installed when you install CPython so just upgrade it:

Mac OS X / Linux: 
```bash
pip install -U pip 
```

Windows: 
```bash
python -m pip install -U pip 
```

### Coding Style Guide
We will be coding according to the
[[https://www.python.org/dev/peps/pep-0008/][PEP8 Style Guide]]

Additionally we will be using the
[[https://www.emacswiki.org/emacs/EightyColumnRule][80 Column-rule]] though
pretty loosely.
You should turn on "Wrapping at preferred length" for whichever text
editor you chose.

And finally, the golden rule, TYPE EVERY LINE OF CODE IN THESE LESSONS.
SERIOUSLY. TYPE IT OUT. DONT COPY AND PASTE.

I've intentionally made the code samples as concise as possible, so
make sure you take the time to type them out, it will help you learn
even if you think it won't.

