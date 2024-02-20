#kotlin 
[[_ the complete Android 14]]

# First code
```kotlin
class MainActivity : ComponentActivity() {  
override fun onCreate(savedInstanceState: Bundle?) {  
super.onCreate(savedInstanceState)  
setContent {  
MyShoppingListAPpTheme {  
// A surface container using the 'background' color from the theme  
Surface(  
modifier = Modifier.fillMaxSize(),  
color = MaterialTheme.colorScheme.background  
) {  
  Column(  
    modifier = Modifier.fillMaxSize(),  
    verticalArrangement = Arrangement.Center  
  ) {  
    Button(  
	    onClick = {},  
		modifier = Modifier.align((Alignment.CenterHorizontally))  
	){  
		Text(text="Add item")  
}  } } } } } } 
```

# `LazyColumn` 
#kotlin/lazycolumn
It only renders  the items visible  on the screen as users scroll












