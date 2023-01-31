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

```python
import unittest  
from twitter import Twitter  
  
  
class TwitterTest(unittest.TestCase):  
    def test_initialization(self):  
        twitter = Twitter()  
        self.assertTrue(twitter)  # sprawdzamy, czy obiekt klasy Twitter w ogóle jest tworzony  
  
  
if __name__ == "__main__":  
    unittest.main()
```


## Podstawowa struktura testu
1. given - sytuacja wejściowa
2. when - wykonanie akcji na sytuacji
3. then - sprawdzenie wyników

```python
import unittest  
from twitter import Twitter  
  
  
class TwitterTest(unittest.TestCase):  
    def test_initialization(self):  
        twitter = Twitter()  
        self.assertTrue(twitter)  # sprawdzamy, czy obiekt klasy Twitter w ogóle jest tworzony  
  
    def test_tweet_single(self):  
        # Given(sytuacja wejściowa)  
        twitter = Twitter()  
  
        # When (działania na sytuacji)  
        twitter.tweet("Test msg")  
  
        # Then (sprawdzenie wyników)  
        self.assertEqual(twitter.tweets, ["Test msg"])  
  
  
if __name__ == "__main__":  
    unittest.main()
```


### `setup` - funkcjonalność wykonywana przed każdym testem
np. w kodzie powyżej powtarzamy tworzenie instansji Twittera, więc możemy to przenieść do `setup`
```python
import unittest  
from twitter import Twitter  
  
  
class TwitterTest(unittest.TestCase):  
  
    def setUp(self):  
        self.twitter = Twitter()  
  
    def test_initialization(self):  
        self.assertTrue(self.twitter)  # sprawdzamy, czy obiekt klasy Twitter w ogóle jest tworzony  
  
    def test_tweet_single(self):  
        # Given(sytuacja wejściowa)  
               # When (działania na sytuacji)  
        self.twitter.tweet("Test msg")  
  
        # Then (sprawdzenie wyników)  
        self.assertEqual(self.twitter.tweets, ["Test msg"])  
  
  
if __name__ == "__main__":  
    unittest.main()
```









