#kotlin #android 

zmiana koloru dla całej aplikacji
`res>values>themes>thems.xml`

```xml
<!-- Base application theme. -->  
<style name="Base.Theme.Calculator" parent="Theme.Material3.DayNight.NoActionBar">  
    <!-- Customize your light theme here. -->  
    <item name="colorPrimary">@color/grey</item>  
</style>
```
`grey` jest zdefiniowany w `res/values/colors/xml`


----
A row of BUTTONS is closed inside the `LinearLayout`
```xml
<Button  
    android:onClick="onDigit"  
    android:layout_width="0dp"  
    android:layout_weight="1" 
    android:layout_height="match_parent"  
    android:text="@string/equality"  
    />
```
`android:text ...` add some string and use a mouse select  (show context actions) `extract string resource`

>Atrybut `android:layout_weight` jest używany w połączeniu z `android:layout_width="0dp"` w układach typu `LinearLayout` w celu rozdzielania dostępnej przestrzeni poziomej między elementami o równym wagom.

> Jeśli użyjesz `android:layout_width="0dp"` w połączeniu z `android:layout_weight`, oznacza to, że szerokość elementu zostanie dynamicznie dostosowana w zależności od wartości `android:layout_weight` oraz dostępnej przestrzeni na ekranie. Jeśli szerokość nie jest ustawiona na "0dp", to element będzie próbował zajmować tyle miejsca, ile jest potrzebne do wyświetlenia jego zawartości, a waga nie będzie miała wpływu na rozmiar elementu.


`android:onClick="onDigit"` 
```kotlin
fun onDigit(view: View){  
    // view will be a button that we click  
    tvInput?.append( (view as Button).text)  
}
```

>In Android development, the `View` parameter typically represents the UI element that triggered the click event, in this case, a button.

> `(view as Button)` is attempting to cast the `view` parameter to a `Button`. This is done because you want to access the `text` property, and `text` is typically associated with buttons in Android.
> `(view as Button).text` retrieves the text from the button that was clicked.


`onClick` is deprecated, you should use 
```kotlin
btnOne=findViewById(R.id.btnOne)
btnOne?.setOnClickListener{
	tvInput?.append("1")
}

```

add clear function
```kotlin
fun onClear(view: View){  
    tvInput?.text=""  
}
```

```xml
<Button  
    android:onClick="onClear"  
    android:id="@+id/btnClear"  
    android:layout_margin="2dp"  
    android:layout_width="0dp"  
    android:layout_height="match_parent"  
    android:layout_weight="1"  
    android:text="@string/clear"  
    />
```

add dot function
```kotlin
  
class MainActivity : AppCompatActivity() {  
  
    private var tvInput : TextView? = null  
    var lastNumeric : Boolean = false  
    var lastDot : Boolean = false
// ...
  
fun onDigit(view: View){  
    // view will be a button that we click  
    tvInput?.append( (view as Button).text)  
    lastNumeric = true  
    lastDot = false  
  
  
}

fun onDecimalPoint(view: View){  
    if(lastNumeric && !lastDot){  
        tvInput?.append(".")  
        lastNumeric = false  
        lastDot = true  
  
    }

```

----------------

## SUbtraction

```xml
<LinearLayout  
    android:layout_width="match_parent"  
    android:layout_height="wrap_content"  
    android:orientation="horizontal"  
    android:layout_weight="2"  
    >  
    <Button        
	    android:onClick="onEqual"  
        android:layout_width="0dp"  
        android:layout_height="match_parent"  
        android:layout_weight="1"  
        android:text="@string/equality"  
        />  
  
  
</LinearLayout>
```

```kotlin
fun onEqual(view: View){  
    if(lastNumeric){  
        var prefix = ""  
        var tvValue = tvInput?.text.toString()  
  
        try{  
            if(tvValue.startsWith("-")){  
                prefix="-"  
                tvValue=tvValue.substring(1)  
            }  
            if(tvValue.contains("-")){  
                var (one, two) = tvValue.split("-")  
  
                if(prefix.isNotEmpty()){  
                    one = prefix + one  
                }  
                tvInput?.text = (one.toDouble() - two.toDouble()).toString()  
  
            }  
  
  
        }catch(e: ArithmeticException){  
            e.printStackTrace()  
        }  
    }  
}
```






