#kotlin 
[[_ the complete Android 12]]




----
# `var`, `val`

fun main(){}` - this function is a special function, it's a staring point of the application

```kotlin
package com.example.kotlin_fund  
  
fun main(){  
    var myName = "John"  
    myName = "Jaśko"  
    print("Heloł łold " + myName)  
  
    val age = 30  
    // age = 31 // error  
}
```

# numbers
#kotlin/comments

```kotlin
// one line comments
/*
 multiple lines comments
*/

// TODO: Define body of that function  
fun hello(){  
  
}
```
There is a tab at the bottom of the window of Android Studio `TODO`, so you can easily find that note in your code

```kotlin
// INTEGER

val x1: Byte = 1              // 8 bit
val x2: Short = 112           // 16
val x3: Int = 1323414         // 32
val x4: Long = 110_20_30_40   //64

val x5: Float = 13.33F
val x6: Double = 323.32423

```
by default it is `Int`  --> `val x = 21 `
by default it is `Double`  --> `val x = 21.12 `

# booleans
```kotlin
var isSunny: Boolean = true
var isActive = false
```

# char , string
```kotlin
var a = 'a'
var name:String = "This is a string"
// name[0] -> 'T'
// name.length


```

## string template/interpolation
```kotlin
print("Your name is $name, Bienvenu")
print("2 + 2 = ${2+2}")
```






