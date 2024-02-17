


> Każda funkcja wyższego rzędu ma uogólnioną implementację, a jej konkretne zachowanie jest definiowane przez wyrażenie lambda przekazywane w jej wywołaniu.


## przygotowanie danych
```kotlin
data class Grocery(val name: String, val category: String,  
val unit: String, val unitPrice: Double,  
val quantity: Int)  
  
fun main() {  
val groceries = listOf(  
	Grocery("Pomidory", "Warzywa", "kg", 10.0, 3),  
	Grocery("Grzyby", "Warzywa", "kg", 12.0, 1),  
	Grocery("Obwarzanki", "Wypieki", "Opakowanie", 3.5, 2),  
	Grocery("Oliwa z oliwek", "Spiżarka", "Butelka", 19.0, 1),  
	Grocery("Lody", "Mrożonki", "Opakowanie", 14.0, 2)  
	)  
}
```


## `min` i `max` tylko na prostych tych danych
> Funkcje min i max działają na typach prostych, gdyż typy te mają określony porządek naturalny.






## `minBy` i `maxBy` na wszystkich typach danych

















