# Methods

```dart
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
  print(
      'Shop assistant: Your are welcome. That\'s your ${shop.sellToy('yo-yo')}');
  print('Shop assistant:\tNow we\'ve got:');
  for (var element in shop.getToys()) {
    print('\t\t  - $element');
  }
}

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

```