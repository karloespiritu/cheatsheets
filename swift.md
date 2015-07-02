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

## Functions

```swift
By default, function parameters are treated as constants, not variables

// simple function
func myFunction() {
  println("This is a simple function")
}
 // with 1 param, ':' memans is type of
func myFunction(name : String) {

}

func myFunction(age : Int) {
  age = age + 1 // not allowed - age is constant
}

// function with mutable parameter
func myFunction(var age : Int) { // to set fxn param as a variable
  age = age + 1                  // age va can now be updated
}

// function that return values
func myFunction() -> String {
  return "Hello"
}

// using a default value param
func myFunction(name : String = "John Doe") {
  println("Hello, \(name)")
}
// to call
myFunction("Jane") //Errror - will not work
myFunction()       //OK - uses default param value
myFunction(name:"Lucy") //OK - provide named argument
```

## Arrays
* Arrays are strongly **typed**
* Array mutability depends on using `'var' or `let`1

```swift
let daysInMonth = [34,2,34,345,45,5]
var colors = ["red","black","white"]

var bands : [String]  // array of strings
bands = ["Motorhead", "Slayer", "Cannibal Corpse"]

//adding to end of array
flavors.append("Nepolitan")   //add to end of array
flavors += ["Wintergreen"]

// Insert at specific position
flavors.insert("Coconut", atIndex: 3)
```

## Dictionaries
* AKA associative array, map, hashtable
* Dictionaries in Swift are strongly typed. All keys and values must be of a specific data type. Dictionaries with keys of different types (i.e Int or String) are not allowed.

```swift
var countries = ["US" : "United Sates", "PH" : "Philippines", "GB" : "United Kingdom"]

// declare dictionary of Int as String values
var products : [Int:String]

// Accessing dictionary values
println(countries["PH"])
// updating or inserting
countries["CA"] = "Canada"  // will change OR insert
countries.updateValue("Singapore", forKey:"SG") // longhand method of above syntax
countries.updateValue("France", forKey:"FR")

//to delete a key/value pair
countries["FR"] = nil
countries.removeValueForKey("FR")

// loop a dictionary
for (key, value) in countries {           // a tuple
  println("\(key) is short for \(value)")
}
```

## Tuples

* A collection of elements that can have different types
* Not intended to replace more formal data structures. It is intended to be a convenient way to temporarily group a few values together
* Still use `struct` or `class` for more formal data structures

```swift
var str = "Lucy"
let num = 666

var myTuple = (str, num)
var myOtherTuple = (str, num, 9876, "Evil One")

// return a tuple from a function
```swift
func getNameAndNumber() -> (name: String, number: Int) {
   return("Lucy Fer", 666)
}

// call function
let result = getNameAndNumber()
// decomposing - option 1
println("The name is \(result.0) and the number is \(result.1)")
// option 2 (using a label)
println("The name is \(result.name) and the number is \(result.number)")
// option 3, assign to a constant
let (name, number) = getNameAndNumber()
println("The name is \(name) and the number is \(number)")
```
## Optionals

* Allows variables to have no value at all
* In Swift, any kind of value can be declared as optional

```swift
var temperature : Int?    // optional Int, the `?` declares that the variable to be a valid `Int` or `nil`

temperature = 65
if temperature != nil {
  // forced unwrapping, use `!`
  println("The temperature is \(temperature!) degrees")
}

var countries = ["US" : "United Sates", "PH" : "Philippines", "GB" : "United Kingdom"]

// Optional binding
if let result = countries["XX"] {
    println("The country name is \(result)")
} else {
    println("No matching key found")
}

var result = countries["XX"]  // since XX does not exist
```

## Enumerations
* declare `enum` as capitalised

```swift
enum SeatPreference {
  case Window
  case Middle
  case Aisle
  case NoPreference
  // or: case Window, Middle, Aisle, NoPreference
}

var myPref : SeatPreference
myPref = SeatPreference.Aisle   // .Aisle for shorthand
var otherPref = .Window
```

## Closures

* Closures group code into self-contained, reusable units
* Functions are a type of closure

```swift

// a simple closure
{
  println("This is the simplest closure in the world.")
}

func performSixTimes( myClosureParameter : ()->() ) {
  for i in 1...6 {
    myClosureParameter()
  }
}

performSixTimes { ()->() in
    println("This is the simplest closure in the world.")
}



// A function that explicitly takes no parameters and returns nothing
func myFunction ()->()  // alternative way of declaring a function that returns nothing

// A closure that explicitly takes no parameters and returns no values
{ ()->() in
    println("This is a simple closure.")
}

// Using sorted function
let unsortedArray = [9182,223,1,244,227,34,11,234,44]

let sortedArray = sorted(unsortedArray, { (first : Int, second : Int) -> Bool in
  return first < second
})

sortedArray
```

## Classes
* In Swift, there is no manual memory management. It uses Automatic Reference Counting(ARC)
* Swift keeps track of whether objects are no longer needed and decides when to deallocate them
* Classes can be either a superclass(right) or subclass(left), i.e. `class AdminUser : User`. `:` character is read as `is of type`
* Add `final` before a method name, variable, or class name to prevent override of a subclass
* Unlike Objective-C, Swift classes do not inherit from a default universal base class

```swift
class User {
    // properties
    var name : String
    var age : Int

    // methods
    func description() -> String {
        return("User \(name) has the age of \(age)")
    }

    // default initializer, init is a reserved keyword
    init() {
        name = "John Doe"
        age = 20
    }

    // custom initializer with parameters
    init(name : String) {
        self.name = name    // use self to refer to current instance of this class' name
        self.age = 20
    }

    deinit {
    // any necessary cleanup code; automatically called when object reach end of its lifetime
    // takes no parameter
    // not needed for majority of classes, but useful if you have a class that iopens a connection to a database or file
    //
    }

}

//instatntiate a new Player object
var firstUser = User()

//use dot syntax
firstUser.name = "Player 1"
firstUser.age = 66
println(firstUser.description())

var secondUser = User(name: "Ozzy")
println(secondUser.description())
```

