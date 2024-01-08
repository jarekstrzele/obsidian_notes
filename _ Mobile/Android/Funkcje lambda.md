#kotlin/lambda_function

### `{ parametry -> ciało_funkcji }`

# FL jak argument innej funkcji ({}) vs {}
W Kotlinie możesz wywoływać funkcje, które przyjmują funkcje lambda jako ostatni argument poza nawiasami, co pozwala na bardziej zwięzły i czytelny kod. To jest znane jako "słodka notacja" (ang. "lambda syntax sugar") i jest jednym z udogodnień języka.

Przykładowo, jeśli funkcja `setOnClickListener` jest metodą, która przyjmuje funkcję lambda jako ostatni argument, możesz ją wywołać w ten sposób:

```kotlin
button.setOnClickListener { view ->
    // Kod reagujący na kliknięcie przycisku
}
```

Zamiast używać nawiasów, możesz użyć nawiasów klamrowych `{}` bezpośrednio po funkcji `setOnClickListener`. Wynika to z faktu, że Kotlin pozwala na przeniesienie ostatniego argumentu funkcji poza nawiasy, co jest bardziej zgodne z konwencją programowania funkcyjnego i bardziej zwięzłe.

Jeśli funkcja przyjmuje tylko jedną funkcję lambda jako argument, to taka notacja jest często preferowana, ponieważ poprawia czytelność kodu i jest bardziej przyjemna w użyciu. Jednak jeśli funkcja przyjmuje wiele argumentów lub jest bardziej złożona, można użyć nawiasów klamrowych `{}` wewnątrz nawiasów, aby bardziej wyraźnie oddzielić argumenty od ciała funkcji lambda, tak jak w przykładzie:

```kotlin
button.setOnClickListener({ view ->
    // Kod reagujący na kliknięcie przycisku
})
```

Obie formy są poprawne w Kotlinie, ale słodka notacja jest często preferowana ze względu na jej czytelność i elegancję, zwłaszcza w przypadku jednoargumentowych funkcji lambda.

---

```kotlin
val numbers = listOf(1, 2, 3, 4, 5)
numbers.forEach { number ->
    println(number)
}

// funkcja lambda to 
//  { number -> println(number) }
```

==każda funkcja lambda ma swój TYP==
przykład:
- `(Int, Int) -> Int` to typ funkcji lambda, która przyjmuje dwie liczby całkowite i zwraca liczbę całkowitą.
- `() -> Unit` to typ funkcji lambda, która nie przyjmuje żadnych argumentów i nie zwraca wartości.


>[!info] Zakres widoczności (Closure):
>Funkcje lambda w Kotlinie mają dostęp do zmiennych z otaczającego je zakresu (closure), co oznacza, że mogą korzystać z zmiennych zadeklarowanych poza nimi.

inne przykłady
```kotlin
// Funkcja lambda przyjmująca dwa argumenty i zwracająca ich sumę
val add: (Int, Int) -> Int = { a, b -> a + b }

// Funkcja lambda przyjmująca jeden argument i zwracająca jego kwadrat
val square: (Int) -> Int = { x -> x * x }

// Funkcja lambda nieprzyjmująca argumentów, wyświetlająca "Hello, World!"
val greet: () -> Unit = { println("Hello, World!") }

```

## Przykłady użycia

### obsługa zdarzeń
```kotlin
button.setOnClickListener { view ->
    // Kod reagujący na kliknięcie przycisku
}

```

### przetwarzanie kolekcji
```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

val evenNumbers = numbers.filter { it % 2 == 0 }
println(evenNumbers) // Wyświetli: [2, 4, 6, 8, 10]

```

### tworzenie wątków
```kotlin
Thread {
    // Kod wykonywany w innym wątku
    println("Hello from another thread!")
}.start()

```

