---
layout: page
title: Bash Scripting
permalink: /bash/
---

## Basics

```bash
# Declaring a variable, no space after equal sign
variable="Hello world."

# Using the variable
echo $variable

# print an expression
echo $(( 660 + 6 ))

# Builtin variables:
echo "Last program return value: $?"
echo "Script's PID: $$"
echo "Number of arguments: $#"
echo "Scripts arguments: $@"
echo "Scripts arguments separated in different variables: $1 $2..."

# Reading a value from input:
echo "What's your name?"
read name     # no need to declare a new variable
echo Hello, $name!
```

## Conditionals

```bash
# basic if structure
if [ $username -ne $USER ]
then
    echo "Your name isn't your username"
else
    echo "Your name is your username"
fi

# conditional execution

echo "Always executed" || echo "Only executed if first command fails"
echo "Always executed" && echo "Only executed if first command does NOT fail"

# use square brackets for multiple conditions
# To use && and || with if statements, you need multiple pairs of square brackets:
if [ $userName == "lucy666" ] && [ $age -eq 15 ]
then
    echo "This will run if $userName is lucy666 AND $Age is 66."
fi

if [ $userName == "bastard21" ] || [ $userName == "evilclown" ]
then
    echo "This will run if $userName is bastard21 OR evilclown."
fi
```

## Switch Statements

```bash
case "$myVar" in
    # List patterns for the conditions you want to meet
    0) echo "There is a zero.";;
    1) echo "There is a one.";;
    *) echo "It is not null.";;
esac
```

## Loop Statements

```bash
# print variable 3 times
for myVar in {1..3}
do
    echo "$myVar"
done

# Or write it the "traditional for loop" way:
for ((i=1; i <= 3; i++))
do
    echo $i
done

# can be used to act on files..
# This will run the command 'cat' on file1 and file2
for myVar in file1 file2
do
    cat "$myVar"
done

# output from a command
# This will cat the output from ls command.
for x in $(ls)
do
    cat "$x"
done

# while loop:
while [ true ]
do
    echo "loop body..."
    break
done
```

## Functions

```bash
# define a function
function foo ()
{
    echo "Arguments work just like script arguments: $@"
    echo "And: $1 $2..."
    echo "This is a function"
    return 0
}

# alternatively, you can also just declare without the function keyword
bar ()
{
    echo "Another way to declare functions!"
    return 0
}

# Calling you function
foo "My name is" $name
```

## Finding files

```bash
# find files that start with the word "text"
find -name "text"

# find only directories
find /var/log -name "syslog" -type d

# find only files
find -type f
```

## Extract, sort and filter data

```bash
grep <someText> <fileName> = search for text in file
        -i = case insensitive
        -I = exclude binary files

grep -E ^<text> <fileName> = search start of lines with the word text
```

```bash
sort <fileName> = sort alphabetically
sort -o <file> <outputFile> = write result to a file
sort -r <fileName> = sort in reverse
sort -R <fileName> = sort randomly
```

```bash
wc <fileName> = word count

options:

  -l (lines), -w (words), -c (byte size), -m (number of characters)
```

```bash
cut = cut a part of a file

options:

  -c --> Ex, cut -c 2-5 names.txt
  (cut the characters 2 to 5 of each line)
  -d (delimiter) (-d & -f good for .csv files)
  -f (# of field to cut)
```
