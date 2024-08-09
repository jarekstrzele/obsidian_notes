

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
https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-array-deque/

https://www.baeldung.com/kotlin/arraydeque
- create `val deque = ArrayDeque<Int>()` or `val deque = ArrayDeque<Int>(listOf(1,2,3,4))`
- add `deque.addFirst(2)`, `deque.addLast(5)`
- remove 
	- `val elem: Int = deque.removeFirst()`, 
	- `val elem: Int = deque.removeFirst()`
	- `val removedElement: Int? = deque.removeFirstOrNull()`
- retrieve:
	- `val firstElemem: Int = deque.first()` without removing
	- `val firstElemem: Int? = deque.firstOrNull()`
	- `deque.get(<index>)`


```kotlin
import kotlin.collections.ArrayDeque

class EmptyBufferException: Exception("Buffer is empty")

class BufferFullException: Exception("Buffer is full")

class CircularBuffer<T>(private val capacity: Int){
	private val buffer: ArrayDeque<T> = ArrayDeque(capacity)

	fun read(): T {
		if (buffer.isEmpty()){
			throw EmptyBufferException()
		}
		return buffer.removeFirst()
	}

	fun write(value: T){
		if(buffer.size >= capacity){
			throw BufferFullException()
		}
		buffer.addLast(value)
	}

	fun overWrite(value: T){
		if (buffer.size >= capacity){
			buffer.removeFirst()
		}
		buffer.addLast(value)
	}

	fun clear(){
		buffer.clear()
	}
	
}




```


-------------

# CryptoSquare
- First, the input is normalized: 
	- the spaces and punctuation are removed from the English text and
	- the message is down-cased.
```kotlin
val text = " This, is some : ; interesting thing. Or something else "
    println(text.replace("[.,!:; ]".toRegex(), "").lowercase())
```

- Then, the normalized characters are broken into rows. These rows can be regarded as forming a rectangle when printed with intervening newlines.
	- If `c` is the number of columns and `r` is the number of rows, then for the rectangle `r` x `c` find the smallest possible integer `c` such that:
		- `r * c >= length of message`,
		- and `c >= r`,
		- and `c - r <= 1`.

























