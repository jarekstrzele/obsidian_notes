```kotlin

package com.example.testing  
  
import android.app.DatePickerDialog  
import android.icu.util.Calendar  
import androidx.appcompat.app.AppCompatActivity  
import android.os.Bundle  
import android.util.Log  
import android.view.View  
import android.widget.AdapterView  
import android.widget.ArrayAdapter  
import android.widget.Button  
import android.widget.DatePicker  
import android.widget.EditText  
import android.widget.Spinner  
import android.widget.TextView  
import android.widget.Toast  
import java.text.SimpleDateFormat  
import java.util.Locale  
  
class MainActivity : AppCompatActivity() {  
  
     lateinit var btnDatePickerDialog: Button  
     lateinit var tvWeight: TextView  
     lateinit var tvShowDate: TextView  
     lateinit var spPlanetes: Spinner  
     lateinit var etWeight: EditText  
     lateinit var btnCountWeigth: Button  
     lateinit var tvWeightResult: TextView  
  
  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
  
        spPlanetes=findViewById(R.id.spPlanets)  
        val planetes = arrayOf("Merkury", "Venus", "Mars", "Jowisz", "Słońce")  
        val adapter = ArrayAdapter(this, android.R.layout.simple_spinner_item, planetes)  
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)  
        spPlanetes.adapter = adapter  
  
        tvWeightResult = findViewById(R.id.tvWeightResult)  
        tvWeight=findViewById(R.id.tvWeight)  
        tvShowDate=findViewById(R.id.tvShowDateInMinutes)  
        etWeight=findViewById(R.id.etWeight)  
  
        btnDatePickerDialog=findViewById(R.id.btnDatePickerDialog)  
        btnDatePickerDialog.setOnClickListener {  
            _ -> clickDataPicker()  
        }  
  
        btnCountWeigth=findViewById(R.id.btnCountWeight)  
        btnCountWeigth.setOnClickListener {  
            _ -> countWeightOnPlanete()  
        }  
  
//  
//        mySpinner.onItemSelectedListener = object : AdapterView.OnItemSelectedListener {  
//            override fun onItemSelected(parent: AdapterView<*>?, view: View?, position: Int, id: Long) {  
//                val selectedCategory = soups[position]  
//               Toast.makeText(applicationContext , selectedCategory, Toast.LENGTH_LONG).show()  
//            }  
//  
//            override fun onNothingSelected(parent: AdapterView<*>?) {  
//                Toast.makeText(applicationContext , "Nic nie wybrano", Toast.LENGTH_LONG).show()  
//  
//            }  
//        }  
    }  
  
    private fun countWeightOnPlanete() {  
        val textFromEtWeight = etWeight.text.toString()  
        val planetFromSpinner = spPlanetes.selectedItem.toString()  
        textFromEtWeight?.let{  
            val intWeight = textFromEtWeight.toInt()  
            val weight = when (planetFromSpinner) {  
                "Merkury" -> intWeight * 0.37  
                "Venus" -> intWeight * 0.881  
                "Mars" -> intWeight * 0.371  
                "Jowisz" -> intWeight * 2.479  
                "Słońce" -> intWeight * 27.4  
                 else -> 0  
  
            }  
            tvWeightResult?.let {  
                tvWeightResult.text = "Twoja waga na planecie $planetFromSpinner wynosi ${String.format("%.4f", weight)} kg"            }  
            Log.d("click", "${tvWeight.text}")  
  
        } ?: run {  
            Toast.makeText(this, "Niepoprawny format liczby", Toast.LENGTH_LONG)  
        }  
  
  
    }  
  
  
  
    private fun clickDataPicker() {  
        val calendar = Calendar.getInstance()  
        val year = calendar.get(Calendar.YEAR)  
        val month = calendar.get(Calendar.MONTH)  
        val dayOfMonth = calendar.get(Calendar.DAY_OF_MONTH)  
        val actualDate = "$dayOfMonth/${month + 1}/$year"  
        //Log.d("klik", actualDate)  
        val datePickerDialog = DatePickerDialog(this,  
            {  
                _, selectedYear, selectedMonth, selectedDay->  
                val selectedDate = String.format("%02d/%02d/%d", selectedDay, selectedMonth + 1, selectedYear)  
                val sdf = SimpleDateFormat("dd/MM/yyyy", Locale("pl", "PL"))  
                val theDate = sdf.parse(selectedDate)  
                theDate?.let{  
                    val selectedDateInMinutes = theDate.time/60_000  
                    Log.d("theDate", "theDate=${theDate.time/60_000}")  
                    val currentDate = sdf.parse(sdf.format(System.currentTimeMillis()))  
                    currentDate?.let{  
  
                        Log.d("theDate", "thecurrentDate: ${currentDate}")  
                        val currentDateInMinutes = currentDate.time/60_000  
                        val diffInMinutes = currentDateInMinutes - selectedDateInMinutes  
                        tvShowDate.setText("Urodziłeś się:\t\t\t$selectedDate\nDzisiaj jest:\t\t\t\t$actualDate\nTwój wiek w minutach:\t$diffInMinutes"   )  
                    }  
  
                }  
  
  
            },  
            year,  
            month,  
            dayOfMonth  
            )  
        datePickerDialog.show()  
    }  
  
  
}

```


