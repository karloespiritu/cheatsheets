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


Connect to mongo

```bash
mongo --port 27017
```

Get last 10 documents in mongoDB

```bash
db.dbname.find().limit(10).sort({$natural:-1})
```

Create admin user

```bash
db.createUser({user: "myusername", pwd: "mypassword", roles: [ { role: "userRole", db:"dbname" }]})
```

