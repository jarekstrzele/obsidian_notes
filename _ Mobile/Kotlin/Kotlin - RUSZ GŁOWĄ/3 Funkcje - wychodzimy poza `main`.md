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


> kompilator gwarantuje bowiem, że funkcja zawsze będzie wywoływana z argumentami odpowiadającymi zadeklarowanym parametrom, a argumenty są automatycznie przypisywane do tych parametrów.

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


zmiana wartości tablicy w funkcji:
```kotlin
fun main() {  
    val options = arrayOf("kamień", "papier", "nożyce")  
    var newValue = options[0]  
    newValue = "nowa wartość"  
  
    println(options.joinToString(separator = " ", prefix = "[", postfix = "]")) //nie zmienia wartości [kamień papier nożyce]  
    
    changeValue(0, options)  
    
    println(options.joinToString(separator = " ", prefix = "[", postfix = "]"))  // zmienia wartość [PPP papier nożyce]

}  
  
  
fun changeValue(index: Int, myArray: Array<String>) {  
    myArray[index] = "PPP"  
}
```