```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    tools:context=".MainActivity"  
    android:orientation="vertical"  
    android:layout_margin="2dp"  
  
    >  
  
  
   <LinearLayout       android:id="@+id/inputData"  
       android:layout_width="match_parent"  
  
       android:layout_height="86dp"  
       android:layout_weight="1"  
       android:background="@color/inputDateBg"  
       android:orientation="vertical"  
       android:padding="5dp"  
       tools:layout_editor_absoluteX="1dp"  
       tools:layout_editor_absoluteY="176dp">  
  
      <TextView          android:id="@+id/tvDate"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:layout_marginTop="20dp"  
          android:layout_marginBottom="10dp"  
          android:gravity="center"  
          android:text="Przeliczę datę twojego urodzenia na minuty"  
          android:textColor="#172469"  
          android:textSize="14sp" />  
  
      <Button          android:id="@+id/btnDatePickerDialog"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
         android:layout_marginTop="5dp"  
          android:backgroundTint="@color/btnBg"  
          android:text="Wybierz datę swojego urodzenia." />  
  
   </LinearLayout>  
   <LinearLayout       android:id="@+id/showDateInMinutes"  
       android:layout_width="match_parent"  
       android:layout_height="wrap_content"  
       android:layout_marginTop="3dp"  
       android:background="@color/outputDateBg"  
       android:padding="5dp"  
       android:layout_weight="1"  
       tools:layout_editor_absoluteX="1dp"  
       tools:layout_editor_absoluteY="176dp"  
       android:layout_marginBottom="5dp">  
  
      <TextView          android:id="@+id/tvShowDateInMinutes"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:gravity="left"  
          android:text="Urodziłeś się:\nDzisiaj jest:\nTwój wiek w minutach:"  
         android:lineSpacingExtra="13dp"  
          android:textColor="@color/white" />  
  
  
   </LinearLayout>  
  
   <LinearLayout       android:id="@+id/inputWeight"  
       android:layout_width="match_parent"  
       android:layout_height="271dp"  
       android:background="@color/inputDateBg"  
       android:gravity="center_horizontal|center_vertical"  
       android:orientation="vertical"  
       android:padding="5dp"  
       tools:layout_editor_absoluteX="1dp"  
       tools:layout_editor_absoluteY="176dp">  
  
  
      <TextView          android:id="@+id/tvWeight"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:layout_marginTop="30dp"  
          android:text="Najpierw podaj swoją wagę: "  
          android:textColor="#172469" />  
  
      <EditText          android:id="@+id/etWeight"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:ems="10"  
          android:hint="Podaj liczbę całkowiką"  
          android:inputType="number" />  
  
      <TextView          android:id="@+id/tvPlanet"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:layout_marginTop="30dp"  
          android:text="Teraz wybierz planetę:"  
          android:textColor="#172469" />  
  
      <Spinner          android:id="@+id/spPlanets"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content" />  
  
  
      <Button          android:id="@+id/btnCountWeight"  
          android:layout_width="match_parent"  
          android:layout_height="wrap_content"  
          android:backgroundTint="@color/btnBg"  
          android:text="Przelicz podaną wagę " />  
   </LinearLayout>  
   <LinearLayout       android:id="@+id/showWeightInPlanete"  
       android:layout_width="match_parent"  
       android:layout_height="156dp"  
       android:layout_marginTop="3dp"  
       android:layout_weight="1"  
       android:background="@color/outputDateBg"  
       android:gravity="center_horizontal|center_vertical"  
       android:padding="5dp"  
       tools:layout_editor_absoluteX="1dp"  
       tools:layout_editor_absoluteY="176dp">  
  
      <TextView          android:id="@+id/tvWeightResult"  
          android:layout_width="372dp"  
          android:layout_height="wrap_content"  
  
          android:gravity="clip_horizontal|center_horizontal"  
  
          android:text="Twoja waga na: "  
          android:textColor="@color/white" />  
  
  
   </LinearLayout>  
  
</LinearLayout>



```


