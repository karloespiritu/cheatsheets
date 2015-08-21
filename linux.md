---
layout: page
title: Linux/Unix
permalink: /linux/
---

A list of useful commands for administering Linux/UNIX servers

```bash
# Check disk usage
$ free -h

# Display all files that are currently open
$ lsof

# Show time since system is running
$ uptime

# Display all currently logged in users
$ w

# List files ordered by modified time
$ ls -ltr

# List all files that are > 20MB
$ find / -type f -size +10M -exec ls -lh {} \; | awk '{ print $NF ": " $5 }'

# Displays processor activity of your system and displays tasks managed by kernel in real time
$ top

# Compress files & folders
$ tar czvf archive.tgz ~/myfolder
# Extract tar archive
$ tar xzvf archive.tgz

# List all system bootup messages to `stdout`
$ dmesg

# Display the system hostname
$ hostname

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

#  Display name server information for domain by querying DNS.
$ nslookup karloespiritu.com

# Force kill a process by name
 $ killall -9 process_name

```
