# Abstraction

Questions:
- How can I create a template for class?
- How can a super-class enforce child behavior?

KeyPoints:
* abstract
* implements
---

An `abstract class` is a blueprint or a template of a class. This blueprint contains definitions of instance variables and instance methods a class must implement. This is useful to enforce a consistent class structure. To force a class to implement the `abstract class`, we use the `implements` keyword just like the `extends` keyword.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Abstract classes are blueprints of how a class should look like.
 * Abstract class provides a `strict` schema to define a class.
 *
 * In Dart, a class is also defined as abstract implicitly. Hence they are called implicit abstracts.
 * We used the `implements` keyword to implement an interface on a class.
 * Unlike inheritance, a class can implement multiple interfaces.
 *
 * 
 * 🔥 TIPS:
 * 1. If a sub-class `extends` an `abstract` super-class with methods lacking body signature,
 * __ these methods must be implemented in the sub-class.
 */
void main() {
  // create Employee object
  var e = Employee('Ross', 'Geller', 1000);

  print('Employee e full name: ${e.getFullName(e.firstName, e.lastName)}');
}

// abstract `Person` class can only be extended or implemented
abstract class Person {
  // instance variables definition
  String firstName, lastName;

  // constructor is not a part of the `Person` interface
  Person(this.firstName, this.lastName);

  // instance method definition
  // method body is optional as `Person` is abstract class
  String getFullName(String firstName, String lastName);
}

// `Employee` implements structure defined by `Person` class
class Employee implements Person {
  // ENFORCED: instance variables declaration from the `Person` interface
  String firstName, lastName;

  int salary; // not enforced as it is missing in `Person` class

  // default constructor
  Employee(this.firstName, this.lastName, this.salary);

  // ENFORCED: method declaration
  // parameters `firstName` and `lastName` gets `String` Data Type
  // from method definition in the `Person` interface
  String getFullName(firstName, lastName) {
    return '$firstName $lastName';
  }
}

```

There are a lot of things going on in the above example. The important thing to remember is that an `abstract class` is just a class and we use the `implements` keyword to enforce a class to declare relevant variables and methods.

An abstract class can not be instantiated, hence we can declare methods without a body as we did with `getFullName` method in the `Person` class. However, an abstract class can be inherited. Hence, any class that inherits an abstract class must override the method that lacks the body.

Unlike inheritance where a sub-class can extend only one super-class, a class can implement multiple classes `A implements B, C, D {...}`.

---

Consider a situation where you have a method that takes an object of type Person or object of the type Employee which inherits from the Person class. What Data Type of the parameter would you choose?

You could choose dynamic which represents everything but then you need to throw an exception if the argument is not of Person or Employee type. This is where Polymorphism saves us.

Polymorphism is a concept in OOP that means one object can have many forms. In a technical sense of statically typed languages like Dart means, a variable has the type of its class or any class that it inherits from.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * Polymorphism is the ability of an object to take any form.
 * Everything in Dart is an object and all objects are inherited from the `Object` class.
 * Hence, for example, a `String` object is both types of `String` and `Object.
 *
 * An object of a class that `inherits` another class, can be represented in both the class types.
 * Also, an object of a class that `implements` another class, can also be represented in both the class types.
 *
 * We use `object.runtimeType` to get an actual type of the object at runtime.
 */
void main() {
  // create `Person` and `Employee` objects
  var p = Person('Joey', 'Tribbiani');
  var e = Employee('Ross', 'Geller', 1000);

  // We can call the `fullName` function with `p` because it accepts argument of type `Person`
  print('Person p full name: ${fullName(p)}');

  // We can call `fullName` function with `e` because `e` is also a type of `Person`
  print('Employee e full name: ${fullName(e)}');
}

// `getFullName` of a `Person` or an `Employee` object
String fullName(Person person) {
  return '${person.firstName} ${person.lastName}';
}

// A `Person` object contains basic personal details
class Person {
  String firstName, lastName;

  // default constructor
  Person(this.firstName, this.lastName);
}

// `Employee` class shares feature of the `Person` class
class Employee extends Person {
  int salary;

  // default constructor
  Employee(String firstName, String lastName, this.salary)
      : super(firstName, lastName);
}

```

In the above example, the object `e` has a type of Employee since it is an instance of that class. But it also has a Person type because Employee inherits from the Person class. Hence the function `fullName` can accept `p` as well as e because they both satisfy the parameter of type Person.

Similar to the case of inheritance, if a class implements an interface, any object that class also has that interface type. We can see the actual Data Type of an object using `object.runtimeType` syntax.