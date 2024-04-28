#andoird/arguments

## definicja
>[!important] `arguments`
> W Kotlinie i w platformie Android, `arguments` jest
>  **predefiniowanym właściwością każdego fragmentu**, 
>  która **zwraca** `Bundle` z argumentami skojarzonymi z fragmentem. 
>  Nie musisz deklarować `arguments` w metodzie `onCreateView` ani w żadnej innej metodzie, ponieważ `arguments` jest już zintegrowaną właściwością klasy `Fragment`.

## ustawianie
```kotlin
val fragment = MyFragment()
val args = Bundle()
args.putInt("key", value)
fragment.arguments = args

```


## odczytywanie
```kotlin
val value = arguments?.getInt("key", defaultValue)

```


W kontekście Androida i fragmentów, **argument** to zestaw danych, które mogą być przekazane do fragmentu przed jego załączeniem do aktywności. Argumenty są używane do przekazywania informacji do fragmentu, zwykle podczas jego tworzenia. Są one podobne do "intent extras" używanych w aktywnościach do przekazywania danych między różnymi komponentami.

### Jak działają argumenty w fragmentach:

1. **Przechowywanie danych**: Argumenty są przechowywane w obiekcie `Bundle`, który jest rodzajem mapy klucz-wartość używanej do przechowywania różnych typów danych, takich jak `String`, `int`, `boolean`, itp.
    
2. **Bezpieczne przekazywanie**: Argumenty są ustawiane przed dołączeniem fragmentu do aktywności i są dostępne nawet po ponownym utworzeniu fragmentu, np. po obrocie ekranu. To zapewnia bezpieczny sposób na przekazywanie danych między cyklami życia fragmentu.
    
3. **Odzyskiwanie danych**: Możesz odzyskać dane przekazane jako argumenty w metodzie `onCreate`, `onCreateView`, lub później, korzystając z metody `getArguments()`, która zwraca `Bundle` z wszystkimi ustawionymi argumentami.
    

### Przykład użycia argumentów w fragmencie:

kotlinCopy code

`companion object {     fun newInstance(imageId: Int, title: String, description: String): DetailsFragment {         val fragment = DetailsFragment()         val args = Bundle()         args.putInt("imageId", imageId)         args.putString("title", title)         args.putString("description", description)         fragment.arguments = args         return fragment     } }`

W powyższym przykładzie:

- Tworzymy nową instancję `DetailsFragment`.
- Tworzymy `Bundle` i dodajemy do niego kilka danych.
- Przypisujemy ten `Bundle` jako argumenty fragmentu za pomocą `fragment.arguments = args`.
- W metodzie `onCreateView` fragmentu, możesz później odzyskać te wartości, jak pokazano w Twoim kodzie:

kotlinCopy code

`val imageId = arguments?.getInt("imageId") ?: R.drawable.default_image val title = arguments?.getString("title") ?: "Domyślny tytuł" val description = arguments?.getString("description") ?: "Domyślny opis"`

### Dlaczego warto używać argumentów:

- **Zachowanie stanu**: Argumenty pomagają zachować stan i informacje, kiedy fragment jest ponownie tworzony po zmianie konfiguracji urządzenia, takiej jak obrót ekranu.
- **Modularyzacja**: Pozwalają na tworzenie bardziej modularnego i ponownie używalnego kodu fragmentów.
- **Bezpieczeństwo**: Argumenty są zarządzane przez system Android i są bezpiecznie przechowywane przez cykle życia fragmentu, co zapewnia, że dane nie zostaną utracone.

Podsumowując, argumenty w fragmentach Androida stanowią efektywny sposób na przekazywanie i przechowywanie danych w ramach fragmentu, zabezpieczając aplikację przed utratą danych w trakcie cyklu życia fragmentu.







