---
layout: page
title: Regular Expressions
permalink: /regex/
---

Some of the useful and common Regex patterns

```bash
//match a proper username; can contain letter, number, underscore, or hyphen and between 3-16 characters
/^[a-z0-9_-]{3,16}$/

//match an email
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

//match a URL
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

//match an IP address
/^(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/


//match an HTML tag
/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

//match a complex password; Only accept a string with 1 uppercase alphabet, 1 lowercase alphabet, 2

//match emojis
/([\uE000-\uF8FF]|\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDDFF])/g

//match ascii characters
/[^\x00-\x7F]/g

```