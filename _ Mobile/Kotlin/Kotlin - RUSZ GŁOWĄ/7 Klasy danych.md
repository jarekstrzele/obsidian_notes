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

>Każda klasa jest klasą pochodną klasy `Any` i dziedziczy jej zachowania. 
>Każda klasa spełnia *test JEST* z klasą `Any`, i to bez żadnego zachodu z naszej strony.

```kotlin
class MyClass{}
// --> kompilator przekształca ten kod do wersji
class MyClass: Any {}
```

metoda `equals` pochodzi z klasy `Any`










