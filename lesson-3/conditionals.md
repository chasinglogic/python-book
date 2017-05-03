<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgb9eb8cd">1. Conditionals</a>
<ul>
<li><a href="#org3cea6ed">1.1. Is Equal To</a></li>
<li><a href="#org8779cfb">1.2. "Less than" or "Greater Than"</a></li>
<li><a href="#org27a72d1">1.3. "Less than or equal to" or "Greater than or equal to"</a></li>
<li><a href="#org0453ffc">1.4. An example script</a></li>
</ul>
</li>
<li><a href="#org921b7c7">2. A quick aside</a></li>
<li><a href="#orgc27fde9">3. Back to conditioning</a></li>
<li><a href="#orgada2e45">4. A little bit of terminology before moving on.</a></li>
<li><a href="#orgeaa0123">5. And now for the last bit, logical operators</a></li>
</ul>
</div>
</div>

<a id="orgb9eb8cd"></a>

# Conditionals

Conditionals (sometimes referred to as Control Flow) are ways that we
can actually make our programs do some logic. The most basic is the if
statement and it's variants which look pretty much how you'd expect.

	if True:
		print("True is true it turns out!")

	if False:
		print("Skip me because False is false!")

What do you think the output will be? You can try it in your
interpreter to find out!

Of course using constant boolean values isn't that helpful since we
always know just by looking at the code whether the branch will
execute or not. To have the computer actually make decisions in Python
we have comparison operators that way we can determine if something is
True or not when our program is running. Starting with:


<a id="org3cea6ed"></a>

## Is Equal To

	==

This means "is equal to" so if you see `5 == 3` that is false but `5
== 5` is true. You can use variables with these comparators to make
decisions dynamically when you don't know the value ahead of
time. For example let's say you have a function like:

	def comparator(x, y):
		return x == y

And you call it with `comparator(5, 3)` it will return False.


<a id="org8779cfb"></a>

## "Less than" or "Greater Than"

	> or <

This is exactly like you remember from middle school (see programming is
so easy you learned most of this when you were 12.) "greater than" or
"less than" is the easiest `5 < 5` is false but `3 < 5` is True.


<a id="org27a72d1"></a>

## "Less than or equal to" or "Greater than or equal to"

	<= or >=

"Less than or equal to" or "Greater than or equal to" these are the same
as above except they also check for `= so =5 < 5` is False but `5 <= 5` is
True


<a id="org0453ffc"></a>

## An example script

With this in mind let's make a simple script called `comparators.py`:

	x = 5
	y = 10

	if x >= y:
		print("x is greater than or equal to y")

	if x < y:
		print("x is less than y")

	if x == y:
		print("x and y have the same value.")

Try to reason through this program before running it. Then I want you to
modify it so that all the conditionals evaluate to True (there are
multiple answers but don't just use True as a literal for all the if
statements.)


<a id="org921b7c7"></a>

# A quick aside

So when we did math operators in Lesson 1 I forgot about an operator
that really only comes into play when dealing with conditionals and that
is the modulo operator. (in python it's represented as %)

The Modulo operator does what every Elementary math student does, long
division with a Remainder. The modulo will return that remainder

So `5 % 3` will give you 2 since 3 only "goes into" 5 once and has 2 left
over.

I think putting an entire refresher on long division in here is
unnecessary and distracting so if you need one I recommend
[this one](https://www.mathsisfun.com/long_division2.html)


<a id="orgc27fde9"></a>

# Back to conditioning

Now if you want to chain conditions you can do as we did above however
if two of the conditions are true (such as if `x = 5` and `y = 5`) you will
trigger two print statements

	if x >= y:
		print("x is greater than or equal to y")

	if x == y:
		print("x and y have the same value.")

Since 5 is greater than or equal to 5 and 5 is also equal to 5.

So what if you only want one print statement to fire? This is where you
need an else if statement.

	if x < y:
		print("x is less than y")
	else:
		print("x is greater than y")

This will execute the first statement if the if is true otherwise it
will execute the else!

For example given that `x = 3` and `y = 5` you will only get one line of
output:

	x is less than y

And if `x = 3` and `y = 3` you will still only get one line of output:

	x is greater than y

Which isn't necessarily true but it does make the above if statement
evaluate to false since 3 is not less than 3

Expanding on this we can do an else if which allows us to chain our
conditions so we can catch this edge case.

	if x < y:
		print("x is less than y")
	elif x == y:
		print("x is equal to y")
	else:
		print("x is greater than y")

Now when we run python will check each condition in order. Here is a
simple plain english explanation of what python does here:

1.  Is x less than y?

2.  If True then print "x is less than y" then stop checking conditions
3.  If False check next condition

4.  Is x equal to y?

5.  If True then print "x is equal to y" then stop checking conditions
6.  If False check next condition

7.  Else is a catch all, if we got here then print "x is greather than y"
	then continue on.

you should go back to our original multiple if statement script and see
if you can explain in plain English what's going on there.


<a id="orgada2e45"></a>

# A little bit of terminology before moving on.

Real quickly I want to stop for a second and explain what some of the
terminology I've been using means. When looking at an if statement
here's how you can describe each part:

	#The if statement
	#|-------|
	   #The condition or expression
	   #|---|
	if x < y:
		# Some code here.
		#|---------------|
		# The code block starts here and ends on the first
		# non-idented line

you've also seen:

	==
	<= or >=
	< or >

Which are called comparison operators


<a id="orgeaa0123"></a>

# And now for the last bit, logical operators

This table is mostly stolen from the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators) and I
modified it for Python because it's a fantastic explanation.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">Operator</th>
<th scope="col" class="org-left">Usage</th>
<th scope="col" class="org-left">Description</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Logical AND</td>
<td class="org-left">expr1 and expr2</td>
<td class="org-left">Returns True if expr1 AND expr2 are both true, if expr1 is false does not evaluate expr2.</td>
</tr>


<tr>
<td class="org-left">Logical OR</td>
<td class="org-left">expr1 or expr2</td>
<td class="org-left">Returns True if expr1 OR expr2 is true, if expr1 is true does not evaluate expr2.</td>
</tr>


<tr>
<td class="org-left">Logical NOT</td>
<td class="org-left">!expr</td>
<td class="org-left">Returns True if expr is False</td>
</tr>
</tbody>
</table>

Logical operators allow you to create "Compound Conditions" which looks
something like the following.

	if x < y and x > 0:
		print("x is a positive number that is less than y")
	elif x < y:
		print("x is less than y but is not a positive number.")
	else:
		print("x is greater than y")

What's going on here is that the statement "x is a positive number
that is less than y" will only be printed if BOTH conditions are
true. That is x is less than y AND x is greater than 0. For instance
if `x = -1` and `y = 2` the condition will check

is `-1 < 2`? Yes is `-1 > 0`? No

So it returns false since both statements are not true. The reverse of
this is the or statement which checks if either condition is true so
for the example above if we wrote it as:

	if x < y or x > 0:
		print("x is a positive number or is less than y")

The condition would be evaluated to true since one side of the
condition is true.

is `-1 < 2`? Yes is `-1 > 0`? No

returns True

Now lets get to looping!
