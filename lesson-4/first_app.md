# Your First Application

So if you recall we had a task list from the start of this lesson:

1.  create a prompt that takes user input
2.  parse user input and execute the proper command
3.  track todos
4.  show todos
5.  list todos
6.  create todos
7.  save and load application state

I like to prioritize my tasks by blockers first then least effort
second so we can save the hard stuff for last. Using this methodology
I put these tasks as the highest priority:

1.  create a prompt that takes user input
2.  parse user input and execute the proper command
3.  show a help message

With that in mind let's create our first python script named `todo.py`
that prints a little welcome message:

	#!/usr/bin/env python3

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

**NOTE:** Remember to run through the git workflow after making a change.

Now the question is how do we prompt a user for input? this is
something we haven't done yet, but after a quick google search you can
find the official Python docs on the subject [here](https://docs.python.org/3/library/functions.html#input)

The tl;dr version is:

> input([prompt])
>
> If the prompt argument is present, it is written to standard output
> without a trailing newline. The function then reads a line from input,
> converts it to a string (stripping a trailing newline), and returns
> that. When EOF is read, EOFError is raised.

And it gives the example:

	>>> s = input('--> ')
	--> Monty Python's Flying Circus
	>>> s
	"Monty Python's Flying Circus"

So for in our case we want to prompt the user for input so let's do
that. In `todo.py`:

	#!/usr/bin/env python3

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	command = input("Command: ")
	print(command)

If you run this script you will see a prompt for a command and whatever
you type will then be print back at you. So now that we are prompting
for input let's parse that input to determine what command we should
run. In `todo.py`:

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	command = input("Command: ")

	if command == "help" or command == "?":
		help()
	elif command == "new":
		print("Sorry that's not implemented yet!")
	elif command == "show":
		print("Sorry that's not implemented yet!")
	elif command == "list":
		print("Sorry that's not implemented yet!")
	elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
	else:
		print("That's not a valid command!")

So now if you type help or ? you will see a worthless help message, quit
will show you the quit message and all other commands will let you know
that they aren't implemented yet, otherwise we'll tell you it was an
invalid command.

Unfortunately our script only asks for a command once, but we want this
application to run until the user is done so to do that we use a loop!

In `todo.py`:

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
		elif command == "new":
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

The import thing to note is the addition of the break keyword to the
quit command that way our infinite loop can end. Run the script now and
you'll notice that you are continually prompted for input until you type
quit!

With that done we've successfully checked three items off of our task
list!

1.  create a prompt that takes user input
2.  parse user input and execute the proper command
3.  show a help message

Next lesson we'll be completing the tasks:

1.  create todos
2.  list todos
