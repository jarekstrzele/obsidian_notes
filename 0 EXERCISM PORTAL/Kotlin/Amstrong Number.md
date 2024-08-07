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









