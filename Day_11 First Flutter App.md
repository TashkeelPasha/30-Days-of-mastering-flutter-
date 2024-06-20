# Day 11 - Introduction to Flutter SDK and Creating Your First App

## What is Flutter?

Flutter is an open-source UI software development kit (SDK) created by Google. It is used to develop cross-platform applications for Android, iOS, Linux, macOS, Windows, Google Fuchsia, and the web from a single codebase. Flutter uses the Dart programming language, which we've been learning in the past 10 days.

## Why Flutter?

- **Cross-Platform Development:** Write once, run anywhere.
- **Fast Development:** Hot reload allows for quick iterations.
- **Expressive and Flexible UI:** Build beautiful UIs with customizable widgets.
- **High Performance:** Compiles to native ARM code for both iOS and Android.

## Setting Up Flutter SDK

### Step 1: Download Flutter SDK

Visit the [Flutter SDK](https://flutter.dev/docs/get-started/install) download page and follow the instructions for your operating system.

### Step 2: Set Up Environment Variables

After downloading and extracting the Flutter SDK, you need to add Flutter to your system's PATH.

- **Windows:**
  ```shell
  set PATH=%PATH%;C:\path\to\flutter\bin

macOS and Linux:
```shell

export PATH="$PATH:`pwd`/flutter/bin"
```

Step 3: Verify Installation
Run the following command to verify that Flutter is correctly installed:
```shell
flutter doctor
```
This command checks your environment and displays a report of the status of your Flutter installation. Make sure there are no issues reported.

Creating Your First Flutter App

Step 1: Create a New Flutter Project

Use the flutter create command to create a new Flutter project:

```shell

flutter create my_first_app
```
Navigate into your project directory:

```shell

cd my_first_app
```
Step 2: Explore the Project Structure

lib/main.dart: The main entry point for your Flutter app.

pubspec.yaml: The configuration file for your Flutter project, including dependencies and assets.


Step 3: Run the App

Use the following command to run your app:

```shell

flutter run
```
You should see a default Flutter app running on your device or emulator.

Step 4: Modify the App
All of our development code goes into lib folder,
Open lib/main.dart in your favorite code editor and replace the default code with the following to create a simple app that displays "Hello, Flutter!":

```dart
//copy and paste this code into main.dart file
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
          title: Text('My First Flutter App'),
        ),
        body: Center(
          child: Text('Hello, Flutter!'),
        ),
      ),
    );
  }
}
```
Save the file and use the hot reload feature (r in the terminal) to see your changes immediately.

Conclusion
Congratulations! You've successfully set up Flutter and created your first app. This is just the beginning of your Flutter journey. In the upcoming days, we'll dive deeper into building more complex and interactive applications with Flutter.

Stay tuned for more exciting Flutter tutorials!

#Flutter #Dart #MobileDevelopment #CrossPlatform #SoftwareDevelopment #Programming #TechJourney #Learning #Coding
