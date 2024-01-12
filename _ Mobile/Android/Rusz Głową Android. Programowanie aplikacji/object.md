#kotlin/object 

>[!info] `object`
>słowo kluczowe `object` może być używane w kilku różnych kontekstach:

## singleton
Obiekt taki ma tylko jedną instancję i jest dostępny globalnie.
```kotlin
object MySingleton {
     fun doSomething() {
        println("Doing something...")
    }
}
```

## instancja anonimowej klasy
tworzy jednorazową instancję anonimowej klasy implementującej interfejs lub rozszerzającej klasę abstrakcyjną.
```kotlin
val myRunnable: Runnable = object : Runnable {
    override fun run() {
        println("Running...")
    }
}

```

## `companion object` 
> Wewnątrz klasy, `object` może być używane jako `companion object`, co oznacza, że jest to obiekt towarzyszący danej klasy. Jest to rodzaj obiektu, który jest związany z klasą, a nie z instancją tej klasy.

```kotlin
class MyClass {
    companion object {
        fun doSomething() {
            println("Doing something in companion object...")
        }
    }
}

```

....










