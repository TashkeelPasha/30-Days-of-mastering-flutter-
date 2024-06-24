# Day 14 - Building a Basic UI with Flutter Widgets

## Overview

Today, we will explore some fundamental Flutter widgets such as `Container`, `Text`, `Row`, and `Column`. After learning about these widgets, we will build a simple user profile UI using them.

By the end of this day, you should have a basic understanding of how to use these widgets to create a custom layout.

## Learning the Basics

### 1. **Container**

The `Container` widget is a versatile widget that can be used for creating rectangles, boxes, and adding padding, margins, borders, and more.

```dart
Container(
  width: 100,
  height: 100,
  padding: EdgeInsets.all(8.0),
  margin: EdgeInsets.all(8.0),
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(10),
  ),
  child: Text('Hello, Container!'),
)
```
2. Text
The Text widget is used to display text in your app.

```dart

Text(
  'Hello, Flutter!',
  style: TextStyle(fontSize: 24, color: Colors.black),
)
```
3. Row and Column
Row and Column are two basic layout widgets that arrange their children in a horizontal or vertical line, respectively.

```dart

Column(
  children: <Widget>[
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)

Row(
  children: <Widget>[
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)
```

Project - Simple User Profile UI
Now, let's use these widgets to build a simple user profile UI.

Project Features
Display a user's profile picture.
Show the user's name and bio.
Arrange the profile information using Container, Text, Row, and Column.
Example Code
Create a new Flutter project and replace the code in lib/main.dart with the following:

```dart

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: UserProfile(),
    );
  }
}

class UserProfile extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('User Profile'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Center(
              child: ProfilePicture(),
            ),
            SizedBox(height: 16),
            Center(
              child: UserName(),
            ),
            SizedBox(height: 8),
            Center(
              child: UserProfession(),
            ),
            SizedBox(height: 16),
            BioTitle(),
            SizedBox(height: 8),
            BioText(),
          ],
        ),
      ),
    );
  }
}

class ProfilePicture extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return CircleAvatar(
      radius: 50,
      backgroundImage: NetworkImage('https://media.licdn.com/dms/image/D4D03AQHE3uhkzVoEcw/profile-displayphoto-shrink_200_200/0/1714672162562?e=1724889600&v=beta&t=5JxssO-1n5OE3nMSKNKIQyl0oKQSpQWNaCgcAhxZeBk'),
    );
  }
}

class UserName extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text(
      'M Tashkeel Pasha',
      style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
    );
  }
}

class UserProfession extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text(
      'Software Developer',
      style: TextStyle(fontSize: 18, color: Colors.grey),
    );
  }
}

class BioTitle extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Text(
      'Bio:',
      style: TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
    ),
    );
  }
}

class BioText extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Text(
        'Studying Computer Science from FAST-NUCES Karachi & currently working on Flutter Application Development.',
        style: TextStyle(fontSize: 16),
      ),
    );
  }
}

```
To check the code, save the changes in lib/main.dart.
![Screenshot 2024-06-24 at 3 18 55 PM](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/40527483-fe3a-42c9-b78f-0a203195aa91)

Visual Examples
User Profile UI Example:



By the end of this project, you should have a solid understanding of how to create a simple yet functional user interface using fundamental Flutter widgets. Happy coding!

#Flutter #Dart #Programming #SoftwareDevelopment #MobileDevelopment #TechJourney #Learning #Coding #FlutterDev #UserProfileApp
