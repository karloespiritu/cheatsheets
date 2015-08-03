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

## Case

```rb
case my_var
when 1..5
  puts "Number is between 1 and 5"
when 6
  puts "Number is 6"
when String
  puts "myVar is a String"
else
  puts "This is the default message"
end
```

## Ternary Operator

```rb
myNumber = 666

puts (myNumber < 666) ? "Not evil enough:(" : "Hellyeah"
```

## Loops

```rb
i = 1

# Loop until break
loop do
  i += 1
  next unless (x % 3) == 0
  puts i  
  break if i >= 15
end

# while loop
j = 1

while j <= 10
  j += 1
  next unless (j % 3) == 0
  puts j
  break if j >= 15
end

k = 1
begin
  k += 1
  next unless (k % 3) == 0
  puts k
  break if k >= 15
end while k <= 15

# until loop

m = 1
until m >= 10
  m += 1
  next unless (m % 3) == 0
  puts m  
end

# for loop
integers = [10, 11, 12, 13, 14, 15]
for integer in integers
  puts "#{number}"
end

songs = ["Stone the Crow", "Mourn", "Conjure", "Dog Tired"]
songs.each do |song|
  puts "Listening to #{song}"
end

(0..666).each do |x|
  puts "# #{x}"
end
```

## Functions

```ruby
# 'return' keyword is optional when returning values
# functions and all statement blocks implicitly return value of last statement

def product(x, y)
  x * y
end  

product 8, 9 # => 72, parentheses is optional; arguments separated by comma

# Yield
# All ruby functions have an implicit, optional block parameter
# which can be called with the 'yield' keyword

def wrap
  puts 'start of method'
  yield
  puts 'end of method'
end

wrap { puts 'incoming code block' }

# This will output:
# => start of method
# => incoming code block
# => end of method

# You can pass a block to a function
# "&" marks a reference to a passed block
def some_function(&block)
  block.call 'some_argument'
end

# You can also pass a list of arguments, which will be converted into an array
# We use the splat operator - ("*")
def users(*array)
  array.each { |user| puts user }
end

users "lucy", "cthulhu", "damien"

# => ["lucy", "cthulhu", "damien"]

```

## Classes

```ruby
# Define a class with 'class' keyword
class Song
  # A class variable, shared by all instances of this class
  @@genre = "Metal"

  # Basic initializer
  def initialize(title, artist, album  = "")
    # Assign the argument to the "title" instance variable for the instance
    @title    = title
    @artist   = artist
    # If no album given, we will fall back to the default value in the arguments list.
    @album    = album
  end

  # Basic setter method
  def title=(title)
    @title = title
  end

  # Basic getter method
  def title
    @title
  end

  # The above functionality can be encapsulated using the attr_accessor method as follows
  attr_accessor :title

  # Getter/setter methods can also be created individually like this
  attr_reader :title
  attr_writer :title

  # A class method uses 'self' to distinguish from instance methods.
  # It can only be called on the class, not in the instance.
  def self.display(msg)
    puts msg
  end  

  def genre
    @@genre
  end

end

class InstrumentalSong < Song
  def initialize(title, artist, album, lyrics)
    super(title, artist, album)
    @lyrics = lyrics
  end
end

# Instantiate a class
song1 = Song.new('Hand of Doom', 'Black Sabbath')
song2 = Song.new('Raining Blood', 'Slayer')

# Let's call a couple of methods
puts song1.genre       # => "Metal"
puts song1.title       # => "Hand of Doom"
puts song1.title = "Butchered at Birth" # => "Butchered at Birth"
puts song1.title       #=> "Butchered at Birth"
puts song2.genre       # => "Metal"
puts song2.title       # => "The Bleeding"

# Call the class method
Song.display('Test message from class') #=> "Test message from class"

# Variable's scopes are defined by the way we name them.
# Variables that start with $ have global scope
$var = "I'm a global var"
defined? $var #=> "global-variable"

# Variables that start with @ have instance scope
@var = "I'm an instance var"
defined? @var #=> "instance-variable"

# Variables that start with @@ have class scope
@@var = "I'm a class var"
defined? @@var #=> "class variable"

# Variables that start with a capital letter are constants
Var = "I'm a constant"
defined? Var #=> "constant"

```
