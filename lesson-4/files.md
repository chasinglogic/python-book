# Persisting to Disk
Currently our application is maintaing a state (in this case it's imply the todos
list) all inside memory while it's running, I'm sure you've noticed that once
you quit the app it loses everything you were doing. That's because when your
application ends the OS will clean up the memory and Python can't get it back
for you.

So what we have to do is save that state to disk and then be able to load it.
This is a form of Data Serialization. Working with files in python is really
easy the tricky part for some people is to realize that all files at the most
basic level are some form of plain text, even image formats like JPG are just
text in a certain way that a program knows how to draw the image. With that
in mind let's do some basic examples of file I/O (input / output) before we 
bring that into our todo app.

In a new folder let's create a file called file.py and create a text file called
sample.txt. Then put the following in the sample.txt file:

**sample.txt**
```
Sample text.
```

Then in file.py to open the file we use the open built in function:

**file.py**
```python
f = open("./sample.txt", "r")
```

`./` is a relative path indicating the present working directory (pwd) so as
long as we run this script from the same folder where sample.txt is and we're
on a unix system this will work.

Now `f` is a file object, we can get info about the file and even pull the text
from the file line by line or all at once. The "r" tells Python what we want
to do with this file, in this instance it's for read, your options are

- "r" for read only
- "w" for write only, this will overwrite an existing file.
- "a" for writing the file but appending if it exists
- "x" for write/creation and fails if file already exists
- "b" for binary mode
- "w+" for reading AND writing, you can use `a+` as well for a simliar effect but appending instead of writing.

First let's print all the text in the file:

```python
f = open("./sample.txt", "r")

print(f.read())

f.close()
```

`read()` will return all of the contents of a file as a string for you to use.


