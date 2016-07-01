# Putting the FUN in FUNction

So we named this script hello.py but it doesn't really say hello, it
just prints the name we put in your_name, which isn't very exciting.

So now we are going to make our script say "Hello your_name"

To do this we are going to write a function. A function in programming
is a set of code that takes some number of arguments (sometimes called 
parameters) does something with those arguments and optionally returns
a value. If this sounds confusing, it's not once you see it in action.

We've already called a function in our last section, the print function.
Calling a function is as simple as writing the name of the function
with parentheses, then putting the arguments in those parentheses.

```python
# No arguments
print()

# With 1 argument
print("Arg1")

# With 2 arguments
print("Arg1", "Arg2")
```

Now I've snuck in one more new concept we'll need going forward,
comments. Any line in python preceded by a # symbol will be skipped
by the interpreter so you can use it write notes to yourself about
what a certain bit of code does. My personal opinion is to use comments
judiciously because it is always hard to put yourself back into the
same place you were when you wrote a bit of code. It's also nice for
others who might have to read your code in the future.

So now that we know how to call a function we need to write one
ourselves. Let's start with a function for saying hello to a name.
Add this code towards the top of your script (before your_name but 
after the shebang)

```python
def say_hello(name):
    print("Hello" + name)
```

Let's break down this new syntax.

```python
def say_hello(name):
```

*def* is a keyword in python. A keyword is a word that has special
meaning to the interpreter and cannot be used for anything execpt it's 
known use. You might also hear the term "reserved word"

The *def* keyword specifies that we are *def*-ining a function.
following the *def* we put the name of our function followed by
parens, in this case, say_hello()

Inside the parentheses we put the arguments we are expecting, in this
case we are expecting a name. Now the name of the argument isn't
important here since it will be substituted with whatever the caller
gives us. We could have easiy written:

```python
def say_hello(fart):
```

And it would still work the same.

Finally we add a : to the end of the line. This tells Python that
everything after this which is indented is part of this "code block"
or function.

```python
    print("Hello" + name)
```

Finally we write the "body" of our function. Everything after our
def line that is indented 4 spaces will be considered part of our
function so our function could be multiple lines of code.

Now let's change our print line from the last section to calling our
new function:

```python
#!/usr/bin/env python3

def say_hello(name):
    print("Hello" + name)

your_name = "Mathew"
say_hello(your_name)
```

