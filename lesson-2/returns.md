<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#org3b27274">1. Return from whence you came</a></li>
</ul>
</div>
</div>

<a id="org3b27274"></a>

# Return from whence you came

In the last section I mentioned that functions can optionally return a
value and now we're going to show you how.

So like before let's define a new function, let's call it add and it
will take two arguments, sum them then return the result.

	def add(x, y):
		return x + y

Now we can do something like:

	sum = add(5, 3)
	print(sum) # prints the number 8

And since Python is duck typed we can do this as well:

	sum = add("Abraham", " Lincoln")
	print(sum) # prints Abraham Lincoln

See how x and y are simply substituted with whatever arguments are
passed into the function? Then the return value is substituted wherever
the function as called.

An important note about returns is they end execution of the function.
So that if you put any code after a return it will not be executed:

	def add(x, y):
		return x + y
		x + 10 + y # This line never gets executed.

You now have all the basics of functions! Pretty soon we'll stop
learning how to speak in Python and how to think programmatically.
