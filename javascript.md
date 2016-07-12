---
layout: page
title: JavaScript
permalink: /javascript/
---

## Overview

* Does not have classes, instead the class functionality is achived using object prototypes
* Functions are objects, and they can hold executable code and be passed around like any other object

## Data Types

### Primitive Types

All primitive types have literal representations of their values.

* [Boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) - `true` or `false`
* [Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number) - Any integer or floating-point numeric value
* [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) - A character or sequence of characters delimited
by either single or double quotes (JavaScript has no separate character type)
* [null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null) - A primitive type that has only one value, null
* [undefined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined) - A primitive type that has only one value, undefined (undefined is the value assigned to a variable that is not initialized)

```js
// use typeof operator to identify primitive types

console.log(typeof "Karlo"); // "string"
console.log(typeof 10); // "number"
console.log(typeof 5.1); // "number"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"

```

#### Primitive  Methods

```js
var name = "Karlo";
var lowercaseName = name.toLowerCase();  // convert to lowercase
var firstLetter = name.charAt(0);  // get first character
var middleOfName = name.substring(2, 5);  // get characters 2-4
var count = 10;
var fixedCount = count.toFixed(2);  // convert to "10.00"
var hexCount = count.toString(16); // convert to "a"
var flag = true;
var stringFlag = flag.toString(); // convert to "true"

```

### Reference Types

Reference values are instances of reference types and are synonymous with objects. Reference types do not store the object directly into the variable to which it is assigned, so the object variable doesn’t actually contain the object instance. Instead, it holds a pointer (or reference) to the location in memory where the object exists. This is the primary difference between objects and primitive values, as the primitive is stored directly in the variable.

