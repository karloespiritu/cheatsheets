---
layout: page
title:  ES6
permalink: /es6/
---

## ES6 New Features:

- [arrows](#arrows)
- [classes](#classes)
- [enhanced object literals](#enhanced-object-literals)
- [template strings](#template-strings)
- [destructuring](#destructuring)
- [default + rest + spread](#default--rest--spread)
- [let + const](#let--const)
- [iterators + for..of](#iterators--forof)
- [generators](#generators)
- [unicode](#unicode)
- [modules](#modules)
- [module loaders](#module-loaders)
- [map + set + weakmap + weakset](#map--set--weakmap--weakset)
- [proxies](#proxies)
- [symbols](#symbols)
- [subclassable built-ins](#subclassable-built-ins)
- [promises](#promises)
- [math + number + string + array + object APIs](#math--number--string--array--object-apis)
- [binary and octal literals](#binary-and-octal-literals)
- [reflect api](#reflect-api)
- [tail calls](#tail-calls)

### Arrows

Arrows are a function shorthand using the => syntax.

```js
// Expression bodies
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + i);

// Statement bodies
nums.forEach(v => {
  if (v % 5 === 0)
    fives.push(v);
});

// Lexical this
var bob = {
  _name: "Bob",
  _friends: [],
  printFriends() {
    this._friends.forEach(f =>
      console.log(this._name + " knows " + f));
  }
}
```

### Enhanced Object Literals

Object literals are extended to support setting the prototype at construction,
shorthand for foo: foo assignments, defining methods and making super calls.

```js
var obj = {
    // __proto__
    __proto__: theProtoObj,
    // Shorthand for ‘handler: handler’
    handler,
    // Methods
    toString() {
     // Super calls
     return "d " + super.toString();
    },
    // Computed (dynamic) property names
    [ "prop_" + (() => 42)() ]: 42
};
```

### Template Strings

```js
let name = "Lemmy", time = "today";
`Hello ${name}, how are you ${time}?`
```

### Let + Const

Block-scoped binding constructs. `let` is the new var. `const` is single-assignment. Static restrictions prevent use before assignment.

Notes:

- You cannot change value of a `const` variable after you create it.
- `let` and `const` varaibles are never hoisted to the top of their scopes.
- `let` has major advantage of rebinding the loop variable on every iteration, so each loop get its 'own' copy, rather than the globally-scoped variable.

```js
function f() {
  {
    let x;
    {
      // okay, block scoped name
      const x = "sneaky";
      // error, const
      x = "foo";
    }
    // error, already declared in block
    let x = "inner";
  }
}
```

### Iterators + For..Of

Generalize `for..in` to custom iterator-based iteration with `for..of`.

```js
let fibonacci = {
  [Symbol.iterator]() {
    let pre = 0, cur = 1;
    return {
      next() {
        [pre, cur] = [cur, pre + cur];
        return { done: false, value: cur }
      }
    }
  }
}

for (var n of fibonacci) {
  // truncate the sequence at 1000
  if (n > 1000)
    break;
  console.log(n);
}
```

### Generators

Generators simplify iterator-authoring using `function*` and `yield`. A function declared as function* returns a Generator instance. Generators are subtypes of iterators which include additional `next` and `throw`. These enable values to flow back into the generator, so `yield` is an expression form which returns a value (or throws).

```js
var fibonacci = {
  [Symbol.iterator]: function*() {
    var pre = 0, cur = 1;
    for (;;) {
      var temp = pre;
      pre = cur;
      cur += temp;
      yield cur;
    }
  }
}

for (var n of fibonacci) {
  // truncate the sequence at 1000
  if (n > 1000)
    break;
  console.log(n);
}
```

### Unicode

Non-breaking additions to support full Unicode, including new Unicode literal form in strings and new RegExp `u`mode to handle code points, as well as new APIs to process strings at the 21bit code points level. These additions support building global apps in JavaScript.

```js
// same as ES5.1
"𠮷".length == 2

// new RegExp behaviour, opt-in ‘u’
"𠮷".match(/./u)[0].length == 2

// new form
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"

// new String ops
"𠮷".codePointAt(0) == 0x20BB7

// for-of iterates code points
for(var c of "𠮷") {
  console.log(c);
}
```

### Modules

Prior to ES6, we used libraries such as [Browserify](http://browserify.org/) to create modules on the client-side, and require in Node.js. With ES6, we can now directly use modules of all types (AMD and CommonJS).

#### Exporting in CommonJS

```js
module.exports = 1;
module.exports = { foo: 'bar' };
module.exports = ['foo', 'bar'];
module.exports = function bar () {};
```

#### Exporting in ES6

Named exports:

```js
export let name = 'Lemmy';
export let age  = 70;​​
```

Exporting a list of objects:

```js
function sumTwo(a, b) {
    return a + b;
}

function sumThree(a, b, c) {
    return a + b + c;
}

export { sumTwo, sumThree };
```

Export functions, objects and values (etc.) simply by using the export keyword:

```js
export function sumTwo(a, b) {
    return a + b;
}

export function sumThree(a, b, c) {
    return a + b + c;
}
```

Export default bindings:

```js
function sumTwo(a, b) {
    return a + b;
}

function sumThree(a, b, c) {
    return a + b + c;
}

let api = {
    sumTwo,
    sumThree
};

export default api;

/* Which is the same as
 * export { api as default };
 */
```

Reference

[Overview of ECMAScript 6 features](https://github.com/lukehoban/es6features)
