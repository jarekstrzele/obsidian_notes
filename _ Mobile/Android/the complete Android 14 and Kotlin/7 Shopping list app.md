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

```kotlin
//..
) { 
//add shoping list state
var shoppingItems by remember { mutableStateOf( listOf<ShoppingItem>() ) }  
Column(  
modifier = Modifier.fillMaxSize(),  
verticalArrangement = Arrangement.Center //...


Button(  
  onClick = {},  
  modifier =  Modifier.align((Alignment.CenterHorizontally))  
){  
  Text(text="Add item")  
} 
// ADD LAZYCOLUMN
  LazyColumn(  
		modifier = Modifier  
			.fillMaxSize()  
			.padding(16.dp)  
){  
	items(shoppingItems){  
  
	}  
}
  //....

// outside
data class ShoppingItem(
	val id: Int,
	var name: String,
	var quantity: Int,
	var isEditing: Boolean=false)
```

## Create new file
create a new file (simple file, not class file) `Shoppinglist.kt`
```kotlin
package com.js.myshoppinglistapp  
  
import androidx.compose.foundation.layout.Arrangement  
import androidx.compose.foundation.layout.Column  
import androidx.compose.foundation.layout.fillMaxSize  
import androidx.compose.foundation.layout.padding  
import androidx.compose.foundation.lazy.LazyColumn  
import androidx.compose.foundation.lazy.items  
import androidx.compose.material3.Button  
import androidx.compose.material3.Text  
import androidx.compose.runtime.Composable  
import androidx.compose.runtime.getValue  
import androidx.compose.runtime.mutableStateOf  
import androidx.compose.runtime.remember  
import androidx.compose.runtime.setValue  
import androidx.compose.ui.Alignment  
import androidx.compose.ui.Modifier  
import androidx.compose.ui.unit.dp  
  
data class ShoppingItem(val id: Int, var name: String, var quantity: Int, var isEditing: Boolean=false)  
  
@Composable  
fun ShoppingListApp(){  
  var shoppingItems by remember { mutableStateOf( listOf<ShoppingItem>() ) }  

  Column(  
    modifier = Modifier.fillMaxSize(),  
    verticalArrangement = Arrangement.Center  
  ) {  
  Button(  
    onClick = {},  
    modifier =    Modifier.align((Alignment.CenterHorizontally))  
){  
      Text(text="Add item")  
}  
  LazyColumn(  
    modifier = Modifier  
			    .fillMaxSize()  
				.padding(16.dp)  
){  
items(shoppingItems){  
}  } } }
```

`MainActivity`
```kotlin
//...
setContent {  
  MyShoppingListAPpTheme {  
// A surface container using the 'background' color from the theme  
  Surface(  
    modifier = Modifier.fillMaxSize(),  
    color = MaterialTheme.colorScheme.background  
) {  
  ShoppingListApp()  
 }  
 }  
}
//...
```


------
# Alert Dialog

ShoppingList.kt
```kotlin
@Composable  
fun ShoppingListApp(){  

// ADD states handler
var shoppingItems by remember { mutableStateOf( listOf<ShoppingItem>() ) }  
var showDialog by remember { mutableStateOf(false) }  
var itemName by remember { mutableStateOf("") }  
var itemQuantity by remember { mutableStateOf("") }

// add a click handler
Button(  
	onClick = {showDialog=true},
//..




  // at the end of the file add if statement
  
if(showDialog){  
  AlertDialog(
    onDismissRequest = { showDialog=false },  
    confirmButton = { /* TODO */},  
    title = { Text(text="Add Shopping Item") },  
    text = {  
      Column {  
         
         OutlinedTextField(  
           value = itemName,  
           onValueChange = { itemName = it },  
           modifier = Modifier.fillMaxWidth().padding(8.dp),  
           singleLine=true  
    )  

		OutlinedTextField(  
		  value = itemQuantity,  
		  onValueChange = { itemQuantity = it },  
		  modifier = Modifier.fillMaxWidth().padding(8.dp),  
		  singleLine=true  
	)  
}  
}  
)  
}
```

