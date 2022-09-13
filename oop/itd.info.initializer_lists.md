# Initializer Lists

```dart
class Currency {
  final String name;
  final String code;
  final String sign;
  final double sellPrice;
  final double buyPrice;

  Currency(this.name, this.code, this.sign, double exchangeRate)
      // Notice `:` after a constructor. Each initialization is divided with `,`.
      : sellPrice = calculateSellPrice(exchangeRate),
        buyPrice = exchangeRate * 0.95;

  static calculateSellPrice(double exchangeRate) {
    if (exchangeRate < 0.5) {
      return 0.5;
    }
    return exchangeRate;
  }
}

void main() {
  final dollar = Currency('dolar', 'USD', '\$', 1.3);
  print('Buy price: ${dollar.buyPrice}');
  print('Sell price: ${dollar.sellPrice}');
}

```

Open in [DartPad](https://dartpad.dev/?id=ff21de3a385c56f5d56edbf74e0fa1ef).
