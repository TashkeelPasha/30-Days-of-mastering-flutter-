# Day 17 - Flutter Calculator App: Logic Implementation

## Overview
Today, we will implement the logic to make our Flutter calculator app functional. We'll handle user inputs, perform calculations, and display the results.


![day17](https://github.com/user-attachments/assets/e9b1dcc7-4cc9-4b6d-ad47-8ab31b052362)


## Final result
https://github.com/user-attachments/assets/ba64d7a2-da31-41fc-bf7c-616ae939685e

<video src='[your URL here](https://github.com/user-attachments/assets/ba64d7a2-da31-41fc-bf7c-616ae939685e
)' width=180/>





## Code Explanation
In this section, we will walk through the code to implement the logic for the calculator.




## home.dart
This file contains the main logic components of the calculator. We will focus on handling user inputs, performing calculations, and updating the display.

```dart
// ignore_for_file: file_names, non_constant_identifier_names

import 'package:flutter/material.dart';
import 'package:math_expressions/math_expressions.dart';

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
              fontWeight: FontWeight.bold),
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
    if (text == "DEL") {
      setState(() {
        userInput = "";
        result = "0";
      });
      return;
    }

    if (text == "C") {
      setState(() {
        if (userInput.isNotEmpty) {
          userInput = userInput.substring(0, userInput.length - 1);
        }
      });
      return;
    }

    if (text == "=") {
      setState(() {
        result = calculate();
        userInput = result;
        if (userInput.endsWith(".0")) {
          userInput = userInput.replaceAll(".0", "");
        }
        if (result.endsWith(".0")) {
          result = result.replaceAll(".0", "");
        }
      });
      return;
    }

    setState(() {
      userInput += text;
    });
  }

  String calculate() {
    try {
      var exp = Parser().parse(userInput);
      var final_result = exp.evaluate(EvaluationType.REAL, ContextModel());
      return final_result.toString();
    } catch (e) {
      return "Error";
    }
  }
}
```
## Explanation
- handlePress(String text)
- DEL: Clears the entire input and resets the result to "0".
- C: Deletes the last character from the user input.
- =: Calculates the result using the calculate method and updates the display.
## calculate()
- download this pakage ```yaml math_expressions: ^2.6.0```
- Parses the user input and evaluates the expression.
- Returns the calculated result or "Error" if the input is invalid.

This concludes the logic implementation of our calculator app. Now, our app can handle user inputs and perform calculations effectively!

#Flutter #Dart #Programming #SoftwareDevelopment #MobileDevelopment #TechJourney #Learning #Coding #FlutterDev #CalculatorApp



