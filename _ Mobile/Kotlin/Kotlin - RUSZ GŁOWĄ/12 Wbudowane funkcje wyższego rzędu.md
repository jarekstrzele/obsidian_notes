


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
#kotlin/minBy  #kotlin/maxBy

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

```kotlin
println("najwięcej: ${groceries.maxBy { it.quantity }}")  // najwięcej: Grocery(name=Pomidory, category=Warzywa, unit=kg, unitPrice=10.0, quantity=3)


println("najtańszy: ${groceries.minBy { it.unitPrice }}") // najtańszy: Grocery(name=Obwarzanki, category=Wypieki, unit=Opakowanie, unitPrice=3.5, quantity=2)
```

## `sumOf` 
#kotlin/sumOf
zastąpiła `sumBy` i `sumByDouble`
>[!tip] `sumBy`
>Funkcja `sumBy` sumuje wartości typu Int i zwraca wynik typu `Int`.


>[!tip] `sumByDouble`
> Funkcja `sumByDouble` sumuje wartości typu `Double` i zwraca wynik typu `Double`.


## `filter`
#kotlin/filter

>[!tip] `filter`
>Pozwala ona wyszukiwać czy też filtrować kolekcje w oparciu o kryterium przekazane w formie wyrażenia lambda.
>
>Dla większości kolekcji funkcja `filter` zwraca kolekcję `List` zawierającą wszystkie elementy spełniające zadane kryterium, której następnie można używać w innych miejscach kodu.
> 
> Jednak w przypadku operowania na kolekcji typu `Map` funkcja `filter` także zwraca kolekcję typu `Map`.
>>  Na przykład w poniższym kodzie użyliśmy funkcji `filter` do przygotowania listy wszystkich elementów kolekcji `groceries`, których właściwość `category` zawiera łańcuch ”Warzywa”.
>>  `val vegetables = groceries.filter { it.category == “Warzywa” }`

`val unitPriceOver9 = groceries.filter { it.unitPrice > 9.0 }` kod zwraca kolekcję List zawierającą referencje do obiektów Grocery, których właściwość unitPrice ma wartość większą od 9.0.


```kotlin
println("tylko warzywa: ${groceries.filter { it.category=="Warzywa" }}")  tylko warzywa: // [Grocery(name=Pomidory, category=Warzywa, unit=kg, unitPrice=10.0, quantity=3), Grocery(name=Grzyby, category=Warzywa, unit=kg, unitPrice=12.0, quantity=1)]

println("tylko NIE warzywa: ${groceries.filterNot { it.category=="Warzywa" }}")
//tylko NIE warzywa: [Grocery(name=Obwarzanki, category=Wypieki, unit=Opakowanie, unitPrice=3.5, quantity=2), Grocery(name=Oliwa z oliwek, category=Spiżarka, unit=Butelka, unitPrice=19.0, quantity=1), Grocery(name=Lody, category=Mrożonki, unit=Opakowanie, unitPrice=14.0, quantity=2)]

```

W języku Kotlin funkcja `filter` ma kilka wariantów, które pozwalają na różne sposoby filtrowania kolekcji. Oto kilka z tych wariantów:

1. **filter**: Funkcja `filter` zwraca nową kolekcję zawierającą elementy, które spełniają określone kryterium.
    
2. **filterTo**: Jak już wspomniano, funkcja `filterTo` filtruje kolekcję i dodaje spełniające kryterium elementy do określonej kolekcji docelowej, zamiast tworzyć nową kolekcję.
    
3. **filterIndexed**: Funkcja `filterIndexed` działa podobnie do zwykłej funkcji `filter`, ale dodaje indeks elementu jako argument do predykatu.
    
4. **filterIndexedTo**: Podobnie jak `filterTo`, ale również dostarcza indeks do funkcji predykatu i dodaje elementy spełniające kryterium do określonej kolekcji docelowej.
    
5. **filterNot**: Funkcja `filterNot` zwraca nową kolekcję zawierającą elementy, które nie spełniają określonego kryterium.
    
6. **filterNotNull**: Funkcja `filterNotNull` zwraca nową kolekcję, która zawiera wszystkie nie-null elementy oryginalnej kolekcji.


