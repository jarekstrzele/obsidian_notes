# Toast


# Snackbar
#android/snackbar

>[!definition] Android SnackBar
>it is light-weight widget and it is used to show messages in the bottom of the application with swiping enabled

Main.kt
```kotlin
package com.js.toastsnackbardialog  
  
import android.os.Bundle  
import android.widget.Button  
import androidx.activity.enableEdgeToEdge  
import androidx.appcompat.app.AppCompatActivity  
import androidx.constraintlayout.widget.ConstraintLayout  
import androidx.constraintlayout.widget.ConstraintSet.Constraint  
import androidx.core.view.ViewCompat  
import androidx.core.view.WindowInsetsCompat  
import com.google.android.material.snackbar.Snackbar  
  
class MainActivity : AppCompatActivity() {  
  
    lateinit var btn: Button  
    lateinit var mylayout: ConstraintLayout  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContentView(R.layout.activity_main)  
  
        btn=findViewById(R.id.button)  
        mylayout=findViewById(R.id.main)  // this is id of the main layout

		//setAction(<String>, <listener>)
        btn.setOnClickListener{  
            Snackbar.make(mylayout, "THis is a Snackbar Message\nsecond row", Snackbar.LENGTH_INDEFINITE).setAction(  
                "close", { }  
            ).show()  
  
        }  
  
    }  
}
```


-------
## Dialog Messages
#android/dialog

>[!definition] Dialog Messages
>It is a small window that prompts the user to make a decision or enter additional information.
>A dialog does not fill the screen and is normally used for modal events that require users to take an action before the can proceed.


### Alert Dialog
In xml you have a button
Main.kt
```kotlin
package com.js.toastsnackbardialog  
  
import android.content.DialogInterface  
import android.os.Bundle  
import android.widget.Button  
import androidx.activity.enableEdgeToEdge  
import androidx.appcompat.app.AlertDialog  
import androidx.appcompat.app.AppCompatActivity  
import androidx.constraintlayout.widget.ConstraintLayout  
import androidx.constraintlayout.widget.ConstraintSet.Constraint  
import androidx.core.view.ViewCompat  
import androidx.core.view.WindowInsetsCompat  
import com.google.android.material.snackbar.Snackbar  
  
class MainActivity : AppCompatActivity() {  
  
     
    lateinit var mylayout: ConstraintLayout  
    lateinit var showDialog: Button  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContentView(R.layout.activity_main)  
  
        mylayout=findViewById(R.id.main)  
  
        showDialog=findViewById(R.id.buttonDialog)  
        showDialog.setOnClickListener{  
            showAlertDialog()  
        }  
    }  
  
    fun showAlertDialog(){  
        var alertDialog = AlertDialog.Builder(this@MainActivity)  
        alertDialog.setTitle("Change")  
            .setMessage(("Dou you want to change the text of the button"))  
            .setIcon(R.drawable.report_problem_black_24dp)  
            .setCancelable(false)  
            .setNegativeButton("No, ", DialogInterface.OnClickListener { dialog, which ->  
                dialog.cancel()  
            })  
            .setPositiveButton("Yes", DialogInterface.OnClickListener { dialog, which ->  
                showDialog.text="Alert Dialog"  
            } )  
  
        alertDialog.create().show()  
    }  
  
  
  
}
```

### Input Dialog

You have to make a new layout for input data dialog:
`input_dialog.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout 
	xmlns:android="http://schemas.android.com/apk/res/android"  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:orientation="vertical"  
    android:padding="16dp"  
    >  
  
    <TextView        
	    android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:text="Enter your name:"  
        android:textSize="18sp"  
        android:textColor="@color/black"  
        android:layout_marginBottom="8dp" />  
  
    <EditText        
	    android:id="@+id/edittext_input"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:hint="Your name"  
        android:textSize="16sp" />  
  
</LinearLayout>
```

>[!tip] `LayoutInflater` 
>> - jest klasą, która służy do tworzenia widoków z plików XML layout.
>> - `from(this@MainActivity)` pobiera inflater powiązany z bieżącą aktywnością (`MainActivity`).
>> - `LayoutInflater.from(this@MainActivity)`: Tworzy instancję `LayoutInflater` związanej z daną aktywnością (`MainActivity`). `LayoutInflater` jest obiektem, który może przekształcać pliki XML na obiekty widoku.
>> - **inflater** to narzędzie służące do tworzenia widoków z plików XML layout. Jest to klasa o nazwie `LayoutInflater`, która posiada metody do konwersji layoutów XML na obiekty `View`.


```kotlin
  
class MainActivity : AppCompatActivity() {  
  
  
    lateinit var mylayout: ConstraintLayout  
    lateinit var showDialog: Button  
    lateinit var showData:TextView  
  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContentView(R.layout.activity_main)  
  
        mylayout=findViewById(R.id.main)  //this is id of main layout
        showData=findViewById(R.id.textview_input)  
  
        showDialog=findViewById(R.id.buttonDialog)  
  
        showDialog.setOnClickListener{  
            showInputDialog()  
        }  
    }  
  
    fun showInputDialog(){  
        val inputView = LayoutInflater.from(this@MainActivity).inflate(R.layout.dialog_input, null)  
        var alertDialog = AlertDialog.Builder(this@MainActivity)  
        alertDialog.setView(inputView)  
            .setTitle("Input dialog")  
            .setCancelable(false)  
            .setNegativeButton("Cancel", DialogInterface.OnClickListener { dialog, _ ->  
                dialog.dismiss()  
            })  
            .setPositiveButton("OK", DialogInterface.OnClickListener { dialog, _ ->  
                val editText = inputView.findViewById<EditText>(R.id.edittext_input)  
                val userInput = editText.text.toString()  
                showData.text= userInput  
                dialog.dismiss()  
            } )  
  
        alertDialog.create().show()  
    }  

}
```






