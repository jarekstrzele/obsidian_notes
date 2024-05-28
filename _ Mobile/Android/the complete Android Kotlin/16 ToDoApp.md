[[FileOutputStream]]
[[ObjectOutputStream]]

to add a new icon to app:
`AdroidMainfest.xml` and change: *android:icon* and *android:roundIcon*
```xml
<application  
    android:allowBackup="true"  
    android:dataExtractionRules="@xml/data_extraction_rules"  
    android:fullBackupContent="@xml/backup_rules"  
    android:icon="@drawable/todoapp_icon"  
    android:label="@string/app_name"  
    android:roundIcon="@drawable/todoapp_icon"  
    android:supportsRtl="true"
```

FileHelper.kt
```kotlin
package com.js.todoapp  
  
import android.content.Context  
import java.io.FileInputStream  
import java.io.FileNotFoundException  
import java.io.FileOutputStream  
import java.io.ObjectInputStream  
import java.io.ObjectOutputStream  
  
class FileHelper {  
  
    val FILENAME = "listinfo.dat"  
  
    fun writeData(item: ArrayList<String>, context: Context){  
  
        var fos: FileOutputStream = context.openFileOutput(FILENAME, Context.MODE_PRIVATE)  
  
        var oas = ObjectOutputStream(fos)  
        oas.writeObject(item)  
  
        oas.close()  
    }  
  
    fun readData(context: Context) : ArrayList<String>{  
        var itemList: ArrayList<String>  
  
       try{  
  
           var fis: FileInputStream = context.openFileInput(FILENAME)  
           var ois = ObjectInputStream(fis)  
           itemList = ois.readObject() as ArrayList<String>  
       } catch (e: FileNotFoundException){  
            itemList = ArrayList<String>()  
       }  
  
        return itemList  
    }  
}
```





MainActivity
```kotlin
package com.js.todoapp  
  
import android.os.Bundle  
import android.util.Log  
import android.widget.ArrayAdapter  
import androidx.activity.enableEdgeToEdge  
import androidx.appcompat.app.AlertDialog  
import androidx.appcompat.app.AppCompatActivity  
import androidx.core.view.ViewCompat  
import androidx.core.view.WindowInsetsCompat  
import com.js.todoapp.databinding.ActivityMainBinding  
  
class MainActivity : AppCompatActivity() {  
  
    lateinit var mainBinding: ActivityMainBinding  
    var  itemList = mutableListOf<String>()  
  
    var fileHelper = FileHelper()  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
  
        mainBinding = ActivityMainBinding.inflate(layoutInflater)  
  
        setContentView(mainBinding.root)  
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->  
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)  
            insets  
        }  
  
  
  
        itemList = fileHelper.readData(this)  
        var arrayAdapter = ArrayAdapter<String>(  
            this,  
            android.R.layout.simple_list_item_1,  
            android.R.id.text1,  
            itemList)  
  
        mainBinding.listView.adapter = arrayAdapter  
        mainBinding.button.setOnClickListener {  
            var itemName: String = mainBinding.editText.text.toString()  
            Log.i("task", "itemName")  
            itemList.add(itemName)  
            mainBinding.editText.setText("")  
            fileHelper.writeData(itemList as ArrayList<String>, applicationContext, )  
            arrayAdapter.notifyDataSetChanged()  
  
        }  
  
        mainBinding.listView.setOnItemClickListener { parent, view, position, id ->  
  
            var alert = AlertDialog.Builder(this)  
            alert.setTitle("Delete")  
            alert.setMessage("Do you want to delete this item from the list?")  
            alert.setCancelable(false)  
            alert.setNegativeButton("No") { dialogInterface, i ->  
                dialogInterface.cancel()  
            }  
            alert.setPositiveButton("Yes") { dialogInterface, i ->  
                itemList.removeAt(index = position)  
                arrayAdapter.notifyDataSetChanged()  
                fileHelper.writeData(itemList as ArrayList<String>, applicationContext)  
            }  
        alert.create().show()  
        }  
  
    }  
}
```

activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:id="@+id/main"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    android:background="#87DA8A"  
    android:backgroundTint="#D0E8B5"  
    android:orientation="vertical"  
    tools:context=".MainActivity">  
  
    <com.google.android.material.appbar.AppBarLayout        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:layout_marginBottom="5dp">  
  
        <com.google.android.material.appbar.MaterialToolbar            android:layout_width="match_parent"  
            android:layout_height="wrap_content"  
            android:background="@android:color/holo_orange_light"  
            app:title="To Do App" />  
    </com.google.android.material.appbar.AppBarLayout>  
    <LinearLayout        android:layout_width="match_parent"  
        android:layout_height="wrap_content">  
  
        <EditText            android:id="@+id/editText"  
            android:layout_width="wrap_content"  
            android:layout_height="wrap_content"  
            android:layout_margin="3dp"  
            android:layout_weight="4"  
            android:ems="10"  
            android:hint="Add to do"  
            android:inputType="text"  
            android:typeface="monospace" />  
  
        <Button            android:id="@+id/button"  
            android:layout_width="wrap_content"  
            android:layout_height="wrap_content"  
            android:layout_margin="3dp"  
            android:layout_weight="1"  
            android:text="Button" />  
    </LinearLayout>  
    <ListView        android:id="@+id/listView"  
        android:layout_width="match_parent"  
        android:layout_height="match_parent" />  
  
</LinearLayout>
```








