[[_ the complete Android 12]]

- a new project
- to choose colors https://coolors.co/
you can define your own colors `res/values/colors.xml` (e.g. add `<color name="textBlue">#264653</color>`)
and now you can use this color (`@color/textBlue`)

- change constraint layout to `<LinearLayout>`
- `android:gravity`
- freeze `android:orientation="vertical"`
- add new colors to `res/values/colors.xml`

---
> różnica między nimi polega na tym, że `DatePicker` to stały element interfejsu, który jest zawsze widoczny, podczas gdy `DatePickerDialog` to okno dialogowe, które jest wywoływane w odpowiedzi na konkretne działanie użytkownika i pozwala na wybór daty w określonym kontekście.

---
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

> W jednej godzinie jest 3 600 000 milisekund.
> 


prosty DatePickerDialog ustawiony na EditText
```kotlin
  dateEt =findViewById(R.id.dateEditText)  
    dateEt.setOnClickListener {  
    val calendar = Calendar.getInstance()  
    val year = calendar.get(Calendar.YEAR)  
    val month = calendar.get(Calendar.MONTH)  
    val dayOfMonth = calendar.get(Calendar.DAY_OF_MONTH)  
  
    val datePickerDialog = DatePickerDialog(  
        this,  
        { _, selectedYear, selectedMonth, selectedDay ->  
            val selectedDate = "$selectedYear-${selectedMonth + 1}-$selectedDay"  
            dateEt.setText(selectedDate)  
        },  
        year,  
        month,  
        dayOfMonth  
    )  
  
    datePickerDialog.show()  
}
```



```kotlin
package com.example.calcageapp  
  
import android.app.DatePickerDialog  
import android.icu.util.Calendar  
import androidx.appcompat.app.AppCompatActivity  
import android.os.Bundle  
import android.util.Log  
import android.widget.Button  
import android.widget.DatePicker  
import android.widget.TextView  
import android.widget.Toast  
import org.w3c.dom.Text  
import java.text.SimpleDateFormat  
import java.util.Locale  
  
class MainActivity : AppCompatActivity() {  
  
    var tvSelectedDate : TextView? = null  
    var tvAgeInMinutes: TextView? = null  
 
    override fun onCreate(savedInstanceState: Bundle?) {  
      super.onCreate(savedInstanceState)  
      setContentView(R.layout.activity_main)  
  
        //tvSelectedDate?.text = "$day.${month+1}.$year"  
  
      tvSelectedDate = findViewById(R.id.tvSelectedDate)  
  
      tvAgeInMinutes = findViewById(R.id.tvAgeInMinutes)  
  
      val btnDatePicker : Button = findViewById(R.id.btnDatePicker)  
        btnDatePicker.setOnClickListener { _ ->  
            clickDatePicker()  
        }  
    }  
  
    private fun clickDatePicker(){  
      val myCalendar = Calendar.getInstance()  
      val year = myCalendar.get(Calendar.YEAR)  
      val month = myCalendar.get(Calendar.MONTH)  
      val day = myCalendar.get(Calendar.DAY_OF_MONTH)  
  
        // 'this' wskazuje na aktywność, która jest używana, czyli tutaj to `MainActivity`  
        // `view` to referencja do widoku DatePicker        val dpd =  DatePickerDialog(this,  
        DatePickerDialog.OnDateSetListener{view, selectedYear, selectedMonth, selectedDayOfMonth ->  
//                Toast.makeText(this, "year=$selectedYear,\nmonth=${selectedMonth+1},\nday=${selectedDayOfMonth}",  
//                    Toast.LENGTH_LONG).show()  
     val selectedDate = "$selectedDayOfMonth/${selectedMonth+1}/$selectedYear"  
     tvSelectedDate?.text = selectedDate  
  
     //val sdf = SimpleDateFormat("dd/MM/yyy", Locale.ENGLISH)  
                val sdf = SimpleDateFormat("dd/MM/yyy", Locale("pl", "PL"))  
  
               // if theDate is not empty do  
                val theDate = sdf.parse(selectedDate)  
                theDate?.let {  
                    Toast.makeText(this,theDate.toString(), Toast.LENGTH_LONG ).show()  
                    val selectedDateInMinutes = theDate.time/60_000 // 1 minuta to 60_000 milisekund  
                    val currentDate = sdf.parse(sdf.format(System.currentTimeMillis()))  
                    //Log.i("currDate", currentDate.time.toString())  
                    currentDate?.let{  
                        val currentDateInMinutes = currentDate.time / 60_000  
                        //Log.i("currDate", currentDateInMinutes.toString())  
                        val differenceInMinutes = currentDateInMinutes - selectedDateInMinutes  
                        Log.i("currDate", differenceInMinutes.toString())  
                        tvAgeInMinutes?.text = differenceInMinutes.toString()  
                    }  
  
                }  
            },  
            year,  
            month,  
            day,  
        )  
  
        dpd.datePicker.maxDate = System.currentTimeMillis() - 86_400_000  
        dpd.show()  
  
  
    }  
}
```





