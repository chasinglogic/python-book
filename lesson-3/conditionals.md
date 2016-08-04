# Conditionals

Conditionals (sometimes referred to as Control Flow) are ways that we can
actually make our programs do some logic. The most basic is the if statement and
it's variants which look pretty much how you'd expect.

```python
if True:
	print("True is true it turns out!")

if False:
	print("Skip me because False is false!")
```

What do you think the output will be? Type it out then run this program.

Of course using constants isn't any better since we know that True is true so in
Python we have some comparison operators that way we can determine if something
is True or not when our program is running:

```
==
```

This means "is equal to" so if you see 5 == 3 that is false but 5 == 5 is
true. You can use variables here as well that way you may not know the value
ahead of time. Let's say you have a function

```python
def comparator(x, y):
	return x == y
```

And you call it with comparator(5, 3) it will return False.

```
> or <
```

This is exactly like you remember from middle school (see programming is so easy
you learned most of this when you were 12.) "greater than" or "less than" is the
easiest 5 < 5 is false but 3 < 5 is True.

```
<= or >=
```

"Less than or equal to" or "Greater than or equal to" these are the same as
above except they also check for == so 5 < 5 is False but 5 <= 5 is True

With this in mind let's type a simple script.

```python
x = 5
y = 10

if x >= y:
	print("X is greater than or equal to y")

if x < y:
	print("X is less than y")

if x == y:
	print("X and y have the same value.")
```

Try to reason through this program before running it. Then I want you to modify
it so that all the conditionals evaluate to True (there are multiple answers but
don't just use True as a literal for all the if statements.)

# A quick aside

So when we did math operators in Lesson 1 I forgot about an operator that really
only comes into play when dealing with conditionals and that is the modulo
operator. (in python it's represented as %) 

The Modulo operator does what every Elementary math student does, long division
with a Remainder. The modulo will return that remainder

So 5 % 3 will give you 2 since 3 only "goes into" 5 once and has 2 left over.

I think putting an entire refresher on long division in here is unnecessary and
distracting so if you need one I recommend [this one](https://www.mathsisfun.com/long_division2.html)

# Back to conditioning


