---
layout: page
title: Curl
permalink: /curl/
---

## Verbose Output (-v)

```bash
curl  -v http://karloespiritu.com
```

## Get Request

```bash
curl -kv "https://karloespiritu.com/?foo=bar&memento=mori"
```

## POST or PUT Request

```bash
curl -k -H "Content-Type: application/json" -X POST -d '{"name":"hello","value":"world"}' https://httpbin.org/post
```

```bash
curl -X "PUT"
```
for a PUT request

##Request with Basic Auth

```bash
curl -vvv -u karlo@httpbin.org:mypass http://httpbin.org/basic-auth
```

## Download Files

```bash
curl -LOk  https://raw.github.com/username/reponame/master/filename
```