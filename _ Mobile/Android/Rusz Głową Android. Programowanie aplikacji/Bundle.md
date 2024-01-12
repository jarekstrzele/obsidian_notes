#kotlin/bundle

>[!definition] Bundle
>- klasa `Bundle` jest używana do przechowywania i przesyłania danych między różnymi komponentami aplikacji.
>- dane są przechowywane w formie par klucz-wartość. Klucze są zazwyczaj ciągami znaków, a wartościami mogą być różne typy danych
>

`Bundle` jest często wykorzystywane w kontekście:
- przekazywania danych między 
	- aktywnościami, 
	- fragmentami, 
	- usługami.
```kotlin
val bundle = Bundle()
bundle.putString("key", "wartość")
// Przypięcie bundla do intencji aktywności
val intent = Intent(this, SecondActivity::class.java)
intent.putExtras(bundle)
startActivity(intent)

```
- obsługi cyklu życia aplikacji, takim jak 
	- zapisywanie,
	- odtwarzanie stanu aktywności.
```kotlin
override fun onSaveInstanceState(outState: Bundle) {
    super.onSaveInstanceState(outState)
    outState.putString("key", "wartość")
}

override fun onRestoreInstanceState(savedInstanceState: Bundle) {
    super.onRestoreInstanceState(savedInstanceState)
    val value = savedInstanceState.getString("key")
}

```









