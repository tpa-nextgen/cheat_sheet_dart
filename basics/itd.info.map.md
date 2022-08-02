# Map

The map is a collection of key:value pairs. Dart provides a `Map` class to create a map. A map can contain any type of keys and values.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * A map is a collection of `key:value` pairs.
 * A map resembles the dictionary in Python or object literal in JavaScript.
 * Each keys and values in a map can be fixed to a certain Data Type or can be dynamic.
 * A map in Dart can be `LinkedHashMap` or `HashMap`. Using `Map` class, a `LinkedHashMap` is returned.
 * A `LinkedHashMap` hold keys in the order of their insertion while HashMap does not.
 */
void main() {
  // using Map class
  var myMap = Map(); // creates a Map of `dynamic` keys and `dynamic` values

  // creates a map with `int` keys and `String` values
  var fingers = Map<int,
      String>(); // or `Map<int,String>() fingers = new Map();` declaration

  // assign values to the keys
  fingers[1] = 'THUMB'; // 1 is not an index, its a key
  fingers[2] = 'INDEX';
  print("fingers => $fingers");

  // creating a map with initial values using map literal syntax
  // creates a Map of `dynamic` keys and `dynamic` values
  var info = {
    "CARS": ["AUDI", "BMW"], // String:List<String>
    "FRUITS": ["APPLE", "ORANGE"], // String:List<String>
    true: "YES", // bool:String
    123: [1, 2, 3], // int:List<int>
  };

  print("info[CARS] => ${info['CARS']}");
  print("info[true] => ${info[true]}");
  print("info[123] => ${info[123]}");
  print(
      "info[123] => ${info['123']}"); // returns `null` as map doesn't have a value with '123' key
}
```

We can also iterate over entries of a map that can be accessed from `.entries` property on a map. Dart also provides a `HashMap` class which does not guarantee the retrieval of map keys in the original insertion order.

> ### Additional Materials
> * Dart Academy Boot Camp - Lessons 24 and 25 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart iterables - <https://dart.dev/codelabs/iterables>