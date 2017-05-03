# The Dictionary

Not the merriam webster kind. In Python we have the dictionary to
represent complex data structures. With what you've learned so far you
don't have a way to create a variable which represents, for example, a
person.

Let's stop and think for a moment about what describes a person on a
very simple level:

-   Full Name
-   Age
-   Eye Color
-   Hair Color
-   Has Siblings?

This is just a simple list but you could go on and on. In Python how
would we for example assign this to a variable? `me = ?` one solution
would be to track them seperately:

	full_name = "Mathew Robinson"
	age = 24
	eye_color = "Brown"
	hair_color = "Black"
	has_siblings = True

The problem is with this approach is what if you wanted multiple people?
and how do we know that the information above is related? This is the
exact problem that we solve with Dictionaries and Classes. A dictionary
is sometimes called a hashmap and all that it is is a Key => Value store
where the keys are all strings and the values can be anything. Here is
the dictionary version of the above code:

	me = {
	   'full_name': "Mathew Robinson",
	   'age': 24,
	   'eye_color': "Brown",
	   'hair_color': "Black",
	   'has_siblings': True,
	}

	# print my name
	print("My name is", me["full_name"])

	# print my age
	print("and I am", me["age"], "years old.")

The syntax for dictionaries is pretty simple. Here is a breakdown so you
understand the terminology:

	#               V This denotes the beginning of the dictionary.
	variable_name = {
		# Key Name: Value stored at that key
		#    V       V
		   'key': 'value',
		#                ^ Denotes the end of a key / value pair.
	}
	#^ This denotes the end of the dictionary

	# And just like on arrays you can declare it all on one line as well,
	variable_name = { 'key': 'value' }

The important thing to remember is keys are always strings but values
can be of any type. The way then to pull a value out is much like
accessing an index in an array except you use the key name instead of a
number:

	# prints "value"
	print(variable_name["key"])

The best part about dictionaries is that they are Iterators so you can
use them in a for loop!

	dictionary = {
	   'hello': "A greeting.",
	   'python': "A programming language.",
	   'format': "the way in which something is arranged or set out.",
	   'programming': "the act or job of creating computer programs",
	}

	for word, definition in dictionary.items():
	   print(word)
	   print("\t1.", definition)

We've snuck one more new concept into this snippet! Note the `\t` that
is called an **escape character**. Which is a fancy way to represent
invisible characters to the computer, for instance `\t` is equivalent
to the tab key. Another common example is `\n` which is a "new line"
character and is simliar to presssing enter on your keyboard. For a
full list of escape characters you can look [here](https://docs.python.org/3/reference/lexical_analysis.html#index-18)

Dictionaries are very simple and very powerful. You'll be using them
frequently throughout your python career so make sure you are very
comfortable with these before moving on.
