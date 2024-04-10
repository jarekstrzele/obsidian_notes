
# PROBLEM
> val `intent = Intent(this@MainActivity, SecondActivity : : class.java)` nie rozumiem syntaktyki `SecondActivity : : class.java`, dlaczego nie można przekazać po prostu `SecondActivity`



W Kotlinie, kiedy przekazujesz klasę jako argument do funkcji lub konstruktora (tak jak w przypadku tworzenia `Intent`), musisz użyć specjalnej składni, aby uzyskać referencję do obiektu `Class` tej klasy. Składnia `SecondActivity::class` jest używana w Kotlinie do uzyskania odniesienia do obiektu `KClass`, który reprezentuje klasę `SecondActivity`. Jednak Android SDK jest napisane w Javie, a konstruktor `Intent` oczekuje obiektu `Class` z Javy jako argumentu. Dlatego dodajesz `.java`, aby przekonwertować obiekt `KClass` Kotlinowego odniesienia klasy na obiekt `Class` Javy.

### Przykład składni:

- **W Kotlinie:** Używasz `Klasa::class` do uzyskania referencji do klasy w Kotlinie, co daje ci obiekt `KClass`.
- **Dostosowanie do Javy:** Aby użyć tej referencji klasy z kodem Javy (takim jak Android SDK), konwertujesz ją na obiekt `Class` używany w Javie, dodając `.java` na końcu (np., `SecondActivity::class.java`).

### Dlaczego nie można użyć po prostu `SecondActivity`?

- **Typ Oczekiwany:** Konstruktor `Intent` w Androidzie oczekuje obiektu typu `Class`. Samo `SecondActivity` odnosi się do nazwy klasy, ale nie jest obiektem typu `Class`, który jest wymagany do identyfikacji komponentu w kontekście Androida.
    
- **Konsystencja z Javą:** Android SDK został pierwotnie napisany dla Javy, gdzie do przekazania klasy jako argumentu używa się `SecondActivity.class`. Kotlin zapewnia interoperacyjność z Javą, dlatego konieczne jest stosowanie `.java` po `::class`, aby uzyskać odpowiedni obiekt typu `Class` dla kodu Javy.

#kotlin/object_class
Obiekt typu `Class` w Javie jest podstawą refleksji w tej języku programowania. Refleksja umożliwia programowi introspekcję, czyli możliwość badania lub modyfikacji wewnętrznej struktury i zachowania programu w czasie wykonywania. Obiekt `Class` reprezentuje klasę lub interfejs w czasie wykonania.

Każdy typ danych w Javie (klasy, interfejsy, tablice, typy prymitywne) jest reprezentowany w czasie wykonania przez obiekt typu `Class`. Daje to możliwość badania struktury klasy, uzyskiwania informacji o jej metodach, polach, konstruktorach, a także tworzenia nowych instancji obiektów, wywoływania metod i tak dalej.

### Kluczowe funkcje obiektów typu `Class`:

- **Identifikacja Typu:** Pozwala sprawdzić, jakiego typu jest dany obiekt w czasie wykonania.
- **Tworzenie Instancji:** Możliwość tworzenia nowych instancji klas za pomocą metody `newInstance()` (choć w nowszych wersjach Javy zalecane jest używanie innych, bezpieczniejszych metod, np. poprzez konstruktory z dostępu do obiektu `Constructor`).
- **Introspekcja:** Umożliwia badanie klasy, w tym listowania jej metod, pól, konstruktorów, superklas i interfejsów, które implementuje.
- **Ładowanie Klas:** Możliwość dynamicznego ładowania klas do programu w czasie jego działania.

### Jak uzyskać obiekt typu `Class`?

Można go uzyskać na kilka sposobów, między innymi poprzez:

- Użycie właściwości `class` na obiekcie reprezentującym klasę, np. `String.class` w Javie lub `String::class.java` w Kotlinie.
- Wywołanie metody `getClass()` na instancji obiektu, np. `mojObiekt.getClass()`.
- Użycie metody `Class.forName(String nazwaKlasy)` do dynamicznego ładowania klasy na podstawie jej nazwy jako ciągu znaków.





















