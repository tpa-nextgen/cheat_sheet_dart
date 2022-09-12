# Constructor

### Positional parameters
```dart
void main() {
  Message message = Message('Łukasz', 'Hi!', '3:53PM');
  print(message.author);
  message.author = 'John';
  print(message.author);
}

class Message {
  String author;
  String timestamp;
  String message;

  Message(this.author, this.message, this.timestamp);
}

```

Open in [DartPad](https://dartpad.dev/?id=e8e442590be6acdb5f98b66c23d86827).

### Named parameters
```dart
void main() {
  Message message = Message(author: 'Łukasz', timestamp: '3:58PM');
  print(message.message);
  message.message = 'Hello';
  print(message.message);
}

class Message {
  String author;
  String timestamp;
  String message;

  Message({
    required this.author,
    required this.timestamp, 
    this.message = 'empty message', //default value
  });
}

```

Open in [DartPad](https://dartpad.dev/?id=4a3885a618bc612e651547b28552a897).

### Late fields initialization
```dart
void main() {
  late Message message = Message('Łukasz', 'Hi!', '3:53PM');
  
  // Will cause error because we cannot use this property before initialization
  // print(message.author);
  
  message.author = 'John';
  print(message.author);
}

class Message {
    late String author;
    late String timestamp;
    late String message;
  
    Message(String author, String message, String timestamp) {
      this.author = author.toUpperCase();
      this.message = message;
      this.timestamp = timestamp;
    }
}

```

Open in [DartPad](https://dartpad.dev/?id=a2a4c5f780cb7dd57e8b28959bb14630).

### Named constructors

```dart
void main() {
  Message emptyMessage = Message.empty();
  print(emptyMessage.author);

  Message exampleMessage = Message.example();
  print(exampleMessage.author);
}

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


```

Open in [DartPad](https://dartpad.dev/?id=fa50c68469b969f444c4859110089403).
