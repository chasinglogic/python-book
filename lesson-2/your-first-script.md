<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgec0c5fd">1. Your first script</a></li>
</ul>
</div>
</div>

<a id="orgec0c5fd"></a>

# Your first script

Ok we're going to actually step out of the interpreter and start writing
full programs now.

First make a file named hello.py

Now open that file in your text editor and at the top write

	#!/usr/bin/env python3

This is called a *shebang line* it tells the computer what interpreter
to use when executing this script.

Next let's write a line which makes a variable for your\\<sub>name</sub> and set it
equal to a string of your name. My script now looks like this:

	#!/usr/bin/env python3

	your_name = "Mathew"

Now previously in the interpreter if you wanted to see the value of a
variable you simply typed the name of that variable and it spit it out.

If you try to do that here you will be dissapointed, when working
directly with the interpreter it behaves slightly differently than when
it is interpreting a script. Now if you want text to print to the screen
you need to use the print function.

We haven't really talked about functions yet but here's how you call
print:

	#!/usr/bin/env python3

	your_name = "Mathew"
	print(your_name)

Now if you run that you should see your name printed to the terminal
screen. You can run the script by passing it to the python3 command in
your terminal:

	$ python3 hello.py

You should see the value of your<sub>name</sub> print to the screen. In my
example this would be `Mathew`!
