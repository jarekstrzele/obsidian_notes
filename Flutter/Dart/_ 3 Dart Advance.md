[[_ 1 Dart intro]]
[[_ 2 Dart intermediate]]

----
# 3 Dart Advance
#dart 
[[3.1 Dart Async Programming]]
[[3.2 Compression]]
[[3.3 Encryption]]
[[3.4 Socket programming]]
[[3.5 Database programming]]


```dart
import 'dart:io';

main(List<String> args){
  print("OS: ${Platform.operatingSystem} ${Platform.version}");
}

// OS: linux 2.17.5 (stable) (Unknown timestamp) on "linux_x64"

```

`if (Platform.isWindows)`
`if (Platform.isandroid)` isLinux, ....

>[!`PATH`]
>the `PATH` variable is where the operating system will look for executables
>`print(Platform.environment['PATH']);`
>

`print("Path: ${Platform.script.path}");` -> Path: /home/jarek/IdeaProjects/osVar/main.dart

where is dart?
`print("dart: ${Platform.executable}");`  -> dart: /usr/lib/dart/bin/dart

All the environmental variables:
```dart
import 'dart:io';

main(List<String> args) {
  print("Env:");
  Platform.environment.keys.forEach((key) {
    print(" ${key} ${Platform.environment[key]}");
  }
  );
}

```

## Running processes
**a process** is a copy of an executable file running in memory
list directory
```dart
import 'dart:io';

main(List<String> args) {

  Process.run('ls', ['-l']).then((ProcessResult results) {
    print(results.stdout);
    print('Exit code: ${results.exitCode}');
  });

}

```


## Communicationg with processes
```dart

main(List<String> args) {

  Process.start('cat', []).then( (Process process) {
    //transform the output
    process.stdout.transform(utf8.decoder).listen((data) {
        print(data);
    });

    //send to the process
    process.stdin.writeln("Hello world");

    //stop the process
    Process.killPid(process.pid);

    //get the exit code
    process.exitCode.then( (int code) {
      print("Exit code: ${code}");
    });
  });
}
// -15 because we kill the process
```









