# List


```dart
/**
 * Dart provides a `List` class to create an Array-like data structure.
 * Dart lists can hold data of a fixed data type or 
 * data of any data type, also depending on how it was declared.
 *
 * List<int>(n)        => List of fixed `n` size that can hold elements of `int` data type only
 * []                  => Growable list of infinite size that can hold elements of dynamic data type
 * ['A', 'B']          => Literal expression to declare a growable list with initial values.
 */
void main() {
  // list of fixed-length (below lists contain 3 exact elements)
  // `List dynamicFixedList` is equivalent to `List<dynamic> dynamicFixedList`
  // can contain elements of `num`, `int` or `double`
  List dynamicFixedList = List.filled(3, null, growable: false);
  // dynamicFixedList contains null objects
  print(dynamicFixedList); // [ null, null, null ]

  // override a value of an element in the list
  dynamicFixedList[0] = 'HELLO'; // override value at index 0
  dynamicFixedList[1] = 'WORLD';
  print(dynamicFixedList);
  // because it is dynamic you can override value with any type
  dynamicFixedList[1] = 1; 
  print(dynamicFixedList);

  // calling any method that changes list length will cause error
  // dynamicFixedList.add(1);
  // dynamicFixedList.removeAt(1);
  

  /************************/

  // growable lists
  // can only contain String
  // by default list are growable - their length can change
  List<String> growableStringList = [];
  growableStringList.add("Orange"); // add element to growableStringList
  growableStringList.add("Apple"); // add element to growableStringList
  // growableStringList.add(1); // invalid operation as `1` is not a `String` type value

  // override a value at an existing index
  growableStringList[1] = 'Mango';

  print(growableStringList);

  /************************/

  // declaring a growable list with initial values using List literal syntax
  
  // creates a List<dynamic>
  var growableDynamicList = [
    1,
    "Hello"
  ]; 
  var growableDoubleList = [
    1.0,
    2.1
  ]; // creates a List<double>

  growableDynamicList.add("World");
  print("growableDynamicList => $growableDynamicList");
  print("growableDynamicList.length => ${growableDynamicList.length}");
}

```
