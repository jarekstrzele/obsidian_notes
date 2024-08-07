#kotlin 
[[_ the complete Android 14]]

----
Kotlin programmer dictionary: https://blog.kotlin-academy.com

---
The Content of the note

[[#`var`, `val`]]
[[#numbers]]
[[#booleans]]
[[#char , string]]
[[#arithmetic operators]]
[[#comparison operators]]
[[#assignment, in(de)crement operator]]
[[#`if` statments]]
[[#`when`]]
[[#Loop]]
[[#Function]]




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

>In Kotlin you can use if statement as an expression, for example, you can assign the result of if-else to a variable. Let's look at an example
>
```kotlin
 //Assign the if statement to a variable
 val currentAge = if (age >=drinkingAge){
 println("Now you may drink in the US")
 //return the value for this block
 drinkingAge
 }else {
	println("Error!")
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

```kotlin
fun main(args: Array<String>) {
  var x: Any = "32.34f"

  when(x) {
    is Int -> println("$x is an INT")
    !is Double -> println("$x not is an Double")
    is String -> println("$x is an String") // 
    else -> println("$x is ??")
  }
  
}
```


> Just like if-else, when can also be used as an expression by assigning it to a variable. Here is an example:
```kotlin
1. val x : Any = 13.37
2. //assign when to a variable
3. val result = when(x) {
4. //let condition for each block be only a string
5. is Int -> "is an Int"
6. !is Double -> "is not Double"
7. is String -> "is a String"
8. else -> "is none of the above"
9. }
10. //then print x with the result
11. print("$x $result")
```


# Loop
#kotlin/loop
[[4 Loops in Kotlin]]

you can use `break` or `continue`
```kotlin
while(true){
	print("never ending \n story")
}


do {
	println("Only one ")
} while(false)

// python for i in range(10)
for(num in 1..10){
	print("$num ")
}

// the same result
for(num in 0 until 10){
	print("$num ")
}
// with step
for(num in 0 until 10 step 2){  
    print("$num ")  
}
// the same
for(num in 0.until(10).step(2)){  
    print("$num ")  
}


for(num in 10 downTo 10){  
    print("$num ")  
}
// with step
for(num in 10 downTo 0 step 2){  
    print("$num ")  
}
// the same
for(num in 10.downTo(0).step(2)){  
    print("$num ")  
}




```


----
# Function
#kotlin/function 
[[5 Functions in Android Kotlin]]

```kotlin
fun main(){  
    myFun()  
      
    println(addUp(10, 20))

	println(avg(30.0, 21.0))
}  
  
fun myFun(){  
    print("From myFun")  
}

fun addUp(a:Int, b:Int) : Int{  
    return a + b  
}

  
fun avg(x:Double, y:Double) : Double {  
    return (x+y)/2  
}
```


---
# Nullables
1965 Tony Blair : nullables are part of  Algol language `null references`

> Kiedy używasz operatora `?.`, jest to tzw. operator bezpiecznego wywołania. Oznacza to, że jeśli wartość zmiennej `nullableName` jest `null`, to całe wyrażenie zostanie pominięte, a nie wystąpi błąd NullPointerException.


nullables <--> not type

> Kotlin support is null ability as part of its type system:
> - you can declare whether a variable can hold a null value or not  
> - so compiler can detect possible null pointer exception errors at compile time and reduce the possibility of having them thrown at runtime
> - 


```kotlin
package com.example.myapplication_withlaout  
  
fun main(){  
    var name:String = "Denis"  
    name = "Adam"  
    // name = null // --> Compilation ERROR  
  
    var nullableName : String? = "Denis"  
    nullableName  = null  
  
    // to return a length of the string  
    var len = name.length // ok  
  
    // var len2 = nullableName.length // --> ERROR    // modern solution    var len2 = nullableName?.length  
// old fashion to resolve that problem  
//    if(nullableName != null){  
//        var len2 = nullableName.length  
//    } else {  
//     null  
//    }  
//    println(nullableName?.lowercase())  
//      nullableName?.let{ println(it.length)} ?:  
//     println("Zmienna nullableName ma wertość null")  
//  
  
    nullableName?.let { println(it.length) } ?: println("nullableName is null") // generuje błąd  
  
  
}
```

```kotlin
var name: String? = null  
var len = name?.length  
  
println(len)
```
# Elvis Operator `?:` and not null assertion `!!`

## elvis operator `?:`
>   
Operator [Elvis](https://www.google.com/search?q=Elvis) `?:` w języku [Kotlin](https://www.google.com/search?q=Kotlin) nazywany jest również operatorem "null coalescing". Jest to skrócony zapis warunkowego wyrażenia, które zwraca wartość po lewej stronie, jeśli nie jest ona null, lub wartość po prawej stronie, jeśli wartość po lewej stronie jest null.


```kotlin
fun main(){  
    var nullableName : String? = "Denis"  
    nullableName = null  
  
    //  
    val name = nullableName ?: "Guest" // if nullable is null, the assign "Gust" to nullableName  
    println("name is $name")  
  
}
```



## Not Null Assertion `!!`
It converts a knowable type to a non null type and throws a null pointer exception if knowable type holds a null value.

>Kiedy używasz operatora Not Null Assertion `!!`, mówisz kompilatorowi, że jesteś pewien, że zmienna nie jest null, i że chcesz ją użyć bez sprawdzania nullability. Jeśli jednak zmienna jest faktycznie null, zostanie zgłoszony wyjątek typu `NullPointerException`.









