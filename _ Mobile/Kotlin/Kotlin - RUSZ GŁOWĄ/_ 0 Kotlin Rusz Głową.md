#kotlin #rusz_głową 

---
[[2 Typy proste i zmienn]]
[[3 Funkcje - wychodzimy poza `main`]]
[[4 Klasy i obiekty]]
[[5 Klasy pochodne i bazowe]]
[[6.1 Klasy abstrakcyjne]]
[[6.2. Interfejsy]]
[[7 Klasy danych]]
[[7.0. Wprowadzenie do  klas danych]]
[[7.1. Klasa danych `data class`]]
[[8. Wartość `null` i  wyjątki]]
[[8.1. Wyjątki]]
[[9. Kolekcje]]
[[10 Typy sparametryzowane]]
[[11. Lambda i funkcje wyższego rzędu]]











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











