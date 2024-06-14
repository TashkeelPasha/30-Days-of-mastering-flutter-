# Day 6: Object-Oriented Programming (OOP) in Dart

## Introduction to Classes in Dart

In Dart, a class is a blueprint for creating objects. It defines a data structure that contains fields (variables) and methods (functions) to operate on the data. Classes help organize and structure your code in a modular and reusable way.

![day 6](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/d14a5833-a14e-42ec-a7cb-cc100f2afce0)




### Syntax for Declaring a Class

Here’s a basic structure of a Dart class:

```dart
class ClassName {
  // Fields
  dataType fieldName;

  // Constructor
  ClassName(this.fieldName);

  // Methods
  void methodName() {
    // Method code
  }
}
```

Example: Defining a Simple Class
```dart

class Person {
  String name;
  int age;

  // Constructor
  Person(this.name, this.age);

  // Method
  void introduce() {
    print('Hello, my name is $name and I am $age years old.');
  }
}
```
Understanding Objects
Objects are instances of classes. When you create an object, you are creating an instance of a class with actual values. This instance can then be used to access the fields and methods defined in the class.

Creating and Using Objects
```dart

void main() {
  // Creating an object of the Person class
  Person person = Person('Alice', 25);
  
  // Accessing a method
  person.introduce(); // prints "Hello, my name is Alice and I am 25 years old."
}
```
Constructors in Dart

Constructors are special methods that are called when an object is instantiated. They are used to initialize the object's properties.

Types of Constructors

Default Constructor: Automatically provided if no constructors are defined.

```dart

class Person {
  String name;
  int age;
  
  // Default constructor
  Person();
}
```
Parameterized Constructor: Allows you to pass parameters during object creation.
```dart

class Person {
  String name;
  int age;

  // Parameterized constructor
  Person(this.name, this.age);
}
```
Named Constructor: Used to provide multiple constructors with different names.
```dart

class Person {
  String name;
  int age;

  // Named constructor
  Person.withName(this.name);
  Person.withAge(this.age);
}
```
Factory Constructor: Used to control the instance creation.
```dart

class Singleton {
  static final Singleton _instance = Singleton._internal();

  // Private constructor
  Singleton._internal();

  // Factory constructor
  factory Singleton() {
    return _instance;
  }
}
```
Example Project 1: Library Management System
Let’s create a simple program to manage books in a library. We’ll define classes for Book, Library, and implement various constructors.

Defining Classes
```dart

class Book {
  String title;
  String author;
  int publicationYear;

  // Parameterized constructor
  Book(this.title, this.author, this.publicationYear);

  // Named constructor
  Book.withoutYear(this.title, this.author);

  // Method to display book info
  void displayInfo() {
    print('Title: $title, Author: $author, Year: $publicationYear');
  }
}

class Library {
  String name;
  List<Book> books = [];

  // Default constructor
  Library(this.name);

  // Method to add a book
  void addBook(Book book) {
    books.add(book);
    print('Book added: ${book.title}');
  }

  // Method to display all books
  void displayBooks() {
    print('Library: $name');
    for (Book book in books) {
      book.displayInfo();
    }
  }
}

void main() {
  // Creating books
  Book book1 = Book('1984', 'George Orwell', 1949);
  Book book2 = Book.withoutYear('To Kill a Mockingbird', 'Harper Lee');

  // Creating a library
  Library library = Library('City Library');

  // Adding books to the library
  library.addBook(book1);
  library.addBook(book2);

  // Displaying all books in the library
  library.displayBooks();
}
```
Output
```yaml

Book added: 1984
Book added: To Kill a Mockingbird
Library: City Library
Title: 1984, Author: George Orwell, Year: 1949
Title: To Kill a Mockingbird, Author: Harper Lee, Year: null
```
Example Project 2: Vehicle Management System
For this project, we will create a system to manage vehicles. We’ll define classes for Vehicle, Car, and Motorcycle, and demonstrate inheritance and method overriding.


```dart

class Vehicle {
  String make;
  String model;
  int year;

  // Parameterized constructor
  Vehicle(this.make, this.model, this.year);

  // Method to display vehicle info
  void displayInfo() {
    print('Make: $make, Model: $model, Year: $year');
  }
}

class Car extends Vehicle {
  int numberOfDoors;

  // Parameterized constructor
  Car(String make, String model, int year, this.numberOfDoors) : super(make, model, year);

  // Overriding method
  @override
  void displayInfo() {
    super.displayInfo();
    print('Number of Doors: $numberOfDoors');
  }
}

class Motorcycle extends Vehicle {
  bool hasSidecar;

  // Parameterized constructor
  Motorcycle(String make, String model, int year, this.hasSidecar) : super(make, model, year);

  // Overriding method
  @override
  void displayInfo() {
    super.displayInfo();
    print('Has Sidecar: $hasSidecar');
  }
}

void main() {
  // Creating a car
  Car car = Car('Toyota', 'Corolla', 2020, 4);

  // Creating a motorcycle
  Motorcycle motorcycle = Motorcycle('Harley-Davidson', 'Street 750', 2019, false);

  // Displaying vehicle info
  car.displayInfo();
  motorcycle.displayInfo();
}
```
Output
```yaml
Copy code
Make: Toyota, Model: Corolla, Year: 2020
Number of Doors: 4
Make: Harley-Davidson, Model: Street 750, Year: 2019
Has Sidecar: false
```
Example Program 3: Article Data Source
This example demonstrates how to create an abstract class and implement it with concrete classes.


```dart

abstract class ArticleDataSource {
  void getArticle(String id);
  void deleteArticle(String id);
}

class ArticleLocalDataSource implements ArticleDataSource {
  // Factory constructor
  factory ArticleLocalDataSource() => ArticleLocalDataSource._internal();

  ArticleLocalDataSource._internal();

  @override
  void getArticle(String id) {
    print('Get Local $id');
  }

  @override
  void deleteArticle(String id) {
    print('Delete Local $id');
  }
}

class ArticleAPIDataSource implements ArticleDataSource {
  // Factory constructor
  factory ArticleAPIDataSource() => ArticleAPIDataSource._internal();

  ArticleAPIDataSource._internal();

  @override
  void getArticle(String id) {
    print('Get API $id');
  }

  @override
  void deleteArticle(String id) {
    print('Delete API $id');
  }
}

void main() {
  // Using ArticleLocalDataSource
  ArticleLocalDataSource localDataSource = ArticleLocalDataSource();
  localDataSource.getArticle('dart-today-and-tomorrow');
  localDataSource.deleteArticle('dart-today-and-tomorrow');

  // Using ArticleAPIDataSource
  ArticleAPIDataSource apiDataSource = ArticleAPIDataSource();
  apiDataSource.getArticle('dart-today-and-tomorrow');
  apiDataSource.deleteArticle('dart-today-and-tomorrow');
}

```

```yaml

Get Local dart-today-and-tomorrow
Delete Local dart-today-and-tomorrow
Get API dart-today-and-tomorrow
Delete API dart-today-and-tomorrow
```


Conclusion
By the end of this day, you should have a good understanding of how to create classes and objects in Dart, and how to use constructors to initialize them. You should also be familiar with the different types of constructors and how to implement them in your programs.

Feel free to experiment with the examples provided and try creating your own classes and objects to solidify your understanding of Object-Oriented Programming in Dart.



#DartLang #Programming #OOP #ObjectOrientedProgramming #DartProgramming #SoftwareDevelopment #Coding #TechLearning #LearningToCode #Developer #TechEducation #DartTutorial #CodeNewbie #ProgrammingTips #TechCommunity #SoftwareEngineering
