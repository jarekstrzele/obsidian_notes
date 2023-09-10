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

# arithmetic operators
`+ - * / % `
with ` = ` --> `...*=...`, `...+=...` , ...

`.toInt()`


# comparison operators
` ==, !=, <, >, <=, >=`

```kotlin
print("Is -5 greater the 3? ${-5>3}")
```

# assignment, in(de)crement operator

`c = 10`

`x++`, `++x `
`--y`, `y--`

# `if` statments

```kotlin
if(<condition>) {
 // /....
} else if (<condition>){
 // ...
} else {

}
```

# `when`
#kotlin/when 
almost like `switch`
```kotlin
var season = 3
when(season){
	1 -> println("Spring")
	2 -> println("Summer")
	3 -> {
		println("Dall")
		println("Autumn")
	}
	4 -> println("Winter")
	else -> println("Invalid Season")
}
```

```kotlin
var = month = 3
whaen(month) {
	in 3..5 -> println("Spring")
	in 6..8 -> println("Summer")
	in 8..11 -> println("Fall")
	12, 1, 2 -> println("Winter")
	else -> println("Invalid Season")
}
```

```kotlin
var age = 20
when(age){
	!in 0..20 -> println("now you may drink in the US")
	in 18..20 -> println("you can vote now")
	16,16 -> println("you may drive now")
	else -> println("you are too young")
}
```









