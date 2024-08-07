[[_ the complete Android Kotlin]]

#kotlin/function #kotlin/null_safety

OPERATOR `!!` *Null Safe*ty
> Należy jednak pamiętać, że zbyt częste używanie operatora `!!` może prowadzić do trudności w zarządzaniu wartościami null i utrudniać zrozumienie i utrzymanie kodu. Dlatego zaleca się stosowanie operatora `!!` tylko wtedy, gdy masz pewność, że wartość nie będzie null, lub w przypadkach specjalnych, takich jak testowanie lub debugowanie. W większości sytuacji lepiej jest używać operatora safe call `?.` i odpowiednio obsługiwać wartości null w swoim kodzie.

```kotlin
fun addNumber(x:Int, y:Int):Int {
	var sum = 0
	sum = x + y
	return sum ;
}
```


```kotlin
fun funName(parameters:Type): returnType {
	//
	return returnValue
}
```

## Types of Functions
- standard Library Functions
- User-Defined Functions

==every function in Kotlin returns==
- some value (e.g. returns nothing `void`)
- primitive (char, int, boolean ...)
- non-primitive (reference data types: object of Class, String etc.)


```kotlin
fun main() {
  print("Please enter the first number: ")
  var number1:Int = readLine()!!.toInt()
  print("Please enter the second number: ")
  var number2:Int = readLine()!!.toInt()
  
  show(number1, number2)
  println(add(number1, number2))
  println(findMinimumNumber(number1, number2))
  
  
}

//fun show(num1:Int, num2:Int) {
fun show(num1:Int, num2:Int) : Unit 
{
  println("You enter $num1 and $num2")  
}

fun add(num1:Int, num2:Int) : Int
{
  return num1+num2
}

fun findMinimumNumber(a: Int, b: Int) : Int 
{
  if (a > b) {
    return a
  }else {
    return b
  }
}
```
