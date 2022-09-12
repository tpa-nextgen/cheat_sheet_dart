# Loops


```dart
/**
 * Dart supports C style for a loop as well as python style for-in loops.
 *
 * [type 1]
 * for( init_statements, compare_statement, increment_statements ) { ... }
 *
 * [type 2]
 * for( var variable in iterator ) { ... }
 *
 * [type 3]
 * final iterator = list.iterator;
 * while (iterator.moveNext()) {
 *   print(iterator.current);
 * }
 */
void main() {
  // C style for loop
  for (int i = 0; i < 5; i++) {
    print("$i ");
  }

  print(""); // print newline

  // python style for-in loop to loop over a list or an iterator
  var fruits = ["Mango", "Apple", 'Banana'];
  for (var fruit in fruits) {
    print("$fruit ");
  }

  // using iterator directly to loop over a list
  final iterator = fruits.iterator;
  while (iterator.moveNext()) {
    print(iterator.current);
  }
}

```

Open in [DartPad](https://dartpad.dev/?id=854835f93a42efb0344a6d7dbf4205d3).

Variables declared inside the `for` or `for-in` loop do not hoist outside. For example, `i` in the first loop and `fruit` in the second loop can not be accessed outside these loops.


```dart
/**
 * We can skip an iteration using the `continue` keyword,
 * or terminate the loop using the `break` keyword.
 
 * If we have nested loops,
 * `break` and `continue` will only affect the current loop.
 */
void main() {
  for (var i = 0; i < 10; i++) {
    print("Parent iteration $i: ");

    // [child] for-in loop
    for (var side in ['LEFT', 'RIGHT']) {
      if (side == 'LEFT') {
        continue; // skip iteration when `side` is `LEFT`
      } else if (i >= 6) {
        break; // stop loop when `i` is greater than or equal to 6
      } else {
        print("SIDE => $side | ");
      }
    }

    print("");
  }
}

```

Open in [DartPad](https://dartpad.dev/?id=0aa296470a0245e7b01d3f54cd54f484).


```dart
/**
 * Dart supports `while` and `do/while` loops in the same syntax format of JavaScript.
 * 
 * [while]
 * while (condition) { statements; }
 *
 * [do/while]
 * do{ statements; } while( condition );
 *
 */
void main() {
  var i = 0;
  while (i < 5) {
    print("$i ");
    i++;
  }

  print("");

  var j = 10;
  do {
    print('do-while: $j');
    j++;
  } while (j < 15);
}

```

Open in [DartPad](https://dartpad.dev/?id=d119e59a3a611f3bc7d3702e0ebfd55d).
