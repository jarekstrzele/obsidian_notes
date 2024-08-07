[[_ Kotlin bez tajemnic]]

------------

[[3.1. Fragments]]
[[3.2. View Models]]
[[3.3. View Binding]]


-----------------
# Android Studio 
- `File>Settings>Plugin`:
	- rainbow brackets
	- nyan progress bar


# Activity and lifecycle

- `: AppCompatActivity()` dziedziczenie po tej klasie sprawia, że dana klasa jest `activity`
- definicja startowej aktywności  oraz wszystkie pozostałe aktywności w `AndroidManifest`

```xml
<activity  
    android:name=".MainActivity"  
    android:exported="true"  
    android:screenOrientation="portrait">  
    <intent-filter>  
        <action android:name="android.intent.action.MAIN" />  
  
        <category android:name="android.intent.category.LAUNCHER" />  
    </intent-filter>  
</activity>
```

- aktywności należy dzielić na fragmenty, a nie tworzyć nowe aktywności
- 



------
# View models

## **MVVM**
- widok/*view* to w naszym przypadku fragment i aktywność:
	- odpowiadają za wyświetlanie treści
	- odpowiadają za odbieranie akcji użytkownika
	- jest połączony z *view model*
- *view model* :
	- tu zachodzi cała logika biznesowa:
		- np. pobieranie informacji z modelu
		- np. zapisywanie zmodyfikowanych danych do repozytorium



## MVVM w Androidzie
0. DODAWANIE - dodaj do `build.gradle` biblioteki :
	- `fragment` - `implementation 'androidx.fragment-ktx:.4.0' `
	- `lifecycle` - 
		- `implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.4.0'`
		- `implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.4.0'`
		- `implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.4.0'`
	zsynchronizuj projekt

1. TWORZENIE VIEWMODELS - stworzymy `viewmodele` dla `HomeFragment` i `MainActivity`:
	- `new>kotlin class> <nazwa jak klasa, której służą z sufiksem ViewModel>` - np. `HomeFragmentViewModel` albo `MainActivityViewModel`
	- ta nowa klasa musi dziedziczyć z `ViewModel()`
2. PORZĄDKI - aby uporządkować pliki:
	- utwórz folder `home` z zawartością `new>package> <packagename>.home`:
		- `HomeFragment`
		- `HomeFragmentViewModel`
	- utwórz folder `main` z zawartością:
		- `MainActivity`
		- `MainActivityViewModel`


4. PODPIĘCIE  `viewmodels` do ich `view`:
	- w `MainActivity` dodaj "globalną"/atrybut obiektu zmienną `private val viewModel: MainActivityViewModel by viewModels` (*by viewModels* stworzy instancję klasy `MainAcitivityViewModel`, oczywiście `viewModels` trzeba do importować)
	- w `HomeFragment` dodaj "globalną"/atrybut obiektu zmienną `private val viewModel: HomeFragmentViewModel by viewModels` (*by viewModel* stworzy instancję klasy `HomeFragmentViewModel`, oczywiście `viewModels` trzeba do importować)

5.  PODZIAŁ odpowiedzialności
	- widok wyświetla dane, *viewModel* zajmuje się logiką biznesową
	- `viewModel` będzie zarządzał zawartością pola tekstowego 
	- `fragment` będzie wyświetlał przekazaną informację
dodatkowy kod:
- w layoucie `fragment_home.xml` `TextView` nadajemy id  `my_textview`
- w `HomeFragment.kt` zmieniamy
```kotlin
...

onCreateView(....){

	val view = inflater.inflate(R.layout.fragment_home, containte, false)

	val myTextView = view.findViewById<TExtView>(R.id.my_textview)
	//myTextView.text = "a new text from fragment" // jest niezgodny ze wzorcem MVVM, bo to viewmodel ma zarządzać zawartością pola text
	myTextView.text = viewModel.getText()
	
	
	return view

}
```

```kotlin
class HomeFragmentViewModel: ViewModel(){
	//fun getText(): String {
	//	return "a new text from viewmodel"
	//} // równoważna jej funkcja:
	fun getText()= "a new text from viewmodel"

}
```

--------








