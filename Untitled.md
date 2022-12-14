
# OOP
## PO Programowanie obiektowe


## KLASA
- definicja obiektu
- wzorzec ("drukarka")

## Obiekt
- instancja/wystąpienie klasy
- ma:
  - tożsamość
  - atrybuty (aktualny stan obiektu)
  - metody (funkcje zdefiniowane w klasie)

  
  

>[!info] **Abstrakcja**
>Każdy obiekt w systemie służy jako model abstrakcyjnego
>„wykonawcy”, który może wykonywać pracę, 
>opisywać i zmieniać swój stan oraz komunikować się z innymi obiektami w systemie
> bez ujawniania, w jaki sposób zaimplementowano dane cechy. 
> Klasa stanowi zamkniętą całość.

>[!info] **Hermetyzacja**
>Inaczej: ukrywanie implementacji, enkapsulacja. Zapewnia,
>że obiekt nie może zmieniać stanu wewnętrznego innych obiektów w nieoczekiwany sposób. Tylko własne metody obiektu są uprawnione do zmiany jego stanu.
> Każdy typ obiektu prezentuje innym obiektom swój interfejs, który określa dopuszczalne metody współpracy.


>[!info] **Polimorfizm**
>Referencje i kolekcje obiektów mogą dotyczyć obiektów różnego typu, 
>a wywołanie metody dla referencji spowoduje zachowanie odpowiednie dla pełnego typu obiektu wywoływanego.
> Jeśli dzieje się to w czasie działania programu, 
> wówczas nazywa się to późnym wiązaniem lub wiązaniem dynamicznym.
  

>[info] **Dziedziczenie**
>Porządkuje i wspomaga polimorfizm i enkapsulację dzięki umożliwieniu definiowania i tworzenia specjalizowanych obiektów na podstawie bardziej ogólnych. 
>Dla obiektów specjalizowanych nie trzeba redefiniować całej funkcjonalności, lecz tylko tę, której nie ma obiekt ogólniejszy.
>W typowym przypadku powstają grupy obiektów zwane klasami oraz grupy klas zwane drzewami.Odzwierciedlają one wspólne cechy obiektów.
 

```python
class A:
  def __init__(self,name):
    self.name=name

  def ide(self):
    print("obiekt klasy A idzie")

a = A("bobaTraba")
print(a.name)
a.ide()
```

## ZADANIE 1
Zgodnie z zasadami programowania obiektowego napisz program, który definiuje klasę `Osoba` i następujące metody:
  - `czytaj_dane()` i `wyświetl_dane()`.

Metoda `czytaj_dane()` pozwala na wprowadzenie do programu
takich danych jak:
 - nazwisko, 
 - imię i 
 - ulica. 

Metoda `wyświetl_dane()`  wyświetla na ekranie monitora wprowadzone wcześniej dane nazwisko, imię i ulica.







