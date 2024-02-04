#kotlin/regular_expressions 

# Wprowadzenie

## tworzenie
```kotlin
val regex: Regex = Regex(pattern)

```

## sprawdzanie dopasowań
```kotlin
val text = "Przykładowy tekst"
val pattern = "tekst"

if (regex.containsMatchIn(text)) {
    println("Znaleziono dopasowanie")
} else {
    println("Brak dopasowania")
}

```








# czy ciąg znaków jest liczbą?
```kotlin
fun main(args: Array<String>) {

    val regex = Regex("[0-9]+")

    val testStr1 = "9876"
    val testStr2 = "zyx9876"

    // czy ciąg znaków jest liczbą
    println(regex.matches(testStr1)) // true 
    println(regex.matches(testStr2)) //false

    println("the end")
}
```

- Wyrażenie `[0-9]` oznacza dokładnie jedną cyfrę od 0 do 9.
- Wyrażenie `[0-9]+` oznacza jedną lub więcej cyfr od 0 do 9.

Przykłady:

1. Dla `[0-9]`:
    
    - `1` - pasuje (jedna cyfra)
    - `5` - pasuje (jedna cyfra)
    - `123` - nie pasuje (więcej niż jedna cyfra)
2. Dla `[0-9]+`:
    
    - `1` - pasuje (jedna cyfra)
    - `5` - pasuje (jedna cyfra)
    - `123` - pasuje (więcej niż jedna cyfra)

Podsumowując, jeśli pominiemy znak `+`, wyrażenie `[0-9]` dopasuje dokładnie jedną cyfrę, podczas gdy `[0-9]+` dopasuje jedną lub więcej cyfr.


# wyodrębnianie adresu email


















