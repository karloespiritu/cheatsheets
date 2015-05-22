---
layout: page
title: Coffeescript
permalink: /coffeescript/
---

## Install

```bash
npm install -g coffee-script
```

## Compile to JS

```bash
// watch & recompile an entire project as you work

coffee -o lib/ -cw src
```
## Join Files

Compile `.coffee` files to a single `.js` file.

```bash
coffee -j js/app.js -c src/*.coffee
```

## Syntax

### Assignment

Coffeescript:

```coffeescript
# Assignment:
number   = 42
opposite = true
```
JS:

```js
var number, opposite;

number = 42;
opposite = true;
```

### Conditions

Coffeescript:

```coffeescript
number = -42 if opposite
```

JS:

```js
var number;

if (opposite) {
  number = -42;
}
```

### Functions

Coffeescript:

```coffeescript
square = (x) -> x * x
```

```js
var square;

square = function(x) {
  return x * x;
};
```

### Arrays

Coffeescript:

```coffeescript
# Arrays:
list = [1, 2, 3, 4, 5]
```

```js
var list;
list = [1, 2, 3, 4, 5];
```

### Objects

Coffeescript:

```coffeescript
# Objects:
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x
```

JS:

```js
var math;

math = {
  root: Math.sqrt,
  square: square,
  cube: function(x) {
    return x * square(x);
  }
};
```

### Splats

Coffeescript:

```coffeescript
race = (winner, runners...) ->
  print winner, runners
```

JS:

```js
var race,
  slice = [].slice;

race = function() {
  var runners, winner;
  winner = arguments[0], runners = 2 <= arguments.length ? slice.call(arguments, 1) : [];
  return print(winner, runners);
};
```

### Existence

Coffeescript:

```coffeescript
# Existence:
console.log "I knew it!" if elvis?
```

JS:

```js
if (typeof elvis !== "undefined" && elvis !== null) {
  console.log("I knew it!");
}
```

### Array Comprehensions

Coffeescript:

```coffeescript
# Array comprehensions:
cubes = (math.cube num for num in list)
```

```js
var cubes, num;

cubes = (function() {
  var i, len, results;
  results = [];
  for (i = 0, len = list.length; i < len; i++) {
    num = list[i];
    results.push(math.cube(num));
  }
  return results;
})();
```

#### Reference

[http://coffeescript.org/](http://coffeescript.org)