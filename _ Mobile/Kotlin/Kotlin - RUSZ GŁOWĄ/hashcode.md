#kotlin/hashcode

>[!info] `hashCode` 
>- to jest metodą, która jest dziedziczona z klasy `Any`, bazowej klasy dla wszystkich klas w Kotlinie,
>- metoda `hashCode` służy do generowania liczbowego kodu skrótu (*hash code*), który jest używany w różnych kontekstach, takich jak:
>> - implementacje kolekcji, 
>> - indeksowania obiektów,
>> - porównywanie obiektów.


Główne zasady związane z metodą `hashCode` to:

1. **Consistency with equals**: Jeśli dwa obiekty są równe według metody `equals()`, to ich `hashCode` powinien zwracać tę samą wartość. Z tego wynika, że obiekty różne pod względem `equals()` powinny mieć różne `hashCode`.
    
2. **Konsystencja w czasie życia obiektu**: Dla danego obiektu, `hashCode` powinien zawsze zwracać tę samą wartość podczas trwania życia tego obiektu, jeśli żadna zmienna wpływająca na wynik `hashCode` nie została zmieniona.












