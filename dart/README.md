# Dart


## Basic level


What are the features if Dart?

* Dart is a class-based programming language.
* It is an object-oriented, single inheritance.
* Dart supports interfaces and abstract classes, reified generics
* Dart used Single threaded (asynchronous)
* Optional typing / type annotations

---

Where does Dart run?

* Dart run in First Command-line using Dart VM
* In a browser in Dart VM (Chromium + Dart = Dartium)
* Compiled to JavaScript in any browser. (dart2js)

---

What is Libraries in dart? And what are types of Libraries?

Libraries: In Dart, libraries is used to support web and web server development. Dart libraries not only provide APIs, but it is a unit of privacy: they can implement details such as private variables. There are some of libraries of Dart:

* I/O Library: Read and write files.
* Dart core: data structure and operations.
* Dart async: Support for asynchronous programming, with classes such as Future and Stream.
* Dart math: Mathematical constants and functions, plus a random number generator.
* Html Library: HTML5 DOM.
* Isolate Library: spawning and communicating with isolates
* Crypto Library: SHA1, MD5, SHA256 and HMAC support.
* Json Library: parse and produce JSON-encoded text.
* Unit Test Library: function and classes.
* Dart convert: Encoders and decoders for converting between different data representations, including JSON and UTF-8.

---

What is Libraries in dart? And what are types of Libraries?

The Dart programming language supports the following types:

* `Numbers:` In Dart, int, double are used.
* `Strings:` A Dart string is a sequence of UTF-16 code units. You can use either single or double quotes to create a string
* `Booleans:` Dart uses the bool keyword to represent a Boolean value
* `Lists:` A List is an ordered group of objects.
* `Maps:` The Map data type represents a set of values as key value pairs.
* `Dynamic Type:` The dynamic keyword can also be used as a type annotation explicitly.

---

What is Dart strings?

Strings represent a sequence of characters. For instance, if you were to store some data like name, address etc. the string data type should be used. A Dart string is a sequence of UTF-16 code units. You can use either single or double quotes to create a string:

var s1 = ‘Single quotes work well for string literals.’;
var s2 = “Double quotes work just as well.”;
var s3 = ‘It\’s easy to escape the string delimiter.’;
var s4 = “It’s even easier to use the other delimiter.”;

---

What are the Snapchots in Dart?

Snapshots are a core part of the Dart VM. Snapshots are files which store objects and other runtime data.

There are three type of snapshots:
* `Script snapshots:` Dart programs can be compiled into snapshot files. These files contain all of the program code and dependencies preparsed and ready to execute. This allows fast startups.
* `Full snapshots:` The Dart core libraries can be compiled into a snapshot file which allows fast loading of the libraries. Most standard distributions of the main Dart VM have a prebuilt snapshot for the core libraries which is loaded at runtime.
* `Object snapshots:` art is a very asynchronous language. With this, it uses isolates for concurrency. Since these are workers which pass messages, it needs a way to serialize a message. This is done using a snapshot, which is generated from a given object, and then this is transferred to another isolate for deserializing.

---

What Is Type-checking In Dart?

In Dart, type-checking is used to check that a variable hold only specific to a data type.

```dart
String name = 'Smith';
int num = 10;
```

```dart
void main() {
   String name = 1; // variable Not Match
}
```

---

What Are Various String Functions In Dart?


There are given various string functions:

* toLowerCase():It converts all string characters in to lower case.
* toUpperCase():It converts all string characters in this to upper case.
* trim():It returns the string without any whitespace.
* compareTo():It compares this object to another.

---

What Are The Types Of List In Dirt?

There are two types of list in Dirt that are given below:

* Fixed Length List : (length fixed)
* Growable List: (Length can change at runtime.

---

What Is Rune In Dart?

In Dart, rune is an integer representing Unicode code point.

---

Does Dart Has A Syntax For Declaring Interfaces?

No, Dart has not syntax for declaring interface.

despite, [you should read the following](https://dart.dev/guides/language/language-tour#ch02-implicit-interfaces)

---

What are the errors in dart?

There are different types of error will be generates. Here

* Static warnings
* Dynamic errors
* Compile Time errors
* Runtime error

---

What Is Lambda Function?

A Lambda function is a concise mechanism to represent functions. These functions are known as Arrow functions.

```dart
void main() {
   printMsg();
   print(test());
}

printMsg()=>
print("hello");
int test()=>123;
// returning function
```

---

What Is The Use Of This Keyword In Dart?

In Dart, this keyword refers to the current instance of the class.

```dart
void main() {
   Car c1 = new Car('E1001');
}

class Car {
   String engine;

   Car(String engine) {
      this.engine = engine;
      print("The engine is : ");
   }
}
```

---

What Are Getters And Setters?

Getters and Setters allow the program to initialize and retrieve the value of class fields. It is also known as accessors and mutators.

---

What Are The Various Types Of Operators In Dart?

In Dart, there are various types of operators:

* Arithmetic Operators
* Equality and Relational Operators
* Type test Operators
* Bitwise Operators
* Assignment Operators
* Logical Operators

---

What Is The Use Of Truncate Methods?

Truncate method is used to return an integer after discarding any fractions digits.

```dart
void main() {
   double n1 = 2.123;
   var value = n1.truncate();
   print("The truncated value of 2.123 = ");
}
```

---

What Is The Syntax To Declare Class?

The following is the syntax to declare class:

```dart
class class_name {
   <fields>
   <getters/setters>
   <constructors>
   <functions>
}
```

---

What Are Getters And Setters In Dart?

In Dart, Getters and Setters is also known as accessors and mutators. It allows the program to initialize and retrieve the values of class fields.

```dart
class Vehicle {
  String make;
  String model;
  int manufactureYear;
  int vehicleAge;
  String color;

  int get age {
    return vehicleAge;
  }

  void set age(int currentYear) {
    vehicleAge = currentYear - manufactureYear;
  }

  Vehicle({this.make,this.model,this.manufactureYear,this.color,});
}
```

---

What Is Method Overriding In Dart?


In Dart, Method Overriding is a technique that child class redefines a method in its parent class.

```dart
void main() {
   Child c = new Child();
   c.m1(12);
}

class Parent {
   void m1(int a){ print("value of a ");}
}

class Child extends Parent {
   @override
   void m1(int b) {
      print("value of b ");
   }
}
```

---

What Is Pub In Dart?

In Dart, pub is a tool for manage Dart packages.

---

What Is The Syntax To Handle An Exception?

```dart
try {
   // code that might throw an exception
}

on Exception1 {
   // code for handling exception
}

catch Exception2 {
   // code for handling exception
}
```

---

What Is Typedef In Dart?

In Dart, A typedef (Or function types alias) helps to define pointer to execute code within memory.

Syntax:

`typedef function_name(parameters)`

---
