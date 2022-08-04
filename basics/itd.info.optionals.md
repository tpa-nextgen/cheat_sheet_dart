### Optionals

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
* `Null Safety` means that when we declare variable we need to decide 
* if we allow it to take null values or not. 
* Thanks to that Dart can detect "null point exceptions" before running application. 
* To specify if the variable can be `null`, you can use the nullable type `?` operator.
*/
void main() {
  String spaceTelescope;
  // This line would cause an error because we declared spaceTelescope
  // as non-nullable but we didn't initialize it so we can't use it yet.
  // printType(spaceTelescope);

  // This line would cause an error during compilation:
  // "A value of type 'Null' can't be assigned to a variable of type 'String'.""
  // spaceTelescope = null;
  spaceTelescope = 'JWST';
  printType(spaceTelescope);

  String? spaceRocket;
  // This line will not cause an error
  // because we declared spaceRocket as nullable.
  // It takes null as the default value if none is given.
  printType(spaceRocket);
  spaceRocket = 'Saturn V';

  // If a variable is initialized with a non-null value its type will be non-null.
  // spaceStation is String type.
  var spaceStation = 'ISS';
  // This line would cause an error:
  // "A value of type 'Null' can't be assigned to a variable of type 'String'.""
  // spaceStation = null;
  printType(spaceStation);

  // If a variable is initialized with a null value (or nothing)
  // its type will be dynamic, which also accepts null as a value.
  // spaceShuttle is dynamic type.
  var spaceShuttle = null;
  spaceShuttle = 'Endeavour';
  printType(spaceShuttle);
}

// Do not worry about this code :)
void printType<T>(T object) {
  print('Type: $T, value: $object');
}

```