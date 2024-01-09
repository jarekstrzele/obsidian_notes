#kotlin/class 
[[_ 0 Kotlin Rusz Głową]]

> Projektując z wykorzystaniem dziedziczenia, wspólny kod umieszcza się w jednej klasie, a inne, bardziej wyspecjalizowane klasy mogą po niej dziedziczyć. 
> W razie konieczności zmodyfikowania kodu trzeba to będzie zrobić tylko w jednym miejscu, a zmiany w zachowaniu zostaną uwzględnione we wszystkich klasach dziedziczących to zachowanie.


>[!info] klasa bazowa
>klasa zawierająca wspólny kod 

>[!info] klasa pochodna
>- klasa dziedzicząca z klasy bazowej
>- klasa pochodna może zawierać dodatkowe właściwości i funkcje, jak również **może przesłaniać składowe odziedziczone** po klasie bazowej
>

---
# Projektowanie hierarchii dziedziczenia

>używaj dziedziczenia, aby unikać powielania kodu w klasach pochodnych



1. **Przyjrzyj się** atrybutom i zachowaniom, które są **wspólne** dla wszystkich obiektów.

2. **Zaprojektuj klasę** bazową reprezentującą wspólne stany i zachowania
klasa bazowa `Animal`:
- właściwości:
	- `image`
	- `food`
	- `habitat` podstawowe środowisko
	- `hunger` poziom głodu
- metody:
	- `makeNoise()` wydawane odgłosy
	- `eat()` 
	- `roam()` co robi, gdy nie je i nie śpi
	- `sleep()`
klasy pochodne:
`Lion`
`Hippo`
`Lynnx`
`Fox`
`Wolf`
`Cheetah`

3. **Zdecyduj**, czy klasy pochodne mają mieć charakterystyczne dla siebie **domyślne wartości** właściwości oraz **implementacje** funkcji.
wszystkie klasy pochodne będą:
- miały swoje charakterystyczne wartości właściwości (oprócz `hunger`)
- własna implementacja `makeNoise()` oraz `eat()`


4. **Szukaj** okazji **do wyodrębniania właściwości i funkcji** poprzez znajdowanie dwóch lub większej liczby klas pochodnych mających wspólne cechy lub zachowania.
wśród klas pochodnych mamy
- 2 przedstawicieli rodziny PSOWATYCH `Canine`
- 3 przedstawicieli kotowatych `Feline`

5. Uzupełnij hierarchię klas.
nowa klasa `Feline`:
- ma własną implementację `roam()`
- klasy pochodne: `Lion`, `Cheetah`, `Lynnx`
now klasa `Canine`:
	- ma własną implementację `roam()`
	- klasy pochodne `Fox`, `Wolf`
klasa `Hippo` bez zmian, dziedziczy bezpośrednio z klasy `Animal`

>[!important] test JEST
>Czy stwierdzenie, że *typ X JEST typem Y* ma sens>?
>- Jeżeli tak, to być może mogą one wystąpić w tej samej hierarchii dziedziczenia
>- to jest test jednokierunkowy: *X jest Y*, ale *Y* nie jest *X*
>- przykład: *Czy hipopotam JEST zwierzęciem?* , tak, ale zwierzę nie musi być hipopotanem
>- działa w dowolnym miejscu drzewa dziedziczenia: A jest B, B jest C, więc też A jest C
>	- `Wolf` jest `Canine`, więc `Wolf` może zrobić wszystko to samo co Canine, 
>	- `Wolf` jest `Animal`, zatem może zrobić wszystko to samo co `Animal`
>

>[!important] test MA
>Czy stwierdzenie, że *typ X ma/zawiera typ Y* ma sens?
>- np. *Czy kuchnia ma lodówkę?*, tak, więc obiekt klasy `Kuchnia` zwiera referencję do obiektu klasy `Lodowka`, czyli klasa `Kuchnia` ma właściwość `Lodowka`

----------
# Klasy w Kotlinie
#kotlin/class 

Intellij: *Następnie utwórz plik Animals.kt; w tym celu zaznacz katalog `src` i wybierz z menu głównego opcję `File/New/Kotlin` `File/Class`. Następnie w wyświetlonym oknie dialogowym, w polu Name wpisz Animals, a z listy Kind wybierz opcję `File`.*

