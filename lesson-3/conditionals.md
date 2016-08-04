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

Now if you want to chain conditions you can do as we did above however if two of
the conditions are true (such as if x = 5 and y = 5) you will trigger two print
statements

```python
if x >= y:
	print("X is greater than or equal to y")

if x == y:
	print("X and y have the same value.")

```

Since 5 is greater than or equal to 5 and 5 is also equal to 5.

So what if you only want one print statement to fire? This is where you need an
else if statement.

```python
if x < y:
	print("X is less than Y")
else:
	print("X is greater than Y")
```

This will execute the first statement if the if is true otherwise it will execute
the else!

For example given that X = 3 and Y = 5 you will only get one line of output:

```
X is less than Y
```

And if X = 3 and Y = 3 you will still only get one line of output:

```
X is greater than Y
```

Which isn't necessarily true but it does make the above if statement evaluate to
false since 3 is not less than 3

Expanding on this we can do an else if which allows us to chain our conditions
so we can catch this edge case.

```python
if x < y:
    print("X is less than Y")
elif x == y:
    print("X is equal to Y")
else:
    print("X is greater than Y")
```

Now when we run python will check each condition in order. Here is a simple plain
english explanation of what python does here:

1. Is X less than Y?
 - If True then print "X is less than Y" then stop checking conditions
 - If False check next condition
2. Is X equal to Y?
 - If True then print "X is equal to Y" then stop checking conditions
 - If False check next condition
2. Else is a catch all, if we got here then print "X is greather than Y" then
continue on.

You should go back to our original multiple if statement script and see if you
can explain in plain English what's going on there.

# A little bit of terminology before moving on.

Real quickly I want to stop for a second and explain what some of the terminology
I've been using means. When looking at an if statement here's how you can describe
each part:

```python
#The if statement
#|-------|
   #The condition or expression
   #|---|
if x < y:
    # Some code here.
    #|---------------|
      #The code block
```

You've also seen:

```
==
<= or >=
< or >
```

Which are called comparison operators

# And now for the last bit, logical operators

This table is mostly stolen from the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) 
and I modified it for Python because it's a fantastic explanation.

|Operator|Usage|Description|
|-----------|--------|--------|
|Logical AND|expr1 and expr2|Returns expr1 if it can be converted to false; otherwise, returns expr2. Thus, when used with Boolean values, and returns true if both operands can be converted to true; otherwise, returns false.|
|Logical OR|expr1 or expr2|Returns expr1 if it can be converted to true; otherwise, returns expr2. Thus, when used with Boolean values, or returns true if either operand can be converted to true; if both can be converted to false, returns false.|
|Logical NOT|!expr|Returns false if its single operand can be converted to true; otherwise, returns true.|

Logical operators allow you to create "Compound Conditions" which looks something
like the following.

```python
if x < y and x > 0:
    print("X is a positive number that is less than Y")
elif x < y:
    print("X is less than Y but is not a positive number.")
else:
    print("X is greater than Y")
```
