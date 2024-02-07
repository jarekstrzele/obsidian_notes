#udemy #android #kotlin  #panjuta_denis

---------
OLDER (Android 12)
[[2 Getting ready with Android Studio]]
[[3 Kotlin fundamentals]]
[[4. OOP Kotlin]]

[[6 Age in Minute Calculator]]

---------
# intro
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

ACTIVITY - is what you see on your phone / a screen

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

`Surface` - is the whole background




