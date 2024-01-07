[[_ Rusz Głową Android. Programowanie aplikacji]]

> W tym rozdziale napiszemy aplikację składającą się z dwóch aktywności. 
> - Pierwsza z nich będzie umożliwiała wpisanie wiadomości.
> - Kliknięcie przycisku wyświetlanego w pierwszej aktywności spowoduje uruchomienie drugiej aktywności i przekazanie do niej treści wiadomości. Ta druga aktywność wyświetli wiadomość.

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
>
```xml
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"  
xmlns:app="http://schemas.android.com/apk/res-auto"  
xmlns:tools="http://schemas.android.com/tools"  
android:layout_width="match_parent"  
android:layout_height="match_parent"  
android:padding="16dp"  
android:orientation="vertical"  
tools:context=".ReceiveMessageActivity">  
  
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











