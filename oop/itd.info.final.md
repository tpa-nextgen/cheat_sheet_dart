# Immutable properties - final

```dart
class Account {
  final String currencyName;
  final String currencyCode;
  final String? currencySign;
  double cash;

  Account(
    this.currencyName,
    this.currencyCode, {
    this.currencySign,
    required this.cash, // By default named parameters are optional.
    // If field is non null parameter needs to be required or
    // you need to provide default value.
  });
}

void main() {
  final account1 = Account('dollar', 'USD', currencySign: '\$', cash: 1000);
  final account2 = Account('peso', 'MXN', cash: 2000);
  if(account1.currencySign != null) {
      print('${account1.currencyName} (${account1.currencySign}): ${account1.cash}');
  } else {
    print('${account1.currencyName}: ${account1.cash}');
  }
  if(account2.currencySign != null) {
      print('${account2.currencyName} (${account2.currencySign}): ${account2.cash}');
  } else {
    print('${account2.currencyName}: ${account2.cash}');
  }
}

```

Open in [DartPad](https://dartpad.dev/?id=4c69d1dfb2eee0fb77bcbfdea7279229).
