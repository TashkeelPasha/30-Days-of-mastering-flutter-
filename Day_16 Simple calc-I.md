# Day 16 - Flutter Calculator App: UI Design

## Overview
Today, we will create the user interface (UI) for a simple calculator app using Flutter. We'll design a clean and intuitive layout, ensuring it is visually appealing and user-friendly. In the next post, we will handle the logic behind the calculator.

![day16](https://github.com/user-attachments/assets/8acef6d0-8b60-47ab-a151-839180ee64b5)


## Code Explanation
In this section, we will walk through the code to create the UI of the calculator.

## main.dart
This file is the entry point of our Flutter application. It sets up the basic structure and directs to the home screen.
```dart

import 'package:calculator/Home.dart';
import 'package:flutter/material.dart';

void main(){
  runApp(Calculator());
}

class Calculator extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Home(),
    );
  }
}


```


## home.dart
This file contains the main UI components of the calculator. It consists of the screen display and the buttons.

```dart
// ignore_for_file: file_names, non_constant_identifier_names

import 'package:flutter/material.dart';

class Home extends StatefulWidget {
  const Home({super.key});

  @override
  State<Home> createState() => _HomeState();
}

class _HomeState extends State<Home> {
  String userInput = "";
  String result = "0";
  List<String> buttonList = [
    'C', '(', ')', '/', '7', '8', '9', '*', 
    '4', '5', '6', '-', '1', '2', '3', '+', 
    '.', '0', 'DEL', '='
  ];

  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Scaffold(
        body: Column(
          children: [
            Container(
              alignment: Alignment.bottomRight,
              height: MediaQuery.of(context).size.height / 2.9,
              child: resultWidget(),
            ),
            Expanded(child: buttonWidget()),
          ],
        ),
      ),
    );
  }

  Widget resultWidget() {
    return Container(
      padding: const EdgeInsets.all(10),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.end,
        crossAxisAlignment: CrossAxisAlignment.end,
        children: [
          Text(
            userInput,
            style: const TextStyle(fontSize: 30, fontWeight: FontWeight.bold),
          ),
          const SizedBox(height: 25),
          Text(
            result,
            style: const TextStyle(fontSize: 50, fontWeight: FontWeight.bold),
          ),
        ],
      ),
    );
  }

  Widget buttonWidget() {
    return Container(
      padding: const EdgeInsets.all(10),
      child: GridView.builder(
        gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
          crossAxisCount: 4,
          crossAxisSpacing: 10,
          mainAxisSpacing: 10,
        ),
        itemCount: buttonList.length,
        itemBuilder: (context, index) {
          return button(buttonList[index]);
        },
      ),
    );
  }

  Widget button(String text) {
    return InkWell(
      onTap: () {
        setState(() {
          handlePress(text);
        });
      },
      child: Container(
        decoration: BoxDecoration(
          color: getBGcolor(text),
          borderRadius: BorderRadius.circular(10),
          boxShadow: [
            BoxShadow(
              color: Colors.grey.withOpacity(0.1),
              blurRadius: 1,
              spreadRadius: 1,
            ),
          ],
        ),
        child: Center(
          child: Text(
            text,
            style: TextStyle(
              color: getColor(text),
              fontSize: 30,
              fontWeight: FontWeight.bold,
            ),
          ),
        ),
      ),
    );
  }

  Color getColor(String text) {
    if (text == "/" || text == "*" || text == "+" || text == "-" || text == "C" || text == "(" || text == ")") {
      return const Color.fromARGB(255, 163, 39, 30);
    }
    if (text == "=" || text == "DEL") {
      return Colors.white;
    }
    return Colors.indigo;
  }

  Color getBGcolor(String text) {
    if (text == "DEL") {
      return Colors.red;
    }
    if (text == "=") {
      return const Color.fromARGB(255, 122, 219, 125);
    }
    return Colors.white;
  }

  void handlePress(String text) {
    setState(() {
      userInput += text;
    });
  }
}

```

## Explanation
## main.dart:

The main() function initializes the app by calling runApp(Calculator()).
The Calculator class extends StatelessWidget and returns a MaterialApp widget with Home as the home screen.

## home.dart:

The Home class extends StatefulWidget to manage the state of the user input and the result.
The buttonList contains all the button labels for the calculator.
The build() method returns a Scaffold widget with a column layout, containing the display and the buttons.
The resultWidget() method returns a container with the user input and the result.
The buttonWidget() method creates a grid view of buttons using GridView.builder.
The button() method returns an InkWell widget to handle button taps and style the buttons.
The getColor() and getBGcolor() methods determine the text and background colors of the buttons based on their labels.
This concludes the UI part of our calculator app. Stay tuned for the next post where we will implement the logic behind the calculator.

#Flutter #Dart #Programming #SoftwareDevelopment #MobileDevelopment #TechJourney #Learning #Coding #FlutterDev #CalculatorApp
