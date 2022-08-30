[[_ 1 Dart intro]]
[[_ 3 Dart Advance]]

-----
# Dart intermediate
[[2.1 - Classes]]
[[2.2 - Scope]]
[[2.3. Polymorphism]]
[[2.4. Abstraction]]
[[2.5 Generics]]
[[2.6 File system]]


package repo: https://pub.dev/  (old: pub.dartlang.org)

>[!Dart]
>- is more than language
>- is a collection of packages 
>- is available for Web (FLUTTER)
>



---
## IMPORT
`'dart: ...'` it's built into the framework
`import 'dart:convert';`


`'package: ...'` it's not built in the dark, it was created separately
`import 'package:inter/inter.dart' as mycode;`
package is in the inter folder in the lib subfolder

```dart
import 'package:inter/inter.dart' as mycode;
import 'dart:convert';

void main(List<String> arguments) {
  mycode.sayHello();
  String text = 'Hello World';
  var utf8text =  utf8.encode(text);
  String base64text = base64.encode(utf8text);

  print('Encoded: ${base64text}');

  var rbase64 = base64.decode(base64text);
  String decoded = utf8.decode(rbase64);
  print('Decoded ${decoded}');
}
```
#dart/encode 

---
### HTTP package
package http: https://pub.dev/packages/http
install -> use:
	- `$ dart pub add http` -> this add `dependecies: {http: ^0.13.4` to `pubspec.yaml` file

or you can `dart pub get`

now you can write in the code `import 'package:http/http/dart;'`

```dart
import 'package:http/http.dart' as http;

void main(List<String> arguments) {

    var url = "http://www.voidrealms.com";
    
    http.get(Uri.parse(url)).then((resp) => {
      // 200 means ok
      print("Response status: ${resp.statusCode}"),
      print("Response body: ${resp.body}"),
      print("ok")
});
}
```

#### path 
#dart/path
in the `pubspec.yaml` :
```yaml
dependencies:
	path: ^1.8.0
```

```dart
import 'package:path/path.dart' as p;

void main(List<String> arguments) {
  String path = p.join("Directory", "file.txt");
  print(path);
}
```