* [Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
* [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
  - [Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function)
  - [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) (just a special kind of object)
  - [Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
  - [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)
* [Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) (new in ES6)



## Numbers

- Numbers in JavaScript are "double-precision 64-bit format IEEE 754 values", which as interesting consequences
- There's no such thing as an integer in JavaScript
- There's a built-in object, `Math` that provides advanced mathematical functions and constants:

```js
Math.sin(3.5);
var circumference = Math.PI;
```

Use `parseint()` to convert string to an integer:

```js
parseInt("123", 10); // 123
parseInt("010", 10); // 10

//If you don't provide the base, you can get surprising results in older browsers (pre-2013

parseInt("010");  //  8
parseInt("0x10"); // 16

// To convert a binary number to an integer, just change the base

parseInt("11", 2); // 3

// You can also use the unary `+` operator to convert values to numbers:
+ "42";   // 42
+ "010";  // 10
+ "0x10"; // 16
```

A special value called `NaN` (short for "Not a Number") is returned if the string is non-numeric

```js
parseInt("hello", 10); // NaN
```

## Strings

- Strings in JavaScript are sequences of [Unicode characters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#Unicode).
- More accurately, they are sequences of UTF-16 code units; each code unit is represented by a 16-bit number. Each Unicode character is represented by either 1 or 2 code units.
- Strings can be used as objects, and they have methods as well

```js
"hello".charAt(0); // "h"
"hello, world".replace("hello", "goodbye"); // "goodbye, world"
"hello".toUpperCase(); // "HELLO"
```

## Other Types

- `null` - indicates a deliberate non-value (and is only accessible through the `null` keyword)
- `undefined` - a value of type undefined that indicates an uninitialized value -- that is, a value hasn't even been assigned yet.
- `undefined` is actually a constant.

### Boolean

- Possible values are -- `true` and `false` (both of which are keywords.)
- Any value can be converted to a boolean according to the following rules:

  - `false`, `0`, empty strings (""), `NaN`, `null`, and `undefined` all become false.
  - All other values become `true`.

## Variables

- New variables in JavaScript are declared using the `var` keyword:
- In JavaScript, blocks do not have scope; ONLY functions have scope.
- So if a variable is defined using `var` in a compound statement (for example inside an if control structure), it will be visible to the ENTIRE function.
 - starting with ECMAScript 6, [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) and [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) declarations allow you to create block-scoped variables.

```js
var a;
var name = "Lemmy";
```
- `let` - declares a block scope local variable, optionally initializing it to a value
- `const` - creates a read-only reference to a value. It does not mean the value it holds is immutable, just that the variable identifier cannot be reassigned.

## Operators

- JavaScript's numeric operators are `+`, `-`, `*`, `/` and `%` -- which is the remainder operator (which is not the same as modulo.)
- Values are assigned using `=`, and there are also compound assignment statements such as `+=` and `-=`. These extend out to `x = x operator y`.
- Comparisons in JavaScript can be made using `<`, `>`, `<=` and `>=`. These work for both strings and numbers.
- Equality is a little less straightforward. The double-equals operator performs type coercion if you give it different types, with sometimes interesting results:

```js
123 == "123"; // true
1 == true; // true
```

- To avoid type coercion and make sure your comparisons are always accurate, you should always use the triple-equals operator:

```js
123 === "123"; // false
1 === true;    // false
```

- JavaScript also has [bitwise operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators).


## Control Structures

- `if` and `else`

```js
var name = "kittens";
if (name == "puppies") {
  name += "!";
} else if (name == "kittens") {
  name += "!!";
} else {
  name = "!" + name;
}
name == "kittens!!"
```

- `while` loops and `do-while` loops

```js
while (true) {
  // an infinite loop!
}

var input;
do {
  input = get_input();
} while (inputIsNotValid(input))
```

- `for` loop

```
for (var i = 0; i < 5; i++) {
  // Will execute 5 times
}
```

- `&&` and `||` operators - use short-circuit logic, which means whether they will execute their second operand is dependent on the first. This is useful for checking for null objects before accessing their attributes:

```js
var name = o && o.getName();

// Or for setting default values:
var name = otherName || "default";

// JavaScript has a ternary operator for conditional expressions:
var allowed = (age > 18) ? "yes" : "no";
```

- `switch` statement can be used for multiple branches based on a number or string:

```js
switch(action) {
  case 'draw':
    drawIt();
    break;
  case 'eat':
    eatIt();
    break;
  default:
    doNothing();
}
```

## Objects

- JavaScript objects can be thought of as simple collections of name-value pairs. As such, hashes in Perl and Ruby, and Dictionaries in Python.

- Object literal syntax is the preferred choice for creating new objects:

```js
var obj = {
  name: "Carrot",
  "for": "Max",
  details: {
    color: "orange",
    size: 12
  }
}
```

- Attribute access can be chained together:

```js
obj.details.color;      // orange
obj["details"]["size"]; // 12
```

- The following example creates an object prototype, `Person`, and instance of that prototype, `You`.

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Define an object
var You = new Person("You", 24);
// We are creating a new person named "You"
// (that was the first parameter, and the age..)
```

- For more on objects and prototypes see: [Object.prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype).

## Arrays

- Arrays in JavaScript are actually a special type of object.
- They work very much like regular objects (numerical properties can naturally be accessed only using [] syntax) but they have one magic property called `length`. This is always one more than the highest index in the array.

```js
var myArray = ["Lucy", 666, false]
myArray.length; // 3
```

- Note that `array.length` isn't necessarily the number of items in the array. Consider the following:

```js
var a = ["dog", "cat", "hen"];
a[100] = "fox";
a.length; // 101

typeof a[90]; // undefined
```

- You can iterate over an array using the following:

```js
//  slightly inefficient as you are looking up the length property once every loop.
for (var i = 0; i < a.length; i++) {
  // Do something with a[i]
}

// An improvement is this:
for (var i = 0, item; item = a[i++];) {
  // Do something with item
}

// Here we are setting up two variables. The assignment in the middle part of the for loop is also tested for truthfulness — if it succeeds, the loop continues. Since i is incremented each time, items from the array will be assigned to item in sequential order. The loop stops when a "falsy" item is found (such as undefined).
```

- Another way of iterating over an array that was added with ECMAScript 5 is `forEach()`:

```js
["dog", "cat", "hen"].forEach(function(currentValue, index, array) {
  // Do something with currentValue or array[index]
});
```

- Arrays come with a number of methods. See also the [full documentation for array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

### Array Methods

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

## Functions

- Functions are actually objects in JavaScript. The defining characteristic of a function, what distin-guishes it from any other object is the presence of an internal property named [[Call]].

- Without parentheses right after a function name, a function can be accessed as an object.

- Along with objects, functions are the core component in understanding JavaScript

- A most basic function:

```js
function add(x, y) {
  var total = x + y;
  return total;
}
```

- A JavaScript function can take 0 or more named parameters. The function body can contain as many statements as you like, and can declare its own variables which are local to that function.

- The return statement can be used to return a value at any time, terminating the function. If no return statement is used (or an empty return with no value), JavaScript returns `undefined`.

- You can call a function without passing the parameters it expects, in which case they will be set to `undefined`:

```js
add(); // NaN
// You can't perform addition on undefined
```

- You can also pass in more arguments than the function is expecting:

```js
add(2, 3, 4); // 5
// added the first two; 4 was ignored
```

- That may seem a little silly, but functions have access to an additional variable inside their body called `arguments`, which is an array-like object holding all of the values passed to the function. Let's re-write the add function to take as many values as we want:

```js
function add() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i < j; i++) {
    sum += arguments[i];
  }
  return sum;
}

add(2, 3, 4, 5); // 14
```

- JavaScript lets you call a function and call it with an arbitrary array of arguments, using the `apply()` method of any function object.

```js
avg.apply(null, [2, 3, 4, 5]); // 3.5
```

- The first argument to apply() is the object that should be treated as 'this'.

- JavaScript allows creation of anonymous functions.

```js
// This is semantically equivalent to the function avg() form

var avg = function() {
  var sum = 0;
  for (var i = 0, j = arguments.length; i < j; i++) {
    sum += arguments[i];
  }
  return sum / arguments.length;
};
```

- This is very powerful as it lets you put a full function definition anywhere that you would normally put an expression. This enables all sorts of clever tricks. Here's a way of "hiding" some local variables — like block scope in C:

```js
var a = 1;
var b = 2;

(function() {
  var b = 3;
  a += b;
})();

a; // 4
b; // 2
```

- JavaScript allows you to call functions recursively. This is particularly useful for dealing with tree structures, such as those found in the browser DOM.

```js
function countChars(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += countChars(child);
  }
  return count;
}
```

- JavaScript lets you name function expressions. You can use *named IIFEs* (Immediately Invoked Function Expressions) as shown below:

```js
var charsInBody = (function counter(elm) {
  if (elm.nodeType == 3) { // TEXT_NODE
    return elm.nodeValue.length;
  }
  var count = 0;
  for (var i = 0, child; child = elm.childNodes[i]; i++) {
    count += counter(child);
  }
  return count;
})(document.body);
```

- The name provided to a function expression as above is only available to the function's own scope. This allows more optimizations to be done by the engine and results in more readable code. The name also shows up in the debugger and some stack traces, which can save you time when debugging.

- JavaScript functions are themselves objects — like everything else in JavaScript — and you can add or change properties on them.


## Custom Objects

- JavaScript is a prototype-based language that contains no class statement, as you'd find in C++ or Java

- Instead, JavaScript uses **functions as classes**. Let's consider a person object with first and last name fields. There are two ways in which the name might be displayed: as "first last" or as "last, first".

- All objects inherit from `Object.prototype`. b=

```js
function makePerson(first, last) {
  return {
    first: first,
    last: last
  };
}
function personFullName(person) {
  return person.first + ' ' + person.last;
}
function personFullNameReversed(person) {
  return person.last + ', ' + person.first;
}

s = makePerson("Lemmy", "Kilmister");
personFullName(s); // "Lemmy Kilmister"
personFullNameReversed(s); // "Kilmister, Lemmy"
```

- This works, but it's pretty ugly. You end up with dozens of functions in your global namespace. What we really need is a way to attach a function to an object. Since functions are objects, this is easy:

```js
function makePerson(first, last) {
  return {
    first: first,
    last: last,
    fullName: function() {
      return this.first + ' ' + this.last;
    },
    fullNameReversed: function() {
      return this.last + ', ' + this.first;
    }
  };
}

s = makePerson("Lemmy", "Kilmister")
s.fullName(); // "Lemmy Kilmister"
s.fullNameReversed(); // "Kilmister, Lemmy"
```

### `Object.prototype` methods

* hasOwnProperty() - Determines whether an own property with the given name exists
* propertyIsEnumerable() - Determines whether an own property is enumerable
* isPrototypeOf() - Determines whether the object is the prototype of another
* valueOf() - Returns the value representation of the object
* toString() - Returns a string representation of the object


### `this` keyword

- Used inside a function, `this` refers to the current object. What that actually means is specified by the way in which you called that function.

- If you called it using dot notation or bracket notation on an object, that object becomes `this`. If dot notation wasn't used for the call, this refers to the *global object*.

- Note that `this` is a frequent cause of mistakes. For example:

```js
s = makePerson("Lemmy", "Kilmister");
var fullName = s.fullName;
fullName(); // undefined undefined
```

- We can take advantage of the this keyword to improve our makePerson function:

```js
function Person(first, last) {
  this.first = first;
  this.last = last;
  this.fullName = function() {
    return this.first + ' ' + this.last;
  };
  this.fullNameReversed = function() {
    return this.last + ', ' + this.first;
  };
}
var s = new Person("Lemmy", "Kilmister");
```

- We have introduced another keyword: `new`. new is strongly related to `this`. It creates a brand new *empty object*, and then calls the function specified, with this set to that new object. Notice though that the function specified with `this` does not return a value but merely modifies the `this` object. It's `new` that returns the `this` object to the calling site.

- Functions that are designed to be called by `new` are called constructor functions.

- Common practice is to **capitalize** these functions as a reminder to call them with `new`.

- Our person objects are getting better, but there are still some ugly edges to them. Every time we create a person object we are creating two brand new function objects within it — it be better if this code was shared:

```js
function personFullName() {
  return this.first + ' ' + this.last;
}
function personFullNameReversed() {
  return this.last + ', ' + this.first;
}
function Person(first, last) {
  this.first = first;
  this.last = last;
  this.fullName = personFullName;
  this.fullNameReversed = personFullNameReversed;
}
```

- That's better: we are creating the method functions only once, and assigning references to them inside the constructor.

- We can improve it by:

```js
function Person(first, last) {
  this.first = first;
  this.last = last;
}
Person.prototype.fullName = function fullName() {
  return this.first + ' ' + this.last;
};
Person.prototype.fullNameReversed = function fullNameReversed() {
  return this.last + ', ' + this.first;
};
```

- `Person.prototype` is an object shared by all instances of `Person`. It forms part of a lookup chain (that has a special name, "prototype chain"): any time you attempt to access a property of `Person` that isn't set, JavaScript will check Person.prototype to see if that property exists there instead. As a result, anything assigned to Person.prototype becomes available to all instances of that constructor via the `this` object.

- This is an incredibly powerful tool. JavaScript lets you modify something's prototype at any time in your program, which means you can add extra methods to existing objects at runtime:

```js
s = new Person("Lemmy", "Kilmister");
s.firstNameCaps(); // TypeError on line 1: s.firstNameCaps is not a function

Person.prototype.firstNameCaps = function firstNameCaps() {
  return this.first.toUpperCase()
};
s.firstNameCaps(); // "Lemmy"
```

- Interestingly, you can also add things to the prototype of built-in JavaScript objects. Let's add a `method` to `String` that returns that string in reverse:

```js
var s = "Lemmy";
s.reversed(); // TypeError on line 1: s.reversed is not a function

String.prototype.reversed = function reversed() {
  var r = "";
  for (var i = this.length - 1; i >= 0; i--) {
    r += this[i];
  }
  return r;
};

s.reversed(); // ymmeL
```

- Our new method even works on string literals!

```js
"This can now be reversed".reversed(); // desrever eb won nac sihT
```

- As I mentioned before, the prototype forms part of a chain. The root of that chain is `Object.prototype`, whose methods include toString() — it is this method that is called when you try to represent an object as a string. This is useful for debugging our Person objects:

```js
var s = new Person("Lemmy", "Kilmister");
s; // [object Object]

Person.prototype.toString = function() {
  return '<Person: ' + this.fullName() + '>';
}

s.toString(); // "<Person: Lemmy Kilmister>"
```

- Remember how `avg.apply()` had a null first argument? We can revisit that now. The first argument to apply() is the object that should be treated as `this`. For example, here's a trivial implementation of new:

```js
function trivialNew(constructor, ...args) {
  var o = {}; // Create an object
  constructor.apply(o, args);
  return o;
}
```

- This isn't an exact replica of `new` as it doesn't set up the prototype chain (it would be difficult to illustrate). This is not something you use very often, but it's useful to know about. In this snippet, `...args` (including the ellipsis) is called the "[rest arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)" — as the name implies, this contains the rest of the arguments.

Calling

```js
var bill = trivialNew(Person, "William", "Orange");
```

is therefore almost equivalent to

```js
var bill = new Person("William", "Orange");
```

- `apply()` has a similar function named `call`, which lets you set `this` but takes an expanded argument list as opposed to an array.

```js
function lastNameCaps() {
  return this.last.toUpperCase();
}
var s = new Person("Simon", "Willison");
lastNameCaps.call(s);
// Is the same as:
s.lastNameCaps = lastNameCaps;
s.lastNameCaps();
```

### `call` vs `apply` vs `bind`

Use `.bind()` when you want a function to later be called with a certain context, useful in events. Use `.call()` or `.apply()` when you want to invoke the function immediately, and modify the context.

`Call`/`apply` call the function immediately, whereas `bind` returns a function that when later executed will have the correct context set for calling the original function. This way you can maintain context in async callbacks, and events.

A simple implementation of `bind` would be:

```js
Function.prototype.bind = function (scope) {
    var fn = this;
    return function () {
        return fn.apply(scope);
    };
}
```


### Inner functions

- JavaScript function declarations are allowed inside other functions. We've seen this once before, with an earlier `makePerson()` function. An important detail of nested functions in JavaScript is that they can access variables in their parent function's scope:

```js
function betterExampleNeeded() {
  var a = 1;
  function oneMoreThanA() {
    return a + 1;
  }
  return oneMoreThanA();
}
```

- This provides a great deal of utility in writing more maintainable code. If a function relies on one or two other functions that are not useful to any other part of your code, you can nest those utility functions inside the function that will be called from elsewhere. This keeps the number of functions that are in the global scope down, which is always a good thing.


## Closures

-  The most powerful abstractions that JavaScript has to offer, but potentially confusing

```js
function makeAdder(a) {
  return function(b) {
    return a + b;
  };
}
var x = makeAdder(5);
var y = makeAdder(20);
x(6); // 11
y(7); // 27
```

- The `makeAdder` function creates a new 'adder' functions, which when called with one argument adds it to the argument that they were created with.

- A function defined inside another function has access to the outer function's variables. The only difference here is that the outer function has returned, and hence common sense would seem to dictate that its local variables no longer exist. But they do still exist — otherwise the adder functions would be unable to work. What's more, there are two different "copies" of makeAdder's local variables — one in which a is 5 and one in which a is 20.

- Here's what's actually happening. Whenever JavaScript executes a function, a 'scope' object is created to hold the local variables created within that function. It is initialised with any variables passed in as function parameters.

- This is similar to the global object that all global variables and functions live in, but with a couple of important differences:

  - firstly, a brand new scope object is created every time a function starts executing;
  - secondly, unlike the global object (which is accessible as `this` and in browsers as window) these scope objects cannot be directly accessed from your JavaScript code. There is no mechanism for iterating over the properties of the current scope object, for example.

- When `makeAdder` is called, a scope object is created with one property: a, which is the argument passed to the `makeAdder` function.

- `makeAdder` then returns a newly created function. Normally JavaScript's garbage collector would clean up the scope object created for `makeAdder` at this point, but the returned function maintains a reference back to that scope object. As a result, the scope object will not be garbage collected until there are no more references to the function object that `makeAdder` returned.

- Scope objects form a chain called the scope chain, similar to the prototype chain used by JavaScript's object system.

- A **closure** is the combination of a function and the scope object in which it was created.

- Closures let you save state — as such, they can often be used in place of objects. You can find [several excellent introductions to closures](http://stackoverflow.com/questions/111102/how-do-javascript-closures-work).

## Reference

[A re-introduction to JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)

