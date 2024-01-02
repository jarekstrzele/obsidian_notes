#android/intention 

[[_ Rusz Głową Android. Programowanie aplikacji]]

>[!info] intencja
>- to rodzaj komunikatu
>- zawsze, gdy chcemy uruchomić jedną aktywność z poziomu innej aktywności, musimy w tym celu użyć **intencji**
>- jeśli jedna aktywność chce uruchomić drugą, robi to, przesyłając do systemu Android odpowiednią intencję.
>


```kotlin
val intent = Intent(this, KlasaDocelowa::class.java)

startActivity(intent) 
```
`this` informuje system, z jakiego obiektu pochodzi intencja.
`KlasaDocelowa::class.java` nazwa klasy aktywności, do której intencja jest skierowana.
`startActivity(intent)` uruchamia aktywność określoną w intencji



>[!definition] class reference
> - it is an object that represents the class itself
> - to obtain a class reference use `::class` syntax
> - the reference is an instance of the `KClass`
> 	- e.g.:
> 		- `SomeClass::class` provides a reference to the `SomeClass`
> 		- `SomeClass::class.java` provides the `Class`  object for the `SomeClass` class
