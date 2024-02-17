


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

```kotlin
val ints = listOf(1,2,3,4,0,1,2,3)  
println("max=${ints.max()}") // 4
```

Te metody pracują na typach implementujących interface `Comparable` - typy proste implementują ten interfejs.




## `minBy` i `maxBy` na wszystkich typach danych

> Aby znaleźć najmniejszą lub największą wartość bardziej złożonego typu danych, należy użyć odpowiednio funkcji `minBy` lub `maxBy`. 
> Funkcje te działają podobnie do funkcji `min` i `max`, z tą różnicą, że musimy do nich przekazać kryteria porównywania wartości.


> Funkcje `minBy` i `maxBy` mają tylko jeden parametr: wyrażenie lambda określające właściwość, której należy użyć w celu określenia najmniejszego lub największego elementu kolekcji.
> 
> `{ i: typ_elementu -> kryterium }`
>`{ i: Grocery -> kryterium }`
>


`val highestUnitPrice = groceries.maxBy { it.unitPrice}` Ten kod to tak, jakby powiedzieć: „Znajdź w kolekcji groceries element o najwyższej wartości właściwości unitPrice”.

`val lowestQuantity = groceries.minBy { it.quantity }` Ten wiersz zwraca referencję do elementu kolekcji groceries, który ma najmniejszą wartość właściwości quantity.


>[!tip]  `minBy` , `maxBy`
>Funkcje `minBy` i `maxBy` działają na kolekcjach zawierających obiekty dowolnego typu, przez co są znacznie bardziej elastyczne od funkcji `min` i `max`
>
>Jeśli wywołamy funkcję `minBy` lub `maxBy` na rzecz kolekcji, która nie zawiera żadnego elementu, to wywołanie zwróci wartość `null`.
>
>==Typ wyniku zwracanego== przez funkcje `minBy` i `maxBy` odpowiada typowi elementów kolekcji. 
>Jeśli użyjemy funkcji `minBy` na kolekcji typu `List<Grocery>`, to zwróci ona wynik typu `Grocery`. Jeżeli użyjemy funkcji `maxBy` na zbiorze typu `Set<Duck>`, to zwróci ona wynik typu `Duck`.














