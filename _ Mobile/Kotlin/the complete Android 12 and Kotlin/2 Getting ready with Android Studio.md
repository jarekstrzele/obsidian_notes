

[[_ the complete Android 12]]

when you create a new project `pakage name`  must be unique

`SDK` Software Development Kit (collection of software development tools in one installable package)

`MainActivity` the most important file, because it is a start point of the app (it is in `java/<package_name>` folder )
`activity_main.xmal` the file takes care of  the user interface (it is in the `res/layout` folder) 

these files are connected because in `MainActivity`:
```kotlin
  
class MainActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
    }  
}
```

the code `setContentView(R.layout.activity_main)` the app screen should use the `activity_main` file as a interface (`R.layout.activity_main` `res/layout/activity_main`)

every screen is `activity` ( screen=activity)


## set up the AVD
AVD is `Android Virtual Device` emulates Android on your PC


## Example Counter App
- add a button in the screen centre, but in the smartphone the button will be on the top, not in the centre (you will have one label and one button)
- you can magically link the button and the label below (the magic icon) but better way is to do it yourself ( four circle on the button icon with arrows)
- to modify a distance between objects (the label and the button) `Attributs`>`Layout` and change the constrains (check `20` (it's up), `-20` it's down)
- `Declared Attributes` change the property `text` ('Click Me') and the property `Id` ('mybtn')
- go to `MainActivity.kt` and register the `mybtn`
```kotlin
  
class MainActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
  
        val myBtnClickMe = findViewById<Button>(R.id.mybtn)  
        // myBtnClickMe.text = "Hahha" //this code override the value of text attribute  
        val myTextView = findViewById<TextView>(R.id.textView2)  
        var timesCounter = 0  
        myBtnClickMe.setOnClickListener{  
           //myBtnClickMe.text = "Hahha"  
           // myTextView.text = "Łałłłłł"            timesCounter += 1  
            myTextView.text = timesCounter.toString()  
  
            //Ładny tekst  
            //makeText(kontekst, zawaertość, czas)            Toast.makeText(this, "Fajny toast jestemn", Toast.LENGTH_LONG).show()  
        }  
    }  
}
```


## Connect your app to your phone

You have to switch on `USB debugging` <-- in your settings find `Build Number` --> touch it multiple time untile you have to write your access code 
now find `Developer options` and find and activate `USB debugging`