## klasa bazowa

>[!important] `open` - używanie klasy jako bazowej
>Aby można było używać klasy jako klasy bazowej, trzeba ją zadeklarować jako otworzoną. Wszystko, co chcemy przesłaniać, musi być poprzedzone słowem kluczowym `open`

```kotlin
open class Animal {  
    open val image = ""  
    open val food = ""  
    open val habitat = ""  
    var hunger = 10  // tej właściwości nie będziemy przesłaniać?
  
    open fun makeNoise(){  
        println("Zwierzę wydaje dźwięki,")  
    }  
    open fun eat() = println("Zwierzę je.")  
    open fun roam() = println("Zwierzę wałęsa się.")  
    fun sleep() = println("Zwierzę śpi.")  // tej metody nie będziemy przesłaniać?
}
```

## klasy pochodne
> jeśli klasa bazowa definiuje konstruktor podstawowy, to musimy wywołać go w nagłówku klasy pochodnej, gdyż w przeciwnym razie nie uda się skompilować kodu

```kotlin
class Hippo : Animal() {}
```
`: Animal()` wywołanie konstruktora klasy `Animal`

> jeśli konstruktor klasy bazowej zawiera parametry, to w jego wywołaniu musimy przekazać wartości tych parametrów
np.
```kotlin
open class Car(val make: String, val model:Sring){}

class ConvertibleCar(make_param: String, model_param: String) : Car(make_param, model_param)
```
>> Konstruktor klasy `ConvertibleCar` ma dwa parametry 
>> — `make_param` oraz `model_param`. Wartości tych parametrów są przekazywane w wywołaniu konstruktora klasy `Car`, który z kolei użyje ich do zainicjowania właściwości `make` i `model`.


### Jak i kiedy przesłaniać właściwości?

> Właściwości odziedziczone po klasie bazowej można przesłaniać poprzez dodanie ich do klasy pochodnej i poprzedzenie słowem kluczowym `override`.

```kotlin
class Hippo : Animal() {
	override val image = "hippo.jpg"
	override val food = "trawa"
	override val habitat = "woda"
}
```
>[!danger]
>jeśli w klasie bazowej zdefiniujemy właściwości, używając słowa kluczowego `val`, i jeśli w klasie pochodnej chcemy przypisać im inne wartości, to musimy przesłonić je w klasie pochodnej.
>
> Jeśli natomiast właściwości klasy bazowej zostały zdefiniowane z użyciem słowa kluczowego var, to nie musimy ich przesłaniać, gdyż zmienne zdefiniowane z użyciem var można aktualizować.
```kotlin
open class Animal {
	var image = ""
	//....
}

class Hippo : Animal(){
	init {
		image = "hippo.jpg"
	}
}
```

==przesłanianie==, aby:
- określanie innych wartości niż w klasie bazowej,
- zmieniania akcesorów `get` i `set`,
- właściwość z `val` z klasy bazowej zamienić na `var` (nie działa z `var` -na-> `val` ),
- zmienić typ właściwości z klasy bazowej na inny lecz pochodny względem typu bazowego


### Jak przesłaniać funkcje?

> Funkcje przesłaniamy w podobny sposób jak właściwości: 
> 	- dodając je do klasy pochodnej i 
> 	- poprzedzając słowem kluczowym `override`.

```kotlin
class Animal {
	// ...
	open fun makeNoise(){
	//..
	}

	open fun eat(){
		///
	}
	
}

class Hippo: Animal(){
	//...

	override fun makeNoise() {
		println("Hrummm!)
	}
	override fun eat(){
		println("Główne pożywienie to $food")
	}

}


```

> [!imporant] REGUŁY PRZESŁANIANIA FUNKCJI:
> - parametry funkcji w klasie pochodnej muszą odpowiadać parametrom funkcji w klasie bazowej,
> - typy wartości zwracanych przez funkcje muszą być zgodne, czyli takie same lub pochodne

