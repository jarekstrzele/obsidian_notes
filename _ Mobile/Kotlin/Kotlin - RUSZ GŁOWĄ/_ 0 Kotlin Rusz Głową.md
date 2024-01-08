#kotlin #rusz_głową 

---
[[2 Typy proste i zmienn]]
[[3 Funkcje - wychodzimy poza `main`]]






----------
**IntelliJ Community Edition** - to darmowe zintegrowane środowisko programistyczne `IDE` opracowane przez `JetBrains`:
- **edytor kodu**
- **narzędzia do budowy** kod można kompilować i uruchamiać
- **Kotlin REPL** testowanie fragmentów kodu poza główną bazą kodu projektu
- **Kontrola wersji**: GIt, SVN, CVS, ...

Nowy projekt w Kotlinie w JVM uruchamiany

> `fun main(){}` tylko w jednym pliku może znajdować ta funkcja

`run` :
1. IDE kompiluje kod napisanyw Kotlinie do postaci kodów bajtowy Javy
2. IDE uruchamia JVM, a nastęnie wykonuje klasę `AppKt.class`

```kotlin
for (i in 1..5) {  
     println("i = $i")  
}


```

W przypadku stosowania `if` jako wyrażenia, MUSISZ użyć także klauzuli `else`
```kotlin
println(if (x>y) "x jest większe od y" else "x nie jest większe od y")
```

REPL
`Tools>Kotlin>REPL`
```kotlin
val x = 6
val y = 8
println(if(x>y) x else y)
8
```











