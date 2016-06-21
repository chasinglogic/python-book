# Types and duck-typing

In Python there are a few "primitive types":

- *Integers*
Are simple whole numbers or "counting numbers" 1, 2, 3 but not 1.12 etc.
- *Floats*
Are numbers that contain a decimal point such as 1.23 or 2.34 or 3.14
- *Booleans*
These are True or False, you will use these a lot as switches. 
(Note: that true and false are not booleans. Capitalization matters!)
- *Strings*
Strings are "strings of characters" as a matter of fact that previous 
statement in quotes is itself a string. In Python any characters between
double quotes is considered a string.

We can store anything of these types in a variable so lets make some!
Try typing all of these into your interpreter.

```python
>>> na = "Na"
>>> batman = " Batman!"
>>> num1 = 5
>>> num2 = 6
>>> float1 = 1.2
>>> float2 = 3.14
>>> this_is_python = True
```

Now since Python is a dynamically typed language it doesn't enforce any
checks on what you can put into a variable. So a variable really is a 
generic bucket.

But what happens if you multiply a string by 16? What happens when you 
add two strings?
Try typing this into your interpreter (See if you can guess what will 
happen first):

```python
>>> na * 16 + batman
```
....

Pretty cool right? When you multiply a string, Python will create a new
string where the original is repeated that many times and adding a string
simply "mushes" the two strings together!

What if you add an integer to a string?

```python
>>> batman + 10
```

...

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Can't convert 'int' object to str implicitly
```

Whoops! It didn't like that very much! Look at the error message:

```
TypeError: Can't convert 'int' object to str implicitly
```

Can you figure out what it's telling you?

Basically, it's saying I don't know how to add an integer type to a 
string type so you've given me invalid input.

Python will do a "type conversion" for you if it's one that it knows
how to do automatically. For example adding an integer and a float:

```python
>>> num1 + float2
```

...

You got 8.14 right? That's a float! So Python knows that when adding an
int and a float to convert the int to a float first.

Generally speaking Python will do what you expect with types, but be
on the lookout for nasty TypeError's that usually means you're not
recieving a value that your expecting.

