# A new data type.

I'm going to introduce a new data type in this chapter before we can
talk more in depth about loops and introduce the second kind of loop you
will need. This data type is called a List in Python. In other
programming languages it's called an Array so if you ever hear the word
Array know that it's like a List.

A List like it's name implies is good for holding a list of things. For
instance if we wanted to have a list of all the snakes in Ohio which
aren't poisonous:

	# This is not a complete list.
	goodness_snakes = [
	   "Midland Brownsnake",
	   "Eastern Gartersnake",
	   "Plains Gartersnake",
	]

The variable `goodness_snakes` is now of the type List and it has 3
elements. The elements of the list are **0 indexed** that is in bold
because you should remember it. What that means is that the elements in
the list have an index by which you can access them and the numbering
starts at 0. For example:

	#         0                      1                      2
	[ "Midland Brownsnake", "Eastern Gartersnake", "Plains Gartersnake"]

The length of the list is denoted by the total number of elements. So
the length is 3 but the last element is accessed by the index which is
equal to **length - 1** to access an **element** of the list you use the
syntax like so:

	# This is not a complete list.
	goodness_snakes = [
	   "Midland Brownsnake",
	   "Eastern Gartersnake",
	   "Plains Gartersnake",
	]

	print(goodness_snakes[0])

`goodness_snakes[0]` will give us the first element in the list and so
it will print "Midland Brownsnake". See if you can modify this to print
"Eastern Gatersnake"


# Final note on lists.

List elements can be of any type in python, so you can have a list of
ints, floats strings, class objects, etc. But the index by which you
access the elements is **ALWAYS** an integer.

	list_of_ints = [1, 2, 3, 4, 5]
	list_of_floats = [1.0, 2.0, 3.0, 4.0, 5.0]

so to get the number 3 out of the list of ints you would do
`list_of_ints[2]` intuitive right?&#x2026;..


# Literally for goodness\\<sub>snakes</sub>

So what if I told you to print each item in `goodness_snakes`? You could
use our new while loop to do that. Since each index is just an integer
we could **iterate** using the following:

	goodness_snakes = [
	   "Midland Brownsnake",
	   "Eastern Gartersnake",
	   "Plains Gartersnake",
	]

	i = 0
	while i < len(goodness_snakes):
	   print(goodness_snakes[i])

**NOTE** the global function len returns the length of the array

But this is what I would call a less than optimal solution since it
doesn't read very well. Your brain doesn't immediatly know what
`goodness_snakes[i]` is and since Python is all about readability we
have a much better loop for **iterating** over an **iterator**. The for
loop. Our code now now becomes:

	goodness_snakes = [
	   "Midland Brownsnake",
	   "Eastern Gartersnake",
	   "Plains Gartersnake",
	]

	for snake in goodness_snakes:
	   print(snake)

Let's take a quick second to define an iterator and break down what the
for loop is doing.

An iterator is any object (sort of like a type) that implements (has a)
next() method. List's already have this method.

What next() does is give you the next element in the iterator until you
get to the end then it returns None.

What the for loop does is on each iteration it calls iterator.next() and
assigns the return to the variable name you give it, `snake` in this
case. Then inside the loops code block you can reference that variable.

The next few sections / lessons is where the difficulty ramps up quickly
but stick with it once you get over this hump the rest becomes easy and
we can start writing real programs.
