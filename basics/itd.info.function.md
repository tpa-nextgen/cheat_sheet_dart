# Function

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * In Dart, functions can be defined in the file scope or inside another function.
 *
 * Functions defined in the file scope, like the `main` function is hoisted.
 * Hence we can call one function from another despite their order on appearance in the file.
 */
void main() {
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

// function with named parameters, name is required and age is optional
void getNamedInfo({required String? name, int? age}) {
  print("getNamedInfo():=> $name, $age");
}

// function with positional and named parameters, only `name` argument is required
// positional parameters must appear before the named parameters
void getSafeNamedInfo(String name, {int? age, bool isMarried = false}) {
  print("getSafeNamedInfo():=> $name, $age, $isMarried");
}

```
