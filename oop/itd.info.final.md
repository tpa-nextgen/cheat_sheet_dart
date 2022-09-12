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

```

Open in [DartPad](https://dartpad.dev/?id=4c69d1dfb2eee0fb77bcbfdea7279229).
