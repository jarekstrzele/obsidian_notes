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


















