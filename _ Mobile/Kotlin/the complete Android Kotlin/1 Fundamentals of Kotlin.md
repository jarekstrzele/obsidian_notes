#kotlin 

[[_ the complete Android Kotlin]]


1. create a new project in AnSt (Android Studio)
2. add a new file (`FileName`) 
3. add a new cod
```kotlin
package com.firstkotlinprogram  
  
fun main(args: Array<String>)  
{  
    print("Hello World") ;  
}
```


## Variable
- *variable* it is a container that holds value
- reserve space n memory
- is assigned a data type
- holds quantity of value

`var age = 37;`

Kotlin is sensitive programming language (`s` != `S`)

`var age =23 ;`
`var myAge =22;` 

types:
- mutable variables `var speed = 100;`
- immutable variable `val speed = 100;`

```kotlin
package com.firstkotlinprogram.ui.theme  
  
fun main(args:Array<String>){  
    var a = 10  
    var b = 20  
    var c = a + b  
  
    println(c)  
    println(a+b)  
  
    var _age = 21 //valid  
    var age3 = 22 // valid  
    /*    var 3age = 22 is invalid     */  
    var age = 30  
    age  = 10  
    println(age) // --> 10  
  
    val year = 2020  
    //  year = 2019 // error  
}
```


---
## data types
- Boolean
- Character
	- `Char`
- Numbers
	- Integer
		- `Byte` (-128,127)
		- `Short` (-32 768, 32767)
		- `Int`
		- `l=Long`
	- Floating point
		- `float`
		- `double`
- String
- Array











