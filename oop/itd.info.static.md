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
