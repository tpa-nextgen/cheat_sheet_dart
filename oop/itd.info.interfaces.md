```dart
/**
* In Dart every class implicitly defines an interface. 
* That shifts responsibility from parent to child to decide: 
* do you want to extend class (build upon it) or 
* implement class (implement every aspect of a class, inheriting only declarations).
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

class Person {
  String firstName, lastName;

  // default constructor
  Person(this.firstName, this.lastName);

  // named constructor
  Person.withUpperCase(this.firstName, this.lastName);

  String fullName() {
    return '$firstName $lastName';
  }
}

// Employee also inherits fields and have ability to call parent constructors and methods
class Employee extends Person {
  int salary;

  Employee(String firstName, String lastName, this.salary)
      : super(firstName, lastName);

  String fullNameWithSalary() {
    return '${fullName()} : $salary';
  }
}

// // Student class shares feature of Person class
class Student implements Person {
  @override
  String firstName;
  @override
  String lastName;
  late num score;

  Student(this.firstName, this.lastName, num marks) {
    score = num.parse(((marks / 500) * 100).toStringAsFixed(6));
  }

  @override
  String fullName() {
    // Student class is forced to implement parent method again
    return '${firstName.toUpperCase()} $lastName';
  }
}

```