# Day 15 - Advanced Flutter UI: SingleChildScrollView, ListView, GridView, Assets, and Stateful Widgets

## Overview

Today, we will explore more advanced Flutter widgets and concepts such as `SingleChildScrollView`, `ListView`, `GridView`, handling assets like images and fonts, and creating stateful widgets. By the end of the day, you should be able to create complex UI layouts and manage state effectively.


![day 15](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/557c3067-7341-439c-8fbd-ef2b90e252dd)



## SingleChildScrollView

The `SingleChildScrollView` widget is used when you have a single child that you want to make scrollable.

```dart
SingleChildScrollView(
  child: Column(
    children: <Widget>[
      Text('Item 1'),
      Text('Item 2'),
      Text('Item 3'),
      // Add more items here
    ],
  ),
)
```
ListView
The ListView widget is perfect for displaying a scrollable list of items. It can be used with both static and dynamic content.

Static ListView
```dart

ListView(
  children: <Widget>[
    ListTile(
      title: Text('Item 1'),
    ),
    ListTile(
      title: Text('Item 2'),
    ),
    ListTile(
      title: Text('Item 3'),
    ),
  ],
)
```
Dynamic ListView
```dart

ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
)
```
GridView
The GridView widget is used to display items in a grid layout.

Static GridView
```dart

GridView.count(
  crossAxisCount: 2,
  children: <Widget>[
    Container(color: Colors.red, child: Center(child: Text('Item 1'))),
    Container(color: Colors.green, child: Center(child: Text('Item 2'))),
    Container(color: Colors.blue, child: Center(child: Text('Item 3'))),
  ],
)
```
Dynamic GridView
```dart

GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 2),
  itemCount: 10,
  itemBuilder: (context, index) {
    return Container(
      color: Colors.blueAccent,
      child: Center(child: Text('Item $index')),
    );
  },
)
```

This image shows everything we have implemented with these concepts:

![Screenshot 2024-06-25 at 2 08 32 PM](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/21bd3295-2754-48de-a991-8c081f464988)


complete code of the image:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Scrolling and Grid',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: ScrollingAndGrid(),
    );
  }
}

class ScrollingAndGrid extends StatefulWidget {
  @override
  _ScrollingAndGridState createState() => _ScrollingAndGridState();
}

class _ScrollingAndGridState extends State<ScrollingAndGrid> {
  List<String> _items = [];

  @override
  void initState() {
    super.initState();
    for (int i = 0; i < 50; i++) {
      _items.add('Item $i');
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Scrolling and Grid'),
      ),
      body: Column(
        children: <Widget>[
          SingleChildScrollView(
            child: Column(
              children: <Widget>[
                Text('Item 1'),
                Text('Item 2'),
                Text('Item 3'),
                // Add more items here
              ],
            ),
          ),
          Expanded(
            child: ListView.builder(
              itemCount: _items.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(_items[index]),
                );
              },
            ),
          ),
          Expanded(
            child: GridView.count(
              crossAxisCount: 2,
              children: <Widget>[
                Container(color: Colors.red, child: Center(child: Text('Item 1'))),
                Container(color: Colors.green, child: Center(child: Text('Item 2'))),
                Container(color: Colors.blue, child: Center(child: Text('Item 3'))),
              ],
            ),
          ),
          Expanded(
            child: GridView.builder(
              gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 2),
              itemCount: 10,
              itemBuilder: (context, index) {
                return Container(
                  color: Colors.blueAccent,
                  child: Center(child: Text('Item $index')),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
```

Assets: Images and Fonts
Adding Images
Add your image to the assets/images directory.
Update pubspec.yaml:
```yaml

flutter:
  assets:
    - assets/images/my_image.png
```
Using Images
```dart

Image.asset('assets/images/my_image.png')
```
Adding Custom Fonts
Add your font files to the assets/fonts directory.
Update pubspec.yaml:
```yaml

flutter:
  fonts:
    - family: CustomFont
      fonts:
        - asset: assets/fonts/CustomFont-Regular.ttf
```
Using Custom Fonts
```dart

Text(
  'Custom Font Text',
  style: TextStyle(fontFamily: 'CustomFont'),
)
```
Stateful Widgets
Stateful widgets maintain state that might change during the lifetime of the widget.

Example of a Stateful Widget
```dart

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Tap to Show Message',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: TapToShowMessage(),
    );
  }
}

class TapToShowMessage extends StatefulWidget {
  @override
  _TapToShowMessageState createState() => _TapToShowMessageState();
}

class _TapToShowMessageState extends State<TapToShowMessage> {
  List<String> _items = [];
  String _message = '';

  @override
  void initState() {
    super.initState();
    for (int i = 0; i < 50; i++) {
      _items.add('Item $i');
    }
  }

  void _showMessage(String item) {
    setState(() {
      _message = 'You tapped on $item';
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Tap to Show Message'),
      ),
      body: Column(
        children: <Widget>[
          Text(_message),
          Expanded(
            child: ListView.builder(
              itemCount: _items.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(_items[index]),
                  onTap: () {
                    _showMessage(_items[index]);
                  },
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
```

![Screenshot 2024-06-25 at 2 14 50 PM](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/115eca73-d51a-48bb-a9bd-b97b3557faf4)



Project - ToDo App


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
      title: 'To-Do List',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: ToDoList(),
    );
  }
}

class ToDoList extends StatefulWidget {
  @override
  _ToDoListState createState() => _ToDoListState();
}

class _ToDoListState extends State<ToDoList> {
  List<String> _tasks = [];
  List<bool> _taskStatus = [];

  final _taskController = TextEditingController();

  void _addTask() {
    if (_taskController.text.isNotEmpty) {
      setState(() {
        _tasks.add(_taskController.text);
        _taskStatus.add(false);
        _taskController.clear();
      });
    }
  }

  void _toggleTaskStatus(int index) {
    setState(() {
      _taskStatus[index] = !_taskStatus[index];
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('To-Do List'),
      ),
      body: Column(
        children: <Widget>[
          TextField(
            controller: _taskController,
            decoration: InputDecoration(
              labelText: 'Enter a task',
              suffixIcon: IconButton(
                icon: Icon(Icons.add),
                onPressed: _addTask,
              ),
            ),
          ),
          Expanded(
            child: ListView.builder(
              itemCount: _tasks.length,
              itemBuilder: (context, index) {
                return ListTile(
                  title: Text(_tasks[index]),
                  trailing: Checkbox(
                    value: _taskStatus[index],
                    onChanged: (value) {
                      _toggleTaskStatus(index);
                    },
                  ),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
```



![Screenshot 2024-06-25 at 2 17 13 PM](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/e5743a3d-2616-4083-a202-0c9267ce196f)


By the end of this project, you should have a solid understanding of how to create more advanced UI layouts using Flutter's scrolling and grid widgets, handle assets like images and fonts, and implement stateful widgets. Happy coding!

#Flutter #Dart #Programming #SoftwareDevelopment #MobileDevelopment #TechJourney #Learning #Coding #FlutterDev #ImageGalleryApp


