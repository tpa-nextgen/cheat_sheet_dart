# Map


```dart
/**
 * A Map resembles the dictionary in Python or object literal in JavaScript.
 * A map in Dart can be `LinkedHashMap` or `HashMap`. Using `Map` class, a `LinkedHashMap` is returned.
 * A `LinkedHashMap` hold keys in the order of their insertion while HashMap does not.
 */
void main() {
  var dynamicMap =
      Map(); // creates a Map of `dynamic` keys and `dynamic` values
  dynamicMap[1] = 1;
  dynamicMap[1.123] = 2;
  dynamicMap['string'] = 3;
  dynamicMap[true] = 4;
  print("dynamicMap => $dynamicMap");

  // creates a map with `String` keys and `String` values
  var fingers = Map<String, String>();
  fingers['big finger'] = 'THUMB';
  fingers['pointy finger'] = 'INDEX';
  print("fingers => $fingers");
  print("fingers keys: ${fingers.keys}");
  print("fingers values: ${fingers.values}");
  print("fingers entries: ${fingers.entries}");

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
  
  // returns `null` as map doesn't have a value with '123' String key
  print("info[123] => ${info['123']}");
}

```

Open in [DartPad](https://dartpad.dev/?id=677ffe8cd80a448deb0f7847be419552).
