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

## negacja
Znak negacji w wyrażeniach regularnych to `^`, ale ma on specyficzne znaczenie w zależności od tego, gdzie jest używany.

1. **Wewnątrz zakresu znaków `[]`:** Wewnątrz zakresu znaków, `^` pełni rolę znaku negacji, oznaczając, że dopasowanie ma zachodzić dla znaków, które nie należą do podanego zakresu. Na przykład:
    
    - `[^a-z]` - Oznacza dowolny znak, który nie jest małą literą od 'a' do 'z'.
    - `[^0-9]` - Oznacza dowolny znak, który nie jest cyfrą od '0' do '9'.
2. **Na początku wyrażenia regularnego `^`:** Jeśli `^` jest umieszczone na początku wyrażenia regularnego (poza zakresem znaków), to oznacza początek tekstu.
    
3. **Wewnątrz wyrażenia regularnego `(?!...)`:** W przypadku wyrażeń regularnych z wyrażeniem "negative lookahead", składnia to `(?!...)`. Na przykład:
    
    - `^(?!abc)` - Oznacza, że wyrażenie będzie dopasowane, jeśli tekst na początku nie zaczyna się od "abc".

Warto zauważyć, że znak negacji w kontekście zakresu znaków `[...]` różni się od znaku negacji wykorzystywanego w logicznych operacjach logicznych.


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

## sprawdzenie numeru telefonu
```kotlin
fun main() {
  val regex = Regex("^[0-9]{3}-[0-9]{3}-[0-9]{3}$")

  val phone_OK = "213-321-212"
  val phone_NO = "123-456-43"

  println(regex.matches(phone_OK)) // true
  println(regex.matches(phone_NO)) // false

}
```

`^[0-9]{3}(-[0-9]+)*$` 
Ten wzorzec oznacza:
- `^[0-9]{3}` - Początek tekstu musi zawierać dokładnie trzy cyfry.
- `(-[0-9]+)*$` - Następnie może występować zero lub więcej razy myślnik, a po nim co najmniej jedna cyfra, do samego końca tekstu.

```kotlin
fun main() {
  val regex = Regex("^[0-9]-[0-9]-[0-9]$")

  val phone_OK = "213-321-212"
  val phone_NO = "123-456-43"
  val ok = "1-2-3"

  println(regex.matches(phone_OK)) // false
  println(regex.matches(phone_NO)) // false
  println(regex.matches(ok)) // true

}
```


## hasła

#### hasło 8 znakowe z dowolnych liter, cyfr i znaków specjalnych
```kotlin
fun main() {
    val password = "Abc123!@"
    val regex = "^[a-zA-Z0-9!@#$%^&*()-_+=<>?/\\\\]+$".toRegex()

    if (password.matches(regex)) {
        println("Hasło jest zgodne z wzorcem.") //spełnia
    } else {
        println("Hasło nie spełnia wymagań.")
    }
}

```

#### bez znaków specjalnych
`^[a-zA-Z0-9]{8}$`

#### hasło od 8 do 16 znaków zawierający dowolne litery w tym przynajmniej dwie cyfry
`^(?=.*[0-9].*[0-9])[a-zA-Z0-9]{8,16}$`

Wyjaśnienie:
- `^` - Początek tekstu.
- `(?=.*[0-9].*[0-9])` - *Positive lookahead*, oznaczające, że w dowolnym miejscu w ciągu muszą wystąpić przynajmniej dwie cyfry.
- `[a-zA-Z0-9]{8,16}` - Oznacza od 8 do 16 dowolnych znaków będących literami (zarówno małymi, jak i dużymi) lub cyframi.
- `$` - Koniec tekstu.

>[!tip] POSITIVE LOOKAHEAD
> - `(?= ...)` - Jest to składnia "positive lookahead". To sprawdzenie wygląda naprzód, aby sprawdzić, czy w danym miejscu w tekście (ciągu znaków) występuje pewien wzorzec, ale nie przenosi się do tego miejsca.
> - `.*` dwolony ciąg znaków

Rozbijmy to na części:

- `.*` - Oznacza dowolny ciąg znaków (zero lub więcej powtórzeń dowolnego znaku).
- `[0-9]` - Oznacza jedną cyfrę.
- `.*` - Ponownie dowolny ciąg znaków (zero lub więcej powtórzeń dowolnego znaku).
- `[0-9]` - Kolejna jedna cyfra.




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

# skróty
## `\d`
`\d` jest równoznaczne z wyrażeniem `[0-9]`, czyli dopasowuje dowolną cyfrę od 0 do 9.
Przykłady użycia:

- `\d{3}` - Dopasuje trzy kolejne cyfry.
- `\d+` - Dopasuje jedną lub więcej cyfr.
- `^\d{4}$` - Dopasuje dokładnie cztery cyfry na początku i końcu tekstu.

W skrócie, `\d` to jedna cyfra w kontekście wyrażeń regularnych.


## inne
Oto kilka przykładów:

1. `\d` - Oznacza dowolną cyfrę od 0 do 9.
2. `\w` - Oznacza dowolny znak "word character", który obejmuje litery (małe i duże), cyfry i znak podkreślenia `_`. to skrót dla `[a-zA-Z0-9_]`
3. `\s` - Oznacza dowolny biały znak (spacja, tabulator, znak nowej linii) - to równoważnik `[\t\n\.


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


```kotlin
fun main() {
  val regex = Regex("[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}")

  val email1 = "jan.kowalski@gmail.com"
  val email2 = "jan.kowalski@gmail"

  println(regex.matches(email1)) // true
  println(regex.matches(email2)) // false

}
```











