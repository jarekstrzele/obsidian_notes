#kotlin/datepicker

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








