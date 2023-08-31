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













