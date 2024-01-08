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

---
# Pętle

>Trzeba zwrócić uwagę, że operator `..` tworzy zakres, który zawiera górną granicę (czyli drugą z podanych liczb). 
>Gdybyśmy chcieli utworzyć zakres, który nie zawiera tej górnej granicy, to operator `..` trzeba by zastąpić funkcją `until`. 

`for(x in 1..100) println(x)` od 1 do 100 włącznie
`for (x until 100) println` od 1 do 99 włącznie


```kotlin
for(x in 1..10) print("$x ")  
println()  
for(x in 10 downTo 1) print("$x ")  
println()  
for (x in 15 downTo 2 step 3) print("$x ")
```
 1 2 3 4 5 6 7 8 9 10 
10 9 8 7 6 5 4 3 2 1 
15 12 9 6 3 

```kotlin
val options = arrayOf("kamień", "papier", "nożyce")  
for (item in options) print("$item ")  
println()  
for(index in options.indices) print("$index ")  
println()  
for((index, item) in options.withIndex()) print("index=$index, item=$item")
```
kamień papier nożyce 
0 1 2 
index=0, item=kamieńindex=1, item=papierindex=2, item=nożyce


-------
# gra papier, kamień, nożyce

```kotlin

fun main() {  
    val options = arrayOf("kamień", "papier", "nożyce")  
    val gameChoice = getGameChoice(options)  
    val userChoice = getUserChoice(options)  
    println("komputer: $gameChoice, ty: $userChoice") //, wynik: ${getResult(gameChoice, userChoice)" )  
    println("wynik: ${getResult(gameChoice,userChoice)}")  
  
  
}  
  
fun getGameChoice(optionsParam: Array<String>) = optionsParam[(Math.random() * optionsParam.size).toInt()] 

fun getUserChoice(optionsParam: Array<String>) : String {  
    var isValideChoice = false  
    var userChoice = ""  
  
    while(!isValideChoice){  
        print("Wpisz jedną  z opcji:")  
        for(item in optionsParam) print(" $item")  
        println(".")  
  
        val userInput = readLine()  
        if (userInput != null && userInput in optionsParam){  
            isValideChoice = true  
            userChoice = userInput  
        }  
        if(!isValideChoice) println("Musisz wpisać jedną z dostępnych opcji.")  
    }  
  
    return userChoice  
}  
  
fun getResult(computerChoice: String, userChoice: String) : String {  
   return when{  
        computerChoice == userChoice -> "Remis"  
        (computerChoice =="papier" && userChoice == "nożyce") ||  
        (computerChoice=="nożyce" && userChoice=="kamień") ||  
        (computerChoice=="kamien" && userChoice=="papier") -> "Wygrałeś"  
        else -> "przegrałeś"  
    }  
}
```




















