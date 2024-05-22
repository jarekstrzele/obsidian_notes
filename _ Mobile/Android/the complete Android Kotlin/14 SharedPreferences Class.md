[[_ the complete Android Kotlin]]

# SharedPreference Class Description

- Android provides many ways of storing data
- Shared Preferences Class is just one of them:
	- with that class you can save primitive types of data:
		- integer
		- boolean
		- string
		- ...
	- you can save and retrieve data in the form of *key-value pair.*
	- you can reach the save data types anywhere within the application
	- use that class: a transition between running apps
		- you do a text msg, and a call is coming, so your app with text will be stopped)
		- you play a game and a phone call is coming, so game data have to be saved
		- in a logg-in situation
	- 


# Saving Data Local Memory

## `getSharedPreferences`

Metoda `getSharedPreferences` jest używana do uzyskania instancji `SharedPreferences`, która jest specyficzna dla Twojej aplikacji. `SharedPreferences` pozwala na przechowywanie par klucz-wartość, które są zachowywane pomiędzy sesjami aplikacji.

### Argumenty `getSharedPreferences`

1. **Pierwszy argument: `"saveData"`**
    
    - **Typ:** `String`
    - **Opis:** Nazwa pliku, w którym będą przechowywane dane.
    - **Szczegóły:**
        - Jest to nazwa pliku preferencji, który będzie przechowywany w wewnętrznej przestrzeni dyskowej Twojej aplikacji. Plik ten będzie dostępny tylko dla Twojej aplikacji.
        - Możesz użyć dowolnej unikalnej nazwy, aby odróżnić różne zestawy preferencji, np. `"userPreferences"`, `"appSettings"` itp.
2. **Drugi argument: `Context.MODE_PRIVATE`**
    
    - **Typ:** `Int`
    - **Opis:** Tryb dostępu do pliku preferencji.
    - **Szczegóły:**
        - `Context.MODE_PRIVATE` oznacza, że plik preferencji jest dostępny tylko dla Twojej aplikacji (nie może być odczytywany ani zapisywany przez inne aplikacje). Jest to najczęściej używany tryb, ponieważ zapewnia prywatność danych.
        - Inne dostępne tryby (które obecnie są przestarzałe i zazwyczaj nie są używane) to:
            - `Context.MODE_APPEND`: Otwiera plik preferencji w trybie dołączania, co oznacza, że nowe dane będą dołączane do istniejących danych.
            - `Context.MODE_WORLD_READABLE` (przestarzałe): Umożliwia odczyt danych przez inne aplikacje.
            - `Context.MODE_WORLD_WRITEABLE` (przestarzałe): Umożliwia zapis danych przez inne aplikacje.

### Poprawny sposób użycia `SharedPreferences`

1. **Inicjalizacja `SharedPreferences`**: `getSharedPreferences` jest używane do uzyskania instancji `SharedPreferences`, która identyfikuje plik, w którym będą przechowywane dane.
    
2. **Zapis danych**: Za pomocą metody `edit` uzyskujesz edytor (`SharedPreferences.Editor`), który umożliwia zapisanie danych.
    
3. **Odczyt danych**: Metody takie jak `getString`, `getInt`, `getBoolean` są używane do odczytywania zapisanych danych.









