[[_ the complete Android Kotlin]]

# kiedy używać:
[[SharedPreferences - when to use]]

# SharedPreference Class Description

- Android provides many ways of storing data
- Shared Preferences Class is just one of them:
	- with that class you can save primitive types of data:
		- integer
		- boolean
		- string
		- ...
	- you can save and retrieve data in the form of *key-value pair.*
	- you can reach the save data types anywhere within the application
	- use that class: a transition between running apps
		- you do a text msg, and a call is coming, so your app with text will be stopped)
		- you play a game and a phone call is coming, so game data have to be saved
		- in a logg-in situation



# Saving Data Local Memory and Calling Back Data

## `getSharedPreferences`

Metoda `getSharedPreferences` jest używana do uzyskania instancji `SharedPreferences`, która jest specyficzna dla Twojej aplikacji. `SharedPreferences` pozwala na przechowywanie par klucz-wartość, które są zachowywane pomiędzy sesjami aplikacji.

### Argumenty `getSharedPreferences`

1. **Pierwszy argument: `"saveData"`**
    
    - **Typ:** `String`
    - **Opis:** Nazwa pliku, w którym będą przechowywane dane.
    - **Szczegóły:**
        - Jest to nazwa pliku preferencji, który będzie przechowywany w wewnętrznej przestrzeni dyskowej Twojej aplikacji. Plik ten będzie dostępny tylko dla Twojej aplikacji.
        - Możesz użyć dowolnej unikalnej nazwy, aby odróżnić różne zestawy preferencji, np. `"userPreferences"`, `"appSettings"` itp.
2. **Drugi argument: `Context.MODE_PRIVATE`**
    
    - **Typ:** `Int`
    - **Opis:** Tryb dostępu do pliku preferencji.
    - **Szczegóły:**
        - `Context.MODE_PRIVATE` oznacza, że plik preferencji jest dostępny tylko dla Twojej aplikacji (nie może być odczytywany ani zapisywany przez inne aplikacje). Jest to najczęściej używany tryb, ponieważ zapewnia prywatność danych.
        - Inne dostępne tryby (które obecnie są przestarzałe i zazwyczaj nie są używane) to:
            - `Context.MODE_APPEND`: Otwiera plik preferencji w trybie dołączania, co oznacza, że nowe dane będą dołączane do istniejących danych.
            - `Context.MODE_WORLD_READABLE` (przestarzałe): Umożliwia odczyt danych przez inne aplikacje.
            - `Context.MODE_WORLD_WRITEABLE` (przestarzałe): Umożliwia zapis danych przez inne aplikacje.

### Poprawny sposób użycia `SharedPreferences`

1. **Inicjalizacja `SharedPreferences`**: `getSharedPreferences` jest używane do uzyskania instancji `SharedPreferences`, która identyfikuje plik, w którym będą przechowywane dane.
    
2. **Zapis danych**: Za pomocą metody `edit` uzyskujesz edytor (`SharedPreferences.Editor`), który umożliwia zapisanie danych.
    
3. **Odczyt danych**: Metody takie jak `getString`, `getInt`, `getBoolean` są używane do odczytywania zapisanych danych.






# app


```kotlin
package com.js.mysharedpreferenceclass  
  
import android.content.Context  
import android.content.SharedPreferences  
import android.os.Bundle  
import android.util.Log  
import android.widget.Toast  
import androidx.activity.enableEdgeToEdge  
import androidx.appcompat.app.AppCompatActivity  
import androidx.core.view.ViewCompat  
import androidx.core.view.WindowInsetsCompat  
import com.js.mysharedpreferenceclass.databinding.ActivityMainBinding  
  
class MainActivity : AppCompatActivity() {  
  
    lateinit var mainBinding: ActivityMainBinding  
  
    var count: Int = 0  
    var userName: String? = null  
    var msg: String? = null  
    var isChecked: Boolean? = null  
    
    lateinit var sharedPreferences: SharedPreferences   
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        Log.i("info", "onCreate")  
        enableEdgeToEdge()  
  
        mainBinding = ActivityMainBinding.inflate(layoutInflater)  
  
        setContentView(mainBinding.root)  
  
        sharedPreferences =this.getSharedPreferences("saveData", Context.MODE_PRIVATE) //mode_private - give me acces permission to save data from everywhere in the app  
         retreiveData()  
  
  
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->  
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)  
            insets  
        }  
  
        mainBinding.button.setOnClickListener {  
            count++  
            mainBinding.button.text="$count"  
        }  
    }  
  
  
    override fun onPause() {  
        super.onPause()  
        Log.i("info", "onPause")  
        saveData()  
    }  
  
    fun saveData(){  
  
  
        //  // Pobranie danych z widoków  
        userName = mainBinding.editTextName.text.toString()  
        msg = mainBinding.editTextMessage.text.toString()  
        count = mainBinding.button.text.toString().toInt()  
        isChecked = mainBinding.checkBox.isChecked  
  
        // Zapisanie danych do SharedPreferences  
        val editor = sharedPreferences.edit() // I will save my data using this editor object  
        editor.putString("key_name", userName)  
        editor.putString("key_message", msg)  
        editor.putInt("key_count", count)  
        editor.putBoolean("key_checkbox", isChecked!!)  
  
        // Zastosowanie zmian  
        editor.apply() // it stores data  
  
        Toast.makeText(this, "Your data is saved", Toast.LENGTH_LONG).show()  
  
    }  
  
    fun retreiveData(){  
  
        userName = sharedPreferences.getString("key_name", null)  
        msg = sharedPreferences.getString("key_message", null)  
        count = sharedPreferences.getInt("key_count", 0)  
        isChecked = sharedPreferences.getBoolean("key_checkbox", false)  
  
        mainBinding.editTextName.setText(userName)  
        mainBinding.editTextMessage.setText(msg)  
        mainBinding.button.setText("$count")  
        mainBinding.checkBox.isChecked = isChecked ?: false  
  
  
    }  
  
  
}
```

```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
  
    xmlns:tools="http://schemas.android.com/tools"  
    android:id="@+id/main"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    tools:context=".MainActivity"  
    android:orientation="vertical"  
    >  
  
    <EditText        android:id="@+id/editText_name"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_marginStart="20dp"  
        android:layout_marginTop="20dp"  
        android:layout_marginEnd="20dp"  
        android:layout_marginBottom="20dp"  
  
        android:ems="10"  
        android:hint="name"  
        android:inputType="text"  
        android:textSize="22dp" />  
  
    <EditText        android:id="@+id/editTextMessage"  
        android:layout_width="match_parent"  
        android:layout_height="200dp"  
        android:layout_marginStart="20dp"  
        android:layout_marginTop="20dp"  
        android:layout_marginEnd="20dp"  
        android:layout_marginBottom="20dp"  
        android:layout_weight="1"  
        android:ems="10"  
        android:gravity="start|top"  
        android:hint="write something"  
        android:inputType="textMultiLine"  
        android:textSize="24dp" />  
  
    <Button        android:id="@+id/button"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_marginStart="20dp"  
        android:layout_marginTop="20dp"  
        android:layout_marginEnd="20dp"  
        android:layout_marginBottom="20dp"  
        android:layout_weight="1"  
        android:text="0" />  
  
    <CheckBox        android:id="@+id/checkBox"  
        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_marginStart="20dp"  
        android:layout_marginTop="20dp"  
        android:layout_marginEnd="20dp"  
        android:layout_marginBottom="20dp"  
        android:layout_weight="1"  
        android:text="CheckBox" />  
  
</LinearLayout>
```






