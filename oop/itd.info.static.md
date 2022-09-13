# Static

```dart
class Disk {
  static const pi = 3.14159;
  final double radius;
  Disk(this.radius);

  double get area => calculateArea(radius);

  static calculateArea(double r) {
    return pi*r*r;
  }
}

void main() {
  final disk1 = Disk(3.0);
  final disk2 = Disk(5.0);
  print(disk1.area);
  print(disk2.area);
  print(Disk.calculateArea(2.0));
}

```

Open in [DartPad](https://dartpad.dev/?id=febfe4b3b5900a1e19e4273bd79d00f7).
