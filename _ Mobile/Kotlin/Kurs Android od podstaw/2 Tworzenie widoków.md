[[_ Kurs Android od podstaw]]

>[!definition] Activity
> - jest odpowiedzialne za wyświetlanie całego ekranu w aplikacji (teksty, przyciski, ....
> - jest odpowiedzialne za wchodzenie interakcji  z użytkownikiem
> - w momencie tworzenia widoku jest wywoływana metoda `onCreate` w jej wnętrzu umieszczamy elementy statyczne, które mają pojawić się 


## `setContent`
> to funkcja będąca połaczeniem między klasą `activity` a elementami wyświetlanymi


`setContent { Text(text="Witam w Androidzie")}` ten kod jest równoważny:
`setContent( content = { Text(text="Witam w Androidzie")})`
parameter `content` jest ostatnim parametrem, więc, można go napisać jak wyżej 


## tworzenie funkcji do wyświetlania elementów graficznych

takie specjalne funkcje zaczynają się z DUŻEJ litery z adnotacją `@Componsable` (trzeba do importować ją)

```kotlin
class MainActivity : ComponentActivity() {  
	override fun onCreate(savedInstanceState: Bundle?) {  
	super.onCreate(savedInstanceState)  
		setContent {  
			MyElement()  
	}  
	}  
  
	@Composable  
	fun MyElement() {  
		Text(text="Jestem tekstem z MyElement")  
	}  
}
```



# Layout
https://developer.android.com/reference/kotlin/androidx/compose/foundation/layout/package-summary.html

## column
```kotlin
class MainActivity : ComponentActivity() {  
override fun onCreate(savedInstanceState: Bundle?) {  
	super.onCreate(savedInstanceState)  
		setContent {  
		MyColumn()  
	}  
}  
  
@Composable  
fun MyColumn(){  
//Alignment: Start, End, Centerhirizontally  
//bez fillMaxSize() ustawienia dotyczą tylko samego tekstu  
// a nie całego ekrany  
//verticalArrangement - jest jak rozbudowany flex  
	Column(  
		modifier = Modifier.background(Color.Cyan).fillMaxSize(),  
		horizontalAlignment = Alignment.CenterHorizontally,  
		verticalArrangement = Arrangement.Center  
	  
	) {  
		Text(text="Jestem tekstem z MyElement")  
		Text(text="JDrugi element")  
		Text(text="Trzeci tekst")  
		}  
}
```


## row
```kotlin
@Composable  
fun MyRow(){  
Row(  
modifier = Modifier.fillMaxSize(),  
verticalAlignment = Alignment.CenterVertically, //Top,CenterVertically, Bottom  
horizontalArrangement = Arrangement.SpaceAround  
){  
  
Text(text="Jestem z MyElement")  
Text(text="JDrugi element")  
Text(text="Trzeci tekst")  
}  
}
```


## `modifier`
służy do modyfikacji elementów graficznych.
```kotlin
@Composable  
fun MyModifier(){  
Column(  
modifier = Modifier  
	.background(Color.Cyan)  
	// .fillMaxHeight()  
	// .fillMaxWidth()  
	.fillMaxSize()  
	// .height(100.dp)  
	// .width(100.dp)  
	//.size(height = 100.dp, width = 100.dp)  
	// .padding(top=50.dp, bottom=150.dp, start=15.dp, end=200.dp)  
	.padding(horizontal = 20.dp, vertical = 120.dp),  
	verticalArrangement = Arrangement.Center,  
	horizontalAlignment = Alignment.CenterHorizontally  
	){  
		Text(text="Jestem z MyElement super z MyModifier 123455667" )  
Text(  
text="Drugi element",  
modifier = Modifier  
.width(75.dp)  
.background(Color.Yellow, CircleShape)//RectanleShape, CircleShape, RoundedCornerShape(), CutCornerShape()  
.clip(CircleShape)  
.padding(10.dp)  
.rotate(45f)  
.border(width=2.dp,color=Color.Blue, shape=RoundedCornerShape(5.dp))  
)  
Text(  
text="wielokrotne dodawnie modifierów",  
modifier = Modifier  
.width(175.dp)  
.background(Color.Magenta)  
.padding(10.dp)  
.background(Color.LightGray)  
.padding(15.dp)  
.background(Color.Cyan)  
.rotate(45f) // obróci się tylko test bo jest na końcu  
.border(2.dp, Color.Red) // border też się obróci  
)  
  
}  
}
```
























