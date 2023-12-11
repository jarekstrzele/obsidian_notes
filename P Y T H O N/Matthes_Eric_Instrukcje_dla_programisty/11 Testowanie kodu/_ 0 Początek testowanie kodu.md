#python 
#test
#unittest


## Testowanie funkcji

### Test jednostkowy i zestaw testów

`unittest` moduł pochodzi z biblioteki standardowej Python

>[!test jednostkowy]
>sprawdza poprawność jednego konkrentego aspektu zachowania funkcji


>[!zestw testów]
>kolekcja testów jednostkowych sprawdzająca działanie danej funkcji w szerokiej gamie sytuacji
>- gdy duży projekt, najpierw wystarczy przygotować testy dla szczególnie istotnych fragmentów kodu

### Zaliczenie testu
aby utworzyć zestaw testów dla funkcji:
1. zaimportuj moduł `unittest` oraz funkcję do przetestowania
2. utwórz klasę dziedziczącą po `unittest.TestCase`
3. przygotuj serię metod odpowiedzialnych za przetestowanie różnych apsektów działania sprawdzanej funkcji

dana jest prosta funkcja `name_function.py`
```python
def get_formatted_name(first, last): 
   """Generuje elegancko sformatowane pełne imię i nazwisko.""" 
   full_name = f"{first} {last}" 
   return full_name.title()
```
chcemy ją rozbudować o formatowanie również drugiego imienia, o ile występuje

`test_name_functiosn.py`
```python
import unittest
from name_function import get_formatted_name

# nazwa klasy musi zawierać słowo 'Test'
# powinna być jakoś powiązana z tym, co robi
class NameTestCase(unittest.TestCase):
  """Testy dla programu 'name_function.py' """

  # każda metoda o nazwie ROZPOCZYNAJĄCEJ się
  # od `test_` będzie wykonywana automatycznie po uruchomieniu `test_name_functions.py`	
  def test_first_last_name(self):
    "Czy dane wpostaci 'Janis Joplin' są obsługiwane prawidłowo??"
    formatted_name = get_formatted_name('janis', 'joplin')

    # jedna z najbardziej użytecznych metod -> asercja
    # sprawdza, czy otrzymany wynik odpowiada oczekiwanemu
    self.assertEqual(formatted_name, 'Janis Joplin')

in __name__ == '__main__':

  # funkcja odpowiedzialna za wykonanie zestawu testów
  unittest.main()
```
output:
```
.
---------------------------------------------------------------------- Ran 1 test in 0.000s O
```
`.` informuje o zaliczeniu pojedynczego testu


### Niezaliczenie testu
zmieńmy naszą funkcję
```python
def get_formatted_name(first, middle, last): 
  """Generuje elegancko sformatowane pełne imię i nazwisko.""" 
  full_name = f"{first} {middle} {last}" 
  return full_name.title()
```
teraz otrzymamy `error`










