---
layout: page
title: Mac OS X
permalink: /macosx/
---

## Show Existing Wifi Passwords in Keychain


1. Open "Keychain Access" App
2. On the left panel, highlight the "System" keychain
3. Select "Passwords" under the category
4. Double-click on the Airport network password you want to remember
5. Select the "Show password" checkbox

## Spectacle Shortcuts

Spectacle allows you to easily organize windows without using a mouse - [http://spectacleapp.com](http://spectacleapp.com).

* Move to center of screen - Cmd + Alt + C

* Move to the left half - Cmd + Alt + ←
* Move to the right half - Cmd + Alt + →
* Move to the top half - Cmd + Alt + →
* Move to the bottom half - Cmd + Alt + ↑

* Move to the upper left - Cmd + Ctrl + ←
* Move to the lower left - Cmd + Shift + Ctrl + ←
* Move to the upper right - Cmd + Ctrl + →
* Move to the lower right - Cmd + Shift + Ctrl + →

* Left Display - Cmd + Alt + Ctrl + ←
* Right Display - Cmd + Alt + Ctrl + →

## Installing MySQL, Postgresql, MongoDB, Redis, RabbitMQ

```bash
# MySQL
brew install mysql
ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents  
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist  

# Postgresql
brew install postgresql  
ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents  
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

# MongoDB
brew install mongodb  
ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents  
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist  

# Redis
brew install redis  
ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents  
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist  

# RabbitMQ
brew install rabbitmq  
ln -sfv /usr/local/opt/rabbitmq/*.plist ~/Library/LaunchAgents  
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.rabbitmq.plist
```
