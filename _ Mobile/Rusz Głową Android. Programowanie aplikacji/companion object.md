#kotlin/companion_object

>  
W języku Kotlin `companion object` to specjalny blok wewnątrz klasy, który pozwala na definiowanie funkcji i właściwości, które są powiązane z samą klasą, a nie z instancjami tej klasy. Jest to odpowiednik statycznych pól i metod w języku Java, ale z bardziej ekspresywną składnią i możliwościami


Oto kilka kluczowych aspektów związanych z `companion object`:

1. **Statyczność:**
    - `companion object` działa jako kontener na elementy, które mają być statyczne w kontekście danej klasy.
    - Elementy te są dostępne bez potrzeby tworzenia instancji klasy.
2. **Dostęp do elementów:**
    - Można uzyskać dostęp do elementów `companion object` bezpośrednio za pomocą nazwy klasy, podobnie jak w przypadku wywoływania statycznych pól i metod w Javie.
```kotlin
MyClass.Companion.myFunction() 
MyClass.myFunction() // Skrócona forma, gdy Companion nie jest nadany`
```

3. **Właściwości i funkcje:**
    - Wewnątrz `companion object` możesz definiować zarówno właściwości (*properties*) jak i funkcje.
    - Działa to podobnie jak dla innych obiektów, z tą różnicą, że elementy są dostępne bezpośrednio na poziomie klasy.
```kotlin
class MyClass {
    companion object {
        val myProperty: Int = 42
        fun myFunction() {
            // ...
        }
    }
}

```

4. **Domyślne nazwy:**    
    - Jeśli nie nadasz nazwy dla `companion object`, Kotlin dostarczy domyślną nazwę `Companion`.
    - Możesz jednak nadawać mu własne nazwy.
```kotlin
    class MyClass {
	    companion object MyCompanion {
        // ...
    }
}
```

Dzięki `companion object` w Kotlinie, możesz grupować funkcje i właściwości, które są powiązane z daną klasą, a jednocześnie są dostępne bez tworzenia instancji tej klasy. To sprawia, że kod staje się bardziej zorganizowany i czytelny.




