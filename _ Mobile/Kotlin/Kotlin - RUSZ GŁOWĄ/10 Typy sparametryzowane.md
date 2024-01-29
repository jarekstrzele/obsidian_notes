#kotlin/generics 

[[_ 0 Kotlin Rusz Głową]]

>[!tip] np. `MutableList` bez parametrów
>- kolekcja przechowywałaby referencje do różnych typów obiektów,
> - Bez zastosowania **typów sparametryzowanych** nie byłoby możliwości zadeklarowania, jakiego typu obiekty kolekcja może zawierać,
> - z kolekcji byłby odczytywane jako obiekty typu `Any`
>

Stosując typy sparametryzowane, możemy zyskać pewność, że nasza kolekcja będzie zawierać jedynie obiekty odpowiedniego typu. Nie musimy martwić się, że ktoś zapisze obiekt typu `Pumpkin` w liście typu `MutableList<Duck>` albo że obiekt pobrany z tej listy będzie innego typu niż `Duck`.

 
>[!question] Jak zdefiniowny jest typ `MutableList`?
>- `MutableList` używa `E` jako zamiennika dla typu elementów, które chcemy przechowywać w kolekcji i z niej pobierać.
>- Kiedy tworzymy listę `MutableList`, używając w tym celu funkcji `mutableListOf`, system utworzy implementację tego interfejsu.
>uproszczona wersja:
```kotlin
interface MutableList<E>: List<E>, MutableCollection<E>{
	fun add(index: Int, element: E): Unit
	//...
}
```
> [!question] c.d.
> Innymi słowy, litera `E` jest zastępowana przez faktyczny typ (nazywany także parametrem typu), którego użyjemy podczas definiowania listy `MutableList`. I to właśnie dlatego funkcja `add` nie pozwoli nam dodać do listy żadnego obiektu, którego typ nie będzie zgodny z typem `E`.


**Generyczne klasy i interfejsy** — można tworzyć:
- instancje klasy generycznej,
- funkcje pobierające argumenty generyczne,
- funkcje zwracające wartości generyczne.

np:
```kotlin
class Contest<T: Pet> {

	val scores: MutableMap<T, Int> = mutableMapOf()

	fun addScore(t: T, score: Int = 0) { 
		if (score >= 0) scores.put(t, score)
	}

}
```
- klasa generyczna, w której `T` musi być typu `Pet` lub musi być jego typem pochodnym,
- właściwość `scores` będzie mapą typu `MutableMap`, z kluczami typu `T` i wartościami typu `Int`, gdzie `T` jest parametrem typu generycznego klasy `Contest`, przy czym może być typem `Pet` lub jego typem pochodnym.
- `addScore`  zapisuje obiekt zwierzaka oraz jego wynik w mapie `MutableMap`, o ile tylko uzyskany wynik będzie większy lub równy `0`.

```kotlin
fun getWinners(): MutableSet<T> { 
	val highScore = scores.values.max()
	val winners: MutableSet<T> = mutableSetOf()

	for ((t, score) in scores) {
		if (score == highScore) winners.add(t)
	}

	return winners
}
```

>[!danger] funkcja z własnym parameterm typu
>Jeśli chcemy zdefiniować funkcję, która ma swój własny parametr typu, to możemy to zrobić, deklarując parametr typu jako element definicji funkcji.
```kotlin
fun <T: Pet> listPet(t: T): MutableList<T>{
	println("tworzę i zwracam MutableList")
	return mytableListOf()
	
}
```
>[!danger] wywołanie takie funkcji
```kotlin
val catLIst = listPet<Cat>(Cat("Kocilla"))
//lub
val catList = listPet(Cat("Kocilla")) // kompliator wywnioskuje typ obiektu, na którym funkcja ma operować
```


KLASA GENERYCZNA Z metodą generyczną akceptującą `null`
```kotlin
class MyClass<T> { 
	fun myFun(): T?

}
```


KLASA GENERYCZNA Z WIĘKSZĄ ILOŚCIĄ PARAMETRÓW
```kotlin
class MyMap<K, V> {

// Kod klasy...

}
```

## retailer
> Użyjemy teraz stworzonej wcześniej hierarchii klas Pet do przygotowania hierarchii sprzedawców, którzy będą sprzedawali poszczególne rodzaje zwierzaków. W tym celu zdefiniujemy:
> -  interfejs `Retailer<T>` mający jedną funkcję — `sell(): T` — oraz trzy klasy konkretne implementujące ten interfejs:
>> - `CatRetailer` i `sell(): Cat`- sprzedaje jedynie obiekty typu `Cat`,
>> - `DogRetailer`  i `sell(): Dog`,
>> - `FishRetailer` i `sell(): Fish`.

```kotlin
interface Retailer<T>{
	fun sell(): T
}
```

```kotlin
class CatRetailer: Retailer<Cat>{
	override fun sell(): Cat {
		println("Sprzedaję kota.")
		return Cat("")
	}
}
val carR1 - CatRetailer()
val carR2: CatRetailer = CatRetailer()



class DogRetailer: Retailer<Dog>{
	override fun sell(): Dog {
		println("Sprzedaję psa.")
		return Dog("")
	}

class DogRetailer: Retailer<Fish>{
	override fun sell(): Fish {
		println("Sprzedaję psa.")
		return Fish("")
	}
}
```

>[!tip]
>A zatem zastosowanie typów sparametryzowanych oznacza, że możemy narzucić ograniczenia określające, jak klasa może posługiwać się swoimi typami, poprawiając przy tym spójność i niezawodność kodu

### polimorfizm
kod zadziała, bo klasy implementują interfejs `Retailer`
```kotlin
val dogRetailer: Retailer<Dog> = DogRetailer()
val catRetailer: Retailer<Cat> = CatRetailer()
```

ten kod nie zadziała:
```kotlin
val petRetailer: Retaier<Pet> = CatRetailer()
```

jednak:
> możemy zmodyfikować parametr typu w definicji interfejsu `Retailer` w taki sposób, by kontrolować, jakie typy obiektów będzie można zapisywać w zmiennej typu `Retailer<Pet>`.

#### `out` typ generyczny będzie kowariantny.

#kotlin/out #covariant 

>[!success] kowariantny
>Jeśłi typ sparametryzowany jest **kowariantny**, to w parametrze typo `T` będzie można używać typu pochodnego w miejscu typu bazowego.

```kotlin
interface Retailer<out T>{
	fun sell(): T
}
```
czyli
> Wprowadzenie powyższej zmiany oznacza, że teraz w zmiennej typu `Retailer<Pet>` będziemy mogli zapisywać obiekty typu `Retailer` operujące na obiektach klas pochodnych klasy `Pet`. A zatem teraz poniższy kod uda się już skompilować:
```kotlin
val petRetailer: Retailer<Pet> = CatRetailer()
```


>[!danger] ważne
>- parametr typu poprzedzony słowem kluczowym `out` może być używany w miejscu o charakterze „wyjścia”, czyli na przykład jako typ wyniku zwracanego przez funkcję. 
>- z drugiej strony takiego typu nie można używać w miejscu o charakterze „wejścia”; zatem funkcja nie może mieć parametrów typu kowariantnego.

na przykład
kolekcja List to `public interface List<out E> ... { ... }`
więc możemy przypisać listę obiektów `Cat` do listy obiektów `Pet`:
```kotlin
val catList: List<Cat> = listOf(Cat(""), Cat(""))
val petList: List<Pet> = catList
```













