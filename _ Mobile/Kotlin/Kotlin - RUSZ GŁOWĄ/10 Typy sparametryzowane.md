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






