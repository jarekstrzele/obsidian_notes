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

access modifiers:
- `private` means visible inside this class only (including all its members)
- `protected` is the same as `private` but is also visible in subclasses
- `internal` 


CREATE an OBJECT
`var objectName = ClassName()`

*objectName* is the reference which holds the memory address of the ClassName object