--------
## `map` do przekształcania kolekcji
#kotlin/map

>[!tip] `map`
>Funkcja `map` pobiera kolejno poszczególne elementy kolekcji i przekształca każdy z nich według określonego wzoru. 
>Funkcja ta ==zwraca kolekcję typu== `List` zawierającą efekt tych przekształceń.

```kotlin
val ints = listOf(1,2,3,4)  
val doubleInts = ints.map{it*2}  
println(doubleInts) // [2, 4, 6, 8]
```

`val groceryNames = groceries.map { it.name }` - To wywołanie tworzy nową kolekcję typu `List`i zapisuje w niej wartości właściwości name wszystkich obiektów `Grocery` z listy `groceries`.

INNE RODZAJA `map`
- `mapTo` (która dodaje wynik przekształcenia do istniejącej kolekcji), 
- `mapNotNull` (która pomija wartości null) oraz
- `mapValues` (która operuje na kolekcji Map i ją zwraca). Więcej informacji o nich można znaleźć na stronie:

## wywołania funkcji można łączyć

```kotlin
val newPrices = groceries.filter { it.unitPrice > 14.0 }	
				.map { it.unitPrice * 2 }
```
Ta instrukcja najpierw wywołuje funkcję `filter`, a następnie funkcję `map` na rzecz listy zwróconej przez pierwsze wywołanie.


### `forEach`
#kotlin/forEach
Funkcji `forEach` można używać do operowania na tablicach, kolekcjach `List`, `Set` oraz właściwościach `entries`. `key`, `values` kolekcji `Map`.

`groceries.forEach{println(it.name)}`

można `forEach` używać w łańcuchach wywołań:
```kotlin
groceries.filter { it.unitPrice > 14.0 }
		 .forEach { println(it.name) }
```
ALE `forEach` ZWRACA `Unit`, więc nie można tego wyniku używać do jakiś obliczeń

DOMKNIĘCIE
#kotlin/closure 
```kotlin
var itemNames = ””
groceries.forEach({ itemNames += ”${it.name} ” }) // domknięcie lambdy przechwyciło zmienną `itemsNames`
println(”itemNames: $itemNames”)

```

>[!tip] domknięcie
>> Domknięcie oznacza, że wyrażenie lambda ma dostęp do zmiennych lokalnych, które przechwytuje.


---
## `groupBy`
#kotlin/groupBy
aby podzielić kolekcję na grupy.

>[!danger] ważne
>Zwróć uwagę, że funkcji groupBy nie można używać bezpośrednio do operowania na kolekcjach typu Map; niemniej jednak można jej używać do operowania na kolekcjach zwracanych przez właściwości keys, values oraz entries.

`groupBy` - pozwala na grupowanie elementów kolekcji na podstawie podanego kryterium, takiego jak wartość właściwości. Można by jej użyć (w połączeniu z wywołaniami innych funkcji) na przykład do wyświetlenia nazw produktów z kolekcji `groceries` pogrupowanych według wartości właściwości`category`:


> `val groupByCategory = groceries.groupBy {it.category}` „Pogrupuj wszystkie elementy kolekcji `groceries` na podstawie wartości właściwości `category`”.

==ZWRACA==:
kolekcję typu `Map`:
- **klucze**: wartości kryterium przekazanego do funkcji w formie wyrażenia lambda
- **wartości** kolekcje typypu `List` zawierające elementy pierwotnej kolekcji
```kotlin
println("groupBY category: ${groceries.groupBy { it.category} }")

// groupBY category: {Warzywa=[Grocery(name=Pomidory, category=Warzywa, unit=kg, unitPrice=10.0, quantity=3), Grocery(name=Grzyby, category=Warzywa, unit=kg, unitPrice=12.0, quantity=1)], Wypieki=[Grocery(name=Obwarzanki, category=Wypieki, unit=Opakowanie, unitPrice=3.5, quantity=2)], Spiżarka=[Grocery(name=Oliwa z oliwek, category=Spiżarka, unit=Butelka, unitPrice=19.0, quantity=1)], Mrożonki=[Grocery(name=Lody, category=Mrożonki, unit=Opakowanie, unitPrice=14.0, quantity=2)]}

```

