[[_ the complete Android Kotlin]]

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

















