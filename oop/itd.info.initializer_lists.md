# Initializer Lists

Sometimes you may want to use some values passed to the constructor to calculate the fields of a class. In many languages it would look something like this (here in Java):

```java
class Currency {
  final String name;
  final String code;
  final String sign;
  final double sellPrice;
  final double buyPrice;

  Currency(String name, String code, String sign, double exchangeRate) {
    this.name = name;
    this.code = code;
    this.sign = sign;
    sellPrice = exchangeRate;
    buyPrice = exchangeRate * 0.95;
  }
}
```

Dart will not allow this. You will get an error: `Final field ... is not initialized`. Any final field must be initialized before a body of a constructor. But how to execute code before a constructor? This is a place where an initializer list comes in.

```dart
class Currency {
  final String name;
  final String code;
  final String sign;
  final double sellPrice;
  final double buyPrice;

  Currency(this.name, this.code, this.sign, double exchangeRate)
      : sellPrice = exchangeRate,
        buyPrice = exchangeRate * 0.95;
}
```

Notice `:` after a constructor. Each initialization is divided with `,`.

What if you want to make some more complex calculations? You can use static methods to keep code clean:

```dart
class Currency {
  final String name;
  final String code;
  final String sign;
  final double sellPrice;
  final double buyPrice;

  Currency(this.name, this.code, this.sign, double exchangeRate)
      : sellPrice = calculateSellPrice(exchangeRate),
        buyPrice = exchangeRate * 0.95;

  static calculateSellPrice(double exchangeRate) {
    if (exchangeRate < 0.5) {
      return 0.5;
    }
    return exchangeRate;
  }
}
```