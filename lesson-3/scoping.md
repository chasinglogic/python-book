# Variable Scoping
The last topic I want to touch on in this lesson is variable scoping. When you
create a variable at the "global level" it is accesible to anything inside the
script however when you create a variable inside a code block it is only known
inside that code block.

For example:

```python
# This variable can be referenced anywhere
globe_trotter = 5

def anotherfunction():
    # this will cause the script to fail. y is not defined in this scope
    print(y)

def afunction():
    print(globe_trotter)
    y = 10

print(globe_trotter)
afunction()
anotherfunction() 
```

This also means that anything you create inside a loop is not accessible outside
the loop. This includes the variables made in a for loop:

```python
some_names = ["mat", "joey", "scott"]

for name in names:
   # This will work since it is inside the loop
   print(name)

# This will fail because it is not inside the loop so name is undefined.
print(name)
```

This should be pretty simple but can lead to some gotcha moments.
