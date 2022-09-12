```dart
import 'package:two_fer/two_fer.dart';

void main(List<String> arguments) {
  print(twoFer());
}

/**
 * Here you can write 
 * multiline
 * documentation comments. 
 * Notice double ** at the beginning.
 */
void functionWithBlocComments() {
  /*
   * If you start bloc comment with a single *
   * it means that this is a comment, not part of the documentation.
   */
}

/// This is currently recommended style.
/// For documentation, you start every
/// line
/// with triple ///.
void functionWithRecommendedStyleOfComments() {
  // Comments that start with // are not considered part of the documentation.
}

/// Dart documentation support [markdown](https://dart-lang.github.io/markdown/)
/// so you can **format it**
/// * to
/// * your
/// * liking
///
/// You can reference other declarations by using brackets: [OtherClass].
/// Including fields [OtherClass.foo] and methods [OtherClass.bar]
///
/// You can document any declaration of:
///
/// classes
class SomeClass {
  /// fields
  final int field;

  /// constructors
  SomeClass(this.field);

  /// methods
  void method() {}
}

/// and functions
void function() {}

/// Other class see [SomeClass]
class OtherClass {
  /// Field doc
  int foo = 1;

  /// Method doc.
  void bar() {}
}

```

Open in [DartPad](https://dartpad.dev/?id=83ed3ad8e0dd5165ec2457d03ec0d639).
