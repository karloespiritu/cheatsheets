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
// Examples
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

### Conditions must be true or false:

```swift
var x = 0 // typed as Int
if x {    //will not compile, as it is not a boolean.
  // doSomething()
}
```

### Multiple conditions

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

```swift
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
By default, function parameters are treated as constants, not variables

```swift

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
myFunction("Jane")      // Errror - will not work
myFunction()            // OK - uses default param value
myFunction(name:"Lucy") // OK - provide named argument
```

## Arrays
* Arrays are strongly **typed**
* Array mutability depends on using `var` or `let`

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
for (key, value) in countries {          // a tuple
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
* Class-level methods and properties are called type properties and type methods respectively; declared using `class` keyword at the beginning of property/method

```swift
class User {
    // STORED properties
    var firstName : String
    var lastName : String
    var score : Int

    // COMPUTED properties, get & set blocks are optional and can be omitted
    var fullName : String {
            // return the computed propery
            return firstName + " " + lastName
    }

    // methods
    func description() -> String {
        return("User \(firstName) has the score of \(score)")
    }

    // default initializer, init is a reserved keyword
    init() {
        firstName = "John"
        lastName = "Doe"
        score = 0
    }

    // custom initializer with parameters
    init(first : String, last : String) {
        self.firstName = first    // use self to refer to current instance of this class' name
        self.lastName = last
        self.score = 20
    }

    deinit {
    // any necessary cleanup code; automatically called when object reach end of its lifetime
    // takes no parameter
    // not needed for majority of classes, but useful if you have a class that iopens a connection to a database or file
    //
    }

}

// instatntiate a new Player object
var firstUser = User()

// use dot syntax
firstUser.firstName = "Player 1"
firstUser.score = 66
println(firstUser.description())

var secondUser = User(first: "Ozzy", last: "Osbourne")
println(secondUser.fullName)

class EliteUser : User {
    //additional properties
    var userLevel : String

    // override required when you subclass a superclass because an init() already exists in the superclass
    override init() {
        userLevel = "Elite"
        super.init()  //this is required to also initialize the superclass variables
    }

    override func description() -> String {
        let originalMessage = super.description()
        return("\(originalMessage) and is a \(userLevel) user")
    }

    // additional methods
    func calculateBonus() {
        self.score += 1000
        println("New score is \(self.score)")
    }
}

var newPlayer = EliteUser()
newPlayer.description()
newPlayer.calculateBonus()
```

### Lazy properties
* Using a lazy property, Swift won't bother initializing until someone attempts to access it

```swift
import UIKit

class Gamer {
    // properties
    var name : String = "John Doe"
    var score = 0
    lazy var bonus = getDailyRandomNumber()

    // methods
    func description() -> String {
        return("Player \(name) has a score of \(score)")
    }

}

var anotherGamer = Gamer()
println(anotherGamer.bonus)
```

### Property Observers
* These are added to properties to monitor changes to state of objects and automatically run some code whenever a property value changes

```swift
class Gamer {
    // properties
    var name : String = "John Doe" {
        // these two methods are automatically called when the poroperty name changes
        willSet {
            // called just before the property changes
            //'newValue is an implict parameter
            println("About to chnage name to \(newValue)")
        }
        didSet {
            // called right after the property changes
            // oldValue is an implicit parameter
            println("Have changed name from \(oldValue)")
        }
    }
    var score = 0
    lazy var bonus = getDailyRandomNumber()

    // methods
    func description() -> String {
        return("Player \(name) has a score of \(score)")
    }

}

var anotherGamer = Gamer()
anotherGamer.name = "Kerry King"
```

### Access Levels

* `private` - only accessible within the same source code file
* `internal` - This is the default, and means the class, method, or property is accessible across mutiple code files but must be compiled together into the same module.
* `public` - accessible from any module that has imported your code

## Structures

* In Swift, structures and class are very similar to each other. In other languages, structures are just simple containers for a few pieces of data. They don't have methods.
* Structures in Swift can have methods, properties, computed properties, property observers. They can also have initializers.
* Int, Bool, String, Array, Dictionaries, Double, Float, etc. are all implemented as structures in Swift
* Structures in Swift have member-wise initializers, where you can provide arguments for each property of the structure
* Structs have some limitations:
  - do not take part in inheritance
  - cannot use deinitializers
* Structures are still intended for straight-forward data structure tasks. In general, use structures when internal properties are all simple value types such as `String`, `Int`, `Bool`, and `Float`.
* As a general rule, if you would implement a structured data as a class in other languages, do the same in Swift.

### Structures Vs Classes

* Structures are value types (pass by value).
  - When assigned to another variable. or passed to a function, a structure's value is *copied*

* Classes are reference types (pass by reference)
  - When assigned to another variable, or passed to a function, a *reference to the original object* is passed

```swift
//Pass by value
//function that changes an Int
func changeValue(var number : Int) -> Int {
    number += 1000
    return number
}
var myNumber = 666

//define an Int variable (value type)
changeValue(myNumber)

//original var is unchanged = 666
myNumber
```

```swift
// Pass by reference
class SimpleClass {     //change class to struct will keep original value of 'value'
  var value : Int = 99
}

// Simple function that chnages an object
func changeObject(var object : SimpleClass) -> Int {
  object.value += 1000
  return object.value
}
// create a new instance (reference type)
var myObject = SimpleClass()

// pass the object into the function - Pass By Reference
changeObject(myObject)

