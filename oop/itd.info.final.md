# Immutable properties

Questions:
- How to protect properties against change?

KeyPoints:
* final

---

Let's consider an example:

![revolut](https://user-images.githubusercontent.com/85095377/182162860-c72f2098-55ca-448d-8e8b-524fae72b575.jpg)


In the Revolut application, we can have a few different bank accounts with different currencies. Class for that example can be like here:

```dart
class Account {
  String currencyName;
  String currencyCode;
  String currencySign;
  double cash;
  
  Account(this.currencyName, this.currencyCode, this.currencySign, this.cash);
}
```

Later we can use that like here:

```dart
void main() {
  Account euro = Account('Euro', 'EUR', '€', 500);
  Account dollar = Account('US Dollar', 'USD', '\$', 1401.77);
  deposit(100, euro);
  withdraw(123, euro);
  deposit(100.10, dollar);
  withdraw(123.50, dollar);
  print('Account information:');
  print('  - ${euro.currencyName}(${euro.currencyCode}): ${euro.currencySign}${euro.cash}');
  print('  - ${dollar.currencyName}(${dollar.currencyCode}): ${dollar.currencySign}${dollar.cash}');
}

void deposit(double value, Account account) {
  account.cash += value;
}

void withdraw(double value, Account account) {
  account.cash -= value;
}
```

> Account information:
>  - Euro(EUR): €477
>  - US Dollar(USD): $1378.37

As you can see, that's totally useful that we can manipulate cash value. Unfortunately, there is also an additional possibility to make something like here:

```dart
void crashTheSystem(Account account) {
  account.currencyCode = '!#+.!';
  account.currencySign = '1';
}
```

Everything will work, but the business will see that something is wrong with our account. Check it out in [DartPad](https://dartpad.dev/?).

### How we can protect our properties against change?
If you never intend to change a variable, use the `final` keyword instead of `var` or in addition to a type. A `final` variable can be set only once.

```dart
class Account {
  final String currencyName;
  final String currencyCode;
  final String currencySign;
  double cash;
  
  Account(this.currencyName, this.currencyCode, this.currencySign, this.cash);
}
```

Now all properties which are connected with a currency are immutable - that means that you can use them only once.

```dart
void crashTheSystem(Account account) {
  account.currencyCode = '!#+.!';   // Error: 'currencyCode' can't be used as a setter because it's final..
  account.currencySign = '1';   // Error: 'currencySign' can't be used as a setter because it's final.
}
```

### Generate constructor for `finals`

The `final` property must be initialized via a constructor. So, all IDEs (DartPad, Android Studio, and VSCode) support automatically generated constructors for final fields. 

1. Firstly let's do a small refactor and move all properties which are connected with currency to a new class:

```dart
class Currency {
  final String name;
  final String code;
  final String sign;
}
```

2. Right-click on errors and use `Create constructor for final fields`.

![dartpad](https://user-images.githubusercontent.com/85095377/182162882-739ec48b-39c1-4b32-b67b-dab4f409f1de.png)


3. Use Currency object in Account class:

```dart
class Account {
  Currency currency;
  double cash;
  
  Account(this.currency, this.cash);
}
```  
4. Use object:

```dart
void main() {
  Currency dollarCurrency = Currency('US Dollar', 'USD', '\$');
  Account myAccount = Account(dollarCurrency, 1401.77);
  
  print('Account information:');
  print('  - ${myAccount.currency.name}(${myAccount.currency.code}): ${myAccount.currency.sign}${myAccount.cash}');
}
```
