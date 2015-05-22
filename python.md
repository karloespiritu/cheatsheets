---
layout: page
title: Python
permalink: /python/
---

##Strings

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

## Dictionaries

```python
d = {'t': 1, 'f': 0}
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
