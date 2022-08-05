# Inheritance

```dart
/**
 * A Dart class can inherit instance variables and instance methods of another class.
 * Using `extend` keyword, a class basically extends the properties and behaviors of another class.
 *
 * Apart from static properties and constructor functions, everything else is inherited.
 *
 * When a class is inherited, Dart provides `super` keyword in child class to point to parent class.
 * `super` when used as a function calls the `default` constructor of the parent class.
 * We use `super.namedConstructor()` syntax to call a named constructor of the parent class.
 * A child class can access instance methods of the parent class using `super.methodName` syntax.
 *
 * When a parent class constructor function or method is called from the child class,
 * `this` object inside those functions is still pointing to the child class object.
 */
void main() {
  // create an Employee object
  var e = Employee('Ross', 'Geller', 1000);
  print('Employee e : ${e.firstName} ${e.lastName}, salary: ${e.salary}');

  // create Student object
  var s = Student('Rachel', 'Green', 418);
  print('Student s : ${s.firstName} ${s.lastName}, salary: ${s.score}%');

  // create Person object
  var p = Person('Joey', 'Tribbiani');
  print('Person p : ${p.firstName} ${p.lastName}');
}

// [parent class]
// Person class with basic details
class Person {
  String firstName, lastName;

  // default constructor
  Person(this.firstName, this.lastName);

  // named constructor
  Person.withUpperCase(this.firstName, this.lastName);
}

// [child class]
// Employee class shares feature of Person class
class Employee extends Person {
  int salary;

  // default constructor calls the default constructor of `Person` class using `super` function
  // constructor of the `Person` is executed first before the constructor of the `Employee` class
  // arguments of the child class default constructor function are available in `super` call
  Employee(String firstName, String lastName, this.salary)
      : super(firstName, lastName);
}

// Student class shares feature of Person class
class Student extends Person {
  late num score;

  // default constructor calls `Person.withUpperCase` constructor function of `Person` class
  Student(String firstName, String lastName, num marks)
      : super.withUpperCase(firstName, lastName) {
    score = num.parse(
        ((marks / 500) * 100).toStringAsFixed(6)); // limit decimal places to 2
  }
}

```
