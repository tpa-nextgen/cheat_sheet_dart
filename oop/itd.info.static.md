# Static

```dart
class Disk {
  static const pi = 3.14159;
  final double radius;
  Disk(this.radius);

  double get area => calculateArea(radius);

  static calculateArea(double r) {
    return pi*radius*radius;
  }
}
```

Open in [DartPad](https://dartpad.dev/?id=febfe4b3b5900a1e19e4273bd79d00f7).
