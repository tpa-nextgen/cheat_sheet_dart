# Function

Functions in Dart are used to produce a certain output given a particular input. They are one of the basic units for organizing code in a program. When programs get lengthy, functions help you keep things clean and readable, and they keep you from repeating yourself all the time.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * In Dart, functions can be defined in the file scope or inside another function.
 *
 * Functions defined in the file scope, like the `main` function is hoisted.
 * Hence we can call one function from another despite their order on appearance in the file.
 */
void main() {
  // `print` is also a function (built-in)
  print(greet());
  print(sayHello("John"));
  print(getSum(22, 11));
}

// function returns a `String` value
String greet() {
  return "Good Morning";
}

// `sayHello` function is defined with `String` return value and 'String' argument
String sayHello(String name) {
  var greeting = greet(); // call `greet` function
  return "$greeting, $name.";
}

// `getSum` function is defined with `int` return value and two 'int' arguments
int getSum(int a, int b) {
  return a + b;
}
```

### Function Anatomy
As you can see from the above example, there are many ways to create a function. In most cases we can say that function looks like this:

```dart
return_type function_name(list_of_arguments) {
  function_body
  return some_value;
}
```

* **return type** - 
It's a type that you want to return in function output. The Dart function always returns something. When you place the keyword void before the name of a function you're defining, you're saying you don't intend for the function to produce any output, or in programming parlance, it has no return value. Technically, this causes the function's output to be null.

* **function_name** - 
The next part of your function definition is the function's name. This name can be any valid identifier, which is a word that starts with either a letter or an underscore (_), followed by any combination of letters, numbers, and underscores. By convention, function names use the lower camel case. This means you should capitalize the first letter of each word in the identifier, except the first, which is always lowercase. Example: `myFavoriteFunction()`.

* **list_of_arguments** - 
The `greet()` function has an empty set of parentheses because it takes no input. Other functions define a list of arguments that acts as function input.

* **function_body** - 
A place to keep all operations.

* **return some_value** - 
This code produces the function's output.


# Positional and Names Parameters
Dart function supports both positional and named parameters just like in Python. Also, we can provide default values to these parameters in case a function was not invoked with some arguments.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * In Dart, we call a function with arguments in the order defined by the function,
 * or by actually specifying the names of the arguments in the function call.
 *
 * Functions can also have default values so that a caller does not have to provide
 * all the arguments with the function call.
 *
 * [positional parameters]
 * var functionName( a, b, c ) => statement;
 * -> functionName(1, 2, 3) // order matters
 *
 * [optional positional parameters with default values]
 * var functionName( a, [b = 2, c] ) => statement;
 * -> functionName(1) // `b` will be `2` and c will be `null`
 *
 * [named parameters, all parameters are optional]
 * var functionName( { a, b } ) => statement;
 * -> functionName() // `a` & `b` will be `null`
 * -> functionName({b: 2, a: 1}) // order doesn't matter
 *
 * [named parameters with default values]
 * var functionName( { a, b = 2 } ) => statement;
 * -> functionName({a: 1}) // `b` will be 2
 *
 * [mixed positional and named parameters]
 * var functionName( a, b, { c = 3, d } ) => statement;
 * -> functionName(1, 2, {d: 4}) // `c` will be `3`
 * 
 */
void main() {
  // function call with positional arguments
  // appearance order of the arguments is important
  getInfo("Rachel Green", 27);

  // function with positional parameters
  // we can ignore optional arguments
  getSafeInfo("Ross Geller", 31);

  // function with named parameters
  // appearance order of the arguments is not important
  getNamedInfo(name: "Chandler Bing", age: 29);

  // function with positional and named parameters
  // appearance order of arguments is important for positional arguments only
  getSafeNamedInfo("Joey Tribbiani", age: 29);
}

// this function must be called with `name` and `age` arguments in order
void getInfo(String name, int age) {
  print("getInfo():=> $name, $age");
}

// function can use blocks body (defined by {}) or expression body (using =>)
// expression body should be used for short one-liners where {} becomes unnecessary noise
void getInfoExpression(String name, int age, String birthday) =>
    print("getInfo():=> $name, $age, $birthday");

// `isMarried` is optional parameter and it has `false` default value
// `name` and `age` are required arguments
void getSafeInfo(String name, int age, [bool isMarried = false]) {
  print("getSafeInfo():=> $name, $age, $isMarried");
}

// function with named parameters, all parameters are optional
void getNamedInfo({String? name, int? age}) {
  print("getNamedInfo():=> $name, $age");
}

// function with positional and named parameters, only `name` argument is required
// positional parameters must appear before the named parameters
void getSafeNamedInfo(String name, {int? age, bool isMarried = false}) {
  print("getSafeNamedInfo():=> $name, $age, $isMarried");
}

```

> ### Additional Materials
> * Dart Academy Boot Camp - Lessons 17, 18, 19 and 20 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart samples - <https://dart.dev/samples#functions>
