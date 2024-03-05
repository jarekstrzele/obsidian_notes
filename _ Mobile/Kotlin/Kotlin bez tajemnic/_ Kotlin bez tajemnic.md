#kotlin  #android  #helion 


----
[[3 Podstawy tworzenia aplikacji]]



-----
![[Andoid.excalidraw | 600]]


-------
# Podstawy Kotlin

https://play.kotlinlang.org

Jeżeli do zmiennej od razu przypisujesz wartość, nie musisz określać jej typu.
`val x = 10`

Jeżeli  w funkcji użyjesz ` = `, nie musisz pisać `return` i określać typu zwracanego
```kotlin
fun main() {
    println(" ${multiplyByTen(4)}")
}

fun multiplyByTen(x: Int) = x * 10
```


## data class
Wydziela podstawowe dane

```kotlin
fun main() {
    val myMoney = MyMoney(hoursWorked=123, hourlyRate=30, currency="PLN")
    myMoney.earnedMoney = countEarnedMoney(126)
    showEarnedMoney(myMoney)
}

fun countEarnedMoney(hoursWorked:Int, hourlyRate:Int=40) = hoursWorked*hourlyRate
fun showEarnedMoney(myMoney: MyMoney) = println("I earn ${myMoney.earnedMoney} ${myMoney.currency}")

data class MyMoney (val hoursWorked:Int, val hourlyRate:Int, val currency:String, var earnedMoney:Int? = null)
```


## list
```kotlin
fun main() {
    val numbers = listOf(12,15,8,4,111)
    val filteredNumbers = numbers.filter{ it>12 }
    val filteredNumbers1 = numbers.filter({ it > 12 })
    println(filteredNumbers) // [15, 111]
    println(filteredNumbers1) //[15, 111]
    
    numbers.forEach {
        println(it)
    }
//      12
// 		15
// 		8
// 		4
// 		111
    val sortedNumbers = numbers.sorted()
    println(sortedNumbers) // [4, 8, 12, 15, 111]
}
```


### operator `elvisa` *ternary operator*
```kotlin
a ?: b

```
gdzie `a` i `b` są wyrażeniami. Operator elvisa sprawdza, czy `a` jest różne od `null`. Jeśli tak, zwraca `a`; w przeciwnym razie zwraca `b`.

```kotlin
fun main() {
    
    val numbers: List<Int>? = null
    numbers?.let{ println(numbers.size) } ?: println("Pusta lista ma rozmiar 0!")
    
    var x: Int? = null
    (  x?.let{ println("x=${x+5}") } ) ?: ( println("x=$x") )
} 
```



--------
## działania na listach
```kotlin
fun main() {
    
    val numbers = listOf(12,3,92,8,43)
    if(numbers.contains(13)) println("yes")
    else if (numbers.contains(12)) println("yes 12")
    else println("no")
    
    writeNumber(14)
}

fun writeNumber(number:Int){
    when(number){
        12->println("twelve")
        15->println("fifteen")
        8->println("eight")
        else -> println("nothing to print")
    }
}
```

---------
# SOLID
#solid 

## single responsibility principle
błędny kod, bo klasa odpowiada za wyświetlanie i pobieranie
```kotlin
class ShowPicture{
	fun action(){
	}

	fun getPicture(){
	}
}
```

rozwiązanie:
```kotlin
class ShowPicture{
	fun action(){
	}

}

class GetPicture{
	fun getPicture(){
	}
}
```

## open-closed principle
błędne, bo dodanie nowego argumentu do funkcji (np. walutę), więc musimy ingerować w już istniejący kod
```kotlin
fun showAmount(amount:Int){
	println(amount)
}
```
rozwiązanie
```kotlin
fun showAmount(amount:Int, currency: String? = null){
 println(amount)
 currency?.let{ println(currency)}
}
```
albo rozbić tę funkcję na dwie różne

## Liskov substitution principle
poprawny kod
```kotlin
interface Coffee {
	fun makeCoffee()
}

class Espresso : Coffee{
	overrife fun makeCoffee(){
		prinln("making espresso")
	}
	
}

class FlatWhite:Coffee{
	override fun makeCoffee(){
		println("make Flatwhite")
	}
}
```

## Interface segregation principle
błędny kod
```kotlin
interface Animal {
	fun walk()
	fun swim()
	fun fly()
}

class Fish:Animal{
	override walk(){}
	override swin(){}
	override fly(){}
	
}

class Dog: Animal{
	
	override walk(){}
	override swin(){}
	override fly(){}
}
```

lepiej zrobić oddzielne interfejsy, bo przecież `Dog` nie będzie latał, a `Fish` chodził
```kotlin
interface Bird{
	fun fly()
}
```

## Dependency Inversion principle
Moduły wysokopoziomowe powinny być odporne na zmiany modułów niskopoziomowych

błędny kod
```kotlin
class Shelf{
	fun addBook(book:Book){}
	fun addMovie(book:Book){}
	
}
```

lepiej
```kotlin
class Shelf{
	fun addProduct(product: Product){}
}

interface Product{
	 val name: String
}
class Book :Product{
	override val name = "Book"
}

class Movie :Product{
	override val name = "Movie"
}
```



---
# Wzorce programowania

W Andoidzie
- Model-View-ViewModel *MVVM*
- Model-View-Controller *MVC*
- Model-View-Presenter *MVP*

## MVC
>[!info] **CONTROLER**
> - application logic
> - receives user actions
> -  update model


>[!info] MODEL
> - contains data
> - database communication
> - sever communication

>[!info] VIEW
>- user interface


VIEW -- user action --> CONTROLLER
CONTROLLER --update view--> VIEW

MODEL --model changed --> CONTROLLER
CONTROLLER --update model --> MODEL

MODEL --model changed-->VIEW



## MVP bardzo podobny do MVC


## MVVM
PRZEDE WSZYSTKIM TEN SPOSÓB

>[!info] MODEL
>- data repository
>- database communication
>- server communication

>[!info] VIEW
>- user interface
>- business logic
>- observes VIEWMODEL events

>[!info] VIEWMODEL
>- presentation logic
>- receives user actions
>- observes model events

MODEL -- model change callbacks --> VIEWMODEL
VIEW -- UI EVENT --> VIEWMODEL

VIEWMODEL -- send data--> MODEL
VIEWMODEL --data streams--> VIEW











