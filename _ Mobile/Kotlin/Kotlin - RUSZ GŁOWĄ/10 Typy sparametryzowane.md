#kotlin/generics 

[[_ 0 Kotlin Rusz Głową]]

>[!tip] np. `MutableList` bez parametrów
>- kolekcja przechowywałaby referencje do różnych typów obiektów,
> - Bez zastosowania **typów sparametryzowanych** nie byłoby możliwości zadeklarowania, jakiego typu obiekty kolekcja może zawierać,
> - z kolekcji byłby odczytywane jako obiekty typu `Any`
>

Stosując typy sparametryzowane, możemy zyskać pewność, że nasza kolekcja będzie zawierać jedynie obiekty odpowiedniego typu. Nie musimy martwić się, że ktoś zapisze obiekt typu `Pumpkin` w liście typu `MutableList<Duck>` albo że obiekt pobrany z tej listy będzie innego typu niż `Duck`.

 
>[!question] Jak zdefiniowny jest typ `MutableList`?
>- MutableList używa E jako zamiennika dla typu elementów, które chcemy przechowywać w kolekcji i z niej pobierać.
>uproszczona wersja:
```kotlin
interface MutableList<E>: List<E>, MutableCollection<E>{
	fun add(index: Int, element: E): Unit
	//...
}
```









