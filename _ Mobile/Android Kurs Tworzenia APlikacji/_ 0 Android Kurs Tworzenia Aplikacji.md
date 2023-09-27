	#android 
https://www.youtube.com/watch?v=8u7UP4C7OcQ&list=PL7i9G1Htb_PvQhkckHBhaOH3ft5lTNGun

W razie dziwnego działania Android Studio (file: `invalide cache` or `repare IDE`)


# Aplikacja to zbiór aktywności.
*Activity launched*:
1. `onCreate()`
2. `onStart()`
3. `onResume()`
4. *Activity running*
5. `onPause()`
6. `onStop()`
7. `onDestroy()`

MainActivity
```kotlin
package com.example.myapplicationlayouts  
  
import android.graphics.Color  
import androidx.appcompat.app.AppCompatActivity  
import android.os.Bundle  
import android.util.Log  
import android.widget.Button  
import android.widget.EditText  
import android.widget.TextView  
import androidx.core.view.isVisible  
  
class MainActivity : AppCompatActivity() {  
  
    //Log.d - log debug  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
  
    }  
  
    override fun onStart() {  
        super.onStart()  
        //pierwszy to tag
        Log.d("LIFCYCLE", "onStart" )  
    }  
  
    override fun onResume() {  
        super.onResume()  
        Log.d("LIFCYCLE", "onResume" )  
    }  
  
    override fun onPause() {  
        super.onPause()  
        Log.d("LIFCYCLE", "onPause" )  
    }  
  
    override fun onStop() {  
        super.onStop()  
        Log.d("LIFCYCLE", "onStop" )  
    }  
  
    override fun onRestart() {  
        super.onRestart()  
  
        Log.d("LIFCYCLE", "onRestart" )  
    }  
  
  
    override fun onDestroy() {  
        super.onDestroy()  
        Log.d("LIFCYCLE", "onDestroy" )  
    }  
}
```

otwórz *Logcat* i w filtrze `package:mine level:debug LIFCYCLE`
(minimalizuj app, skasuj app, uruchom, a gdy jest uruchomiona to przekręcenie ekranu niszczy app i na nowo ją stawia )


# ViewBinding (6)










