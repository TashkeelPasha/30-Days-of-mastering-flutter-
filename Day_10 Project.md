# Day 10 - Comprehensive Project: Library Management System

## Project Overview
Today, we'll build a comprehensive Library Management System that integrates various Dart programming concepts learned over the past 9 days. This project will demonstrate practical applications of data types, variables, conditionals, functions, async programming, streams, error handling, OOP, advanced OOP, dependency injection, and networking.

## Project Features
- **Data Types, Variables, and Conditionals:** Handle book data and manage library status.
- **Functions:** Modularize and reuse code for library operations.
- **Async Programming, Streams, and Error Handling:** Manage asynchronous operations and real-time updates.
- **Object-Oriented Programming (OOP):** Implement classes and OOP principles.
- **Advanced OOP:** Use mixins and factory constructors for advanced OOP concepts.
- **Dependency Injection:** Manage services for the library system.
- **Networking:** Fetch and update book data from an external API.

## Code Implementation
```dart
import 'dart:convert';
import 'dart:async';
import 'package:http/http.dart' as http;

// Basic Data Types, Variables, and Conditionals
bool isOpen = true;
int availableBooks = 10;

void checkLibraryStatus() {
  if (isOpen && availableBooks > 0) {
    print('The library is open and has books available.');
  } else {
    print('The library is closed or out of books.');
  }
}

// Functions
void addBook(String title) {
  print('Book "$title" added to the library.');
}

// Async Programming, Streams, and Error Handling
Future<void> fetchBookData() async {
  try {
    await Future.delayed(Duration(seconds: 2));
    print('Book data fetched successfully.');
  } catch (e) {
    print('Error fetching book data: $e');
  }
}

// Object-Oriented Programming (OOP)
class Book {
  int id;
  String title;
  String author;

  Book({required this.id, required this.title, required this.author});

  void displayInfo() {
    print('Book ID: $id, Title: $title, Author: $author');
  }
}

// Advanced OOP with Mixins
mixin Borrowable {
  bool isBorrowed = false;

  void borrow() {
    isBorrowed = true;
    print('Item borrowed.');
  }

  void returnItem() {
    isBorrowed = false;
    print('Item returned.');
  }
}

class DVD with Borrowable {
  String title;

  DVD(this.title);
}

// Dependency Injection
class LibraryService {
  void performOperation() {
    print('Performing library operation.');
  }
}

class LibraryManager {
  final LibraryService libraryService;

  LibraryManager(this.libraryService);

  void manageLibrary() {
    libraryService.performOperation();
  }
}

// Networking to Fetch Book Data
class NetworkBook {
  int id;
  String title;
  String author;

  NetworkBook({required this.id, required this.title, required this.author});

  factory NetworkBook.fromJson(Map<String, dynamic> json) {
    return NetworkBook(
      id: json['id'],
      title: json['title'],
      author: json['author'],
    );
  }
}

Future<void> fetchBooks() async {
  final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/posts'));

  if (response.statusCode == 200) {
    List<dynamic> jsonResponse = jsonDecode(response.body);
    List<NetworkBook> books = jsonResponse.map((book) => NetworkBook.fromJson(book)).toList();
    books.forEach((book) => print('Book: ${book.title}, Author: ${book.author}'));
  } else {
    throw Exception('Failed to load books');
  }
}

// Main Function
void main() {
  // Check Library Status
  checkLibraryStatus();

  // Add a Book
  addBook('Dart Programming');

  // Fetch Book Data
  fetchBookData();

  // OOP: Create a Book and Display Info
  Book book = Book(id: 1, title: 'Dart Programming', author: 'Author A');
  book.displayInfo();

  // Advanced OOP: Use Mixin
  DVD dvd = DVD('Inception');
  dvd.borrow();
  dvd.returnItem();

  // Dependency Injection
  LibraryService libraryService = LibraryService();
  LibraryManager libraryManager = LibraryManager(libraryService);
  libraryManager.manageLibrary();

  // Fetch Books from Network
  fetchBooks();
}
```
Conclusion
By understanding and integrating various Dart programming concepts, you can build a comprehensive and functional Library Management System. This project consolidates your learning and provides a practical example of how to apply these concepts in a real-world application.

#Dart #Flutter #Networking #Programming #SoftwareDevelopment #Coding #MobileDevelopment #FlutterDev #DartLang



Basic data types, variables, and conditionals to manage library status.
Functions for modular code.
Async programming, streams, and error handling for fetching book data.
OOP principles with classes, inheritance, and methods.
Advanced OOP with mixins.
Dependency injection to manage services.
Networking to fetch book data from an external API.
