# Constructor

Questions:
- How can I construct objects?

KeyPoints:
- constructor
- required
- named constructor
---

In class-based object-oriented programming, a `constructor` is a special type of subroutine called to create an object. It prepares the new object for use, often accepting arguments that the constructor uses to set required member variables. In this chapter, we will focus on different types of constructors. Let's consider an example class of slack message:

![slack](https://user-images.githubusercontent.com/85095377/182162303-f14eaae1-f36c-4dd1-99dc-47f965ee7f96.jpg)

~~~
class Message {
    String author;
    String timestamp;
    String message;

    // Add constructor here
}
~~~

Below in this chapter, you can find multiple ways how you can define a class constructor.

## 1. No constructor class

In the beginning, let's consider class without constructors.

### 1.1 Initial values

You can define initial values of properties and later change that. 

You can ask, where's the constructor?!?!
In the case where all values are initialized, you can omit the constructor. That means, the compilator sees that all properties are initialized well so it will use `default constructor` which is added implicitly to any class as an empty constructor, e.g. `Message();`.

~~~
class Message {
    String author = 'Łukasz';
    String timestamp = '3:53PM';
    String message = 'Hi!';
}

void main() {
  late Message message = Message(); 
  print(message.author);
  message.author = 'John';
  print(message.author);
}
~~~

> Łukasz
> John

### 1.2 Nullable properties

Similarly to the above situation, you can use only nullable properties, which causes you can fill object properties later.

~~~
class Message {
    String? author;
    String? timestamp;
    String? message;
}

void main() {
  late Message message = Message(); 
  print(message.author);
  message.author = 'John';
  print(message.author);
}
~~~


> null
> John

### 1.3 `Late` properties
Lastly, you can mark a property as `late` and expect that you will remember to assign that before use.

~~~
class Message {
    late String author;
    late String timestamp;
    late String message;
}

void main() {
  late Message message = Message(); 
  //print(message.author); -> Can cause error because we cannot use this property before initialization
  message.author = 'John';
  print(message.author);
}
~~~

> John

#### Where can I use these approaches?

In most cases, it's useful for singular class properties which can be filled initially or can be null. Very rarely is a situation where you omit the constructor totally. 

## 2. Initializing formals

Constructor which uses `Initializing formals` is well-known from previous chapters constructor where you define all properties in brackets with `this` keyword.

~~~
class Message {
    String author;
    String timestamp;
    String message;
  
    Message(this.author, this.message, this.timestamp);
}

void main() {
  late Message message = Message('Łukasz', 'Hi!', '3:53PM'); 
  print(message.author);
  message.author = 'John';
  print(message.author);
}
~~~

> Łukasz
> John

#### Where can I use this approach?

It's probably the most common constructor which you will see in Dart programs. It's easy to understand and always enforce an assignment of all properties.

## 3. Constructor as a function

Basically, constructor is a function (or better - `method`, `function` in class is called `method`), so you can use a constructor similarly to any other method.

### 3.1 Lazy initialization

This type of constructor can have `body` as a normal function, so inside that, you can specify some additional operations like in example:

~~~
class Message {
    late String author;
    late String timestamp;
    late String message;
  
    Message(String author, String message, String timestamp) {
      this.author = author.toUpperCase()
      this.message = message;
      this.timestamp = timestamp;
    }
}

void main() {
  late Message message = Message('Łukasz', 'Hi!', '3:53PM'); 
  print(message.author);
  message.author = 'John';
  print(message.author);
}
~~~

> ŁUKASZ
> John

### 3.2 Named parameters

Similarly, like functions, you can define a constructor with named parameters. With that, you can define `default value` of the parameter or `required` parameter which has to be initialized.

~~~
class Message {
  String author;
  String timestamp;
  String message;

  Message({
    required this.author,
    required this.timestamp,
    this.message = 'empty message',
  });
}

void main() {
  late Message message = Message(
    author: 'Łukasz',
    timestamp: '3:58PM'
  );
  print(message.message);
  message.message = 'Hello';
  print(message.message);
}
~~~

> empty message
> Hello

#### Where can I use these approaches?

These constructors mostly are useful with frameworks/libraries/packages which allow a developer to use universal tools (classes) to produce his/her own implementations. 

## 4. Named constructor

You can use a named constructor to implement multiple constructors for a class or to provide extra clarity. Named constructor is in form: `ClassName.identifier`:

~~~
class Message {
  late String author;
  late String timestamp;
  late String message;

  Message(this.author, this.message, this.timestamp);

  Message.empty() {
    author = '';
    timestamp = '';
    message = '';
  }

  Message.example() {
    author = 'Łukasz';
    timestamp = '3:58PM';
    message = 'Hi!';
  }
}

void main() {
  Message emptyMessage = Message.empty();
  print(emptyMessage.author);
  
  Message exampleMessage = Message.example();
  print(exampleMessage.author);
}
~~~

> Łukasz

#### Where can I use this approach?

In situations where you need more than one way to construct object. For example you need to produce some empty values object or default values object.
