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
    println(k.plus(" language"))  
    println(k.uppercase())  
  
    println("   Rufui  ".trim())  
} 
```


## Arrays
#kotlin/array

`var age = arrayOf(24,14,8,12,16,19,36)`

```kotlin
fun main() {  
  
    var age = arrayOf(1,2,3)  
  
    println("First element of Array = " + age[0])  
    println("Second element of Array = " + age.get(1))  
  
    var cars = arrayOf("Mercedes", "BMW", "Opel")  
    cars.set(2, "Fiat")  
    println(cars[2])  
    println("Size: " + cars.size)  
  
    var carsAndAge = arrayOf("Fiat", 10, "Maluch", 123)  
  
    carsAndAge.set(4, "New element") //error ArrayIndexOutOfBoundsException  
}

```


## ArrayList
#kotlin/arraylist

`var age = arrayList<Int>(2,10,4)`

only init:
`var age = ArrayList<Int>()`

add
`age.add(index:3, element: 20  )`
`age.add(20)`

remove
`age.removeAt(index: 1)`
`age.remove(10)


```kotlin
fun main() {  
  
    var age = ArrayList<Int>()  
  
    age.add(10)  
    age.add(1, 22)  
    age.add(333)  
  
    println("First element of ArrayList = " + age[0])  
    println("Second element of ArrayList = " + age.get(1))  
    println("Third element of ArrayList = ${age[2]} ")  
  
    age.remove(22)  
    println(age.size)  
  
    var cars = arrayListOf< String>("ala", "ma", "kota")  
    cars.add("nowy")  
  
    var mixArrayList = ArrayList<Any>()  
    mixArrayList.add("Ford")  
    mixArrayList.add(5)  
    mixArrayList.add(true)  
  
    println(mixArrayList) // [Ford, 5, true]  
}
```


## Set
#kotlin/set 

`var age = setOf<Int>(1,2,3,2)`
`println(age.siz)` --> 3


```kotlin
fun main() {  
  
    var mySet = setOf<Int>(1,2,3,2)  
    println(mySet.size)  
  
    var mixSet = setOf<Any>(true, 2, 2.3, true)  
    println(mixSet.size) // 3  
    println(mixSet.last()) // 2.3  
}
```



---
## Map
`key:value`

`var age = mapOf<String, Int> ("david" to 20, "ronaldo" to 25)`

`println(age["david"])` -> `20`


```kotlin
fun main() {  
  
    // IMMUTABLE  
    println(" ---- immutable map of -------")  
    var age = mapOf<String, Int>("david" to 20, "ronaldo" to 25)  
    println( "Ronaldo : ${age["ronaldo"]}") // 25  
  
    // MUTABLE    println(" ---- mutable map of -------")  
    var mutableAge = mutableMapOf<String, Int>("david" to 20, "ronaldo" to 25)  
    mutableAge.put("Jaśko", 68)  
    println( "Jaśko : ${mutableAge["Jaśko"]}") // 25  
    println("david: ${mutableAge.get("david")}")  
  
}
```






