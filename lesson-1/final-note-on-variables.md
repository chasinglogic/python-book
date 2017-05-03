<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#a-final-note-on-variables">1. A final note on variables</a></li>
</ul>
</div>
</div>

<a id="a-final-note-on-variables"></a>

# A final note on variables

I know it seems like we're spending a ton of time on variables but
that's because you will use them in EVERY SINGLE python program you
write.

The last couple tricks I want to show you are pretty vital so make sure
you understand all of it before moving on.

You can increment or decrement an integer / float variable like so:

	>>> num1 = 5
	>>> num1 += 1
	>>> num1
	6

If you reverse the signage you will decrement the variable:

	>>> num1 -= 1
	>>> num1
	5

You can reassign a variable to another value, and since Python is duck
typed you can reassign it to a value of a different type.

	>>> num1 = 5
	>>> num1 = "A number"

And that's completely valid (though you probably shouldn't unless you
have a very good reason.)

You can set a variable to the value of another variable then they act
indenpendently. For example:

	>>> num1 = 5
	>>> num2 = num1
	>>> num1 += 5
	>>> num1
	10
	>>> num2
	5

You can set the value of a variable to the result of an operation, such
as a function call (foreshadowing) or math. This can include another
variable as well, for example:

	>>> num1 = 5
	>>> num2 = 5
	>>> num3 = 10 + 3
	>>> num4 = num2 + 8
	>>> num3
	13
	>>> num4
	13
	>>> num2
	5
