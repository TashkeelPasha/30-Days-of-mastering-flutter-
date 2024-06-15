# Day 7 - Advanced OOP in Dart

## Introduction

Today, we will explore advanced Object-Oriented Programming (OOP) concepts in Dart by building a Library Management System. This project will incorporate various OOP principles such as inheritance, encapsulation, polymorphism, abstract classes, interfaces, mixins, static members, and getters/setters.
By the end of this day, you should have a solid understanding of how to create classes and objects in Dart, use constructors, and apply various OOP concepts. These skills are fundamental for developing robust applications in Flutter.

![day 7](https://github.com/TashkeelPasha/30-Days-of-mastering-flutter-/assets/152206485/20c57466-ac50-460c-b4c1-921782757b8a)



---

## 1. Inheritance

Inheritance allows a class to inherit properties and methods from another class, promoting code reusability.

### Example
```dart
class Item {
  void display() {
    print('This is an item');
  }
}

class Book extends Item {
  String title;
  String author;

  Book(this.title, this.author);

  @override
  void display() {
    print('Title: $title, Author: $author');
  }
}
```
2. Encapsulation:
   Encapsulation hides the internal state of an object and requires all interaction to be performed through an object's methods.

Example
```dart

class Member {
  String _name; // Private property

  Member(this._name);

  String get name => _name; // Getter
  set name(String name) => _name = name; // Setter
}

void main() {
  Member member = Member('Alice');
  print(member.name); // Output: Alice
  member.name = 'Bob';
  print(member.name); // Output: Bob
}
```
3. Polymorphism:
   Polymorphism allows methods to perform different tasks based on the object they are acting upon.

Example
```dart

abstract class LibraryItem {
  void checkOut();
}

class Book extends LibraryItem {
  String title;

  Book(this.title);

  @override
  void checkOut() {
    print('Checking out book: $title');
  }
}

class DVD extends LibraryItem {
  String title;

  DVD(this.title);

  @override
  void checkOut() {
    print('Checking out DVD: $title');
  }
}

void main() {
  List<LibraryItem> items = [Book('1984'), DVD('Inception')];

  for (var item in items) {
    item.checkOut();
  }
}
```
4. Abstract Classes and Interfaces:
   Abstract classes cannot be instantiated and are often used to define a blueprint for other classes.

Example
```dart

abstract class DataSource {
  void fetchData();
}

class LocalDataSource implements DataSource {
  @override
  void fetchData() {
    print('Fetching data from local source');
  }
}

class RemoteDataSource implements DataSource {
  @override
  void fetchData() {
    print('Fetching data from remote source');
  }
}
```
5. Mixins:
   Mixins allow you to reuse a class's code in multiple class hierarchies.


Example
```dart

mixin Auditable {
  void audit() {
    print('Audit log created');
  }
}

class LibraryItem with Auditable {}

void main() {
  LibraryItem item = LibraryItem();
  item.audit(); // Output: Audit log created
}
```
6. Static Members:
   Static members belong to the class rather than to any specific object.

Example
```dart

class LibraryUtils {
  static int calculateLateFee(int daysLate) {
    return daysLate * 2;
  }
}

void main() {
  print(LibraryUtils.calculateLateFee(3)); // Output: 6
}
```
7. Getters and Setters:
   Getters and setters provide a way to access and modify the properties of an object.

Example
```dart

class Library {
  String _name;
  List<Book> _books;

  Library(this._name, this._books);

  String get name => _name;
  set name(String value) => _name = value;

  List<Book> get books => _books;
  set books(List<Book> value) => _books = value;
}
```
8. Complete Project: Library Management System
```dart
// Define a class for books
class Book extends LibraryItem {
  String title;
  String author;

  Book(this.title, this.author);

  @override
  void display() {
    print('Book Title: $title, Author: $author');
  }
}

// Define a class for DVDs
class DVD extends LibraryItem {
  String title;

  DVD(this.title);

  @override
  void display() {
    print('DVD Title: $title');
  }
}

// Define a class for magazines
class Magazine extends LibraryItem {
  String title;

  Magazine(this.title);

  @override
  void display() {
    print('Magazine Title: $title');
  }
}

// Define an abstract class for library items
abstract class LibraryItem {
  void display();
}

// Define a mixin for auditing
mixin Auditable {
  void audit() {
    print('Audit log created');
  }
}

// Define a class for library items with auditing
class AuditableLibraryItem with Auditable {}

// Define a class for library utilities
class LibraryUtils {
  static int calculateLateFee(int daysLate) {
    return daysLate * 2;
  }
}

// Define a class for library members
class Member {
  String _name; // Private property

  Member(this._name);

  String get name => _name; // Getter
  set name(String name) => _name = name; // Setter
}

// Define a class for the library
class Library {
  String _name;
  List<LibraryItem> _items;

  Library(this._name, this._items);

  // Named constructor
  Library.empty(this._name) : _items = [];

  // Getter for name
  String get name => _name;
  set name(String value) => _name = value;

  // Getter for items
  List<LibraryItem> get items => _items;
  set items(List<LibraryItem> value) => _items = value;

  // Method to add a library item
  void addItem(LibraryItem item) {
    _items.add(item);
  }

  // Method to show library items
  void showItems() {
    print('Library: $_name');
    for (var item in _items) {
      item.display();
    }
  }
}

// Define abstract class for data source
abstract class DataSource {
  void fetchData();
}

// Define local data source implementing data source
class LocalDataSource implements DataSource {
  @override
  void fetchData() {
    print('Fetching data from local source');
  }
}

// Define remote data source implementing data source
class RemoteDataSource implements DataSource {
  @override
  void fetchData() {
    print('Fetching data from remote source');
  }
}

// Main function to demonstrate the library management system
void main() {
  // Creating books
  Book book1 = Book('1984', 'George Orwell');
  Book book2 = Book('To Kill a Mockingbird', 'Harper Lee');

  // Creating DVDs
  DVD dvd1 = DVD('Inception');
  DVD dvd2 = DVD('The Matrix');

  // Creating magazines
  Magazine magazine1 = Magazine('Time');
  Magazine magazine2 = Magazine('National Geographic');

  // Creating a library
  Library library = Library('City Library', [book1, book2, dvd1, dvd2, magazine1, magazine2]);

  // Adding a new book
  Book book3 = Book('Brave New World', 'Aldous Huxley');
  library.addItem(book3);

  // Displaying library items
  library.showItems();

  // Using mixin
  AuditableLibraryItem item = AuditableLibraryItem();
  item.audit(); // Output: Audit log created

  // Static member usage
  print('Late fee for 3 days: \$${LibraryUtils.calculateLateFee(3)}'); // Output: 6

  // Inheritance and polymorphism
  List<LibraryItem> items = [book1, dvd1, magazine1];
  for (var item in items) {
    item.display();
  }

  // Data sources
  DataSource local = LocalDataSource();
  DataSource remote = RemoteDataSource();
  local.fetchData();  // Output: Fetching data from local source
  remote.fetchData(); // Output: Fetching data from remote source
}
```
Output

```yaml
Library: City Library
Book Title: 1984, Author: George Orwell
Book Title: To Kill a Mockingbird, Author: Harper Lee
DVD Title: Inception
DVD Title: The Matrix
Magazine Title: Time
Magazine Title: National Geographic
Book Title: Brave New World, Author: Aldous Huxley
Audit log created
Late fee for 3 days: $6
Book Title: 1984, Author: George Orwell
DVD Title: Inception
Magazine Title: Time
Fetching data from local source
Fetching data from remote source
```


#Dart #OOP #Flutter #Classes #Objects #Constructors #Inheritance #Polymorphism #Encapsulation #Abstraction #Mixins #LibraryManagementSystem


