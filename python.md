---
layout: page
title: Python
permalink: /python/
---

## Strings

### Format String

```python
"doom %s %d %f" % ("metal", 13, 3.7)
```

### Translate case

```python
"doom".upper()
"DOOM".lower()
"doom".capitalize()
```

### Number to String

```python
"value: " + str(66)
```

### Join Strings

```python
'-'.join(['do', 're', 'mi', 'fa']) # do-re-mi-fa
```

### Split string containing a separator into array of substrings

```python
# ["do", "re", "", "mi"]:
'do re  mi '.split(' ')
# ["do", "re", "mi"]:
'do re  mi '.split()
```

### Check prefix and suffix
```python
'foobar'.startswith('foo')
'foobar'.endswith('bar')
```

## Numbers

### Quotient and remainder with single function call.

```python
q, r = divmod(13, 5)
# Outputs [3, 4]
```
### Power

```python
2**8 #Outputs 256
```

## Time

### Current datetime
```python
import datetime

t = datetime.datetime.now(  # 2015-05-20 01:00:44 +0800
utc = datetime.datetime.utcnow()  # 2015-05-19 17:01:46 UTC
```

### Current Unix epoch

```python
import datetime

t = datetime.datetime.now()
epoch = int(t.strftime("%s"))
```

## Tuples
Tuples consist of a number of values separated by commas. They are useful for ordered pairs and returning several values from a function.

```python
empty_tuple = ()
single_item_tuple = ("corpse",)   # take not of the comma!
my_tuple1 = 33, 666, 'a'
my_tuple2 = (22, 444, 'b')

# accessing a tuple
my_tuple1[1]  # returns 33
```

## List

```python
# define a list
my_list = [6, 5, 'x', 4, 'y']

# access an item list
my_list[0]  # returns 6

# slicing
my_list[1:3]  # returns [5, 'x']
my_list[2:]   # returns ['x', 4, 'y']
my_list[:2]   # returns [6, 5]
my_list[2:-1] # returns 6

# length
len(my_list)  # returns 5

# sort
my_list.sort()  # [4, 5, 6, 'x', 'y']

# add
my_list.append(45)  # [4, 5, 6, 'x', 'y', 45]

# return & remove
my_list.pop()   # returns 45   [4, 5, 6, 'x', 'y']
my_list.pop(1)  # returns 5    [4, 6, 'x', 'y']

# insert
my_list.insert(2, 'z')   # [4, 'z', 6, 'x', 'y']
my_list.remove('x')      # [4, 'z', 6, 'y']
del my_list[0]           # ['z', 6, 'y']

# concatenation
my_list + [0]     # returns ['z',6,'y',0]    ['z',6,'y']

# finding
9 in my_list      # returns True             ['z',6,'y']
```

## Dictionaries

```python
empty_dict = {}

# Here is a prefilled dictionary
filled_dict = {"one": 1, "two": 2, "three": 3}

# Look up values with []
filled_dict["one"]   # => 1

# Get all keys as a list with "keys()"
filled_dict.keys()   # => ["three", "two", "one"]
# Note - Dictionary key ordering is not guaranteed.

# Get all values as a list with "values()"
filled_dict.values()   # => [3, 2, 1]
```

## Control Flow

```python
# declare a variable
my_var = 6

# if statement. Indentation is significant in python!
# prints "my_var is smaller than 10"
if my_var > 10:
    print "my_var is totally bigger than 10."
elif my_var < 10:  # elif clause is optional.
    print "my_var is smaller than 10."
else:           # This is optional too.
    print "my_var is indeed 10."
```

## Loops

```python
# iterate over a list using 'for'
for song in ["Angel of Death", "Necrophobic", "Altar of Sacrifice"]:
    # You can use {0} to interpolate formatted strings.
    print "{0} is a track in Reign In Blood".format(song)

for i in range(5):
    print i
```

```python
# iterate using 'while'
x = 0
while x < 5:
    print x
    x += 1  # shorthand for x = x + 1
```

## Exceptions

Works on Python 2.6 and up:

```python
try:
    # Use "raise" to raise an error
    raise IndexError("This is an index error")
except IndexError as e:
    # Pass is just a no-op. Usually you would do recovery here.
    pass
except (TypeError, NameError):
    # Multiple exceptions can be handled together, if required.
    pass
else:
    # Optional clause to the try/except block. Must follow all except blocks
    # Runs only if the code in try raises no exceptions
    print "All good!"
finally:
    #  Execute under all circumstances
    print "We can clean up resources here"


# Instead of try/finally to cleanup resources you can use a with statement
with open("file.txt") as f:
    for line in f:
        print line
```

## Classes

```python
#!/usr/bin/python

class Song(object):

   def __init__(self):
      self.artist = "Slayer"
      self.title = "Altar of Sacrifice"
      self.album = "Reign in Blood"

   def showTitle(self):
      print self.title

   def showArtist(self):
      print self.artist

song = Song()

song.showTitle()
song.showArtist()
```
