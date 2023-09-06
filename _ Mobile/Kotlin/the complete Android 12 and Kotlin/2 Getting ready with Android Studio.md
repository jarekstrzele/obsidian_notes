

[[_ the complete Android 12]]

when you create a new project `pakage name`  must be unique

`SDK` Software Development Kit (collection of software development tools in one installable package)

`MainActivity` the most important file, because it is a start point of the app (it is in `java/<package_name>` folder )
`activiry_main.xmal` the file takes care of  the user interface (it is in the `res/layout` folder) 

these files are connected because in `MainActivity`:
```kotlin
  
class MainActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
    }  
}
```

the code `setContentView(R.layout.activity_main)` the app screen should use the `activity_main` file as a interface

every screen is `activity` ( screen=activity)


## set up the AVD
AVD is `Android Virtual Device` emulates Android on your PC






