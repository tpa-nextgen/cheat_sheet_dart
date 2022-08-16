# Exceptions

```dart
import 'dart:convert';

void main() {
  try {
    final album = Album.fromJson(jsonDecode(
        '{,,,,"userId": 1,"id": 1,"title": "quidem molestiae enim"}'));
  } on TypeError catch (typeError, stackTrace) {
    print('TypeError:\n$typeError');
  } on FormatException catch (formatError, stackTrace) {
    print('FormatException:\n$formatError');
  } catch (unknownError, stackTrace) {
    print('Unknown:\n$unknownError');
  }
}

class Album {
  int userId;
  int id;
  String title;

  Album.fromJson(Map<String, dynamic> json)
      : userId = json['user_id'],
        id = json['id'],
        title = json['title'];
}

```