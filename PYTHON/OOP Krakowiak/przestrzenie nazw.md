#udemy 
#python/namespaces 
## SECTION 5   PRZESTRZENIE NAZW I ZAKRESY  
#python/namespace  

-  zbiór symboli(nazw), które służą do identyfikacji i stanowią odniesienie do obiektów różnych typów      
-  zapewnia, że wszystkie obiekty mają unikalną nazwę i mogą być łatwo identyfikowalne     
-  w Pythonie jest zaimplementowana jako słownik (mapowanie nazw na obiekty) i jest przechowywana w specjalnym atrybucie `__dict__`
- wbudowana przestrzeń nazw jest tworzona podczas uruchamiania interpretera języka Python i nigdy nie jest usuwana  
- loklana przestrzeń nazwa dla funkcji tworzona jest w momencie jej wywoływania  

  
**przykłady**  
-   przestrzeń nazw modułów      
-   przestrzeń nazw dla funkcji    
-   zestaw atrybutów instancji     
-   przestrzeń nazw wbudowanych (max(), abs()...)   

na najwyższym poziomie modułu nazwwy są przechowywane w atrybucie _ _ dict _ _  
```py
import math

math.__dict__
{
'__name__':'math',  

'__doc__':
...
}  
```

**Z A K R E S**  
#python/scope 
**scope** obszar programu w języku Pthon, w którym przestrzeń nazw jest bezpośrednio dostęna  


REGUŁA   L E G B  
#legb
Python rozwiązuje nazwy przy użyciu tak zwanej reguły ==LEGB==  

**Local** tylko przy wywołaniu funkcji (nazwy w ciele funkcji)   

 **tyle zakresów co wywołań funkcji, gdy funkcja zostaje wykonana, zakres zostaje zniszczony, a nazwy zapomniane**
 zmienna utworzona wew. funkcji należy do zakresu lokalnego, czyli jest dostępna tylko wewnątrz funkcji  

**Enclosing** zakres dla funkcji zagnieżdżonych (**nonlocal**)    

**Global `__main__`** zakres modułu, dostęp z każdego miejsca w kodzie,  jest jeden i istnieje do  momentu zakończenia programu (**dir**)  

 **`globals()`** returns the dict containing the current scope's global variables  

**Built-in**  jest ładowane w momencie uruchamiania Pythona, można go znależć w  
programie w  `__builtins__`

==comprehension działają podobnie jak funkcje==

Tam gdzie definiujesz zmienną, tam będzie dostępna, czyli zdefiniowana globalnie jest globalnie dostępna, lokalnie lokalnie itp.  

Możemy to zachowanie Pythona zmienić używając  
`global var1`
`nonlocal var2`  

---
### __code__
#python/__code__
```python
def stock_info(company, country, price, currency):
    return (
        f'Company: {company}\nCountry: {country}'
        f'\nPrice: {currency} {price}'
    )
 
 
print(stock_info.__code__.co_varnames)
```
output: ('company', 'country', 'price', 'currency')




----

  
**C O M P R E H E N S I O N**  

-   w pętli `for` zmienna jest globalna (`for item in ...` -> `item` jest globalna, o ile `for` było globalne
-   z list comprehension jest jak z funkcją, czyli zewnętrznie nie możemy odwołać się do zmiennej `([var for var in range(10)]` - `var` zewnętrznie nie jest dostępna  
  
==pomocnicze funkcje wbudowane ==
- **`globals()`  (np. `[name for name in globals() if not name.startswith('_')]`
    
- **`locals()`** zwraca słownik zmiennych localny  
    
- **`vars()`** zwraca zawartość attrybutu ___dict___ ( _vars(math)_ ) (klasy i instancje mają atrybut słownikowy ___dict___  
    
-   **`dir()`**  dostajemy nazwy globalne, dir(nazwa modułu) -> nazwy tego modułu  
    

  
