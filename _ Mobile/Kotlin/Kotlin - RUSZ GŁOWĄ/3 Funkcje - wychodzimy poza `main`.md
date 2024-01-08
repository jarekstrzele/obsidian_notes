[[_ 0 Kotlin Rusz Głową]]


>[!info] Argumenty 
>To, co przekazujemy do funkcji. 
>Argument (czyli wartość taka jak 2 lub ”Pizza”) ląduje prosto w parametrze. 
>


>[!info] Parametr 
>To nic innego jak ==zmienna lokalna==: 
>zmienna mająca 
>	- swoją nazwę i 
>	- typ, 
>	- używana wewnątrz ciała funkcji.

```kotlin
//funkcja zwraca Int
fun printSum(int1: Int, int2: Int) : Int{

	val result = int1 + int2 
	
	return result

}

// funkcja nic nie zwraca Unit
fun printSum(int1: Int, int2: Int): Unit {
	val result = int1 + int2 
	println(result)
}


```

gdy ciałem funkcji jest JEDNO WYRAŻENIE
```kotlin
fun max(a: Int, b: Int): Int {
	val maxValue = if (a > b) a else b
	return maxValue 
}
```
można kod uprościć
```kotlin
fun max(a: Int, b: Int): Int = if (a > b) a else b
```
a nawet (bo kompilator domyśli się typu zwracanego)
```kotlin
fun max(a: Int, b: Int) = if (a > b) a else b
```