// the original object has been changed.
myObject.value
```

## Operators
* Swift requires whitespace to be balanced around operators
* Swift does not allow values to overflow, but if needed *overflow operators* are available:
```
&+ &- &* &/ &%
```

### Equality and Identity
* With objects, can also check identity (the same object).

```swift
// Note: this will not work on structures, only on objects
===    // identical to
!==     // not identical to
```

```swift
var dateA = NSDateComponents()
dateA.year = 2015
dateA.month = 01
dateA.day = 01

var dateB = NSDateComponents()
dateB.year = 2015
dateB.month = 01
dateB.day = 01

// check equality: ==
if dateA == dateB {
    println("Yes dateA and dateB are equal to each other")
}

// check Identity
if dateA === dateB {
    println("Yes dateA and dateB are equal to each other")
} else {
    println("They might be equal, but not identical")
}
```

### Advanced Operators

* Nil coalescing operator - `??`
  - used to assigned values to a variable depending if it is a nil or has a value
```swift
var personalSite : String?
let defaultSite = "http://example.com"

var website = personalSite ?? defaultSite
```

* Remainder operator - `%`
  - can also work with negative numbers and floats, unlike in other languages where only positive integers are allowed

## Advanced Language Features

### Type Casting & Casting

* There are times when the data types you use needs to be treated as a different data type.
* Use `?` and `!` to check and unwrap properties of a variable typecasted to a different object type

```swift
let myButton    = UIButton()
let mySlider    = UISlider()
let myTextField = UITextField()
let myDatePicker = UIDatePicker()

let controls = [myButton, mySlider, myTextField, myDatePicker]

for item in controls {
    //option 1: check type with "is"
//    if item is UIDatePicker {
//        println("We have a UIDatePicker")
//        // downcast with "as"
//        let picker = item as UIDatePicker
//        picker.datePickerMode = UIDatePickerMode.CountDownTimer
//    }
    // option 2: try to downcast with as?
//    let picker = item as? UIDatePicker
//    //then check if works, and unwrap the original
//    if picker != nil {
//        // use ! to force unwrap it to get to its properties
//        picker!.datePickerMode = UIDatePickerMode.CountDownTimer
//    }
    // option 3 - most succint way, combination of option 1 & 2
    if let picker = item as? UIDatePicker {
        picker.datePickerMode = UIDatePickerMode.CountDownTimer
    }
}
```

### AnyObject and Any

* Use `AnyObject` and `Any` when dealing with non-specific data
* Important reason for this types is when working with existing frameworks for Cocoa. It is very common for this frameworks' existing methods to get back an array. Objective-C does not have typed arrays. The default array in Objective-C is `NSArray` can hold any type of object at any position. In Swift, when you use existing frameworks, what you get returned is an array of any objects.
* Objective-C `id` maps to Swift `AnyObject`
* Use `is`, `as`, `as?` to check and downcast types into something more specific
* As long as you have an import statement to frameworks such as `UIKit`, Swift `String`, which are structures and not objects, is bridged to Objective-C's `NSString` Object
* Only tupes and closres are not allowed to be assigned as `AnyObject`

```swift
var someObject : AnyObject  // needs to be an object
var something : Any         // means any object or any data type

var arrayOfObjects : [AnyObject]    // array of any type of objects
var arrayOfAnything : [Any]         // array of any type of objects or non-object types including tuples, closures
```

```swift
import UIKit

someObject = "This is a simple message"
someObject = 666

if someObject is String {
    let wordsArray = someObject.componentsSeparatedByString(" ")
}
```

### Protocols

* A protocol in Swift is way to standardize some behaviour across classes without worrying about inheritance or any formal relationship
* It is simply a list of methods that you want some class to perform and properties a class to have. It doesn't say how they're done. When writing protocols, there is no actual impementation code. It doesn't say what class does them. It has nothing to do with inheritance.
* It is a formal list of that any class can volunteer to support
* Pproperties are always decalred as `var`
* A class can inherit from multiple protocols and declared as comma separated right after the `:` in the class declaration

```swift
protocol ExampleProtocol {
    //method signatures
    func simpleMethod() -> Bool
    var simpleProperty : Int { get }
}

class MyClass : ExampleProtocol {
    // provide anything else you need this class to do
    func simpleMethod() -> Bool {
        // do some work
        return true
    }

    var simpleProperty : Int {
        return 666
    }
}
```
### Adding functionality with Extensions

* Add methods and properties to existing types
* Doesn't require source code for the type
* Can be added to classes, structures and enumerations
* A lightweight way of adding useful methods to existing types when you don't have the source code

```swift
extension String {
    func reverseWords() -> String {
        let wordsArray = self.componentsSeparatedByString(" ")
        let reversedArray = wordsArray.reverse()
        var newString = ""
        for eachWord in reversedArray {
            newString += eachWord + " "
        }
    return newString
    }
}

var message = "I want to reverse all the words in this string"

message.reverseWords()
```

### Generics

* A feature in Swift language that lets you get benefits of strong type safety and flexibility all at the same time

```swift
import UIKit

class SimpleClass {
    var singleProperty : String = "A string"
}

let myNumbers = [666, 113, 34, 45, 12, 456, 234]
let myStrings = ["death", "hell", "grave"]
let myObjects = [SimpleClass(), SimpleClass(), SimpleClass(), SimpleClass()]

func displayArray<T>(theArray : [T]) -> T{
    println("Printing the array:")
    for eachItem in theArray {
        print(eachItem)
        print(" : ")
    }
    println()
    let finalElement : T = theArray[theArray.count-1]
    return finalElement
}

var finalInt = displayArray(myNumbers)
++finalInt
var finalString = displayArray(myStrings)
finalString.uppercaseString
displayArray(myStrings)
displayArray(myNumbers)
```
