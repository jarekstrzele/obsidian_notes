[[_ the complete Android Kotlin]]

`+  -  *   /   %`

` = ` simple assignment
`+=` add and assignment
`-=`
`*=`
`/=`
`%=` modulus and assignment

```kotlin
fun main() {

  var num1:Int = 10
  var num2:Int = 3
  var z:Int = 1
  
  z += num1
  println(z) // 11

  z /= num2
  println(z) // 3

  z *= num1
  println(z) // 30

 
  z %= num2+1
  println(z) // 3

}
```

## unary operator
` + -  ++ --  !`

`var number:Int = 1 `
`+number` --> 1
`++number` increment by 1  -> 2
`number++`


---
## equality and relational operators

` ==  !=  >  <  >=  <= `


## conditional operators

`&&` and
`||` or

```kotlin
fun main() {
  println( (10 > 3) && (4 <= 100))

}
```


## operator precedence

unary -- HIGHEST
multi
add
relational
equality
AND
OR
assignment LOWEST )` =  +=  -=  *=   /=  % `


## `rangeTo`  `in`

`some.toRange(other)`
`... in  ...`  included

```kotlin
  
fun main() {
  var myCharRange =  'a'.rangeTo('q')
  // myCharRange = 'a'..'q'
  println(myCharRange) // a..q
  println("b in myCharRange? " + ('b' in myCharRange) ) // true

}

```


---
## Console input

`readLine()` to enter data into the console

`var name:String? = readLine()`  - `?` because the user may not actually enter any data --> returns String

the same one
`var name:String = readLine()!!` --> returns String

`var age:Int? = readLine().toInt()`

```kotlin
fun main() {
  print("What is your name: ")
  var name:String? = readLine()

  print("How old are you? ")
  var age:Int = readLine()!!.toInt()

  println("Your name is $name and your age is $age")

}
```






