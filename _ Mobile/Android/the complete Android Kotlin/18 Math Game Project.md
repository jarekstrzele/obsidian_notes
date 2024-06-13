
### Add new colors in `colors.xml`:
```xml
<color name="green">#028074</color>  
<color name="blue">#0479D6</color>  
<color name="ice_blue">#63B5F6</color>
```

### Change `theme.xml`:
```xml
  <item name="colorPrimary">@color/green</item>  
    <item name="colorPrimaryVariant">@color/green</item>  
    <item name="colorOnPrimary">@color/white</item>  
</style>
```

### Add three images to `res` to background for three activities


### Add to `activity_main.xml`:
- background
- three buttons: `ADDITION`,`SUBSTRACTION`, `MUTLIPLICATION`


![[Pasted image 20240605114748.png]]

### in `MainActivity.kt`

#### binding in gradle 
```  
buildFeatures{  
    viewBinding=true  
}
```

#### in `MainActivity`
```kotlin
class MainActivity : AppCompatActivity() {  
  
    lateinit var mainBinding: ActivityMainBinding  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
  
        mainBinding = ActivityMainBinding.inflate(layoutInflater)  
  
        setContentView(mainBinding.root)  
        // Ustawienie Toolbar jako ActionBar  
        setSupportActionBar(mainBinding.toolbar)  
  
  
  
        ViewCompat.setOnApplyWindowInsetsListener(mainBinding.root) { v, insets ->  
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)  
            insets  
        }  
  
        mainBinding.buttonAdd.setOnClickListener {  
                val intent = Intent(this@MainActivity, GameActivity::class.java)  
                startActivity(intent)  
        }  
    }  
}
```

### in `AndroidMainfest`
```xml
<!-- ...  -->
<activity  
    android:name=".GameActivity" 
    android:exported="false"  
    android:parentActivityName=".MainActivity"  
    />  
<activity  
    android:name=".MainActivity"  
    android:exported="true">  
    <intent-filte
```

`android:exported` - czy aktywność może być uruchamiana przez inne aplikacje




























