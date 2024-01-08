[[_ the complete Android Kotlin]]


### `if`
```kotlin
if (condition) {

}

if (condition) {

} else {


}


//////////
if (cond1) {

} else if (cond2) {

} else {

}

////////////
if (cond) {
	if (cond) {
	
	}
}





```


## `when`
#kotlin/when

```kotlin
when(expression)
{
	value1 -> code to be executed
	value2 -> code to be executed
	...
	else -> if all cases are false 
			code to be executed
}
```

`... -> ...` lambda

```kotlin

fun main() {
  print("Enter the number between 1-7: ")
  
  var dayNumber:Int = readLine()!!.toInt()
  var day:String
  
  when (dayNumber)
  {
    1 -> day = "Monday"
    2 -> day = "Tuesday"
    3 -> day = "Wednesday"
    4 -> day = "Thursday"
    5 -> day = "Friday"
    6 -> day = "Saturday"
    7 -> day = "Sanday"
    else -> day = "invalid day choice"
  }

  println("Day: $day ")

}
```
