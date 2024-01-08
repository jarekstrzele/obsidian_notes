[[_ Rusz Głową Android. Programowanie aplikacji]]

> W tym rozdziale napiszemy aplikację składającą się z dwóch aktywności. 
> - Pierwsza z nich będzie umożliwiała wpisanie wiadomości.
> - Kliknięcie przycisku wyświetlanego w pierwszej aktywności spowoduje uruchomienie drugiej aktywności i przekazanie do niej treści wiadomości. Ta druga aktywność wyświetli wiadomość.

[[#Główna aktywność]]
[[#Druga Aktywność]]
[[#Intencje mogą uruchamiać aktywności w innych aplikacjach]]


# Główna aktywność
główne pliki:
- `CreateMessageActivity.kt`  
- `activity_create_message.xml`

>[!info] `<EditText>`
>- definiuje pole tekstowe służące do wpisywania danych
>- dziedziczy po `View` jak inne komponenty GUI ([[2. Tworzenie interaktywnych aplikacji]] )


```kotlin
class CreateMessageActivity : AppCompatActivity() {  
  
	private var edittextMessage: EditText? = null  
  
	override fun onCreate(savedInstanceState: Bundle?) {  
		super.onCreate(savedInstanceState)  
		setContentView(R.layout.activity_create_message)  
  
		edittextMessage = findViewById(R.id.edittext_message)  
  
		val buttonSender: Button = findViewById(R.id.buttonSend)  
buttonSender.setOnClickListener {  
		val textviewHello : TextView = findViewById(R.id.textview_hello)  
		textviewHello.text = edittextMessage?.text.toString()  
onSendMessage()  
	}  
}  
  
	private fun onSendMessage(){  
  
		val msg: String = edittextMessage?.text.toString()  
println(msg)  
  
		val intent: Intent = Intent(this, ReceiveMessageActivity::class.java).apply {  
	putExtra( "message", msg)  
}  
  
		startActivity(intent)  
  
	}  
}
```

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
xmlns:app="http://schemas.android.com/apk/res-auto"  
xmlns:tools="http://schemas.android.com/tools"  
android:layout_width="match_parent"  
android:layout_height="match_parent"  
android:padding="16dp"  
android:orientation="vertical"  
tools:context=".CreateMessageActivity">  
  
<EditText  
android:id="@+id/edittextMessage"  
android:layout_width="wrap_content"  
android:layout_height="wrap_content"  
android:layout_marginTop="20dp"  
android:hint="@string/hint"  
android:ems="10" />  
  
<Button  
android:id="@+id/buttonSend"  
android:layout_width="wrap_content"  
android:layout_height="wrap_content"  
android:layout_marginTop="20dp"  
  
android:text="@string/send"  
/>  
<TextView  
android:layout_width="wrap_content"  
android:layout_height="wrap_content"  
android:text="Hello World!"  
app:layout_constraintBottom_toBottomOf="parent"  
app:layout_constraintEnd_toEndOf="parent"  
app:layout_constraintStart_toStartOf="parent"  
app:layout_constraintTop_toTopOf="parent" />  
  
</LinearLayout>
```


# Druga Aktywność

[[Intencja]]
>[!info] intencje
>to komunikaty, których komponenty systemy Android używają do wzajemnej komunikacji

>[!info] `putExtra()`
>dodawanie dodatkowych informacji do intencji

>[!info] `get*Extra()`
>pobieranie dodatkowych informacji zapisanych w intencji


```xml
<?xml version="1.0" encoding="utf-8"?>  
	<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
	xmlns:app="http://schemas.android.com/apk/res-auto"  
	xmlns:tools="http://schemas.android.com/tools"  
	android:layout_width="match_parent"  
	android:layout_height="match_parent"  
	android:padding="16dp"  
	android:orientation="vertical"  
	tools:context=".ReceiveMessageActivity"
	>  
  
	<TextView  
		android:id="@+id/message"  
		android:layout_width="wrap_content"  
		android:layout_height="wrap_content"  
	  
	/>  
  
</LinearLayout>
```

[[companion object]]
```kotlin
class ReceiveMessageActivity : AppCompatActivity() {  
	companion object {  
		const val EXTRA_MESSAGE = "message"  
	}  
	
	override fun onCreate(savedInstanceState: Bundle?) {  
		super.onCreate(savedInstanceState)  
		setContentView(R.layout.activity_receive_message)  
  
		val intent = intent  
		val messageText = intent.getStringExtra(EXTRA_MESSAGE)  
		Log.i("msg", "$messageText")  
		val textviewMessage = findViewById<TextView>(R.id.message)  
		textviewMessage.text = messageText  
	}  
}
```

--------

# Intencje mogą uruchamiać aktywności w innych aplikacjach

>Aktywność należąca do naszej aplikacji przekazuje systemowi intencję, ten ją sprawdza, a następnie nakazuje uruchomienie drugiej aktywności, ==nawet jeśli będzie ona należeć do innej aplikacji==


#kotlin/actions
>[!info] akcje
>są to sposoby pozwalające na poinformowanie systemu android o tym, jakie standardowe operacje moe wykonywać dana aktywność

## metoda `Intent.createChooser()`
- wyświetla okno dialogowe wyboru aktywności
- Metoda ta pobiera utworzoną intencję i przekazuje ją do okna dialogowego wyboru aktywności.
- W przypadku zastosowania tej metody wyświetlone okno dialogowe nie daje możliwości określania aktywności domyślnej — użytkownik będzie proszony o wybór aktywności za każdym razem.

```kotlin
val chosenIntent = Intent.createChooser(intent, "Wysyłanie wiadomości...")

```

> Metoda `createChooser()` 
> POBIERA dwa parametry:
> 	- *intencję* i 
> 	- *opcjonalny* łańcuch znaków określający tytuł wyświetlanego okna dialogowego. 
> ZWRACA:
> 	- obiekt `Intent`
> 
> Możemy do niej przekazać utworzoną wcześniej intencję, tę, która korzysta z akcji `ACTION_SEND` i używa danych tekstowych.













