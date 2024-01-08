[[_ 0 Kotlin Rusz Głową]]

#kotlin/class

>[!info] klasy
>Klasy są wzorcami pozwalającymi na tworzenie własnych typów obiektów i definiowanie ich właściwości oraz funkcji.

==typu obiektowe są definiowane przy użyciu klas==


>[!info] obiekt
>- ==właściwości==:
>	- to, co obiekt wie na swój temat
>	- reprezentują stan obiektu (dane)
>- ==funkcje składowe== / ==metody==:
>	- czynności, które obiekt potrafi wykonywać
>	- mogą korzystać z właściwości
>- TWORZENIE OBIEKTU `var obj = MojaKlasa()`:
>	- tworzenie zmiennej `obj`
>	- tworzenie obiektu `MojaKlasa()`
>	- połączenie obiektu ze zmienną, która przechowuje referencję do obiektu


>[!inf] konstruktor
>Konstruktor jest wykonywany podczas tworzenia obiektu. 
>Jest on używany do zdefiniowania
>	-  właściwości obiektu oraz
>	-  określenia ich wartości.


```kotlin
fun main() {  
  
    val reksio = Dog("Reksio", 3, "mieszaniec")  
    reksio.bark()  
    val dogsList = arrayOf(  
        Dog("Burek", 6, "dog niemiecki"),  
        Dog(name="Rufus", age=10, breed="owczarek podchalański")  
    )  
    dogsList[0].bark()  
    dogsList[1].bark()  
}  
  
class Dog(val name: String, val age: Int, val breed: String ){  
  
    fun bark() = println(if (age < 6) "hał" else "HAŁHAŁ")  
}
```









