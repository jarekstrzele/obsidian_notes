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

Na obiektach Bundle używamy następujących metod:

- `putXxx()` - metody te służą do dodawania danych do obiektu `Bundle`.
- `getXxx()` - metody te służą do pobierania danych z obiektu `Bundle`.
- `containsKey()` - metoda ta sprawdza, czy obiekt `Bundle` zawiera dane o podanym kluczu.
- `clear()` - metoda ta usuwa wszystkie dane z obiektu `Bundle`.

np. `putInt(key, value)`, `putBoolean(key, value)`

Obiekt `Bundle` to coś więcej niż zwykła mapa z Javy:
>Obiekty klasy Bundle mają dodatkowe możliwości, którymi nie dysponują mapy. Na przykład można je przekazywać pomiędzy procesami. To naprawdę bardzo przydatna możliwość, gdyż pozwala Androidowi mieć dostęp do bieżącego stanu aktywności.



