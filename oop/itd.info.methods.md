# Methods

Questions:
- How to limit access to properties?
- How to change private properties?
- How to change an object's state?

KeyPoints:
* method

---

# Intro
Methods are functions that provide behavior for an object.
Instance methods on objects can access instance variables. The distanceTo() method in the following sample is an example of an instance method:

```dart
import 'dart:math';

class Point {
  double x = 0;
  double y = 0;

  Point(this.x, this.y);

  double distanceTo(Point other) {
    var dx = x - other.x;
    var dy = y - other.y;
    return sqrt(dx * dx + dy * dy);
  }
}
```

# How to use methods?

Let's consider an example of a shop with toys.

```dart
class ToysShop {
  List<String> toys;

  ToysShop(this.toys);
}

void main() {
  ToysShop shop = ToysShop([
    'robot',
    'ball',
    'doll',
    'spaceman',
    'yo-yo',
    'train',
    'bricks',
    'rattle',
  ]);
}
```

### Problem 1 - any customer can modify list of toys

```dart
shop.toys = [];
```


**Solution** against changes are simple - `final`;

### Problem 2 - any customer can modify toys in list

```dart
shop.toys[0] = 'really ugly toy';
```

**Solution** against these changes are simple - `private property`;

### Problem 3 - customers cannot see toys

**Solution** methods!!!


Please run and consider the following solution for all our problems:

```dart
class ToysShop {
  final List<String> _toys;

  ToysShop(this._toys);
  
  List<String> getToys() {
    return _toys;
  }
  
  bool checkIfExists(String toyName) {
     return _toys.contains(toyName);
  }
  
  String sellToy(String toyName) {
    if (checkIfExists(toyName) && _toys.remove(toyName)) {
      return toyName;
    }
    return 'I\'m so sorry but we haven\'t got $toyName';
  }
}

void main() {
  ToysShop shop = ToysShop([
    'robot',
    'ball',
    'yo-yo',
  ]);
  
  print('Customer:\tCan you show me all toys ?');
  print('Shop assistant:\tSure! We have got:');
  for (var element in shop.getToys()) {
    print('\t\t  - $element');
  }
  print('Customer:\tCan I buy yo-yo ?');
  print('Shop assistant: ${shop.checkIfExists('yo-yo') ? 'Yes' : 'No'}');
  print('Customer:\tThank you!');
  print('Shop assistant: Your are welcome. That\'s your ${shop.sellToy('yo-yo')}');
  print('Shop assistant:\tNow we\'ve got:');
  for (var element in shop.getToys()) {
    print('\t\t  - $element');
  }
}
```
