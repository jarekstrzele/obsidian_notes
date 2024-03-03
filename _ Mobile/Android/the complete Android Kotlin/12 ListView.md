#android/listview

>[!definition] **ListView**
>
> It is a view which groups several items and display them in vertical scrollable list

# Make Toolbar:

activity_main.xml
```xml
<com.google.android.material.appbar.AppBarLayout  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:layout_marginTop="2dp"  
    app:layout_constraintEnd_toEndOf="parent"  
    app:layout_constraintStart_toStartOf="parent"  
    app:layout_constraintTop_toTopOf="parent"  
    android:background="#123abc"  
    >  
  
    <Toolbar        android:layout_width="match_parent"  
        android:layout_height="wrap_content"  
        android:titleTextColor="@color/white"  
        android:title="My ListView"  
        android:layout_gravity="center"  
        />  
  
</com.google.android.material.appbar.AppBarLayout>
```


# Add ListView

Palette>Legacy>ListView
or
add:
```xml
<ListView  
    android:id="@+id/listview"  
    android:layout_width="409dp"  
    android:layout_height="671dp"  
    app:layout_constraintBottom_toBottomOf="parent"  
    app:layout_constraintEnd_toEndOf="parent"  
    app:layout_constraintStart_toStartOf="parent"  
    app:layout_constraintTop_toBottomOf="@+id/appBarLayout" />
```

resource:
```xml
<resources>  
    <string name="app_name">MyListView</string>  
  
    <string-array name="countries">  
        <item>England</item>  
        <item>Netherlands</item>  
        <item>Belgium</item>  
        <item>Germany</item>  
        <item>Finland</item>  
        <item>America</item>  
        <item>Thailand</item>  
        <item>China</item>  
        <item>Mexico</item>  
        <item>Greece</item>  
        <item>Italy</item>  
        <item>Russia</item>  
        <item>Spain</item>  
        <item>Australia</item>  
        <item>Turkey</item>  
    </string-array></resources>
```

MainActivity.kt
```kotlin
class MainActivity : AppCompatActivity() {  
  
    lateinit var listView : ListView  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContentView(R.layout.activity_main)  
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->  
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)  
            insets  
        }  
  
        listView=findViewById(R.id.listview)  
  
        var counteryList = resources.getStringArray(R.array.countries)  
        var arrayAdapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, counteryList)  
  
        listView.adapter = arrayAdapter  
        listView.setOnItemClickListener { parent, view, position, id ->  
            val countryName: String = parent.getItemAtPosition(position).toString()  
            Toast.makeText(applicationContext, countryName, Toast.LENGTH_SHORT).show()  
        }  
  
    }  
}
```

