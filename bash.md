---
layout: page
title: Bash Scripting
permalink: bash/
---

## Finding files

```bash
#find files that start with the word "text"
find -name "text"

#find only directories
find /var/log -name "syslog" -type d

#find only files
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

## Conditionals

```bash
if [ $myVar = "y" ]
then
  echo "Enter total number of items"
  read num
  if [ $num -le 0 ]
  then
     echo "Invalid count of $num was given"
  else
     ... do stuff ...
  fi
fi

```