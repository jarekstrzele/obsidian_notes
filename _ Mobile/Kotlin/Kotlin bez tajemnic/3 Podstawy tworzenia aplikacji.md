[[_ Kotlin bez tajemnic]]

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


# Fragment
- reprezentują zachowanie lub część interfejsu aktywności 
- nie może istnieć fragment bez aktywności, ale aktywność może istnieć bez fragmentu
- posiadają własny widok, ale ich cykl życia zależny jest od aktywności
- są modularne
- można je wielokrotnie wykorzystywać

>[!definition] Fragmenty w Androidzie
> są częściami interfejsu użytkownika lub zachowania aplikacji, które można zintegrować w aktywność, pozwalając na bardziej modułową i wielokrotnego użytku konstrukcję interfejsu.
> Oto kilka kluczowych informacji o fragmentach w Androidzie:
>	1. **Modułowość**: Fragmenty pozwalają deweloperom podzielić interfejs użytkownika na niezależne, wielokrotnego użytku komponenty, co ułatwia zarządzanie i ponowne wykorzystanie kodu.
>	2. **Łatwa integracja**: Fragmenty mogą być łatwo zintegrowane wewnątrz aktywności, co pozwala na elastyczne zarządzanie interfejsami użytkownika w zależności od wielkości ekranu, orientacji urządzenia itp.
>	3. **Cykl życia**: Fragmenty posiadają swój własny cykl życia, co oznacza, że posiadają metody takie jak `onCreate()`, `onStart()`, `onPause()`, `onStop()`, `onDestroy()`, które odpowiadają za zarządzanie ich stanem.
>	4. **Komunikacja między fragmentami**: Fragmenty mogą komunikować się ze sobą poprzez aktywność, co pozwala na wymianę danych i interakcję pomiędzy nimi.
>	5. **Obsługa wielu ekranów**: Fragmenty są używane do tworzenia aplikacji, które mogą dostosowywać swój interfejs użytkownika do różnych rozmiarów ekranów urządzeń.

## tworzenie fragmentu

### automatyczne
new>Fragment>..


### ręczne
#### utwórz nową klasę kotlina
`HomeFragment.kt`
```kotlin
package com.example.cookbook  
  
import androidx.fragment.app.Fragment  
  
class HomeFragment : Fragment() {  
}
```

#### dodaj widok Fragmentu res>layout> new layout resource `fragment_home`
```xml
<?xml version="1.0" encoding="utf-8"?>  
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent">  
  
    <TextView  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:text="Hello from fragment"  
        app:layout_constraintBottom_toBottomOf="parent"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintStart_toStartOf="parent"  
        app:layout_constraintTop_toTopOf="parent" />  
  
</androidx.constraintlayout.widget.ConstraintLayout>
```

#### połącz ten xml z kotlinem 
(inflate - nadmuchaj)
`HomeFragment.kt`
```kotlin
class HomeFragment : Fragment() {  
  
    override fun onCreateView(  
        inflater: LayoutInflater,  
        container: ViewGroup?,  
        savedInstanceState: Bundle?  
    ): View? {  
        return inflater.inflate(R.layout.fragment_home, container, false)  
    }  
}

```

> `inflater.inflate(R.layout.fragment_home, container, false)`: Ta linia kodu odpowiada za "nadmuchanie" (*inflation*) interfejsu użytkownika fragmentu z zasobów XML. 
> >	`R.layout.fragment_home` określa widok fragmentu do nadmuchania, 
> >	`container` to rodzic widoku, do którego ten widok fragmentu zostanie dołączony, a 
> >	`false` oznacza, że widok nie będzie dołączony do rodzica automatycznie (to jest zadanie aktywności lub fragmentu nadrzędnego).


#### dołącz fragment do `activity_main.xml`
usuń `TextView`
w jego miejsce dodaj:
- nadaj id temu `FragmentContainerView`
- połącz go z kotlinowym HomeFragment `android:name="com.example.cookbook.HomeFragment"`
```xml
<androidx.fragment.app.FragmentContainerView  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    android:id="@+id/fragment_container"  
    android:name="com.example.cookbook.HomeFragment"/>	 

```

####  wstrzyknij fragment do tego widoku, czyli zmień `MainActivity.kt`
```kotlin
class MainActivity : AppCompatActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        setContentView(R.layout.activity_main)  
        addFragment()  
    }  
  
    private fun addFragment() {  
       supportFragmentManager.beginTransaction().add(R.id.fragment_container, HomeFragment()).commit()  
  
    }  
  
}
```

`addFragment`:
odpowiedzialna za dodanie fragmentu do interfejsu użytkownika aplikacji:
	1. `supportFragmentManager.beginTransaction()`: Rozpoczyna nową transakcję, która umożliwia modyfikację fragmentów powiązanych z tą aktywnością.
	2. `add(R.id.fragment_container, HomeFragment())`: Dodaje nowy fragment do kontenera określonego przez identyfikator `R.id.fragment_container`. `HomeFragment()` tworzy nową instancję fragmentu `HomeFragment`, która będzie dodana do kontenera.
	3. `commit()`: Potwierdza transakcję, co oznacza, że wszystkie operacje dodawania fragmentu zostaną zatwierdzone i zastosowane.



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

1. TWORZENIE VIEWMODELS - stworzymy `viewmodele` dla `HomeFragment` i `MainActivity`:
	- `new>kotlin class> <nazwa jak klasa, której służą z sufiksem ViewModel>` - np. `HomeFragmentViewModel` albo `MainActivityViewModel`
	- ta nowa klasa musi dziedziczyć z `ViewModel()`
2. PORZĄDKI - aby uporządkować pliki:
	- utwórz folder `home` z zawartością:
		- `HomeFragment`
		- `HomeFragmentViewModel`
	- utwórz folder `main` z zawartością:
		- `MainActivity`
		- `MainActivityViewModel`
3. DODAWANIE - dodaj do `build.gradle` biblioteki :
	- `fragment` - `implementation 'androidx.fragment-ktx:.4.0' `
	- `lifecycle` - 
		- `implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.4.0'`
		- `implementation 'androidx.lifecycle:lifecycle-livedata-ktx:2.4.0'`
		- `implementation 'androidx.lifecycle:lifecycle-runtime-ktx:2.4.0'`
	zsynchronizuj projekt

4. PODPIĘCIE  `viewmodels` do ich `view`:
	- w `MainActivity` dodaj "globalną"/atrybut obiektu zmienną `private val viewModel: MainActivityViewModel by viewModels` (*by viewModel* stworzy instancję klasy `MainAcitivityViewModel`, oczywiście `viewModels` trzeba doimportować)
	- w `HomeFragment` dodaj "globalną"/atrybut obiektu zmienną `private val viewModel: HomeFragmentViewModel by viewModels` (*by viewModel* stworzy instancję klasy `HomeFragmentViewModel`, oczywiście `viewModels` trzeba doimportować)

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
# View binding








