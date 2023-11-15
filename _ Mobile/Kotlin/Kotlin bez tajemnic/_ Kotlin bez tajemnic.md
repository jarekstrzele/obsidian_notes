#kotlin  #android 


![[Andoid.excalidraw | 600]]


-------
# Podstawy Kotlin

https://play.kotlinlang.org

Jeżeli do zmiennej od razu przypisujesz wartość, nie musisz określać jej typu.
`val x = 10`

Jeżeli  w funkcji użyjesz ` = `, nie musisz pisać `return` i określać typu zwracanego
```kotlin
fun main() {
    println(" ${multiplyByTen(4)}")
}

fun multiplyByTen(x: Int) = x * 10
```


## data class
Wydziela podstawowe dane

```kotlin
fun main() {
    val myMoney = MyMoney(hoursWorked=123, hourlyRate=30, currency="PLN")
    myMoney.earnedMoney = countEarnedMoney(126)
    showEarnedMoney(myMoney)
}

fun countEarnedMoney(hoursWorked:Int, hourlyRate:Int=40) = hoursWorked*hourlyRate
fun showEarnedMoney(myMoney: MyMoney) = println("I earn ${myMoney.earnedMoney} ${myMoney.currency}")

data class MyMoney (val hoursWorked:Int, val hourlyRate:Int, val currency:String, var earnedMoney:Int? = null)
```


## list
```kotlin
fun main() {
    val numbers = listOf(12,15,8,4,111)
    val filteredNumbers = numbers.filter{ it>12 }
    val filteredNumbers1 = numbers.filter({ it > 12 })
    println(filteredNumbers) // [15, 111]
    println(filteredNumbers1) //[15, 111]
    
    numbers.forEach {
        println(it)
    }
//      12
// 		15
// 		8
// 		4
// 		111
    val sortedNumbers = numbers.sorted()
    println(sortedNumbers) // [4, 8, 12, 15, 111]
}
```







