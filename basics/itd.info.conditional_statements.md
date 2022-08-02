# Conditional statements

### if/else

Every day, you make assessments and comparisons and based on your findings, you make decisions. Is it cold outside? Yes, I may need to dress warmly. But is it really cold? If so, I may have to dig out my winter coat instead of relying on this flimsy jacket.

Programs need to make decisions, too. Is there a valid user signed in? If so, let the user interact with the UI. Does the file we need to load exist? If so, load it, but if not, create it.

Making decisions is an essential part of all but the simplest of computer programs. You could model some of your internal dialogue about what to wear outside with code like this:

```dart
void main() {
  num cold = 60;
  num temperature = 57;

  print("Is it cold outside?");
  
  if (temperature < cold) {
    print("Yes, a bit.");
  }
}
```

Dart supports the if/else statement in the same way as other popular languages. We can have if only blocks or if/else statement as well as if/else if/else ladder statements. Having one if/else blocks inside another is legal.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * If/Else statements in Dart look exactly similar to the one in JavaScript.
 * if(){ ... } : If only statement
 * if(){} else {}
 * if(){} else if{} else{}
 */
void main() {
  // simple `if` statement
  if (true) {
    print("SIMPLE IF: 'if{}' block executed");
  }

  // simple `if / else` statement
  var result = false;
  if (result) {
    print("SIMPLE IF/ELSE: 'if{}' block executed");
  } else {
    print("SIMPLE IF/ELSE: 'else{}' block executed");
  }

  // simple `if / else if / else` statement
  var grades = 8.2;
  if (grades > 9) {
    print("SIMPLE IF/ELSE IF/ELSE: 'if{}' block executed");
  } else if (grades > 8) {
    print("SIMPLE IF/ELSE IF/ELSE: 'else if{}' block executed");
  } else {
    print("SIMPLE IF/ELSE IF/ELSE: 'else {}' block executed");
  }
}
```

### Ternary operator
Dart also supports our beloved ternary operator to execute if/else statements on a single line with fewer words. The syntax is the same as in JavaScript.

Run ./02_ternary_operator.dart in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Ternary operator are used to evaluate a condition just like if/else but on a single line.
 * 
 * condition ? expr1 : expr2;
 * The `result` of the executed expression can be ignored or saved into a variable.
 */
void main() {
  // execute a statement
  var condition = true;
  condition
      ? print('when condition is "true"')
      : print('when condition is "false"');

  // save the selected value in a variable
  var value = (1 > 2) ? 'STUPID' : 'SMART';
  print("value = $value");

  // save the result of an evaluated expression in a variable
  var name = true ? 'First name' : 'Last name';
  print("name = $name");
}
```

### Non-null selector operator
`??` is the operator Dart provides to select a non-null value.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * ?? operator is used to select the non-null value.
 */
void main() {
  int? x = 10;
  int? y; // y has `null` initial value

  var safe_x = x ?? 0; // since `x` is not null, safe_x get the value of `x` which is `10`
  var safe_y = y ?? 0; // since `y` is `null`, safe_y gets `0` value

  print( "x + y = ${ safe_x + safe_y }" );
}
```

In the above example, we have created safe_x and safe_x to store non-null integer values to make the arithmetic operation successful. If an arithmetic operation is performed on a null value, the Dart program crashes.
?? operator is used to select a non-null value. In the syntax LHS ?? RHS, if the left-hand side expression or a variable is null, then the right-hand side value or result of an expression is returned.

### Switch

In a case when based on one variable we need to handle many cases we can instead of chaining if/else statements can use `switch`.

Run example in [DartPad](https://dartpad.dev/?)

```dart
import 'dart:math';

void main() {
  var name = 'Bob';
  var isDay = Random().nextBool();

  var greeting;
  switch (name) {
    case 'Adam':
      greeting = 'Hi, Adam!';
      break;// Notice those breaks that are added at the end of the code to execute for a given case
    case 'Bob':
      // Notice how each case can consist from multiline blocks of instructions
      if(isDay) {
        greeting = 'Good morning, Bob!';
      } else {
        greeting = 'Good evening, Bob!';
      }
      break;
    case 'David':
      greeting = 'Good to see you, David!';
      break;
    default:
      greeting = 'Good Morning';
  }
  print(greeting);
}

```

> ### Additional Materials
> * Dart Academy Boot Camp - Lesson 8, 9 and 10, 12 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart samples - <https://dart.dev/samples#control-flow-statements>
