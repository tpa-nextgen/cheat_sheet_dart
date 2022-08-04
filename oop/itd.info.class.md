# Define a class with properties that capture the data aspects of a core noun

Goals:
- How can I define data as a class?
- How can I keep data in class? (properties)
- How can I create an instance of a class? (object)

KeyPoints:
- class
- property
- object
---

## 1. What Is an Object in Programming?
Object-oriented programming, or OOP, is an approach to problem-solving where all computations are carried out using objects. An object is a component of a program that knows how to perform certain actions and how to interact with other elements of the program. Objects are the basic units of object-oriented programming. A simple example of an object would be a person. Logically, you would expect a person to have a name. This would be considered the property of the person. You could also expect a person to be able to do something, such as walking or driving. This would be considered a method of the person.

Code in object-oriented programming is organized around objects. Once you have your objects, they can interact with each other to make something happen. Let's say you want to have a program where a person gets into a car and drives it from A to B. You would start by describing the objects, such as a person and a car. That includes methods: a person knows how to drive a car, and a car knows what it is like to be driven. Once you have your objects, you bring them together so the person can get into the car and drive.

## 2. Common problems before OOP
* P1: How can I return more that one value from a function?

~~~
int function(int a, int b) {
    ...
    return a, b; // Error!!!
}
~~~

* P2: When I pass multiple parameters to function it looks sloppy:

~~~
void function(int a, int b, string c, double d, int e, int f, int g....) {
    ...
}
~~~


* P3: How can I keep clean, structured code?

~~~
int a = 10;
int b = 100;
String c = "hello";
String d = World;
double e = 10.10;
~~~


## 3. Class

A class is a blueprint of an object. You can think of a class as a concept, and the object is the embodiment of that concept. You need to have a class before you can create an object. So, let's say you want to use a car in your program. You want to be able to describe the car and have the car do something. A class called 'Car' would provide a blueprint for what a car looks like and what a car can do. To actually use a car in your program, you need to create an object. You use the car class to create an object of the type 'Car.' Now you can describe this car and have it do something.

Classes are very useful in programming. Consider the example of where you don't want to use just one car but 100 cars. Rather than describing each one in detail from scratch, you can use the same car class to create 100 objects of the type 'Car.' You still have to give each one a name and other properties, but the basic structure of what a car looks like is the same.

Let's consider the example of an application where you can find a car ad. One of them can look similarly to:

![car](https://user-images.githubusercontent.com/85095377/182160924-72a8073d-b722-45ce-9953-52a3b7197567.jpeg)

Each ad describes a car in a slightly different way so we need a template to produce that car. What features can we find in this type of ad?

![car2](https://user-images.githubusercontent.com/85095377/182160940-9efa70bc-f28d-4570-ace0-979d3cebd286.jpg)

> Please keep attention of style of naming - it's called [camelCase](https://en.wikipedia.org/wiki/Camel_case).

Okay! All of properties works as a normal variable so we can add a type of them.

![car3](https://user-images.githubusercontent.com/85095377/182160955-ba3ea3e8-6e1c-4d1a-8d6a-7f26c22ec2b9.jpg)

The last step is to create a real class of Car:

~~~
class Car {                     // #1
  String name;                  // #2
  int productionYear;
  double price;
  int travelledKms;
  String engineType;
  double engineCapacity;

  Car(                          // #3
    this.name,                  // #4
    this.productionYear,
    this.price,
    this.travelledKms,
    this.engineType,
    this.engineCapacity,
  );
}
~~~


#### Decomposition:
* **Line #1** To create a minimal class you need to start from the keyword `class`, class name, and brackets:

```dart
class ClassName {}
```


* **Line #2** To keep data within a class you have to define class `properties`. Actually, it looks like any normal variable has got type and name.

~~~
Type name;
~~~


* **Line #3** Any class in Dart requires a special part of code called `constructor` - a definition of how we can construct the object of that class. There a multiple ways to define (or even skip) constructor in Dart. You'll learn about that in the next lessons. Constructor always starts with the class name and in the simplest version defines all `properties` with the special keyword `this`.

~~~
ClassName(this.property1, this.property2)
~~~


* **Line #4** Order of properties doesn't matter, it will enforce order during the creation object (described in a moment). Keyword `this` points to "this specific object". Quite hard, is it? Let's create an object of class!

## 4. Object

An Object is an identifiable entity with some characteristics and behavior. An Object is an instance of a Class. When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.

To create an object of class we have to write:

```dart
ClassName variableType = ClassName(properies);
```


In Car example looks like this:

~~~
Car newCar = Car("audi", 2013, 48000, 270000, "Diesel", 1968);
~~~


So to sum up - we have to create a new variable with the type of class and name: `Car newCar` and later we have to assign that to `constructor` with all filled properties: `= Car("Audi", 2013, 48000, 270000, "Diesel", 1968)`

Furthermore, while we have one `class` of a car means that we can produce as many cars as we want to:
~~~
Car audi = Car("Audi", 2013, 48000, 2780000, "Diesel", 1968);
Car bmw = Car("BMW", 2011, 148000, 270000, "Diesel", 3000);
Car citroen = Car("Citroen", 2017, 100000, 270231, "Diesel", 1000);
Car mazda = Car("Mazda", 2019, 88000, 270100, "Diesel", 1200);
Car fiat = Car("Fiat", 2014, 98000, 27100, "Petrol", 1600);
Car tesla = Car("Tesla", 2020, 248000, 36, "Hybrid", 2200);
~~~


## 5. What I can do with that?

An object is an instance of a class, which means that it has got its own data. 
~~~
Car newCar = Car("Audi", 2013, 48000, 270000, "Diesel", 1968);
~~~


With object we can:

* read values of properties (to do that we use an `.` dot operator which gives us access to object contents):

~~~
print(newCar.name);
~~~

> Audi

* update values of properties (to do that we use an `.` dot operator which gives us access to object contents):

~~~
newCar.engineType = "gasoline";
print(newCar.engineType);
~~~

> gasoline


* pass object as a function parameter

~~~
double getCarPrice(Car car) {
    return car.price;
}

print('${getCarPrice(newCar)} PLN');
~~~

> 48000 PLN

* return object from a function

~~~
Car carFactory(String name, double price) {
    Car newCar = Car(name, 2013, price, 270000, "Diesel", 1968);
    return newCar;
}
~~~

## 6. Answers

* P1: How can I return more that one value from function?

~~~
class Point {
    int x;
    int y;

    Point(this.x, this.y);
}

Point getZeroPoint() {
    Point point = Point(0, 0);
    return point;
}
~~~

* P2: When I pass multiple parameters to function it looks sloppy:

~~~
void showCarInformation(Car car) {
    print(car.name);
    print(car.price);
    print(car.engineType);
}
~~~

* P3: How can I keep clean, structured code?

Classes give us the possibility to keep all data connected to some logical part inside one "box" called a class. For example, everything which is connected to cars can be stored inside the Car class.
