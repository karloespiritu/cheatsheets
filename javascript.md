---
layout: page
title: JavaScript
permalink: /javascript/
---

## Data Types

* Number
* String
* Boolean
* Function
* Object
  - Function
  - Array (just a special kind of object)
  - Date
  - RegExp
* Symbol (new in ES6)

## Closure
* If a function is defined inside another function, the inner function has access to all of the outer function's variables, even after the outer function has returned.

```js
function printName(name){
    var greeting = "Hello, " + name + "!";
    // Inner functions are put in the local scope by default, as if they were
    // declared with `var`.
    function inner(){
        console.log(greeting);
    }
    setTimeout(inner, 2000);
    // setTimeout is asynchronous, so the printName function will
    // exit immediately, and setTimeout will call inner afterwards. However,
    // because inner is "closed over" printName, inner still has
    // access to the `greeting` variable when it is finally called.
}
```

## Array Methods

* `a.toString()` - Returns a string with the toString() of each element separated by commas.
* `a.toLocaleString()` - Returns a string with the `toLocaleString()` of each element separated by commas.
* `a.concat(item1[, item2[, ...[, itemN]]])`
* `a.join(sep)`
* `a.pop()`
* `a.push(item1, ..., itemN)`
* `a.reverse()`
* `a.shift()`
* `a.slice(start, end)`
* `a.sort([cmpfn])`
* `a.splice(start, delcount[, item1[, ...[, itemN]]])`
* `a.unshift([item])`

##
