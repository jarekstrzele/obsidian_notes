#android/sharedpreferences

Obiekty `SharedPreferences` są używane w Androidzie do przechowywania prostych danych w formacie klucz-wartość. Są idealne do przechowywania danych konfiguracyjnych, ustawień aplikacji lub innych niewielkich ilości danych, które muszą być zachowane pomiędzy sesjami użytkownika. Oto kilka kontekstów, w których `SharedPreferences` są często używane:

# 1. **Przechowywanie ustawień aplikacji**
`SharedPreferences` są często używane do przechowywania ustawień aplikacji, takich jak preferencje użytkownika dotyczące wyglądu aplikacji, języka, powiadomień itp.

```kotlin
val sharedPreferences = getSharedPreferences("appSettings", Context.MODE_PRIVATE)

val editor = sharedPreferences.edit()
editor.putBoolean("darkMode", true)
editor.apply()

```

# 2. **Przechowywanie danych użytkownika**
Możesz przechowywać dane takie jak imię użytkownika, email, preferencje itp.
```kotlin
val sharedPreferences = getSharedPreferences("userPrefs", Context.MODE_PRIVATE)
val editor = sharedPreferences.edit()
editor.putString("userName", "John Doe")
editor.putString("email", "john.doe@example.com")
editor.apply()

```

# 3. **Śledzenie stanu aplikacji**
`SharedPreferences` mogą być używane do śledzenia stanu aplikacji, np. ostatnio otwartej karty, postępu użytkownika w grze itp.
```kotlin
val sharedPreferences = getSharedPreferences("appState", Context.MODE_PRIVATE)
val editor = sharedPreferences.edit()
editor.putInt("lastOpenedTab", 2)
editor.putInt("userLevel", 5)
editor.apply()

```

# 4. **Przechowywanie tokenów i sesji**
Możesz używać `SharedPreferences` do przechowywania tokenów autoryzacyjnych lub identyfikatorów sesji.
```kotlin
val sharedPreferences = getSharedPreferences("authPrefs", Context.MODE_PRIVATE)
val editor = sharedPreferences.edit()
editor.putString("authToken", "abcdef123456")
editor.apply()

```

# 5. **Konfiguracja interfejsu użytkownika**
Przechowywanie ustawień dotyczących interfejsu użytkownika, takich jak układ siatki, rozmiar czcionki, itd.
```kotlin
val sharedPreferences = getSharedPreferences("uiPrefs", Context.MODE_PRIVATE)
val editor = sharedPreferences.edit()
editor.putInt("gridSize", 4)
editor.putString("fontSize", "medium")
editor.apply()

```

