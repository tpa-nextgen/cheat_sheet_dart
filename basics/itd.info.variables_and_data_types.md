# Variables and Data Types

Dart is a **statically typed** language which means while declaring a variable, we need to specify what kind of data that variable is going to store. There are basically `int`, `double`, `boolean`, and `string` primitive Data Types in Dart.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Variables without a value must initialize with a data type identifier.
 */
void main() {
  // variables without a Data Type must be defined with Data Type identifiers
  int myNumber = 5; // `int` Data Type is for integer values
  double myDouble = 2.5; // `double` Data Type is for floating-point numbers
  String myString =
      "Hello"; // `String` Data Type is for string values (sequence of characters)
  bool myBoolean = true;

  print(myNumber);
  print(myDouble);
  print(myString);
  print(myBoolean);
}
```

We can assign a value to a variable after it is defined or declare a variable with an initial value. Dart gives us the flexibility to optionally ignore Data Type declaration using the `var` keyword when an initial value is assigned to a variable. Dart can infer the Data Type of a variable from its initial value.

During the lifetime of a variable, the variable must contain only data of the Data Type it was defined with. Any attempt to save data of a different kind will result in a compilation error. Let’s see an example of that.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Dart can infer the data type of a variable from its initial value.
 * Once a variable is defined, it should contain only that data type.
 */
void main() {
  // Dart can infer the Data Type of a variable from its initial value
  var age = 27; // `age` variable has `int` type because `27` is an integer

  // if a variable of `double` Data Type is assigned with `int` value,
  // Dart converts the value to a suitable floating-point number
  double grades = 9; // converted to `9.0`

  // strings in Dart can be defined inside single or double quotes
  var favColor = "Green";
  String favFruit = 'Banana';

  // since the `isMarried` variable has no initial value, we must declare its Data Type
  bool isMarried; // `isMarried` can contain `true` or `false` value

  // we can assign new values to existing variables
  favFruit = 'Mango';
  isMarried = false;
  grades = 10; // converted to 10.0 as `grades` has `double` Data Type

  // Error: A value of type 'int' can't be assigned to a variable of type 'String'.
  // favColor=100;

  print(age);
  print(grades);
  print(favColor);
  print(favFruit);
  print(isMarried);
}
```

There are a few things you should remember from the above example which I have already highlighted in the comments.
* A string literal can be written with both single-quotes (‘) and double-quotes (“). 
* If a variable of double Data Type is assigned with an int value, Dart will convert it to a floating-point number.


Dart has a special Data Type `dynamic` which can hold a value of any Data Type. A typical use case of this Data Type would be to allow users to use your function with an argument of any Data Type but then using its operator, do conditional processing on that argument.

Dart also uses dynamic Data Type in many places when a Data Type is not mentioned in the syntax, like when you create an empty map using a literal expression or the Map class (explained in the next topics).

### `is` operator
We use the `is` and `is!` operators to check if an object is an instance-of or type-of class.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * We use the `is` and `is!` operators to check if an object is an instance-of or type-of class.
 */
void main() {
  
  // check if `"Hello"` is type-of/instance-of `String` class
  print('"Hello" \tis instance of \t"String" class: \t${ "Hello" is String }');
  
  // check if `21` is type-of/instance-of `int` class
  print('27 \t\tis instance of \t"int" class: \t\t${ 21 is int }');
  
  // check if `9.81` is type-of/instance-of `double` class
  print('9.81 \t\tis instance of \t"double" class: \t${ 9.81 is double }');
  
  // check if `true` is type-of/instance-of `bool` class
  print('true \t\tis instance of \t"bool" class: \t\t${ true is bool }');
  
  // check if `null` is type-of/instance-of `Null` class
  print('null \t\tis instance of \t"Null" class: \t\t${ null is Null }');
  
  // check if any object is type-of/instance-of `Object` class
  // since all objects inherit `Object` class, they are type-of `Object`
  print('"Hello" \tis instance of \t"Object" class: \t${ "Hello" is Object }');
  print('null \t\tis instance of \t"Object" class: \t${ null is Object }');
}
```

### Optionals

`Null Safety` in simple words means a variable cannot contain a `null` value unless you initialized with null to that variable. With null safety, all the runtime null-dereference errors will now be shown in compile time. To specify if the variable can be `null`, then you can use the nullable type `?` operator, Let's see an example.

Run example in [DartPad](https://dartpad.dev/?)

```dart
void main() {
  
  String spaceTelescope;
  // This line would cause an error because we declared spaceTelescope as non-nullable but we didn't initialize it so we can't use it yet.
  //printType(spaceTelescope);
  // This line would cause an error: A value of type 'Null' can't be assigned to a variable of type 'String'.
  //spaceTelescope = null;
  spaceTelescope = 'JWST';
  printType(spaceTelescope);

  
  String? spaceRocket;
  // This line will not cause an error because we declared spaceRocket as nullable so it takes null as the default value if none is given.
  printType(spaceRocket);
  spaceRocket = 'Saturn V';
  
  // If a variable is initialized with a non-null value its type will be non-null.
  // spaceStation is String type.
  var spaceStation = 'ISS';  
  // This line would cause an error: A value of type 'Null' can't be assigned to a variable of type 'String'.
  //spaceStation = null;
  printType(spaceStation);

  // If a variable is initialized with a null value (or nothing) its type will be dynamic, which also accepts null as a value.
  // spaceShuttle is dynamic type.
  var spaceShuttle = null;
  spaceShuttle = 'Endeavour';
  printType(spaceShuttle);
}

// Do not worry about this code :)
void printType<T>(T object){
  print('Type: $T, value: $object');
}
```

> ### Additional Materials
> * Dart Academy Boot Camp - Lessons 2, 3, and 4 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart samples - <https://dart.dev/samples#variables>
