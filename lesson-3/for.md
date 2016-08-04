# A new data type.

I'm going to introduce a new data type in this chapter before we can talk more
in depth about loops and introduce the second kind of loop you will need. This
data type is called a List in Python. In other programming languages it's called
an Array so if you ever hear the word Array know that it's like a List.

A List like it's name implies is good for holding a list of things. For instance
if we wanted to have a list of all the snakes in Ohio which aren't poisonous:

```python
# This is not a complete list.
goodness_snakes = [
   "Midland Brownsnake",
   "Eastern Gartersnake",
   "Plains Gartersnake",
]
```

The variable `goodness_snakes` is now of the type List and it has 3 elements.
The elements of the list are *0 indexed* that is in bold because you should
remember it. What that means is that the elements in the list have an index
by which you can access them and the numbering starts at 0. For example:

```
#         0                      1                      2
[ "Midland Brownsnake", "Eastern Gartersnake", "Plains Gartersnake"]
```

The length of the list is denoted by the total number of elements. So the length
is 3 but the last element is accessed by the index which is equal to *length - 1*
to access an *element* of the list you use the syntax like so:

```python
# This is not a complete list.
goodness_snakes = [
   "Midland Brownsnake",
   "Eastern Gartersnake",
   "Plains Gartersnake",
]

print(goodness_snakes[0])
```

`goodness_snakes[0]` will give us the first element in the list and so it will
print "Midland Brownsnake". See if you can modify this to print "Eastern Gatersnake"

# Final note on lists.
List elements can be of any type in python, so you can have a list of ints, floats
strings, class objects, etc. For example:

```python
list_of_ints = [1, 2, 3, 4, 5]
list_of_floats = [1.0, 2.0, 3.0, 4.0, 5.0]
```

so to get the number 3 out of the list of ints you would do `list_of_ints[2]`
