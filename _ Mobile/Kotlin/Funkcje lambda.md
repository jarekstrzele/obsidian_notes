#kotlin/lambda_function

### `{ parametry -> ciało_funkcji }`

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



