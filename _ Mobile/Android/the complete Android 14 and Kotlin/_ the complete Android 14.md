#udemy #android #kotlin  #panjuta_denis

---------
OLDER (Android 12)
[[2 Getting ready with Android Studio]]
[[3 Kotlin fundamentals]]
[[4. OOP Kotlin]]

[[6 Age in Minute Calculator]]

---------------
Kotlin basics:
[[2. Rock, Paper, Scissors]]
[[3. Functions, Objects and Coffee Machine]]
[[4. Lists and Objects]]


JETPACKAGE
[[5. First Android App - Unit Converter]]











----
# Intro

`Empty View` is without xml


```kotlin
@Preview(showBackground = true)  
@Composable  
fun GreetingPreview() {  
	MyemptyviewTheme {  
	Greeting("Android")  
	}  
}
```
it allows to preview the UI without running the app (similar to xml layout)

>[!tip] Preview
> The preview function in Jetpack Compose allows developers to see a visual representation of composables without needing to run the app.


>[!tip] ACTIVITY
> - is what you see on your phone / a screen
> -  represents a single screen with a user interface. It's where various UI elements like buttons, textviews, etc., are placed.

```kotlin
setContent {  
	MyemptyviewTheme {  
		// A surface container using the 'background' color from the theme  
		Surface(  
			modifier = Modifier.fillMaxSize(),  
			color = MaterialTheme.colorScheme.background  
			) {  
			Greeting("Jarek")  
		}  
}
```

`Surface` - is the whole background of that activity
	`modifier = Modifier.fillMaxSize(), ` this surface should fill the entire screen
	 `color = MaterialTheme. ...` set the color
	 `Greeting()` execute this function

>[!tip] a COMPOSABLE
> - it is basically just an element that is something that you can see on the screen:
> 	- a container
> 	- some thing
> - Composables represent UI elements and can be nested within other composables.

```kotlin
  
@Composable  
fun Greeting(name: String, modifier: Modifier = Modifier) {  
	Text(  
		text = "Hello $name!",  
		modifier = modifier  
	)  
}
```

`Text()` - this code is just showing a text composable















