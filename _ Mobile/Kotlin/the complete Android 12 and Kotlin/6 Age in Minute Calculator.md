[[_ the complete Android 12]]

- a new project
- to choose colors https://coolors.co/
you can define your own colors `res/values/colors.xml` (e.g. add `<color name="textBlue">#264653</color>`)
and now you can use this color (`@color/textBlue`)

- change constraint layout to `<LinearLayout>`
- `android:gravity`
- freeze `android:orientation="vertical"`
- add new colors to `res/values/colors.xml`

## a date picker dialog

## to test 
```kotlin
  
val btnDatePicker : Button =findViewById(R.id.btnDatePicker)  
  
btnDatePicker.setOnClickListener {  
    // `this` means "display Toast on this activity"   
    Toast.makeText(this, "btn pressed", Toast.LENGTH_LONG).show()  
}
// czas trwania tosta:
// Toast.LENGTH_LONG
// Toast.LENGTH_SHORT
```

## make date picker 
```kotlin
override fun onCreate(savedInstanceState: Bundle?) {  
    super.onCreate(savedInstanceState)  
    setContentView(R.layout.activity_main)  
  
    val btnDatePicker : Button =findViewById(R.id.btnDatePicker)  
  
    btnDatePicker.setOnClickListener { _ ->  
        clickDatePicker()  
    }  
}  
  
fun clickDatePicker(){  
  
    val myCalendar = Calendar.getInstance()  
    val year = myCalendar.get(Calendar.YEAR)  
    val month = myCalendar.get(Calendar.MONTH)  
    val day = myCalendar.get(Calendar.DAY_OF_MONTH)  
    DatePickerDialog(this,  
        DatePickerDialog.OnDateSetListener{view, year, month, dayOfMonth ->  
            Toast.makeText(this, "Date picker works", Toast.LENGTH_LONG).show()  
        },  
        year,  
        month,  
        day,  
        ).show()  
    // `this` means "display Toast on this activity"  
  
}
```


## take date from the date picker

> `Locale` przyjmuje dwa argumenty: pierwszy to kod języka, a drugi to kod kraju. W przypadku Polski, używamy "pl" jako kodu języka i "PL" jako kodu kraju, aby ustawić lokalizację na polską.











