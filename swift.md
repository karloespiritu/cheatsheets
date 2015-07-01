---
layout: page
title: Swift
permalink: /swift/
---

## Overview

* Not a superset of C, unlike Objective-C
* Still influenced by C but Not C-compatible
* Statements no longer require semicolons. Semicolons are allowed, but not needed.
* No main method/function
* Swift does NOT implicitly convert values

## Variables
Note: Use `let` instead of `var` to create a constant. It is best practice to use `let` as much as possible. In Swift, `let` is immutable, `var` is mutable.

```swift
var faveNumber = 666      //type inferred as Int
var firstName = "Lucifer" // type iniferred as String
var isAwesome = true      // type inferred as Bool

// Basic data types
var myInt : Int           // type annotation (: == is of Type Int)
var myFloat : Float       // 32-bit floating point
var myDouble : Double     // 64-bit floating point

var myString : String
var myChar : Character
var myBool : Bool         // true or false
```

## Range Operators

`...` - closed range operator

```swift
//Examples
0...100   35...66   0...someVar
```

`..<` - half-open range operator. This does not include the last number on the right

```swift
0..<100   35..<66   0..<someArray.count
```


## String Interpolation
Use `\()` for string interpolation

```swift
let location = "Hell"
var temperature = 666

println("It is \(temperature) degrees today in \(location)")

let quantity = 22
let unitPrice = 45.64

println("The amount is \(Double(quantity) * price)")
```

## Conditionals
* Parentheses are not required around the condition.
* Curly braces are required around each code block.
```swift
if myVar < 666 {
  // do something
} else {
  // do something else
}
```
* Conditions must be true or false:
```swift
var x = 0 // typed as Int
if x {    //will not compile, as it is not a boolean.
  // doSomething()
}
```
* Multiple conditions
```swift
// logical AND: &&
if a > 50 && b < 80 { ... }
// logical OR: ||
if isActive || isAdmin { ... }
// use parentheses with complex conditions
if (quantity < 10 && isAvailable) || quantity >= 10 { ... }
```

## Switch Statements
* No implicit fall through from one case to another. Empty cases are not allowed.
* Use ranges for multiple values, use the `...` operator

```switch
let quantity = 5

switch quantity {
  case 1:
    println("Do this for case 1")
  case 2:
    println("Do this for case 2")
  case 3...10:    //3 dots is the range operator
    println("DO this for 3 to 10")
  default:
      break  //to explicitly end this otherwise empty case
}
```

## Loops
The preferred way is using `for-in` loop

```swift
var total = 0
for index in 1...10 {     //for each-item in some-collection
  total = total + index
}
println("The total is \(total")

var name = "karlo"
for eachChar in name {
  println(eachChar)
}

// while loop
while condition {}
  //...
}

//Do loop
do {
    // ...
} while condition  
```
