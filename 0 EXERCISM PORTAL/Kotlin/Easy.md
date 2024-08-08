

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







