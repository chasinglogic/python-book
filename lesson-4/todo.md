# Our first application.
Now we are going to write our first application. It's going to be a simple
command line todo app, starting in this lesson we will be working on this app
throughout the rest of the non-optional parts of this book.

First let's design our app, define a few requirements and then we can start
tackling each piece individually. Writing a paragraph about how you want the app
to work is generally how I start so I can then split it into 'tasks'.

Todo App User Story
"I run the application from the terminal and it gives me a prompt, the prompt
allows me to type in commands, [help, new <todo>, list, show <todo>], help will display
the available options and give me some info on how to use the app, new <todo name>
will create a new todo with the given name and will prompt to write a description
for the todo, list will list all the todos with an index number, and show <todo name
or index> will show the description for the indicated todo. I can then save this
todo list in various forms and load a todo into the app." 

So now that we've defined what we want to do we need to seperate this into a task
list:

Before you look at mine, try to create your own based on the above paragraph then
compare your list with mine.

>! 1. create a prompt that takes user input
>! 2. parse user input and execute the proper command
>! 3. track todos
>! 4. show todos
>! 5. list todos
>! 6. create todos
>! 7. save and load application state
>! 8. show a help message

Take a second and see how I discerned the task list. I know this isn't anything
to do (badumtsss) with coding but it's a very important skill that will take you
from someone who knows code to someone who knows how to create things.

Now that we have a defined task list and some direction we can actually begin
writing code! (Not really now we get to start bootstrapping our application. 
WOOHOO!)
