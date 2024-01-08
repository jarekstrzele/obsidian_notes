[[_ 0 Kotlin Rusz Głową]]

Zmienna jest jak kubek - można w niej coś umieścić.

Aby utworzyć zmienną, kompilator musi znać:
- nazwę
- typ
- modyfikowalność:
	- `var` można zmienić wartość zapisaną w zmiennej,
	- `val` referencja do obiektu pozostanie w tej zmiennej na zawsze i nie będzie mogła zostać zmieniona

Kompilator potrafi jednak wywnioskować typ zmiennej na podstawie wartości, jaką tej zmiennej przypiszemy.

`var x = 5` -> kompilator utworzy obiekt `Int` o wartości `5`,
czyli zmienna `x` przechowuje **referencję** do tego obiektu.

![[kotlin_referencja.excalidraw ]]


# TYPY PROSTE
## liczby całkowite:
- `Byte`
- `Short`
- `Int`
- `Long`

```kotlin
var smallNum: Short = 6
```

## zmiennoprzecinkowe
- `Float` - `var x = 123.5F`
- `Double` - `var x = 123.5`

## wartości logiczne
`true`
`false`

## znaki i łańcuchy
Char: `var letter = 'D'`
String:`var name = "Fido"`


# Konwersja
```kotlin
var x = 5
var z: Long = x.toLong()
```

`toByte()`
`toShort()`
`toInt()`
`toLong()`
`toFloat()`
`toDouble()`

> Próba zapisania dużej wartości w małej zmiennej jest jak próba przelania dużego kubka kawy do maleńkiej filiżanki. Część kawy zmieści się w filiżance, lecz część się wyleje.

-----
# tablica

```kotlin
var myArray = arrayOf(1,2,3)
println(myArray[0])
println(myArray.size)

myArray = arrayOf(10,20,30) // zmienna myArray będzie przechowywać referencję do nowej tablicy

var myArray2: Array<Byte> = arrayOf(1, 2, 3)

```

`val myArray = arrayOf(1,2,3)`
>Kiedy zmiennej zostanie przypisana referencja do tablicy, zmienna będzie ją zawierać już na zawsze. Jednak choć zmienna będzie zawierać referencję do tej samej tablicy, to nic nie stoi na przeszkodzie, by zawartość tablicy ulegała zmianom.
>…jednak zmienne w tablicy będziemy mogli zmieniać|

> Samą tablicę możemy modyfikować, choć zmienna została zadeklarowana z użyciem słowa kluczowego val.
> 
---
# Random 
```kotlin
println("${Math.random()}")
0.5301868452123193

println("${Math.random()}")
0.8473722267596359

println("${(Math.random()*10).toInt()}")
7

println("${(Math.random()*10).toInt()}")
9
```
 


