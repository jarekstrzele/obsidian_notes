#kotlin/regular_expressions 


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





















