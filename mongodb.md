---
layout: page
title: MongoDB
permalink: /mongodb/
---

Connect to mongo

```bash
mongo --port 27017
```

Get last 10 documents in mongoDB

```bash
db.agilesearch.find().limit(10).sort({$natural:-1})
```

Create admin user

```bash
db.createUser({user: "blackswan", pwd: "n3st2014", roles: [ { role: "userAdmin", db:"agilesearch" }]})
```

