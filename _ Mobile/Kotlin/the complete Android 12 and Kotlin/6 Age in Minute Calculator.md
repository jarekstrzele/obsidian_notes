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

to test 
```kotlin
  
val btnDatePicker : Button =findViewById(R.id.btnDatePicker)  
  
btnDatePicker.setOnClickListener {  
    // `this` means "display Toast on this activity"      Toast.makeText(this, "btn pressed", Toast.LENGTH_LONG).show()  
}
```
















