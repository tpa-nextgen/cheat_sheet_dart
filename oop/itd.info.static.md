# Static

Sometimes all objects of a given class share some value, that is the same for all of them. We could do it like this:

```dart
class Circle {
  final pi = 3.14159;
  final double radius;
  Circle(this.radius);
}
```

Doing it in such a way would cause that every time we create a new instance of a given class we would create in computer memory space that would contain the `pi` value. Instead, we can use the `static` keyword that will cause all instances to share one instance of `pi`.

```dart
class StaticCircle {
  static const pi = 3.14159;
  final double radius;
  StaticCircle(this.radius);
}
```

In Dart, each double takes 64 bits in computer memory. So fields of 10 000 instances of Circle would take 1250 KiB of memory, while StaticCircle 625 KiB Using `static const` allows Dart to do some optimizations of the code so the code will also be executed faster.

Static can also be used to define some constants that are used through the app so if we change it in the future we will only need to change it in one place. That will reduce the chance for us to make mistakes. Putting a constant in a class, instead of a global constant, gives future programmers some context and one place to look for values that are connected to each other.

```dart
class TextSize {
  static const title = 20;
  static const text = 12;
}
```
