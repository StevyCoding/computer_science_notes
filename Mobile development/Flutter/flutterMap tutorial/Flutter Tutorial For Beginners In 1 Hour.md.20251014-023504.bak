# Flutter & Dart One-Hour Tutorial Summary

## What You'll Learn

This tutorial teaches you Flutter and Dart basics in one hour. You'll build an app with:

- Bottom navigation bar
- Multiple pages
- Various Flutter widgets
- Page navigation

## Getting Started

### Required Extensions (VS Code)

1. **Flutter Snippet Extension** - Type `statelessw` to auto-generate widget code
2. **Material Icon Theme** - Adds icons to files in the explorer (optional but helpful)

### Project Structure

- All Flutter code goes in `lib/main.dart`
- This is where your app starts

## Core Flutter Concepts

### 🧱 Everything is a Widget

- **Widget** = Anything that starts with a CAPITAL letter (like `Text`, `Container`)
- **Argument** = Anything that starts with a lowercase letter (like `color`, `title`)
- Flutter is "widget inside widget inside widget"

### 📱 Basic App Structure

```dart
void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: RootPage(),
    );
  }
}
```

## Essential Widgets Explained

### 1. MaterialApp

- The root of your app
- Provides themes and overall app settings
- Contains the `home` property for your main page

### 2. Scaffold

- The basic page structure
- Has three main parts:
    - **AppBar** (top section)
    - **Body** (middle section)
    - **BottomNavigationBar** (bottom section)

### 3. StatelessWidget vs StatefulWidget

- **StatelessWidget**: Never changes (like a photo)
- **StatefulWidget**: Can change and refresh (like a counter)
- Use `setState()` to refresh a StatefulWidget

## Building Your First App

### Creating an AppBar

```dart
AppBar(
  title: Text('Flutter App'),
  backgroundColor: Colors.green,
)
```

### Adding a Floating Action Button

```dart
floatingActionButton: FloatingActionButton(
  onPressed: () {
    print('Button pressed!');
  },
  child: Icon(Icons.add),
)
```

### Creating Bottom Navigation

```dart
bottomNavigationBar: NavigationBar(
  selectedIndex: currentPage,
  onDestinationSelected: (int index) {
    setState(() {
      currentPage = index;
    });
  },
  destinations: [
    NavigationDestination(
      icon: Icon(Icons.home),
      label: 'Home',
    ),
    NavigationDestination(
      icon: Icon(Icons.person),
      label: 'Profile',
    ),
  ],
)
```

## Page Navigation

### Moving to a New Page

```dart
Navigator.of(context).push(
  MaterialPageRoute(
    builder: (context) => NewPage(),
  ),
);
```

### Going Back

```dart
Navigator.of(context).pop();
```

## Common Widgets & Their Uses

### Layout Widgets

- **Column**: Arranges widgets vertically (top to bottom)
- **Row**: Arranges widgets horizontally (left to right)
- **Container**: A box that can hold other widgets
- **Center**: Centers its child widget

### Interactive Widgets

- **ElevatedButton**: A raised button
- **OutlinedButton**: A button with just an outline
- **TextButton**: A flat text button
- **Switch**: On/off toggle
- **Checkbox**: Checkable box

### Display Widgets

- **Text**: Shows text
- **Image.asset**: Shows images from your app
- **Image.network**: Shows images from the internet
- **Icon**: Shows icons
- **Divider**: A horizontal line

### Input & Lists

- **ListView.builder**: Creates scrollable lists
- **ListTile**: Individual items in a list
- **GestureDetector**: Detects taps and gestures

## Important Tips for Beginners

### 1. The `const` Keyword

- Add `const` before widgets that never change
- Flutter will suggest this to optimize your app
- Example: `const Text('Hello')`

### 2. Formatting Your Code

- Use `Ctrl + Shift + F` to auto-format
- Always add commas after widgets for better formatting
- Keep your code clean and readable

### 3. Variables and State

- Declare variables before the `build` method
- Use `setState()` to update the screen when variables change
- Variables inside `build` reset every time the screen refreshes

### 4. Making Lists Scrollable

- Wrap your Column in `SingleChildScrollView` to make it scrollable
- Use `ListView.builder` for long lists

## Example: Creating a Simple Counter

```dart
class CounterPage extends StatefulWidget {
  @override
  _CounterPageState createState() => _CounterPageState();
}

class _CounterPageState extends State<CounterPage> {
  int counter = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Counter')),
      body: Center(
        child: Text('Count: $counter'),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: () {
          setState(() {
            counter++;
          });
        },
        child: Icon(Icons.add),
      ),
    );
  }
}
```

## What to Learn Next

After mastering these basics, progress to:

1. **Advanced Widgets** - More complex UI components
2. **Packages** - Pre-built functionality you can add
3. **State Management** - Managing data across your app
4. **Local Storage** - Saving data on the device
5. **Firebase** - Online database and authentication
6. **HTTP Requests** - Getting data from the internet
7. **Publishing** - Getting your app in app stores

## Key Takeaways

- Flutter uses widgets for everything
- Start with basic widgets and combine them
- Use StatefulWidget when things need to change
- Practice with simple projects first
- Don't worry about making mistakes - Flutter gives helpful error messages!

Remember: Learning Flutter is like learning to build with blocks. Start with simple shapes (basic widgets) and gradually build more complex structures (complete apps).