#android/intention 

[[_ Rusz Głową Android. Programowanie aplikacji]]

>[!info] intencja
>- to rodzaj komunikatu
>- zawsze, gdy chcemy uruchomić jedną aktywność z poziomu innej aktywności, musimy w tym celu użyć **intencji**
>- jeśli jedna aktywność chce uruchomić drugą, robi to, przesyłając do systemu Android odpowiednią intencję.
>

# Intencje jawne *explicit intent*

## przykład jawne intencji
`KlasaDocelowa::class.java` - jawnie informujemy system, którą klasę ma uruchiomić
```kotlin
val intent = Intent(this, KlasaDocelowa::class.java)
intent.putExtra( "message", value) // przysyłanie wartość przez klucz "message"
startActivity(intent) 
```
`this` informuje system, z jakiego obiektu pochodzi intencja.
`KlasaDocelowa::class.java` nazwa klasy aktywności, do której intencja jest skierowana.
`startActivity(intent)` uruchamia aktywność określoną w intencji


> Kiedy Android odbierze intencję, sprawdza, czy wszystko jest w porządku, po czym uruchamia aktywność. Jeśli aktywności nie uda się odnaleźć, zgłaszany jest wyjątek ActivityNotFoundException.

>[!definition] class reference
> - it is an object that represents the class itself
> - to obtain a class reference use `::class` syntax
> - the reference is an instance of the `KClass`
> 	- e.g.:
> 		- `SomeClass::class` provides a reference to the `SomeClass`
> 		- `SomeClass::class.java` provides the `Class`  object for the `SomeClass` class



# Intencje niejawne *implicit intent*
Jeżli chcemy wykonać okreśłoną czynność, kecz nie interesuje nas, która aktywność to zrobi, to możemy utworzyć intencję niejawną. W takim pr

















