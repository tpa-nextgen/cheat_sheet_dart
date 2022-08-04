# Conditional statements

### if/else

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

Run example in [DartPad](https://dartpad.dev/?)

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
### Switch

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
      break;// Breaks are added at the end of the code to be executed for a given case
    case 'Bob':
      // Each case can consist from multiline blocks of instructions
      if(isDay) {
        greeting = 'Good morning, Bob!';
      } else {
        greeting = 'Good evening, Bob!';
      }
      break;
    case 'David':
      greeting = 'Good to see you, David!';
      break;
    default: // if no case match default will be executed
      greeting = 'Good Morning';
  }
  print(greeting);
}

```
