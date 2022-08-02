# Dart Introduction: Hello World Program

When a Dart script runs like a standalone program, it should have a `main` function which is the entry point of the execution. As Dart is a statically-typed language, our main method must specify a return type, which normally is `void` when it doesn’t have a `return` statement.

```dart
/**
 * `main` function is the entry point of execution
 * when a .dart file is executed using `dart` command
 */
void main() {
  print( "Hello World" ); // print is built-in function to print an object to the STDOUT
}
```

There are many things to take away from the example. First, single-line comments are written after `//`, and block comments are written inside `/* */`, just like in other languages and they can appear anywhere in the code. Dart also differentiates between comments and comments that are documentation. Single-line documentation is started with `///` and block documentation is written inside `/** */`.

`print` is a built-in function provided by Dart. It is capable of printing any Data Type as well as executing an expression like `1+1`.

Unlike other languages like JavaScript which do not complain when a statement is terminated without `;` (a semicolon), Dart won’t compile a program if a statement is not terminated with a semicolon, for example, avoiding ; at the end of the print statement in the above example.

Use [Dartpad](https://dartpad.dev/) to execute above code.

> ### Additional Materials
> * Dart Academy Boot Camp - Lesson 1 - <https://da-bootcamp.firebaseapp.com/?course=start_programming_dart>
> * Dart samples - <https://dart.dev/samples#hello-world>
