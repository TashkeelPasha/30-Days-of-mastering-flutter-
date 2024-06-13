# Day 5: Mastering Asynchronous Programming, Streams and Error Handling in Dart

Welcome to Day 5 of the #30DaysOfFlutter challenge. Today, we'll explore asynchronous programming and streams in Dart, essential concepts for building responsive applications.

![day 5](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/9af0a6ff-3687-4837-8f07-64aad00bc04b)



## Key Concepts

### Understanding Futures
A `Future` represents a potential value or error that will be available at some time in the future. It's a placeholder for a value that hasn't been computed yet.

```dart
void main() {
  print('Fetching data...');
  fetchData();
}

Future<void> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  print('Data fetched successfully.');
}
```

Using async and await
The async keyword is used to mark a function as asynchronous, allowing you to use the await keyword inside it. await pauses the execution until the awaited Future completes.

```dart

void main() async {
  print('Starting computation...');
  int result = await computeSum(5, 10);
  print('The sum is $result');
}


Future<int> computeSum(int a, int b) async {
  await Future.delayed(Duration(seconds: 1));
  return a + b;
}
```

##Handling Errors in Asynchronous Code

Handling errors in asynchronous functions is crucial for creating robust applications. Use try, catch, and finally blocks to handle potential errors.

```dart

void main() async {
  try {
    print('Fetching user profile...');
    String profile = await fetchUserProfile();
    print('User profile: $profile');
  } catch (e) {
    print('Error: $e');
  } finally {
    print('Fetch attempt completed.');
  }
}

Future<String> fetchUserProfile() async {
  await Future.delayed(Duration(seconds: 2));
  throw 'Failed to fetch user profile';
}

```

Project - Fetching Data from an API
We'll create a simple application that fetches data from an API using asynchronous programming.

```dart

import 'dart:convert';
import 'package:http/http.dart' as http;

void main() async {
  String data = await fetchData();
  print('Data: $data');
}

Future<String> fetchData() async {
  final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/todos/1'));
  
  if (response.statusCode == 200) {
    return json.decode(response.body)['title'];
  } else {
    throw Exception('Failed to load data');
  }
}
```

##Stream
A stream is a sequence of asynchronous events representing multiple values that will arrive in the future. The Stream class deals with sequences of events instead of single events. A stream can have one or more listeners, and all listeners will receive the same value.

##Creating Streams in Dart
You can create a stream using the Stream class. Here’s a function that returns a Stream<String>:

```dart

Stream<String> getUserName() async* {
  await Future.delayed(Duration(seconds: 1));
  yield 'Mark';
  await Future.delayed(Duration(seconds: 1));
  yield 'John';
  await Future.delayed(Duration(seconds: 1));
  yield 'Smith';
}
```
Alternatively, you can create a stream using the Stream.fromIterable() method:

```dart

Stream<String> getUserName() {
  return Stream.fromIterable(['Mark', 'John', 'Smith']);
}
```
##Using Streams in Dart

You can use a stream in Dart by using the await for loop:

```dart

void main() async {
  await for (String name in getUserName()) {
    print(name);
  }
}
```


##Types of Streams
Single Subscription Stream: Default stream type, allows only one listener.
Broadcast Stream: Allows multiple listeners.
Example: Single Subscription Stream
```dart

import 'dart:async';

void main() {
  var controller = StreamController();
  controller.stream.listen((event) {
    print(event);
  });
  controller.add('Hello');
  controller.add(42);
  controller.addError('Error!');
  controller.close();
}
```
Example: Broadcast Stream
```dart

StreamController<int> controller = StreamController<int>.broadcast();

controller.stream.listen((value) {
  print("Listener 1: $value");
});

controller.stream.listen((value) {
  print("Listener 2: $value");
});

controller.add(10);
controller.add(20);
controller.close();

```
Stream Methods
listen(): Subscribes to the stream.
onError(): Handles errors.
cancelOnError: Stops listening after an error if true.
onDone(): Executes code when the stream is finished.
Keywords in Streams
async*: Used with streams, works like async in futures.
yield: Emits values from a generator.
yield*: Calls its iterable or stream function recursively.
Example: Using async*
```dart

Stream<int> countForOneMinute() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(const Duration(seconds: 1));
    yield i;
  }
}

void main() async {
  await for (int i in countForOneMinute()) {
    print(i);
  }
}
```
Example: Using yield*
```dart

Stream<int> str(int n) async* {
  if (n > 0) {
    await Future.delayed(Duration(seconds: 2));
    yield n;
    yield* str(n - 2);
  }
}

void main() {
  str(10).forEach(print);

}
```

Conclusion
Streams in Dart are powerful tools for handling asynchronous data flows. They allow us to process data as it becomes available, rather than waiting for it to be fully loaded before processing. Streams are used in scenarios where data is continuously updated or where we want to handle events as they occur.

By mastering asynchronous programming and streams, you can build responsive and efficient applications. Keep experimenting, and feel free to share your progress and questions!

#Flutter #Dart #FlutterDevelopment #MobileAppDevelopment #AppDevelopment #Programming #Coding #LearnToCode #TechLearning #DevCommunity #SoftwareDevelopment #30DaysOfCode #DeveloperJourney #CodeNewbie #TechEducation #ProgrammingTutorial #FlutterTutorial #DartProgramming #BuildApps #CodeLearning
