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











