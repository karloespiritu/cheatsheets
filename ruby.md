---
layout: page
title: Ruby
permalink: /ruby/
---

##Strings

### Format String

```ruby
"doom %s %d %f" % ["ipsum", 13, 3.7]
```

### Change case

```ruby
"doom".upcase
"DOOM".downcase
"doom".capitalize
```

### Number to String

```ruby
"value: " + 66.to_s
```

### Join Strings

```ruby
%w(fall from grace).join('-') //fall-from-grace
[1, 2, 3].join('-')
```

### Split string containing a separator into array of substrings

```ruby
# ["do", "re", "", "mi"]:
"do re  mi ".split(/ /)
# ["do", "re", "mi"]:
"do re  mi ".split
```

### Split into 2 strings

```ruby
# ["", " re mi fa"]
"do re mi fa".split(/\s+/, 2)
```

### Check prefix and suffix
```ruby
'foobar'.start_with?('foo')
'foobar'.end_with?('bar')
```

## Numbers

### Quotient and remainder with single function call.

```ruby
q, r = 19.divmod(5)
# Outputs [3, 4]
```
### Power

```ruby
2**8 #Outputs 256
```

## Time

### Current datetime
```ruby
t = Time.now  # 2015-05-20 01:00:44 +0800
utc = Time.now.utc  # 2015-05-19 17:01:46 UTC
```

### Current Unix epoch

```ruby
epoch = Time.now.to_i
```

## Dictionaries

```ruby
d = {'t' => 1, 'f' => 0}

# keys are symbols:
symbol_to_int = {t: 1, f: 0}
```

## Classes

```ruby
class Song
  def initialize(title, artist, album)
    @title     = name
    @artist   = artist
    @album = album
  end
end

class InstrumentalSong < Song
  def initialize(name, artist, album, lyrics)
    super(name, artist, album)
    @lyrics = lyrics
  end
end
```
