# Optionals - `is` operator

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * We use the `is` and `is!` operators to check if an object is an instance-of or type-of class.
 */
void main() {
  // check if `"Hello"` is type-of/instance-of `String` class
  print('"Hello" is instance of "String" class: ${ "Hello" is String }');
  
  // check if `21` is type-of/instance-of `int` class
  print('27 is instance of "int" class: ${ 21 is int }');
  
  // check if `9.81` is type-of/instance-of `double` class
  print('9.81 is instance of "double" class: ${ 9.81 is double }');
  
  // check if `true` is type-of/instance-of `bool` class
  print('true is instance of "bool" class: ${ true is bool }');
  print('true is NOT instance of "bool" class: ${ true is! bool }');
  
  // check if `null` is type-of/instance-of `Null` class
  print('null is instance of "Null" class: ${ null is Null }');
  
  // check if any object is type-of/instance-of `Object` class
  // since all objects inherit `Object` class, they are type-of `Object`
  print('"Hello" is instance of "Object" class: ${ "Hello" is Object }');
  print('1 is instance of "Object" class: ${ 1 is Object }');

  // we can test not only values but also types on their own
  print('String is child of Object class: ${ String is Object }'); // true
  print('int is child of Object class: ${ int is Object }');// true
  print('String is child of Object class: ${ dynamic is Object }');// true
}
```