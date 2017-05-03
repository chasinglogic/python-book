<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgd7ca772">1. Create and List todos</a></li>
</ul>
</div>
</div>

<a id="orgd7ca772"></a>

# Create and List todos

So continuing from last time we will be tackling:

1.  create todos
2.  list todos

To list todos we need to be able to create them so let's start there.
The basic version of this command would be `new <todo title>` to do
this we'll need to do newitional text parsing, since `new write my
book` is not equal to `new` as we were previously checking, we need a
new way to tell that I want to run the new command. Consulting the
[Python documentation](https://docs.python.org/3/library/stdtypes.html?highlight=starts#str.startswith) shows us that strings have a startswith method
that checks if a string has a prefix.

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		print("Sorry that's not implemented yet!")
		elif command == "show":
		print("Sorry that's not implemented yet!")
		elif command == "list":
		print("Sorry that's not implemented yet!")
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

Now if you run the script you can successfully run `new write my book`
and get the proper message. Now let's write our new command, when
writing CLI's of any kind I prefer to write each command as it's own
function, the first thing we need to do in our function is extract the
title of the todo from our command. Since the syntax is for our
command is always command space title then we can use this to extract
that title.

Once again we consult the [Python documentation](https://docs.python.org/3/library/stdtypes.html?highlight=starts#str.split) (Starting to see a
theme?) and see that strings have a `split()` method that we can use
to seperate our string into an array that we can use.

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	def new(command):
		parsed_args = command.split(' ')
		print(parsed_args)

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		print("Sorry that's not implemented yet!")
		elif command == "show":
		print("Sorry that's not implemented yet!")
		elif command == "list":
		print("Sorry that's not implemented yet!")
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

If you run the new `new` command you will see it prints an array of
the command where it was seperated on the space character. Now we can
use a python feature called slicing to skip the first part of the
array (which in this case is the word new that we don't need.)

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	def new(command):
		parsed_args = command.split(' ')[1:]
		print(parsed_args)

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		new(command)
		elif command == "show":
		print("Sorry that's not implemented yet!")
		elif command == "list":
		print("Sorry that's not implemented yet!")
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

The output of running our new command should look like this:

	super_todo $ python3 todo.py

	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?

	Command: new write a book
	['write', 'a', 'book']
	Command: quit
	Thanks for using Super Todo!
	super_todo $

Now we need to join our new array back into a string, in python this
is slightly strange since it's a method on strings but not on the
array itself, here is the relevant [docs](https://docs.python.org/3/library/stdtypes.html?highlight=starts#str.join). Using this info our script
looks like this:

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	def new(command):
		parsed_args = command.split(' ')[1:]
		title = ' '.join(parsed_args)
		print("Creating a new todo:", title)

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		new(command)
		elif command == "show":
		print("Sorry that's not implemented yet!")
		elif command == "list":
		print("Sorry that's not implemented yet!")
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

Going forward, I'm only going to show you the relevant function we are
working on since our script is getting rather large. Just know that
the functions all come before our programs main loop.

Ok so now we need to listen for potentially multi-line content from
our users, here is the relevant [StackOverflow](http://stackoverflow.com/questions/17016240/multiline-user-input-python) so let's write a
function to do that:

	def get_longform_user_input():
		lines = []
		line = input()

		while line != '':
		lines.append(line)
		line = input()

		return '\n'.join(lines)

A new concept in this snippet is append. Appending means to "add to
the end to". So in this instance lines is a list and we are adding
each new line of user input to this list, after we are finished we
join the list into a string and return it. Now we can update our new
function:

	def new(command):
		parsed_args = command.split(' ')[1:]
		title = ' '.join(parsed_args)
		print("Creating a new todo:", title)
		print("Write a short description for this todo. Enter an empty line when finished.")
		body = get_longform_user_input()
		return { 'title': title, 'body': body, }

Now we use our new function to get the long input into body, and then
new returns a dictionary of the title and body. Unfortunately our app
isn't keeping track of the created todo's so it just dumps them into
nothingness, let's change that:

	todos = []

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		todos.append(new(command))
		elif command == "show":
		print("Sorry that's not implemented yet!")
		elif command == "list":
		print("Sorry that's not implemented yet!")
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

Now we have a global array of todos and when the user creates a new one
we add it to the array, this won't give us persistence of todos between
runs of the application but it will give us persistence while the
application is running and I'd say that minimally viable for now.

Next lets write the command that will list our current todos:

	def list():
		for todo in todos:
		print(todo)

Since the variable todos is a global variable we can just access it
directly here in our function, this should be a pretty straight
forward function to you now.

Go ahead and test this out, make sure you add the function call to
your while loop or else the list function won't work!

Have you tested it?, alright notice how the output is pretty ugly?
that's because we are just printing the raw dictionary to the user
which is not what we want.

So let's do a little more formatted output:

	def list():
		print()
		print("Your current todo list:")
		print()
		for index, todo in enumerate(todos):
		print("\t", index + 1, todo['title'])
		print()

A couple new things in this snippet, first the [enumerate function](https://docs.python.org/3/library/functions.html#enumerate) is
another builtin function which will give you the index with the
element in your for loop.

Then we are passing multiple arguments to print so it will
automatically concatenate (combine) them for us and do type
conversions where appropriate. The reason we do index + 1 is because
as Humans we start our lists at 1 but remember that arrays are **0
indexed** so we need to add one to make it match our brains. Finally we
only want to print the title here so we get using the accessor.

With our new list function we're actually getting somewhere now! Go
ahead and try it out a few times!

Next chapter we will tackle showing todos and updating our help message
to be more helpful.
