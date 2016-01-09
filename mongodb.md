---
layout: page
title: MongoDB
permalink: /mongodb/
---

Install using Homebrew

```bash
# Update homebrew package database
$ brew update
# Install MongoDB
$ brew install mongodb

# Build MongoDB from Source with TLS/SSL Support¶
$ brew install mongodb --with-openssl
```

Uninstall using Homebrew

```
$ brew uninstall --force mongodb
```

Start & Stop using Homebrew

```bash
$ brew services start mongodb
$ brew services stop mongodb
```

Connect to Mongo

```bash
mongo --port 27017
```

Basic Shell Commands

```bash
# show help for database methods
$ db.help()
# Show help on collection methods. The <collection> can be the name of an existing collection or a non-existing collection.
$ db.<collection>.help()
# Print a list of all databases on the server.
$ show dbs
# Print a list of all collections for current database
$ show collections
# Print a list of all roles, both user-defined and built-in, for the current database.
$ show roles
# Print a list of users for current database.
$ show users
# Print the five most recent operations that took 1 millisecond or more.
$ show profile
# Execute a JavaScript file
$ load()
# Show time spent per operation per collection
$ mongotop
# Shows snapshot on MongoDB system
$ mongostat
```

Get last 10 documents in a collection

```bash
db.<collection>.find().limit(10).sort({$natural:-1})
```

Create admin user

```bash
db.createUser({user: "myusername", pwd: "mypassword", roles: [ { role: "userRole", db:"dbname" }]})
```

