# String Interpolation

String interpolation is a process of evaluating the final string by injecting a variable or an expression in a string literal. Let’s see how we can do that.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * A string interpolation is the process of getting the final string value by evaluating,
 * a string that contains variables and expressions.
 *
 * String interpolation in Dart can be performed directly by using `$variable` syntax
 * inside `single` or `double` quoted string as well as using `${variable}` or `${expression}` syntax.
 *
 * Any object of other than `String` type that is being interpolated in a string,
 * must have `toString` method which returns a string representation of that object.
 */
void main() {
  var name = 'John Doe';
  var age = 27;
  var grades = 8.32;

  // injecting variables in a string
  print("Hello, My name is '$name'.");

  // evaluating variables and expression inside `${...}` syntax
  print('I am \'${age}\' years old and I received "${grades * 10}%" score.');

  // all Dart's objects allow to call .toString() method
  print("Hello, My name is '${name.toString()}'.");
}

```

There are a few things to remember in the above example. 
* The great thing about Dart is, it lets us use single or double quotes to perform string interpolation.
  * Having a single quote character inside a string defined with double quotes and vice-versa is legal but we need to use \ escape character to escape single or double quote characters when they appear in a string defined with single or double quotes respectively.
* We can also use `${}` syntax to interpolate variables but is recommended to use it only for expressions and use `$variable_name` to interpolate variables in a string.
* Dart internally calls toString() on objects that are being interpolated. In the above example, both int and double Data Types have toString method which returns their values in String format. If we need to interpolate a user-defined object, it must have a toString method.

> ### Additional Materials
> * Dart Academy Boot Camp - Lesson 6 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart String Interpolation - <https://shailen.github.io/blog/2012/11/14/dart-string-interpolation/>
