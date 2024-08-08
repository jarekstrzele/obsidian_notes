

# Amstrong Number
10 -> 1^2 + 0^0 = 1 + 0 = 1 - is not
9 -> 9^1 = 9 - it is
153 -> 1^3 + 5^3 + 3^3 = 3 + 125 + 27 = 153 - it is
```kotlin
object ArmstrongNumber {

    fun check(input: Int): Boolean {
        val inputString = input.toString() 
        val power = inputString.length
        var numberToCheck = 0
        for (digit in inputString) {
        val digitValue = digit.digitToInt()
        var tmp = 1
        for (i in 1..power) {
            tmp *= digitValue
        }
        numberToCheck += tmp
    }
    
    return input == numberToCheck
    }

}
```


# Circular buffer
https://en.wikipedia.org/wiki/Circular_buffer

>[!danger] ArrayDeque
> - to struktura danych w Kotlinie i Javie, która implementuje podwójnie zakończoną kolejkę (ang. *double-ended queue*). 
> - Jest to rodzaj ==kolejki==, która pozwala na dodawanie i usuwanie elementów zarówno ==z początku==, jak i ==z końca==, co czyni ją bardzo elastyczną i wydajną do różnych zastosowań.

#kotlin/arraydeque 
```kotlin
fun main() {
    val deque = ArrayDeque<String>()

    // Dodawanie elementów
    deque.addFirst("First")
    deque.addLast("Last")

    println(deque) // Output: [First, Last]

    // Dodawanie elementów za pomocą offer
    deque.offerFirst("New First")
    deque.offerLast("New Last")

    println(deque) // Output: [New First, First, Last, New Last]

    // Usuwanie elementów
    val firstElement = deque.removeFirst()
    val lastElement = deque.removeLast()

    println("Removed: $firstElement and $lastElement") // Output: Removed: New First and New Last
    println(deque) // Output: [First, Last]

    // Podejrzenie elementów
    val firstPeek = deque.peekFirst()
    val lastPeek = deque.peekLast()

    println("First Peek: $firstPeek, Last Peek: $lastPeek") // Output: First Peek: First, Last Peek: Last
}

```

- **`addFirst`:** Rzuca wyjątek, jeśli nie można dodać elementu.
- **`offerFirst`:** Zwraca `false`, jeśli nie można dodać elementu.

- **`removeFirst`:** Rzuca wyjątek `NoSuchElementException` jeśli kolejka jest pusta.
- **`pollFirst`:** Zwraca `null` jeśli kolejka jest pusta.


