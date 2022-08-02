# List
Dart provides a List class which is used to construct an Array-like data structure that can hold a fixed or variable number of similar or dynamic data types. Dart also provides [] literal syntax to create lists.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Dart provides a `List` class to create an Array-like data structure.
 * Dart lists can hold data of a fixed Data Type or data of any data type, also depending on how it was declared.
 *
 *
 * List<int>(n)        => List of fixed `n` size that can hold elements of `int` Data Type only
 * []                  => Growable list of infinite size that can hold elements of dynamic Data Type
 * ['A', 'B']          => Literal expression to declare a growable list with initial values.
 */
void main() {
  // list of fixed length (below lists contain 3 exact elements)
  List<dynamic> stringList = [
    '1',
    '2',
    '3'
  ]; // `List<dynamic> fixedDynamicList` is same as `List fixedDynamicList`
  List<int> numList = [3]; // can contain elements of `num`, `int` or `double`

  // list with fixed length contains null objects
  print(stringList); // [ null, null, null ]

  // override a value of an element in the list
  stringList[1] = 'HELLO'; // override value at index 1

  print(stringList);

  /************************/

  // growable lists
  List<String> growableStringList = [];
  growableStringList.add("Orange"); // add element to growableStringList
  growableStringList.add("Apple"); // add element to growableStringList
  // growableStringList.add( 1 ); // invalid operation as `1` is not a `String` type value

  // override a value at an existing index
  growableStringList[1] = 'Mango';

  print(growableStringList);

  /************************/

  // declaring a growable list with initial values using List literal syntax
  var growableDynamicList = [
    1,
    "Hello"
  ]; // creates a List that can hold objects of any type
  var growableDoubleList = [
    1.0,
    2.1
  ]; // creates a List that can hold only `double` values

  growableDynamicList.add("World");
  print("growableDynamicList => $growableDynamicList");
  print("growableDynamicList.length => ${growableDynamicList.length}");
}
```

From the above example, we can see that a list can be created with initial values using list literal syntax ([]). To add an element to a list, we use the `add` method because we have no information about the index beforehand. And similarly to remove an element from the list, we can use the `remove` method.