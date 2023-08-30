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
- Boolean  false
- Character
	- `Char`
- Numbers
	- Integer
		- `Byte` (-128,127)
		- `Short` (-32 768, 32767)
		- `Int`
		- `Long` 0L
	- Floating point
		- `float` 0.0f
		- `double` 0.0d
- String
- Array

declaration and initialization
`var age : Int = 20`


```kotlin
package com.firstkotlinprogram  
  
fun main() {  
  
    var a:Boolean = true  
    var b:Char = 'R'  
    var c:Byte = 12  
    var d:Short = -356  
    var e:Long = -234556L  
    var q:Float = 222.3333F  
    var w:Double = 83.23434234  
    println(a)  
    println(b)  
    println(c)  
    println(e)  
    println(q)  
  
}
```


---
## type conversions

`toByte()`, `toShort()`, `toLong()`, `toFloat()`, `toDouble()`

```Kotlin
  
fun main() {  
  
    var x:Byte = 127  
    var y:Int = x.toInt()  
    var z:Double = y.toDouble()  
  
    println(x)  
    println(y)  
    print(z)  
      
    var a:Double = 123.32  
    var b:Int = a.toInt()  
  
}
```


---
## String
#kotlin/string

methods:
`length()`
`isEmpty()`
`plus(" ... )"` concatenated string `...` and other
`lowercase()`
`uppercase()`
`trim()`
`equals(Object other)`


```kotlin
fun main() {  
  
    var a:String = "Hello"  
    var b:String = "World"  
    println(a + " " + b ) // Hello World  
  
    var k:String = "Kotlin"  
    println(k + " " + k.length)  
    println(k.equals("domek na prerii"))  
    println(k.isEmpty())  
    println( k.plus(" language"))  
    println(k.uppercase())  
  
    println("   Rufui  ".trim())  
} 
```


## Arrays
#kotlin/array

a lot of value with the same type

`var age = arrayOf(24,14,8,12,16,19,36)`






















