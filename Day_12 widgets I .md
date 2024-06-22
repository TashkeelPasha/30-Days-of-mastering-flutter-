# Day 12 - Understanding Stateless Widgets in Flutter

## What are Stateless Widgets?

In Flutter, a stateless widget is a widget that does not require mutable state. Stateless widgets are immutable, meaning their properties can't change—they are final. They are used when the UI you are building does not change dynamically.

## Example of Stateless Widget

A common use of a stateless widget is to display text or static content.

### Basic Example

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Stateless Widget Example'),
        ),
        body: Center(
          child: Text('Hello, Flutter!'),
        ),
      ),
    );
  }
}
```
Common Stateless Widgets
1. Text
The Text widget is used to display a string of text with a single style.

Example:
```dart

Text(
  'Hello, Flutter!',
  style: TextStyle(fontSize: 24, color: Colors.blue),
)
```
2. Container
The Container widget is used to contain a child widget with specific dimensions, padding, margins, and other properties.

Example:
```dart

Container(
  padding: EdgeInsets.all(16.0),
  margin: EdgeInsets.all(16.0),
  color: Colors.blue,
  child: Text('Hello, Container!'),
)
```
3. Column and Row
Column and Row widgets are used to arrange child widgets in a vertical and horizontal manner, respectively.

Column Example:
```dart

Column(
  children: <Widget>[
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)
```
Row Example:
```dart

Row(
  children: <Widget>[
    Text('Item 1'),
    Text('Item 2'),
    Text('Item 3'),
  ],
)
```
4. Image
The Image widget is used to display an image.

Example:
```dart

Image.network(
  'https://flutter.github.io/assets-for-api-docs/assets/widgets/owl.jpg',
)
```
5. Icon
The Icon widget is used to display an icon from the material design library or a custom icon.

Example:
```dart

Icon(
  Icons.favorite,
  color: Colors.pink,
  size: 24.0,
)
```
Conclusion
Stateless widgets are the foundation of any Flutter application. They are simple to use and perfect for displaying static content. As you continue to explore Flutter, you'll find that understanding stateless widgets is essential for building complex and dynamic user interfaces.

Stay tuned for more advanced topics in Flutter!

#Flutter #Dart #StatelessWidgets #MobileDevelopment #CrossPlatform #SoftwareDevelopment #Programming #TechJourney #Learning #Coding
