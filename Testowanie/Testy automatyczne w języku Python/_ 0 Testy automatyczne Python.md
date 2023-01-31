#helion 

>[!info] test jednostkowy
>test, który sprawdza pojedyczną funkjonalność (jedna funkcja, jedna metoda)

>[!info] testy funkcjonalne
>sprawdzają całą funkcjonalność, a nie tylko jedną funckję

>[!info] testy behawioralne
>- sprawdzają, jak zachowuje się cała nasza aplikacja
>- czy z perspektywy użytkownika wszystko działa
>-(Selenium - sprawdzanie warstwy wizualnej)


# Unittest
#python/unittest
to wbudowana, podstawowa biblioteka  do testowania

TESTY JEDNOSTKOWE - sprawdzają najbardziej bazową funcjonalnosć
praktyka:
- nazwa pliku do testowania to np. `twitter.py`
- nazwa pliku, w której będzie test to `twitter_test.py`

W pliku testującym wszystkie testy umieszczamy w klasie (nazwa klasy jest dowolna)
```python
import unittest   
  
class TwitterTest(unittest.TestCase)
```
każda metoda zaczynająca się od słowa `test_` będzie naszym testem jednostkowym

aby **wywołać testy** piszemy na końcu pliku
#### `unittest.main()`