```kotlin
groceries.groupBy { it.category} .forEach{  
println(it.key)  
it.value.forEach{println(" ${it.name}")}  
}
// Warzywa
//    Pomidory
//    Grzyby
// Wypieki
//   Obwarzanki
// Spiżarka
//   Oliwa z oliwek
// Mrożonki
//    Lody
```



----
## `fold`
#kotlin/fold 

>[!tip] reduce
>W przypadku funkcji `fold` określenie wartości początkowej jest konieczne. Ten parametr jest obowiązkowy i nie można go pominąć. 
>
>Jeśli jednak chcesz ==użyć pierwszego elementu kolekcji jako wartości początkowej==, to możesz to zrobić, stosując funkcję `reduce`. 
>Działa ona podobnie jak `fold`, z tym że podawanie wartości początkowej nie jest konieczne. Ta funkcja automatycznie używa pierwszego elementu kolekcji jako wartości początkowej


>[!tip] fold
>Funkcja `fold` może operować na wartościach właściwości:
>- `keys`, 
>- `values`, 
>- `entries` 
>
>kolekcji typu `Map`, lecz nie bezpośrednio na samej kolekcji.
> 
> Pozwala ona określić wartość początkową, a następnie wykonywać na niej jakieś operacje dla każdego elementu kolekcji.
> 
>> Można jej użyć na przykład do:
>> -  pomnożenia przez siebie wszystkich elementów listy `List<Int>` i zwrócenia wyniku,
>> - połączenia ze sobą nazw wszystkich produktów zapisanych na liście `List<Grocery>`, a wszystko to w jednym wierszu kodu.

```kotlin
val ints = listOf(1,2,3,4)  
val sumOfInts = ints.fold(0){ runningSum, item -> runningSum + item}  
println("sumOfInts=$sumOfInts") // sumOfInts=10
```
>[!success] anatomia `fold`
>- ==pierwszy== parametr funkcji `fold`  to wartość początkowa
>- ==drugim== parametrem jest wyrażenie lambda opisujące operację, jaką chcemy wykonać na wartości początkowej dla każdego elementu kolekcji:
	>>- `runningSum` jego typ określany jest na podstawie wartości początkowej,
	>>- `item` jest tego samego typu co elementy kolekcji,
	>>- Ciało przekazywanego wyrażenia lambda określa operację, którą chcemy wykonać dla każdego elementu kolekcji i której wynik zostanie następnie zapisany w pierwszym parametrze tego wyrażenia.

ILOCZYN
```kotlin
val ints = listOf(1,2,3,4)  
val iloczyn = ints.fold(1){ runningSum, item -> runningSum * item}  
println("sumOfInts=$iloczyn") // iloczyn=24
```

KONKATENACJA
```kotlin
val konkatenacja = groceries.fold(""){ string, item -> string + " " + item.name }  
println("konkatenacja=$konkatenacja") // konkatenacja= Pomidory Grzyby Obwarzanki Oliwa z oliwek Lody
```

ODEJMOWANIE
```kotlin
println("odejmowanie od wartości początkowej sumy wartości elementów=${groceries.fold(100.0){ change, item -> change - item.unitPrice * item.quantity }}") //odejmowanie od wartości początkowej sumy wartości elementów=4.0

```
To wyrażenie odejmuje od change iloczyn `(unitPrice * quantity)` dla każdego produktu na liście groceries.


-----------
>[!danger] Różnica między `List` i `Set` a `Map`
>- W niewidoczny sposób kolekcje `List` i `Set` dziedziczą zachowania po interfejsie `Collection`, 
>- który z kolei dziedziczy je po interfejsie `Iterable`. 
>Typ `Map` nie dziedziczy po żadnym z tych interfejsów. 
>Oznacza to, że `List` i `Set` są typu `Iterable`, 
>natomiast `Map` nie jest.

`fold`, `forEach`, `groupBy` zostały zaprojektowane do obsługi typów `Iterable`
`keys` (to jest `Set`), `values` (to jest `Set`), `entries`  (dziedziczy po `Collection`) są typu `Iterable`







