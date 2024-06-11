# Day 3: Understanding Variables, Data Types, and Basic Operators in Dart

Today on my #30DaysOfFlutter journey, we’re delving into the core concepts of Dart programming: variables, data types, operators, and expressions. These are the fundamental building blocks of any programming language. By the end of today, you’ll have a solid grasp of how to declare and initialize variables, use string interpolation, and work with operators and conditional expressions.

## Project - Simple Calculator

For today’s project, we’ll create a simple calculator that can perform basic arithmetic operations (addition, subtraction, multiplication, division) on two numbers.

## Key Concepts

### Variables and Data Types

Dart supports various data types such as `int`, `double`, `String`, and `bool`. Here’s how you can declare and initialize them:

```dart
void main() {
  // Declare and initialize variables of different data types
  int number1 = 10; // Integer variable
  double number2 = 5.5; // Double variable (floating-point number)
  String greeting = 'Hello, Dart!'; // String variable
  bool isLearning = true; // Boolean variable

  // Printing the variables using string interpolation
  print('Number1: $number1');
  print('Number2: $number2');
  print('Greeting: $greeting');
  print('Is Learning: $isLearning');
}
```
Explanation:

int, double, String, bool: These are Dart's built-in data types for integers, floating-point numbers, strings, and boolean values respectively.
String Interpolation: Using $variableName within a string to include variable values. For example, 'Number1: $number1' will print Number1: 10.
Arithmetic and Comparison Operators
Dart provides a variety of operators to perform arithmetic and comparison operations. Here’s an example:

```dart
void main() {
  // Declare and initialize integer variables
  int a = 10;
  int b = 5;
  
  // Arithmetic operations
  print('Addition: ${a + b}'); // 15
  print('Subtraction: ${a - b}'); // 5
  print('Multiplication: ${a * b}'); // 50
  print('Division: ${a / b}'); // 2.0
  print('Modulus: ${a % b}'); // 0
  
  // Comparison operations
  print('Is a greater than b? ${a > b}'); // true
  print('Is a less than b? ${a < b}'); // false
  print('Is a equal to b? ${a == b}'); // false
  print('Is a not equal to b? ${a != b}'); // true
}
```
Explanation:

Arithmetic Operators: +, -, *, /, % are used for basic arithmetic operations.
a + b (Addition) results in 15.
a - b (Subtraction) results in 5.
a * b (Multiplication) results in 50.
a / b (Division) results in 2.0.
a % b (Modulus) results in 0.
Comparison Operators: >, <, >=, <=, ==, != are used to compare values and return boolean results.
a > b checks if a is greater than b (true).
a < b checks if a is less than b (false).
a == b checks if a is equal to b (false).
a != b checks if a is not equal to b (true).
Conditional Statements
Conditional statements allow you to execute different code blocks based on specific conditions. Here’s an example using if/else:

```dart

void main() {
  // Declare and initialize an integer variable
  int age = 20;
  
  // Conditional statement
  if (age >= 18) {
    print('You are an adult.');
  } else {
    print('You are not yet an adult.');
  }
}
```
Explanation:

if/else Statement: Checks whether the age is 18 or above. If true, it prints "You are an adult.", otherwise, it prints "You are not yet an adult.".
More Examples
String Interpolation
String interpolation is a convenient way to build strings in Dart:

```dart
void main() {
  // Declare and initialize variables
  String name = 'Alice';
  int age = 25;
  
  // Printing variables using string interpolation
  print('My name is $name and I am $age years old.');
}
```
Explanation:

String Interpolation: Using $variableName within a string to include variable values. For example, 'My name is $name and I am $age years old.' will print My name is Alice and I am 25 years old..
Logical Operators
Logical operators (&&, ||, !) can be used to build more complex conditional expressions:

```dart

void main() {
  // Declare and initialize boolean variables
  bool isRaining = true;
  bool isCold = false;
  
  // Conditional statements with logical operators
  if (isRaining && isCold) {
    print('It is raining and cold.');
  } else if (isRaining || isCold) {
    print('It is either raining or cold.');
  } else {
    print('The weather is nice.');
  }
}
```
Explanation:

Logical Operators:
&& (AND): True if both operands are true.
|| (OR): True if at least one operand is true.
! (NOT): Inverts the boolean value.
The code checks if it is both raining and cold, either raining or cold, or neither, and prints a corresponding message.
Tips for Today
Review the basics of variables and data types in Dart. Check out the Dart documentation for more details.
Experiment with declaring and initializing variables of different data types.
Practice using string interpolation to print messages with variables.
Explore arithmetic and comparison operators to perform various calculations.
Write conditional statements using if/else and experiment with logical operators (&&, ||, !).
Feel free to share your progress, tips, and questions in the comments. Let’s continue to learn and grow together! 💪

