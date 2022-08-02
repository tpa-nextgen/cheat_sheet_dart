# Loops

Dart supports for C++ style for loop with `for(initializationStatement; testExpression; updateStatement) { // codes }` syntax as well as Python style for-in loop to iterate over a List of items. For-in loop uses the `iterator` of a given collection. Note that you can't use for-in with `Map` because it doesn't implement `Iterable`. You can also use `iterator` directly.

Run example in [DartPad](https://dartpad.dev/?)

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

Variables declared inside the `for` or `for-in` loop do not hoist outside. For example, `i` in the first loop and `fruit` in the second loop can not be accessed outside these loops.

Dart also supports the `break` and `continue` keywords to break out of a for loop or to skip an iteration. If we have nested for loops, then `break` or `continue` will not affect the parent loops.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * We can skip an iteration using the `continue` keyword,
 * or terminate the loop using the `break` keyword.
 
 * If we have nested loops,
 * `break` and `continue` will only affect the current loop.
 */
void main() {
  // [parent] for loop
  for (var i = 0; i < 10; i++) {
    print(
        "Parent iteration $i: "); // always prints for each iteration of `parent` loop

    // [child] for-in loop
    for (var side in ['LEFT', 'RIGHT']) {
      if (side == 'LEFT') {
        continue; // skip iteration of `child` loop when `side` is `LEFT`
      } else if (i >= 6) {
        break; // break `child` loop when `i` is greater than or equal to 6
      } else {
        print("SIDE => $side | ");
      }
    }

    print(""); // print new line
  }
}
```

From the above example, we can see that `continue` keyword only skipped the iteration of the inner `for-in` loop, as well as `break`, terminated the inner `for-in` loop while the outer for loop kept working.

Dart supports also `while` and `do-while` loops. In the case of `while(condition){}` loop, statement inside `while` block is only executed when `condition` is true. However, in the case of `do{} while(condition)` loop, do block is executed first, and then the `condition` is checked in the `while` block.

Run example in [DartPad](https://dartpad.dev/?)

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
 * In the case of `while` loops, `condition` is first evaluated and then `statements` are executed.
 * But in the case of `do/while` loop, `statements` inside `do` block is first executed, and then `condition` is evaluated.
 */
void main() {
  // simple `while` loop
  var i = 0;
  while (i < 5) {
    print("$i ");
    i++; // increment i to avoid infinite iteration
  }

  print(""); // print newline

  // simple `do/while` loop
  var j = 10;

  do {
    print('do-while: $j');
  } while (j < 10);
}
```


> ### Additional Materials
> * Dart Academy Boot Camp - Lessons 14, 15, and 16 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart flow control - loops - <https://www.youtube.com/watch?v=VNPPApTef-E>
