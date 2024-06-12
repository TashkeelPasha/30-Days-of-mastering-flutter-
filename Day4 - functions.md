# 🚀 Day 4: Mastering Functions in Dart 🚀

Welcome to Day 4 of my #30DaysOfFlutter journey! Today, we're diving into the world of functions in Dart. Functions are essential building blocks in programming, allowing us to write reusable code for specific tasks. By the end of today, you'll understand different types of functions, how to define and call them, and the concept of optional parameters.



## 📝 Key Concepts

### Types of Functions
Dart supports various types of functions based on parameters and return types. Here are some examples:

#### 1. Function with No Parameters and No Return Type
```dart
void main() {
  printName();
}

void printName() {
  print("My name is John Doe.");
}
```
2. Function with Parameters and No Return Type
```dart

void main() {
  printName("Pasha");
}

void printName(String name) {
  print("Welcome, ${name}.");
}
```

3. Function with No Parameters and a Return Type
```dart

void main() {
  String name = primeMinisterName();
  print("The Name from function is $name.");
}

String primeMinisterName() {
  return "Pasha";
}

```
4. Function with Parameters and a Return Type
```dart
void main() {
  int total = add(10, 20);
  print("The sum is $total.");
}

int add(int a, int b) {
  return a + b;
}
```

Optional Parameters
Dart allows optional parameters, which can be useful when certain arguments are not always needed. Optional parameters can be positional or named, and can also have default values.

1. Optional Positional Parameters
```dart

void greet([String name = 'Guest']) {
  print('Hello, $name!');
}

```
2. Optional Named Parameters
```dart

void greet({String? name}) {
  print('Hello, ${name ?? 'Guest'}!');
}
```
3. Default Parameter Values
```dart

void greet({String name = 'Guest'}) {
  print('Hello, $name!');

}
```
🎯 Project - Enhanced Calculator
For today’s project, we’ll enhance our simple calculator to include functions for addition, subtraction, multiplication, and division, utilizing both parameters and return types.

```dart

void main() {
  double num1 = 10.5;
  double num2 = 5.5;

  print("Addition: ${add(num1, num2)}");
  print("Subtraction: ${subtract(num1, num2)}");
  print("Multiplication: ${multiply(num1, num2)}");
  print("Division: ${divide(num1, num2)}");
}

double add(double a, double b) => a + b;
double subtract(double a, double b) => a - b;
double multiply(double a, double b) => a * b;
double divide(double a, double b) => a / b;
```

🌟 Tips for Today
Practice defining and calling different types of functions in Dart.
Experiment with optional parameters to make your functions more flexible.
Enhance your calculator project with additional functionalities and improve code reusability.
Share your progress, tips, and questions in the comments. Let's continue to learn and grow together! 💪
Tags

#Flutter #Dart #FlutterDevelopment #MobileAppDevelopment #AppDevelopment #Programming #Coding #LearnToCode #TechLearning #DevCommunity #SoftwareDevelopment #30DaysOfCode #DeveloperJourney #CodeNewbie #TechEducation #ProgrammingTutorial #FlutterTutorial #DartProgramming #BuildApps #CodeLearning
