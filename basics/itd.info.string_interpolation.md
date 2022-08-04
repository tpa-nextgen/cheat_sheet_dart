# String Interpolation

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 *
 * String interpolation in Dart can be performed directly by using `$variable` syntax
 * inside `single` or `double` quoted string as well as using `$variable` or `${expression}` syntax.
 *
 * Any object of other than `String` type that is being interpolated in a string,
 * must have `toString` method which returns a string representation of that object.
 */
void main() {
  var grade = 8.32;

  // escaping " and '
  print('""\'\''); // String declared with ''
  print("\"\"''"); // String declared with ""

  // injecting variables in a string
  print("Hello, My grade is '$grade'.");
  // is a short cut to writing:
  print("Hello, My grade is '" + grade.toString() + "'.");

  // evaluating variables and expression inside `${...}` syntax
  print('I am \'${20 + 10}\' years old and I received "${grade * 10}%" score.');
}

```
