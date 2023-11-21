#kotlin/spinner

> W poniższym kodzie jest inicjalizowany `Adapter` dla komponentu Spinner.
> 	 - ==Adapter jest pośrednikiem== między źródłem danych (w tym przypadku tablicą `categories`) a komponentem Spinner. --
> 	 - Adapter 
> 		 - dostarcza dane do wyświetlenia w Spinnerze i 
> 		 - obsługuje
> 			 - wybór użytkownika oraz 
> 			 - sposób, w jaki dane są wyświetlane w Spinnerze.


```kotlin

lateinit var mySpinner: Spinner

override fun onCreate(savedInstanceState: Bundle?) {  
    super.onCreate(savedInstanceState)  
    setContentView(R.layout.activity_main)

val soups = arrayOf("Pomidorówka", "Rosół", "Ramen")  
val adapter = ArrayAdapter(this, android.R.layout.simple_spinner_item, categories)  
adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)  
mySpinner.adapter = adapter  
  
mySpinner.onItemSelectedListener = object : AdapterView.OnItemSelectedListener {  
    override fun onItemSelected(parent: AdapterView<*>?, view: View?, position: Int, id: Long) {  
        val selectedCategory = categories[position]  
       Toast.makeText(applicationContext , selectedCategory, Toast.LENGTH_LONG).show()  
    }  
  
    override fun onNothingSelected(parent: AdapterView<*>?) {  
        Toast.makeText(applicationContext , "Nic nie wybrano", Toast.LENGTH_LONG).show()  
  
    }  
}


}
```


> `ArrayAdapter(this, android.R.layout.simple_spinner_item, categories)`: W tym kroku
> 	- tworzony jest adapter typu `ArrayAdapter`. 
> 	- `this` odnosi się do bieżącej aktywności lub kontekstu, w której ten kod jest wykonywany. 
> 	- drugi argument, `android.R.layout.simple_spinner_item`, to gotowy do użycia zasób dostarczony przez system Android, który definiuje sposób, w jaki pojedyncza opcja będzie wyświetlana w rozwijanej liście Spinnera.
> 	- ostatni argument `categories` to tablica lub lista opcji, które chcesz wyświetlić w Spinnerze.

> `adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)`: W tym kroku 
> 	- ustawiasz specjalny zasób (`simple_spinner_dropdown_item`) jako wygląd elementów rozwijanej listy Spinnera.
> 	- ten zasób definiuje sposób, w jaki opcje będą wyglądać w rozwijanej liście, co może być nieco innym wyglądem niż pojedyncza opcja w zamkniętym Spinnerze.

> `categorySpinner.adapter = adapter`: Przypisujesz przygotowany adapter do Spinnera, co powoduje, że dane z tablicy `categories` zostaną wyświetlone w Spinnerze. Spinner teraz używa dostosowanego adaptera do obsługi wyboru opcji.







