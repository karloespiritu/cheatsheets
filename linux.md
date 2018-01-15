---
layout: page
title: Linux/Unix
permalink: /linux/
---

A list of useful commands for administering Linux/UNIX servers


## System Information

```bash
# Check system version
$ lsb_release -a  // Ubuntu

# Check disk usage
$ df -h

# Displays processor activity of your system and displays tasks managed by kernel in real time
$ top

# Outputs operating system, hostname, kernel version, date and timp, and processor.
$ uname -a

# List all system bootup messages to `stdout`
$ dmesg

# Display the system hostname
$ hostname

# Display system uptime
$ uptime

# Show who is logged on and what they are doing
$ w

# Reboot system
$ shutdown -r now
```

## Network Information
```bash
# Check active network interfaces
$ ifconfig
# Check all network interfaces
$ ifconfig -a
# Disable an interface
$ ifconfig eth0 down
# Enable an interface
$ ifconfig eth0 up
# Assign IP Address to an Interface
$ ifconfig eth0 192.168.1.12
# Change Subnet Mask of Interface eth0
$ ifconfig eth0 netmask 255.255.255.
# Change Broadcast Address of Interface eth0
$ ifconfig eth0 broadcast 192.168.1.255

# List All Network Ports
$ nestat -a
# List All TCP Ports
$ nestat -at
# List All Used TCP Ports
$ netstat -ntlp | grep LISTEN

# Display name server information for domain by querying DNS.
$ nslookup karloespiritu.com
```

## Process Management

```bash
# End a process
$ kill -9 1666

# Force kill process by name
$ killall -9 httpd

# Find process ID of a running program
$ pidof httpd

# List process in tree format
$ pstree

# Locate the binary, source, and manual page files for a command.
$ whereis nginx
```

## File Management

```bash
# Count lines of a file
$ wc -l /etc/passwd

# Output the first part of files.
$ head -10 access_log

# Show last part of a file
$ tail -2 httpd.log

# Display all files that are currently open
$ lsof

# Print the strings of printable characters of a file
$ strings my_script

# Show file status
$ stat access.log

$ Display contents of file with line numbers
$ nl my_script.rb

# Create symbolic link between files
$ ln -s target.txt symlink.txt

# List files ordered by modified time
$ ls -ltr

# To get the summary of a grand total disk usage size of a directory
$ du -sh /var/www/mysite

# List all files that are > 20MB
$ find / -type f -size +10M -exec ls -lh {} \; | awk '{ print $NF ": " $5 }'

# Find the biggest files (but not directories) in current directory
$  find . -type f -exec du -Sh {} + | sort -rh | head -n 15

# COMPRESS
# Compress files & folders
$ tar czvf archive.tgz ~/myfolder

# Compress files and exclude specific directory
$ tar czvf target.tgz --exclude='dir1' --exclude='<dir2>' /path_of_dr/to/backup

# Extract tar archive
$ tar xzvf archive.tgz

# CUT
# Display only specific column using a delimiter
$ cut -f 1 -d ':' /etc/passwd
# Display specific fields with a specified delimeter and output using custom output delimeter
$ cut -f 1,3 -d ':' --output-delimiter=' ' /etc/passwd

# SORTING
# Sort a file in ascending order
$ sort names.md

# Sort a file in descending order
$ sort -r names.md

# Sort password file by 4th field
$ sort -t: -k 4n /etc/passwd | more

# COPYING
# Copy all jpgs to a directory
$ find / -name *.jpg -type f -print | xargs tar -czvf images.tgz

# DIFF
# compare files while ignoring white space
$ diff -w list1.md list2.md

# Finding files
# list files by filename pattern
$ find -iname "log-2015*."

# RENAME
# Rename multiple files by pattern in current directory
$ rename 's/text_to_find/text_replacement/' *.html
```

## User Management

```bash
# Add user
$ adduser newuser

# Delete user
$ deluser newuser

# Grant sudo privileges to a user
$ visudo
# Then search and copy the line for --> root ALL=(ALL:ALL) ALL

# Outpust user ID, group ID,, and groups of a username
$ id username

# List usernames of users currently logged in
$ users

# Show listing of last logged in users.
$ last -n 4

# Add user to sudo group with sudo privileges
$ usermod -aG sudo <username>
```

## SSH

```bash
# Prevent timeouts in SSH
$ ssh -o ServerAliveInterval=100 user@yourdomain.com
```
