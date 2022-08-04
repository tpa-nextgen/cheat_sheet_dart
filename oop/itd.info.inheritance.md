# Inheritance

Questions:
- How can I extend class features?
- How can I reuse my classes?
- What means `extends` keyword
- What means `super` keyword in a constructor

KeyPoints:
* inheritance
* extends
* super

---

Inheritance is a very useful and powerful concept of object-oriented programming. In Dart, using the inheritance concept, we can use the existing features of one class in another class. The inheritance provides a great advantage called code re-usability. With the help of code re-usability, the commonly used code in an application need not be written again and again.

* The `Parent class` is the class that provides features to another class. The parent class is also known as `Base class` or `Superclass`.

* The `Child class` is the class that receives features from another class. The child class is also known as the `Derived Class` or `Subclass`.

Run example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * A Dart class can inherit instance variables and instance methods of another class.
 * Using `extend` keyword, a class basically extends the properties and behaviors of another class.
 *
 * Apart from static properties and constructor functions, everything else is inherited.
 * A class that is inheriting another class is called a sub-class while the class that it inherits from is called a `super-class`.
 *
 * When a class is inherited, Dart provides `super` keyword in `sub-class` to point to `super-class`.
 * `super` when used as a function calls the `default` constructor of the `super-class`.
 * We use `super.namedConstructor()` syntax to call a named constructor of the `super-class`.
 * A `sub-class` can access instance methods of the `super-class` using `super.methodName` syntax.
 *
 * When a `super-class` constructor function or method is called from the `sub-class`,
 * `this` object inside those functions is still pointing to the `sub-class` object.
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

// [super-class]
// Person class with basic details
class Person {
  String firstName, lastName;

  // default constructor
  Person(this.firstName, this.lastName);

  // named constructor
  Person.withUpperCase(this.firstName, this.lastName);
}

// [sub-class]
// Employee class shares feature of Person class
class Employee extends Person {
  int salary;

  // default constructor calls the default constructor of `Person` class using `super` function
  // constructor of the `Person` is executed first before the constructor of the `Employee` class
  // arguments of the `sub-class` default constructor function are available in `super` call
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

* If a super-class (the one we `extends` to) default constructor does not take any arguments, we can avoid `:super()` call in the `sub-class`. It will be called implicitly by the Dart when an object is created from the sub-class.
* If we do not want a parent class to be instantiated or created objects from, we can make it `abstract` using `abstract` keyword.
* When we inherit a class, its methods are also available on the sub-class. We have learned that `super()` function calls the super-class constructor and super keyword points to the super-class. We can also call super-class instance methods using `super.superClassMethod()` syntax.

Run next example in [DartPad](https://dartpad.dev/?)

```dart
/**
 * When both `sub-class` and `super-class` has a method with a common name,
 * then the method in the `sub-class` is used instead.
 *
 * This is called method overriding as a method in the `sub-class` is preferred over method in the `super-class`,
 * which is more like overriding the functionality of the `super-class` method.
 *
 * If the intention of the method overriding is to extend the functionality of the `super-class` method,
 * then the original method should be used from inside the method in the `sub-class` using `super` keyword.
 *
 * Dart recommended annotating an overriding method using `@override` annotation.
 *
 * An `abstract` class can not be instantiated. It can only be inherited.
 */
void main() {
  
  // create Employee object
  var e = Employee( 'Ross', 'Geller', 1000 );
  print( e );
  
}

// A `Person` object contains basic personal details
// Since `Person` is abstract, it can not be instantiated
abstract class Person {
  
  // instance variables
  String firstName, lastName;

  // default constructor
  Person( this.firstName, this.lastName );
  
  // get full name
  String getFullName() {
    return '${ this.firstName } ${ this.lastName }';
  }

  // return `String` value format of the `Person` object
  @override
  // override `toString` method of `Object` class
  String toString() {
    return 'Person: ${ this.getFullName() }';
  }
}

// `Employee` class shares feature of `Person` class
class Employee extends Person {
  int salary;

  // default constructor
  Employee( String firstName, String lastName, this.salary ): super( firstName, lastName );

  // return `String` value format of the `Employee` object
  // overrides `toString` method of `Person` class
  @override
  String toString() {
    
    // execute parent `toString` method
    var rprPerson = super.toString(); // `Person` object String representation
    
    return 'Employee: (${ rprPerson }) with salary ${ this.salary }'; 
  }
}

```

When we create a method on a sub-class with the name same as on the super-class, it is called method overriding. This is because when this method is invoked on the sub-class object, the method of the sub-class object is used.
