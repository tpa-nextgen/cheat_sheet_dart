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
### Late fields initialization
```dart
void main() {
  late Message message = Message('Łukasz', 'Hi!', '3:53PM'); 
  print(message.author);
  message.author = 'John';
  print(message.author);
}

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

```

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