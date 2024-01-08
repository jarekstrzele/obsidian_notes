[[_ 0 Kotlin Rusz Głową]]

#kotlin/class

>[!info] klasy
>Klasy są wzorcami pozwalającymi na tworzenie własnych typów obiektów i definiowanie ich właściwości oraz funkcji.

==typu obiektowe są definiowane przy użyciu klas==


>[!info] obiekt
>- ==właściwości==:
>	- to, co obiekt wie na swój temat
>	- reprezentują stan obiektu (dane)
>	- jest zmienną lokalną dostępną w obiekcie
>- ==funkcje składowe== / ==metody==:
>	- czynności, które obiekt potrafi wykonywać
>	- mogą korzystać z właściwości
>- TWORZENIE OBIEKTU `var obj = MojaKlasa()`:
>	- tworzenie zmiennej `obj`
>	- tworzenie obiektu `MojaKlasa()`
>	- połączenie obiektu ze zmienną, która przechowuje referencję do obiektu
>- miejsce w pamięci dla obiektu przypisuje system
>- Każdą właściwość obiektu trzeba zainicjować, zanim będzie można jej użyć.


>[!inf] konstruktor
>Konstruktor jest wykonywany podczas tworzenia obiektu. 
>Jest on używany do zdefiniowania
>	-  właściwości obiektu oraz
>	-  określenia ich wartości.
>`class Dog(val name: String, val age: Int, val breed: String ){  }`
>*(val name: String, val age: Int, val breed: String )* to podstawowy konstruktor  
>
>Konstruktor jedynie inicjuje obiekt, więc upewnia się, czy zostały utworzone jego właściwości i czy zostały im przypisane wartości początkowe. Za zarządzanie pamięcią w całości odpowiada system.




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

**Konstruktor** klasy `Dog` definiuje trzy właściwości — `name`, `age` oraz `breed`. Każdy obiekt `Dog` będzie zawierać te trzy właściwości, a podczas jego tworzenia konstruktor określi ich wartości.

KOD (właściwości zdefiniowane wewnątrz konstruktora)
```kotlin
class Dog(val name: String, val age: Int){}
```
JEST RÓWNOWAŻNY (właściwości zdefiniowane w ciele klasy):
```kotlin
class Dog(name: String, age: Int){
	val name = name
	val age = age
}
```

ten drugi sposób jest bardzej elastyczny:
```kotlin
class Dog(val name: String, age_param: Int,, breed_param: String){
	var activities = arrayOf("spaceruje)
	var age = age_param
	val breed = breed_param.toUpperCase()
}

val reksio = Dog("Reks", 10, "owczarek podhalański")
```


