[[_ 0 Kotlin Rusz Głową]]

#kotlin/class

# Klasa

>[!info] klasy
>Klasy są wzorcami pozwalającymi na tworzenie własnych typów obiektów i definiowanie ich właściwości oraz funkcji.

==typy obiektowe są definiowane przy użyciu klas==

>:Słowa kluczowego `lateinit` można używać wyłącznie z właściwościami zdefiniowanymi z użyciem słowa kluczowego `var`, przy czym nie mogą to być właściwości następujących typów: 
>- `Byte`,  `Short`, `Int`,`Long`, 
>- `Float`, `Double`, 
>- `Char` 
>- `Boolean`. 
>- Ograniczenie to wiąże się ze sposobem obsługi tych typów danych w JVM. Oznacza to, że właściwości wymienionych typów muszą być inicjowane w momencie definiowania bądź też wewnątrz bloku inicjalizatora.

# obiekt

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


# Konstruktor

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

## Bloki inicjalizatora
#kotlin/init 

> [!info] Bloki inicjalizatora 
> są wykonywane 
> 	-  podczas inicjalizacji obiektu,
> 	-  bezpośrednio po wywołaniu jego konstruktora, 
> a w kodzie klasy definiuje się je, poprzedzając blok kodu słowem kluczowym `init`.
> 
> Klasa może zawierać więcej niż jeden blok inicjalizatora.















