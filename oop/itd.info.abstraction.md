# Abstraction

```dart
/**
 * Abstract classes are blueprints of how a class should look like.
 * Abstract class cannot be instantiated. It may provided additional
 * declarations that must be fulfilled by child class.
 *
 * If a sub-class `extends` an `abstract` super-class with methods lacking body signature,
 * these methods must be implemented in the sub-class.
 */
void main() {
  // create Employee object
  var e = Employee('Ross', 'Geller', 1000);

  print('Employee e initials: ${e.getInitials()}');
  print('Employee e full name: ${e.getFullName()}');
}

// abstract `Person` class can only be extended or implemented
abstract class Person {
  // instance variables definition
  String firstName, lastName;

  // constructor is not a part of the `Person` interface
  Person(this.firstName, this.lastName);

  // this method will be inherited and accessible by child classes
  String getInitials() {
    return '${firstName[0]}${lastName[0]}';
  }

  // instance method definition
  // method body is optional as `Person` is abstract class
  // child class of this class will be forced to implement body of this method
  String getFullName();
}

// `Employee` implements structure defined by `Person` class
class Employee extends Person {
  int salary;

  // default constructor
  Employee(String firstName, String lastName, this.salary)
      : super(firstName, lastName);

  // ENFORCED: method declaration
  // parameters `firstName` and `lastName` gets `String` data type
  // from method definition in the `Person` interface
  @override
  String getFullName() {
    return '$firstName $lastName';
  }
}


```

Open in [DartPad](https://dartpad.dev/?id=66ee69496554c2a839e8ff37e3918dc7).
