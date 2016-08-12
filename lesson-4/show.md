# Showing a todo

So just so we're on the same page here is a dump of the current full script:

**todo.py**
```python
#!/usr/bin/env python3

def help():
    print("Available commands are new, show, list, and quit.")

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
    elif command == "show":
        print("Sorry that's not implemented yet!")
    elif command == "list":
        list()
    elif command == "quit" or command == "exit":
        print("Thanks for using Super Todo!")
        break
    else:
        print("That's not a valid command!")
```

Alright moving on to our show command, like all the other's let's think about
how we need to accomplish the task then write the function.

We want the user to be able to say `show 1` to show the first todo or to type
`show write a book` to reference it by title, so we need to be able to determine
if they entered an integer or not, and if not we need to search through the todos
by title.

```python
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
```

Once again we've introduced a couple of new concepts here, first we are using
a try except block. If you've noticed whenever you've had a stack trace in your
program and it crashed Python told you about some kind of error, like a 
TypeError from Lesson 1. What a try except block does is it will try the code in
the try code block and if an exception is thrown the except block will catch it,
you can use this so your program can recover from errors. Here we are using it to
catch a specific kind of error a `ValueError` which is what is thrown by int()
when you give it something it cannot convert. The easiest way to find this is by
trying it in your python interpreter:

```
>>> int("mathew")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'mathew'
>>>
```

if a ValueError is thrown then we know tha the user didn't input a number so
we then iterate over our todos looking for a title which matches the input. We
then return out of the function once we find a match so we don't keep iterating
over todos that we don't need. 

The last thing we want to accomplish is to make our help message more helpful,
now that we know how each command will work we can write better help docs.
I'll let you figure this out since it's your application, just think about it
from the perspective of someone who's never used a CLI before.

In the next section we'll save our application state between runs.
