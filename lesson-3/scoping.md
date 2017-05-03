<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#org660e6a9">1. Variable Scoping</a></li>
</ul>
</div>
</div>

<a id="org660e6a9"></a>

# Variable Scoping

The last topic I want to touch on in this lesson is variable scoping.
When you create a variable at the "global level" it is accesible to
anything inside the script however when you create a variable inside a
code block it is only known inside that code block.

For example:

	# This variable can be referenced anywhere
	globe_trotter = 5

	def anotherfunction():
		# this will cause the script to fail. y is not defined in this scope
		print(y)

	def afunction():
		print(globe_trotter)
		y = 10

	print(globe_trotter)
	afunction()
	anotherfunction()

This also means that anything you create inside a loop is not accessible
outside the loop. This includes the variables made in a for loop:

	some_names = ["mat", "joey", "scott"]

	for name in names:
	   # This will work since it is inside the loop
	   print(name)

	# This will fail because it is not inside the loop so name is undefined.
	print(name)

Additionally if we want to modify a global inside a function we have
to specify this using the global keyword.

	globe_trotter = 5

	def afunction():
		print(globe_trotter)
		y = 10


	def bfunction():
		global globe_trotter
		globe_trotter += 1

	afunction() # prints 5
	bfunction()
	afunction() # prints 6

global will either declare a new global or grab an existing global
variable and let you modify it.

This should be pretty simple but can lead to some gotcha moments.
