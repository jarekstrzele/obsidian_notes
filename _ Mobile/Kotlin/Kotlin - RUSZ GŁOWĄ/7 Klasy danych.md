#kotlin/dataclass 


# operator ` == `  --   `equals`


> Każdy obiekt dysponuje metodą `equals`, która jest wykonywana, gdy zostanie użyty operator ` == `  

> dymyślnie metoda `equals` sprawdza, czy dwie zmienne zawierają referencje do tego samego obiektu

```kotlin
val w1 = Wolf()
val w2 = w1
println(w1==w2) // --> true

val w3 = Wolf()
println(w1==w3) // --> false

```

# `Any`
#kotlin/any 

==metoda `equals` pochodzi z klasy `Any`==

>Każda klasa jest klasą pochodną klasy `Any` i dziedziczy jej zachowania. 
>Każda klasa spełnia *test JEST* z klasą `Any`, i to bez żadnego zachodu z naszej strony.

```kotlin
class MyClass{}
// --> kompilator przekształca ten kod do wersji
class MyClass: Any {}
```

## korzyści z `Any`
Korzyści wynikające z tego "powszechnego" dziedziczenia:
- gwarancja, że **wszystkie klasy będą dziedziczyć wspólne zachowania**
- we wszystkich obiektach możemy używać ==polimorfizmu==
```kotlin
val myArray = arrayOf(Car(), Guitar(), Giraffe()) // kompilator utworzy tablicę tyou `Array<Any>`, bo wspólną klasa bazową dla obiektów zapisanych w tablicy jest klasa `Any`
```

## zachowania z `Any`
najważniejsze zachowania:
- `equals(any: Any) : Boolean`
- `hashCode(): Int` funkcja zwraca kod mieszający dla obiektu. Kody mieszające są często żywane przez różnego rodzaju struktury danych do wydajniejszego zapisywania i pobierania danych
```kotlin
val w = Wolf()
println(w.hashCode()) //--> 52342937
```
- `toString(): String` tekstowa reprezentacja obiektu (nazwa klasy i jakaś liczba)

można nadpisać każdą z tych metod
















