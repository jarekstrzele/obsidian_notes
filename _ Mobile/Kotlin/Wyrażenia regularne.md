#kotlin/regular_expressions 

# Wprowadzenie


## tworzenie
```kotlin
val regex: Regex = Regex(pattern)
val regex = Regex("[0-9]+")

```


## metaznaki
- `.` - dowolny znak
- `*` - zero lub więcej powtórzeń poprzedniego znaku
- `+` - jedno lub więcej powtórzeń poprzedniego znaku
- `?` - zero lub jedno powtórzenie poprzedniego znaku
- `|` - alternatywa (np. `a|b` oznacza "a" lub "b")
- `[]` - zakres znaków (np. `[a-z]` oznacza dowolną małą literę)

## **Operatory:**

- `&&` - iloczyn logiczny
- `||` - suma logiczna
- `^` - początek tekstu
- `$` - koniec tekstu

## przykłady
regex:
- pierwsze 3 znaki to małe listery, 
- potem dwie liczby, 
- potem zero lub więcej jednego ze znaków "xzy"
`^[a-z]{3}\d{2}[xzy]*$
`
- `Regex("^[0-9]+$")`: Pasuje do ciągu składającego się z jednej lub więcej cyfr.
- `Regex("^[0-9]*$")`: Pasuje do ciągu składającego się z żadnej, jednej lub więcej cyfr
- `Regex("^[0-9]$")`: To wyrażenie regularne pasuje do dokładnie jednej cyfry, ponieważ jest ograniczone przez `^` (początek tekstu) i `$` (koniec tekstu).




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

Wyrażenie to służy do walidacji adresów e-mail i ma następujące elementy:

```kotlin
fun main(args: Array<String>) {


   val regex = Regex("[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}")

   val text = "Mój adres e-mail to jan.kowalski@gmail.com."

   val match = regex.find(text)

   if (match != null) {
     println("Adres e-mail: ${match.value}")
   } else {
     println("Nie znaleziono adresu e-mail.")
   }
}

```


1. `[a-zA-Z0-9._%+-]+`: Oznacza, że na początku adresu e-mail musi wystąpić co najmniej jedna lub więcej liter (zarówno małych, jak i dużych), cyfr lub innych dozwolonych znaków, takich jak kropka (`.`), podkreślenie (`_`), procent (`%`), plus (`+`) lub myślnik (`-`).
    
2. `@`: Oznacza, że po tym fragmencie musi wystąpić znak '@', który jest niezbędny w prawidłowym adresie e-mail.
    
3. `[a-zA-Z0-9.-]+`: Określa, że po znaku '@' musi wystąpić co najmniej jedna lub więcej liter, cyfr lub innych dozwolonych znaków, takich jak kropka (`.`), myślnik (`-`) lub podkreślenie (`_`).
    
4. `\\.`: Oznacza, że po drugiej części adresu e-mail musi wystąpić kropka, ale ze względu na specyfikę języka Kotlin, używamy dwukropka (`\.``) jako escape character, ponieważ kropka jest znakiem specjalnym w wyrażeniach regularnych.
    
5. `[a-zA-Z]{2,}`: Określa, że na końcu adresu e-mail muszą wystąpić co najmniej dwie litery (małe lub duże).
6. 

---
# program sprawdzający poprawność mejla
```kotlin
fun main() {
    println("Podaj adres e-mail:")
    val email = readLine()

    val regex = Regex("[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}")

    if (email != null && regex.matches(email)) {
        println("Podany adres e-mail jest poprawny.")
    } else {
        println("Podany adres e-mail jest niepoprawny.")
    }
}
```














