# Generics
```dart
/**
* Generic allows us to handle objects that type is unknown at the time of writing the code. Their type will be decided at runtime.
*/
main() {
  final intsBox = Box([1, 2, 3, 4]);
  print(intsBox.getPackageAt(1));

  final boxesBox = Box([
    Box(['a', 'b', 'c']),
    Box(['d', 'e', 'f']),
  ]);
  print(boxesBox.getPackageAt(1)?.getPackageAt(1));
}

class Box<PackageType> {
  List<PackageType> _packages;

  // Passing different instances of objects to constructor will affect what `PackageType` will become at runtime
  Box(this._packages);

  // Returned type depends on what type of object is passed in constructor
  PackageType? getPackageAt(int idx) {
    if (_packages.length <= idx) {
      return null;
    }
    return _packages[idx];
  }
}

```

Open in [DartPad](https://dartpad.dev/?id=862e771a581de8225ce21f83b9ab78aa).
