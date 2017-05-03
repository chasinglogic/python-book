<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#not-an-empty-nester.">1. Not an empty nester.</a></li>
<li><a href="#multi-dimensional-arrays">2. Multi dimensional arrays</a></li>
</ul>
</div>
</div>

<a id="not-an-empty-nester."></a>

# Not an empty nester.

So far the world we've been working in is flat with simple one line code
blocks for the most part. But you can nest code blocks indefinitely. For
example you can put if's and loops in a function or if's and loops
inside of if's and loops!

	def iterate_until_two(list_of_numbers):
	   for num in list_of_numbers:
		  # If num is equal to 2 return out of the function.
		  if num == 2:
		 return

		  print(num)


	iterate_until_two([1, 3, 2, 4, 5])

Now here we used a sweet trick with the return statement to end
execution of the loop early. However Python provides us with two
keywords for controlling iteration of our loops `continue` and `break`.

-   continue will basically "skip" an iteration of the loop.
-   break will stop iteration of the loop.

For instance if we have a list of strings and want to stop when we get
the word "STOP" and we want to skip when we have the word "SKIP"

	words = [
	   "I",
	   "Have",
	   "SKIP",
	   "The"
	   "Best",
	   "SKIP",
	   "Words",
	   "STOP",
	   "Ever.",
	]

	for word in words:
	   if word == "SKIP":
		  continue

	   if word == "STOP":
		  break

	   print(word)

Try to guess what the output of this script will be. Write it down then
type in the script and run it and see how close you were.


<a id="multi-dimensional-arrays"></a>

# Multi dimensional arrays

You can also put lists inside of lists. This is called a 2 dimensional
list or array. It looks something like this:

	names = [
	   ["m", "a", "t"],
	   ["j", "o", "e"],
	   ["p", "a", "m"],
	   ["a", "n", "g", "i", "e"],
	]

	for name in names:
	   for letter in name:
		  print(letter)

	   print("")

See if you can reason about what the input will be here then type the
script like always and see if you were right. After you understand
what's going on see if you can modify the script so it won't print the
letter "a"
