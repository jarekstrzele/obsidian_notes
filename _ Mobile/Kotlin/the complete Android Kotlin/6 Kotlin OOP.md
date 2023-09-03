[[_ the complete Android Kotlin]]

---
[[#Constructor]]
[[#Inheritance]]
[[#Function overriding]]
[[#Abstract class]]
[[#Interfejs]]





-----
==class== is a group of similar entities (doesn't consume memory)

==object== is a instance of class (consumes memory):
- state (data of the object) `property`
- behaviour (action of the object) `method`
- identity (used internally by Java) 

```kotlin
class ClassName{
	private var name = somevalue
	protected var color = someValue
	internal var model = someValu

	fun methodName(){
	
	}
}
```

access modifiers (by default `public`):
- `private` means visible inside this class only (including all its members)
- `protected` is the same as `private` but is also visible in subclasses
- `internal` means that any client inside this module who sees the declaring class sees its internal members
- `public` means that any client who sees the declaring class sees its public members


CREATE an OBJECT
`var objectName = ClassName()`

*objectName* is the reference which holds the memory address of the ClassName object



## Naming convention
- Class Name: a noun, uppercase `String, Car, ...`
- function Name: a verb, lowercase `start(), actionPerformed(), ...`
- variable Name: lowercase `firstName, year, color, etc.`

KOTLIN:
- ==camelCasing== : `firstName`, `actionPerformed`
- ==casesensitive==

----
# Constructor

## primary Constructor
```kotlin
class Cars constructor(name: String, model: Int)
{
	init
	{
		println("My car is $name and its model is $model")
	}
	
}
```

## secondary Constructor
```kotlin
class Cars()
{
	var name:String? = null
	var model:Int? = null

	constructor() //empty constructor

	constructor(name:String, model:Int)
	{
		this.name = name
		this.model = model
	}
}
```

EXAMPLE
the files are in the same package `package com.example.oopkotlin `

 
`Cars.kt` (class file)
```kotlin
package com.example.oopkotlin  
  
class Cars {  
  
    // this syntax with `?` prevent the program for throwing up  
    // any errors, even if we forget to transfer value to the variables later    var name:String? = null  
    var model:Int? = null  
  
}
```


`file1.kt`
```kotlin
package com.example.oopkotlin  
  
fun main(){  
    var myCar = Cars()  
    myCar.name = "Ferrari"  
    myCar.model = 2021  
  
    println("My car ${myCar.name} and its model is ${myCar.model}")  
  
}
```



or PRIMARY CONSTRUCTOR
```kotlin
class MyCars constructor (var name:String, var model:Int){  
    init {  
        println("My car $name model $model")  
    }  
  
}
```

```kotlin
  
fun main(){  
  
    var myNewCar = MyCars("Fiat", 1977)  
    println("My car ${myNewCar.name} and its model is ${myNewCar.model}")  
  
}
```


SECOND CONSTRUCTOR
```kotlin
class MySecondaryConstructor {  
  
    var name: String? = null  
    var model: Int? = null  
  
    constructor()  
    constructor(name: String?, model: Int?) {  
        this.name = name  
        this.model = model  
    }  
  
  
}
```

```kotlin
fun main(){  
  
    var mySecCar = MySecondaryConstructor("Trubo Ferarr", 2000)  
    mySecCar.model = 2100  
    println("My car ${mySecCar.name} and its model is ${mySecCar.model}")  
  
}
```

-----
## encapsulation

```kotlin
class MySecondaryConstructor {  
  
    var name: String? = null 
	var model: Int? = null  
	    private set    
	    get
```


----
# Inheritance
- **Klasy** i **methody** domyślnie są `final`, więc nie moga być dziedziczone
- aby umożliwić dziedziczenie 
```kotlin
open class ClassName {

}
```

```kotlin
open class Vehicle {
    // Implementacja klasy Vehicle
}

class SpaceShip : Vehicle {
    // Implementacja klasy SpaceShip
}

class SpaceShipWithConstructor : Vehicle() {
    // Implementacja klasy SpaceShipWithConstructor
}
```

klasa `SpaceShip` dziedziczy po klasie `Vehicle` bez wywoływania konstruktora klasy bazowej. Oznacza to, że klasa `SpaceShip` nie inicjalizuje żadnych właściwości lub stanu klasy `Vehicle` w swoim konstruktorze.


--------
# Function overriding
functions must have
	- same name
	- same parameter
	- same return type

```kotlin
open class Vehicle {
	open fun stop() {
		print("Vehicle has stopped")
	}
}

class Car : Vehicle() {

	override fun stop() {
		print("Car has stoppted")
	}
}
```


### example
create NEW PACKAGE

`Vehicle.kt`
```kotlin
package com.example.oopkotlin.overriding  
  
open class Vehicle {  
  
    open fun start(){  
        println("Vehicle has startted")  
    }  
  
    open fun accelerate(speed:Int){  
        println("Vehicle accelerates at $speed")  
    }  
  
    open fun stop() {  
        println("Vehicle has stopped")  
    }  
}
```

`Car.kt`
```kotlin
package com.example.oopkotlin.overriding  
  
class Car : Vehicle() {  
  
    fun superStop() {  
        // super -> access to Vehicle class  
        super.stop()  
    }  
  
    override fun start(){  
        println("Car has startted")  
    }  
  
    override fun accelerate(speed:Int){  
        println("Car accelerates at $speed")  
    }  
  
    override fun stop() {  
        println("Car has stopped")  
    }  
}
```

`OverridTest.kt`
```kotlin
package com.example.oopkotlin.overriding  
  
fun main() {  
  
    var v = Vehicle()  
    v.start()  
    v.accelerate(100)  
    v.stop()  
  
    println("------------------")  
    var c = Car()  
    c.start()  
    c.accelerate(100)  
    c.stop()  
    c.superStop()  
}
```



----
# Abstract class
#kotlin/abstract

**abstract class** you wouldn't be able to create any objects using it
**abstract method** contains no body

```kotlin
abstract class Vehicle
{
	abstract fun getMaxSpeed()
}

class Car: Vehicle()
{
	override fun getMaxSpeed(){
		// function body
	}
}
```


create a new package
`Vehicle.kt`
```kotlin
package com.example.oopkotlin.abstract  
  
abstract class Vehicle {  
  
	abstract fun vehicleName(name: String) :String  
  
    fun vehicleType(type:String) : String  
    {  
        return type  
    }  
  
    abstract var model: Int  
    var speed: Int? = null  
}
```

`Car.kt`
```kotlin
package com.example.oopkotlin.abstract  
  
class Car(override var model: Int) : Vehicle() {  
    override fun vehicleName(name: String): String {  
        return name  
    }  
  
}
```

`AbstractTest.tk`
```kotlin
package com.example.oopkotlin.abstract  
  
fun main() {  
  
    var car = Car(2022)  
    car.speed = 300  
    println("Name: ${car.vehicleName("ferrari")}\n"+  
            "Type : ${car.vehicleType("Car")}\n" +  
            "Model : ${car.model}\n" +  
            "Spped : ${car.speed}"  
    )  
  
}
```


--------
# Interfejs
#kotlin/interface

**interfaces** 
- are custom types provided by common
- define a form of behaviour
- contain definitions of properties and methods that the concrete types must have

In Kotlin class can in inherit only one class
```kotlin
interface InterfaceName
{
	//......
}
```


`Cango.kt`
```kotlin
interface CanGo {  
    // fun go()  
    // or  
    fun go()  
    {  
        println("vehicle can go")  
    }  
  
    //property can't be initialize  
    val name:String  
  
  
}
```

`Canstop.kt`
```kotlin
interface CanStop {  
    fun stop()  
}
```

`Vehicle.kt`
```kotlin
class Vehicle: CanGo, CanStop  {  
    override val name: String  
        get() = "Ferrari"  
  
    override fun stop() {  
        println("Vehicle stop")  
    }  
}
```

`TestFile.kt`
```kotlin
fun main(){  
  
    var vehicle = Vehicle()  
  
    println("Name: ${vehicle.name}")  
    vehicle.go()  
    vehicle.stop()  
}
```




