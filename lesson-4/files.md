# Persisting to Disk

Currently our application is maintaing a state (in this case it's
simply the todos list) all inside memory while it's running, I'm sure
you've noticed that once you quit the app it loses everything you were
doing. That's because when your application ends the OS will clean up
the memory and Python can't get it back for you.

So what we have to do is save that state to disk and then be able to
load it. This is a form of **Data Serialization**. Working with files in
python is really easy the tricky part for some people is to realize
that all files at the most basic level are some form of plain text,
even image formats like JPG are just text in a certain way that a
program knows how to draw the image. With that in mind let's do some
basic examples of file I/O (input / output) before we bring that into
our todo app.

In a new folder let's create a file called file.py and create a text
file called sample.txt. Then put the following in the sample.txt file:

**sample.txt**

	Sample text.

Then in file.py to open the file we use the open built in function:

**files.py**

	f = open("./sample.txt", "r")

`./` is a relative path indicating the present working directory (pwd)
so as long as we run this script from the same folder where sample.txt
is and we're on a unix system this will work.

Now `f` is a file object, we can get info about the file and even pull
the text from the file line by line or all at once. The "r" tells Python
what we want to do with this file, in this instance it's for read, your
options are

-   "r" for read only
-   "w" for write only, this will overwrite an existing file.
-   "a" for writing the file but appending if it exists
-   "x" for write/creation and fails if file already exists
-   "b" for binary mode
-   "w+" for reading AND writing, you can use `a+` as well for a simliar
	effect but appending instead of writing.

First let's print all the text in the file:

	f = open("./sample.txt", "r")

	print(f.read())

	f.close()

`read()` returns the contents of the file as a string for you to
use. An important note on the above script is the `f.close()` call, if
we forget to put this then Python never closes the file and keeps it
open in memory until our program ends. This is called a memory leak
and is very bad. As always though Python has our back and provides
functionality called a Context Manager which open is. So we can do
this instead:

**files.py**

	with open("./sample.txt", "r") as f:
		print(f.read())

Now Python will make sure the file gets cleaned up appropriate for us
and we don't have to remember to do anything!

Using a different "file mode" we can instead write to the file:

**files.py**

	with open("./sample.txt", "w") as f:
		f.write("Not sample text.")

Now if you open the text file:

**sample.txt**

	Not sample text.

`w` mode will always replace the existing file. For a more in depth
explanation here are the [Official Python Docs on open](https://docs.python.org/3/library/functions.html#open).

With this new found knowledge in mind let's go back to our todo app:

**todo.py**

	#!/usr/bin/env python3

	def help():
		print("Available commands are new, show, list, and quit.")

	def print_todo(todo):
		print()
		print("Title:")
		print(todo["title"])
		print()
		print("Description:")
		print(todo["body"])
		print()

	def show(command):
		parsed_args = command.split(' ')[1:]
		target = ' '.join(parsed_args)

		try:
		idx = int(target)
		print_todo(todos[idx - 1])
		except ValueError:
		for todo in todos:
		if todo["title"] == target:
			print_todo(todo)
			return

	def get_longform_user_input():
		lines = []
		line = input()

		while line != '':
		lines.append(line)
		line = input()

		return '\n'.join(lines)

	def new(command):
		parsed_args = command.split(' ')[1:]
		title = ' '.join(parsed_args)
		print("Creating a new todo:", title)
		print("Write a short description for this todo. Enter an empty line when finished.")
		body = get_longform_user_input()
		return { 'title': title, 'body': body, }

	def list():
		print()
		print("Your current todo list:")
		print()
		for index, todo in enumerate(todos):
		print("\t", index + 1, todo['title'])
		print()

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	todos = []

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		todos.append(new(command))
		elif command.startswith("show"):
		show(command)
		elif command == "list":
		list()
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		break
		else:
		print("That's not a valid command!")

So all of our application state is stored in the global todos variable
and somehow we need to save that state to disk and load it back from
disk when we are done. But the list is a **data structure** and so we
need to convert it to and from text. This is called **data
serialization** - the process of translating data structures or object
state into a format that can be stored.

We are going to store our state using JSON which is a very popular and
simple serialization format. JSON stands for
<b>J</b>ava<b>S</b>cript
<b>O</b>bject <b>N</b>otation so
as you can imagine it has it's roots in web development.

Luckily the Python standard library includes a way for us to do
this. At the top of our script let's import it:

**todo.py**

	import json

This is importing a library named `json`. A library is someone
else's code that you didn't write but have access to. Libraries and
how Python resolves imports are topics which we'll cover in lesson 6
for now let's just go with the magic.

To access functions from inside of the library we simply predicate
their names with the library name and a dot. Let's add two new
functions to our todo app:

	def load_todos():
		global todos
		# Use a try except block, that way if the file doesn't already
		# exist our program doesn't crash
		try:
		with open("./todos.json", "r") as f:
			todos = json.load(f)
		except:
		todos = []



	def save_todos():
		with open("./todos.json", "w") as f:
		json.dump(todos, f)

Now we need to add these to our main loop, it will look like so:

	load_todos()

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		todos.append(new(command))
		elif command.startswith("show"):
		show(command)
		elif command == "list":
		list()
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		save_todos()
		break
		else:
		print("That's not a valid command!")

You can remove the old `todos = []` line as it's no longer
necessary. With that our app now saves and loads state from the hard
drive! Whew, let's take a break and admire our hard work:

**todo.py**

	#!/usr/bin/env python3

	import json

	def help():
		print("Available commands are new, show, list, and quit.")

	def print_todo(todo):
		print()
		print("Title:")
		print(todo["title"])
		print()
		print("Description:")
		print(todo["body"])
		print()

	def show(command):
		parsed_args = command.split(' ')[1:]
		target = ' '.join(parsed_args)

		try:
		idx = int(target)
		print_todo(todos[idx - 1])
		except ValueError:
		for todo in todos:
			if todo["title"] == target:
			print_todo(todo)
			return

	def get_longform_user_input():
		lines = []
		line = input()

		while line != '':
		lines.append(line)
		line = input()

		return '\n'.join(lines)

	def new(command):
		parsed_args = command.split(' ')[1:]
		title = ' '.join(parsed_args)
		print("Creating a new todo:", title)
		print("Write a short description for this todo. Enter an empty line when finished.")
		body = get_longform_user_input()
		return { 'title': title, 'body': body, }

	def list():
		print()
		print("Your current todo list:")
		print()
		for index, todo in enumerate(todos):
		print("\t", index + 1, todo['title'])
		print()

	print("""
	Welcome to Super Todo! This is a CLI to organize your life like it's 1999!
	Just type a command to get started, if you need to know what commands are
	available then just type help or ?
	""")

	def load_todos():
		global todos
		try:
		with open("./todos.json", "r") as f:
			todos = json.load(f)
		except:
		todos = []

	def save_todos():
		with open("./todos.json", "w") as f:
		json.dump(todos, f)

	load_todos()

	while True:
		command = input("Command: ")

		if command == "help" or command == "?":
		help()
		elif command.startswith("new"):
		todos.append(new(command))
		elif command.startswith("show"):
		show(command)
		elif command == "list":
		list()
		elif command == "quit" or command == "exit":
		print("Thanks for using Super Todo!")
		save_todos()
		break
		else:
		print("That's not a valid command!")

You have successfully wrote your first app!
