# Variables and data types


```dart
/**
 * Dart is a **statically typed** language. 
 * It means while declaring a variable, we need to specify 
 * what kind of data that variable is going to store.
 */
void main() {
  // variables without a data type must be defined with data type identifiers
  int myNumber;
  double myDouble;
  String myString;
  bool myBoolean;

  myNumber = 5;
  myDouble = 2.5;
  myString = 'Hello';
  myBoolean = true;

  print(myNumber);
  print(myDouble);
  print(myString);
  print(myBoolean);

  var age = 27; // `age` variable has `int` type because `27` is an integer
  double grades = 9; // converted to `9.0`

  var favColor = "Green";
  String favFruit = 'Banana';

  //dynamic type accepts every value
  dynamic any = 'hello';
  any = 1;
  any = [1, 2, 3];

  // there are no primitives types in Dart
  print('int is object: ${int is Object}'); //true
  print('bool is object: ${bool is Object}'); //true
  print('double is object: ${double is Object}'); //true
  print('dynamic is object: ${dynamic is Object}'); //true
}

```
