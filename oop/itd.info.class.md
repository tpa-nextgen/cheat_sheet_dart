# Class

```dart
void main() {
  Car audi = Car("audi", 48000, 2013, 270000, "diesel", 1968, 'John');

  print(audi.name);
  audi.engineType = "gasoline";
}

class Car {
  final String name;
  final int productionYear;
  double price;
  int traveledKms;
  String engineType;
  double engineCapacity;
  String _previousOwner; //private fields start with _

  Car(
    this.name,
    this.price,
    this.productionYear,
    this.traveledKms,
    this.engineType,
    this.engineCapacity,
    this._previousOwner,
  );
}

```

Open in [DartPad](https://dartpad.dev/?id=320b14d5a98fa33746e1c21ececd43b0).
