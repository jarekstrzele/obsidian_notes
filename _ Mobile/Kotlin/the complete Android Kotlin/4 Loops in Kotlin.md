[[_ the complete Android Kotlin]]

```kotlin
for (i in 0..10)
{
	// loop body
}
```


```kotlin
fun main() {

  var myNumList = arrayListOf<Int>(1,2,3,4,5)

  for (y in myNumList)
  {
    println(y)
  }
println("----------------")
    for (y in 0..(myNumList.size)-1)
  {
    println("My list index $y = ${myNumList[y]}" )
  }

  println("----- the same one -----------")
    for (y in myNumList.indices)
  {
    println("My list index $y = ${myNumList[y]}" )
  }

}
```


## FOREACH`
#kotlin/foreach

```kotlin
  
fun main() {

  var myNumList = arrayListOf<Int>(1,2,3,4,5)

  myNumList.forEach{ println(it)}
}
```


## `while` loop
```kotlin
var i = 0
while(i<=10){
	i++
}
```


```kotlin
var i = 0
do{
	i++
} while(i<10)
```


------
## random
#kotlin/random
```kotlin
import kotlin.random.Random 

  
fun main() {

  val num = Random.nextInt(0,100)
  println(num)
  
}
```





