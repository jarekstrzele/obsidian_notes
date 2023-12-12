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