> - jeśli chcemy przesłonić funkcję lub właściwość, to w klasie bazowej musimy zadeklarować ją jako otworzoną, używając słowa kluczowego `open`. 
> - takie funkcje lub właściwości **pozostają otworzone we wszystkich klasach pochodnych** i to nawet jeśli zostaną przesłonięte; dzięki temu w kolejnych klasach pochodnych nie musimy ponownie deklarować ich jako otworzonych.

```kotlin
open class Vehicle {
	open fun lowerTemp() {
		//...
	}
}

open class Car: Vehicle(){
	override fun lowerTemp() {
		//...
	}
}

class ConvertibleCar: Car(){
	override fun lowerTemp(){
		//...
	}

}
```

ALE użycie `final` będzie oznaczać, że w klasach pochodnych nie będzie można jej przesłaniać.
```kotlin
open class Car : Vehicle(){
	final override fun lowerTemp() {
		//...
	}
}
```


>[!important] kolejność wywołania
>Kiedy wywołujemy funkcję, używając w tym celu referencji do obiektu, wywołujemy najbardziej precyzyjnie określoną wersję funkcji istniejącą dla danego typu obiektu: czyli ==funkcję znajdującą się najniżej w drzewie dziedziczenia==.

*przykład*
> Na przykład jeśli wywołamy funkcję na rzecz obiektu klasy Wolf, to system w pierwszej kolejności postara się znaleźć ją w samej klasie Wolf. Jeśli uda się znaleźć funkcję w tej klasie, to zostanie ona wykonana. Jeżeli jednak nie uda się znaleźć funkcji w klasie Wolf, to system przejdzie w górę drzewa dziedziczenia, czyli do klasy Canine. Jeśli funkcja została w niej zdefiniowana, to system ją wykona, jeśli nie — przejdzie do następnej klasy położonej wyżej w drzewie dziedziczenia. System kontynuuje to sprawdzanie kolejnych klas aż do momentu znalezienia funkcji.


>[!danger] gwarancja z dziedziczenia
>Dziedziczenie gwarantuje, że wszystkie klasy pochodne będą mieć właściwości i funkcje zdefiniowane w klasie bazowej
>	
>	Na przykład *dla wszystkich typów pochodnych zwierząt klasa Animal tworzy wspólny protokół, który stwierdza: „Zwierzę ma właściwości o nazwach image, food, habitat i hunger oraz funkcje: makeNoise, roam, eat oraz sleep”*


### Typy bazowa - Typy pochodne

>[!important] klasa pochodna -> klasa bazowa
>Wszędzie, gdzie możemy użyć klasy bazowej, możemy także użyć dowolnej z jej klas pochodnych
`val animal : Animal = Wolf()`, bo *Wolf* JEST *Animal*

>[!danger] DenDŻER
>Jeśli zmienna typu Animal wskazuje na obiekt typu Wolf, to wywołanie jej funkcji eat() sprawi, że zostanie wykonana funkcja zdefiniowana w klasie Wolf.
```kotlin
val animal : Animal = Wolf()
animal.eat() // --> zostanie wykonana metoda zdefiniowana w klasie `Wolf`
```

```kotlin
val animals = arrayOf(
	Hippo(),
	Wolf(),
	Lion(),
	Cheetah(),
	Lynx(),
	Fox()
)
```
Kompilator zauważy, że to wszystko są obiekty klas pochodnych klasy Animal, dlatego też utworzy tablicę typu `Array<Animal>`.

>[!important] typ bazowy w funkcji
>- jako parametr:
>	- typów bazowych można używać w parametrach funkcji 
>- jako typu zwracanego wyniku
```kotlin
class Vet {
	fun giveShot(animal: Animal){
		animal.makeNoise()
	}
}

val vet = Vet()
val wolf = Wolf()
val hippo = Hippo()
vet.giveShot(wolf)
vet.giveShot(hippo)

```

>[!definition] polimorfizm
>- Możliwość zastosowania obiektów jednego typu w miejscu, w którym jawnie są oczekiwane obiekty innego typu, jest nazywana polimorfizmem.
>- "wiele form" - różne klasy pochodne mogą mieć odmienne implementacje tej samej funkcji















