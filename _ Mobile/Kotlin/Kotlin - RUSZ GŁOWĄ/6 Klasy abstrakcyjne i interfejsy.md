#kotlin   #polimorfizm 
[[_ 0 Kotlin Rusz Głową]]
[[5 Klasy pochodne i bazowe]]

projekt zwierząt będzie przekształcany
```kotlin
open class Animal {  
    open val image = ""  
    open val food = ""  
    open val habitat = ""  
    var hunger = 10  
  
    open fun makeNoise(){  
        println("Zwierzę wydaje dźwięki,")  
    }  
    open fun eat() = println("Zwierzę je.")  
    open fun roam() = println("Zwierzę wałęsa się.")  
    fun sleep() = println("Zwierzę śpi.")  
}  
  
class Hippo : Animal(){  
    override val image = "hippo.jpg"  
    override val food = "trawa"  
    override val habitat = "woda"  
  
    override fun makeNoise(){  
        println("Hrum! Hrum")  
    }  
  
    override fun eat(){  
        println("Pożywienie to $food")  
    }  
}  
  
open class Canine : Animal(){  
    override fun roam(){  
        println("Psowate wałęsają się")  
    }  
}  
  
class Wolf : Canine(){  
    override val image = "wolf.jpg"  
    override val food = "mięso"  
    override val habitat = "lasy"  
  
    override fun makeNoise() {  
        //super.makeNoise()  
        println("Auuu")  
    }  
  
    override fun eat(){  
        println("główne pożywienie to $food")  
    }  
}  
  
class Vet {  
    fun giveShot(animal: Animal){  
        animal.makeNoise()  
    }  
}  
  
fun main(args: Array<String>){  
    val animals = arrayOf(Hippo(), Wolf())  
    for(item in animals){  
        item.roam()  
        item.eat()  
    }  
  
    val vet = Vet()  
    val wolf = Wolf()  
    val hippo = Hippo()  
    vet.giveShot(wolf)  
    vet.giveShot(hippo)  
}
```

-----------
# Klasa abstrakcyjna

> Wiemy, jak wyglądają obiekty `Wolf`, `Hippo` czy `Fox`; ale jak miałby wyglądać obiekt `Animal`? Czy może ma futro? Czym się żywi, jak spędza czas, gdy nie śpi ani nie szuka pożywienia?

```kotlin
abstract class Animal {

}
```

#kotlin/abstract_class 
>[!imporant] KLASA ABSTRAKCYJNA
> - Jeśli klasa bazowa zostanie oznaczona jako abstrakcyjna, nie trzeba deklarować jej jako otworzonej `open`
> - Ogólnie rzecz biorąc, to, czy jakaś klasa będzie abstrakcyjna czy konkretna, zależy od kontekstu aplikacji.
> - Klasa abstrakcyjna może zawierać
> 	- abstrakcyjne i nieabstrakcyjne właściwości i funkcje.
> 	- Nic nie stoi na przeszkodzie, by klasa abstrakcyjna nie zawierała żadnych składowych abstrakcyjnych.
> - Jeżeli w klasie umieścisz choćby jedną właściwość lub funkcję abstrakcyjną, to także klasę będziesz musiał oznaczyć jako abstrakcyjną.

==Właściwości i funkcji abstrakcyjnych nie trzeba oznaczać jako otworzonych `open`.==

```kotlin
abstract class Animal {
	abstract val image: String
	abstract val food: String
	abstract val habitat: String
	var hunger = 10
}
```
>[!info] właściwość abstrakcyjna
>oznaczając właściwość jako abstrakcyjną, uznajemy, że nie ma żadnej sensownej wartości początkowej, którą można by jej przypisać, ani żadnych sensownych implementacji akcesorów `get` i `set`.

```kotlin
abstract class Animal {

	abstract fun makeNoise()
	abstract fun eat()
	
	open fun roam(){
		println("Zwierzę wałęsa się.")
	}
	open fun sleep(){
		println("Zwierzę śpi.")
	}
}
```

`abstract fun makeNoise(){}` --> kodu  nie da się skompilować
`abstract fun makeNoise()` --> ten kod się skompiluje













