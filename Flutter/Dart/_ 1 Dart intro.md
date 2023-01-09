#dart #udemy #billennium 
#cairns_bryan #oop

[[_ 2 Dart intermediate]]
[[_ 3 Dart Advance]]

---
# Dart Beginners Course
Dart is focused on frontend (mobile apps, web) user interface (UI) development

Dart is an OOP & Strongly Typed -> everything is an object
*object* is something that exists
[[1.3 - Dart Collections]]
[[1.4 - Dart Flow Control]]
[[1.5 - Dart Functions]]
[[1.6 - Error handling]]

---
## IDE
- DartPad web-based tool
- IntelliJ IDEA
- Android Studio
- VisualCode
- Atom
- Vim [[Dart&Vim]]

---
file: `.dart` --> `main.dart`
```dart
void main(){
	print("hello world");
}
```

in the shell:
`dart main.drat`


---

https://dart.dev/

to install dart: https://dart.dev/get-dart
to install IDE: IntelliJ IDEA

**the Dart SDK** has libraries and command-line tools that you need to develop Dart command-line, server, and non-Flutter web apps

- in IntelliJ install dart plugin
- create a project (look for a Dart  icon) "helloworld"

`.bin` is your project
`lib` library

```dart
import 'package:helloworld/hellowprld/dart' as helloworld

main(List<String> arguments){
	print('Hello wolrd:);
}
```

----
## comments
`// comment`
`/* mutipl line comment */`


## boolean
`bool isOn;`
`bool isDog = false;`
`print(isOn);` -> null (object doesn't exist)
`print(isDog);` -> 'false'

`isOn = true;`
`print('isOn = ${isOn}');` -> 'isOn = true'

## object
everything is an object, so `isOn` is an object, so:
`print('isOn is a ${isOn.runtimeType})'`-> isOn is a bool

`var isOn;` - `var` it's a generic object and Dart is smart enough to know what it is when we runthis

## numbers
`num age;` - `num` it's a generic number

**Int**
`int people = 6;`

**Double**
`double temp = 32.06;`

**parse**
`int test = int.parse('12');` -> text = 12
`int err = int.parse)'12.09', onError: (source) => 0);`

## string
`String hello = 'hello';`
`print(hello)`

```dart
String name = 'Bryan Cairns';
print('Hello ${name}'); //->Hello Bryan Cairns
```

**substring**
```dart
String name = '123456'
print("Hello ${name.substring(0,5)}");

```
output: Hello 12345

**index, length, contains**
```dart
void main(){
 
  String name = 'jarek strzelecki';
  int index = name.indexOf(' ');
  String lastname = name.substring(index).trim();
  print('lastname = ${lastname}');
  print("lendth ${name.length}");
  print(name.contains('jarek'));
 
 }
```

```
```shell
$ dart main.dart
lastname = strzelecki
lendth 16
true

```

## list
```dart
String name = 'jarek strzelecki';
 List parts = name.split(' ');
 print(parts);
 print(parts[1]);

```
output: 
	[jarek, strzelecki]
	strzelecki

## constant
`const String = 'Kotek'`

## user input
```dart
import 'dart:io'; //standart output input
import 'dart:async';

main(List<String> arguments){
  stdout.write("What is your name?\r\n");
  // String? -> is a string or null
  String? name = stdin.readLineSync();
  stdout.write("Hello ${name}\r\n");
  print(name);
}
```

>[!STDIN]
> is the the standard way of asking the user for input












