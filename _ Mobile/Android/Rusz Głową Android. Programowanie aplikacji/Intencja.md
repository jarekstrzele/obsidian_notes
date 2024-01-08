#android/intention 

[[_ Rusz Głową Android. Programowanie aplikacji]]

>[!info] intencja
>- to rodzaj komunikatu
>- zawsze, gdy chcemy uruchomić jedną aktywność z poziomu innej aktywności, musimy w tym celu użyć **intencji**
>- jeśli jedna aktywność chce uruchomić drugą, robi to, przesyłając do systemu Android odpowiednią intencję.
>

# Intencje jawne *explicit intent*

## przykład jawne intencji
### `KlasaDocelowa::class.java`
 jawnie informujemy system, którą klasę ma uruchiomić

```kotlin
val intent = Intent(this, KlasaDocelowa::class.java)
intent.putExtra( "message", value) // przysyłanie wartość przez klucz "message"
startActivity(intent) 
```
`this` informuje system, z jakiego obiektu pochodzi intencja.
`KlasaDocelowa::class.java` nazwa klasy aktywności, do której intencja jest skierowana.
`startActivity(intent)` uruchamia aktywność określoną w intencji


> Kiedy Android odbierze intencję, sprawdza, czy wszystko jest w porządku, po czym uruchamia aktywność. Jeśli aktywności nie uda się odnaleźć, zgłaszany jest wyjątek ActivityNotFoundException.

>[!definition] class reference
> - it is an object that represents the class itself
> - to obtain a class reference use `::class` syntax
> - the reference is an instance of the `KClass`
> 	- e.g.:
> 		- `SomeClass::class` provides a reference to the `SomeClass`
> 		- `SomeClass::class.java` provides the `Class`  object for the `SomeClass` class



# Intencje niejawne *implicit intent*
Jeżli chcemy wykonać okreśłoną czynność, kecz nie interesuje nas, która aktywność to zrobi, to możemy utworzyć intencję niejawną. W takim przypadku określamy akcję, którą chcemy wykonać , pozostawiając Androidowi możliwość doboru odpowiednich aktywności

### `val intent = Intent(action)`
`action` określa typ akcji, którą aktywność ma wykonać
przykłady:
- `Intent.Action_DIAL` akcja, pozwalając wybrać numer telefonu
- `Intent.ACTION_WEB_SEARCH` akcja pozwalająca wyszukać frazę w internecie
- `Intent.ACTION_SEND` akcja pozwalająca na wysłanie wiadomości

```kotlin
val intent = Intent(Intent.ACTION_SEND)

```

```kotlin
val intent = Intent(Intent.ACTION_SEND)
intent.type = "text/plain"
intent.putExtra(Intent.EXTRA_TEXT, messageText)

```
`text/plain` to MIME Type: [[MIME TYPE]]

ten sam kod z `apply`
```kotlin
val intent = Intent(Intent.ACTION_SEND).apply {
    type = "text/plain"
    putExtra(Intent.EXTRA_TEXT, messageText)
}

```


zmiana pliku `CreateMessageActivity`
```kotlin
  
private fun onSendMessage(){  
  
	val msg: String = edittextMessage?.text.toString()  
	println(msg)  
	  
	// val intent: Intent = Intent(this, ReceiveMessageActivity::class.java).apply {  
	// putExtra( "message", msg)  
	// }  
	val intent = Intent(Intent.ACTION_SEND).apply {  
	type = "text/plain"  
	putExtra(Intent.EXTRA_TEXT, msg)  
	}  
	  
	  
	startActivity(intent)  
	  
}
```

## Filtr intencji niejawnej *intent filter*
Filtr intencji określa typ intencji, które mogą być obsługiwane przez dany komponent.

przykład - *AndroidMainfest.xml*:
```xml
<activity android:name=”ShareActivity”>
	<intent-filter>
	
		<action android:name=”android.intent.action.SEND”/>
		<category android:name=”android.intent.category.DEFAULT”/>
		<data android:mimeType=”text/plain”/> 
		<data android:mimeType=”image/*”/>

	</intent-filter>
</activity>
```

`.action.SEND` aktywność jest w stanie obsługiwać akcję *ACTION_SEND*
`DEFAULT` filtr intencji  musi określać kategorię o wartości DEFAULT, aby mógł obsługiwać intencje niejawne

