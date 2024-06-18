# Day 9 - Networking in Dart

## Networking in Dart

Networking in Dart involves making HTTP requests to web APIs to retrieve or send data. The `http` package is an official and popular package in Dart that makes it easy to perform HTTP requests.

## Project - Movie Searcher

Today, we'll create a Dart console program that uses the OMDB movie API to provide the following functionalities:
- Search for movie information by title.
- View a list of upcoming films.
- Get a list of the best-rated movies.
- Compile a list of popular films.

By the end of this day, you should have a basic understanding of how to make HTTP requests using the `http` package and how to parse JSON data in Dart.

## Tips

### 1. Study HTTP Requests

Learn how to make HTTP requests using the `http` package.

```dart
import 'package:http/http.dart' as http;

void main() async {
  var response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/posts'));
  print(response.body);
}
```

In this example, we import the http package and use the get method to make a GET request to the specified URL. The await keyword is used to wait for the response, which is then printed to the console.

2. Parse JSON Data
Many web APIs return data in JSON format. Dart provides built-in support for parsing JSON data using the dart:convert library.

```dart

import 'dart:convert';

void main() {
  String jsonData = '{"name": "John", "age": 30}';
  Map<String, dynamic> data = jsonDecode(jsonData);
  print(data['name']); // Output: John
}
```
In this example, we have a JSON string representing an object with two properties, name and age. We use the jsonDecode function to parse the JSON data into a Map object. We can then access the properties of the object using the keys.

3. Make POST Requests
Use the http package to make GET and POST requests to a web API.

To make a POST request using the http package, we can use the post method.

```dart

import 'package:http/http.dart' as http;

void main() async {
  var url = Uri.parse('https://jsonplaceholder.typicode.com/posts');
  var response = await http.post(url, body: {'title': 'foo', 'body': 'bar', 'userId': '1'});
  print(response.statusCode);
}
```
In this example, we make a POST request to the specified URL and pass in a Map object as the body parameter.

4. Parse JSON Data into Dart Objects
When we receive JSON data from a web API, we often want to convert it into Dart objects for easier manipulation. We can create Dart classes that mirror the structure of the JSON data and then use the jsonDecode function to convert the JSON data into Dart objects.

```dart

import 'dart:convert';

class Post {
  int id;
  String title;
  String body;

  Post({required this.id, required this.title, required this.body});

  factory Post.fromJson(Map<String, dynamic> json) {
    return Post(
      id: json['id'],
      title: json['title'],
      body: json['body'],
    );
  }
}

void main() {
  String jsonData = '{"id": 1, "title": "foo", "body": "bar"}';
  Map<String, dynamic> data = jsonDecode(jsonData);
  Post post = Post.fromJson(data);
  print(post.title); // Output: foo
}
```
In this example, we have a Dart class Post that represents a post object with three properties: id, title, and body. We also have a factory constructor fromJson that takes a JSON object and returns a Post object.

Conclusion
By understanding how to handle networking in Dart, you can create applications that interact with web APIs, retrieve data, and display it in a meaningful way. Today's project helps solidify these concepts by providing a practical example of making HTTP requests, parsing JSON data, and working with external APIs.

#Dart #Flutter #Networking #Programming #SoftwareDevelopment #Coding #MobileDevelopment #FlutterDev #DartLang


