Krawkowiak
#krakowiak

[[2 OOP Krakowiak]]
[[classmethod]]
[[Dziedziczenie]]
[[metody specjalne]]
[[Podstawy OOP]]
[[przestrzenie nazw]]
[[staticmethod]]
[[widoczność zmiennych]]


C O L A B  
#colab
dysk google -> otwórz -> więcej -> colaboraty  
w prawym górnym rogu jest ikona connect -> connect to hosted runtime i już  

``!python --version  

python 3.7  

  
możemy podłączyć naszą lokalną wersję Pythona z colab  

1. W anacondzie tworzymy nowe środowisko (environment->create)  
      w zakładce home wybieramy nowo powstałe środowisko  
      jeszcze instalujemy w anacondzie power shell  

1. ta sama ikonka j/w -> connect to local runtime  

dostaniemy okienko z linkiem do instrukcji, a w tym okienku (po wypełnieniu instrukcji) wkleimy link łączący colab z naszym lokalnym środowiskiem  
  

otwieramy w nowym środowiku w anakondzie power shella i :  

```
pip install jupyter_http_over_ws
jupyter serverextension enable --py jupyter_http_over_ws  
```

teraz uruchamiany nasz serwer  
```
jupyter notebook --NotebookApp.allow_origin='https://colab.research.google.com' --port=8888  --NotebookApp.port_retries=0  
```

trzeba usunąć '/'; w/w kodzie już to zrobiłem, ale na stronie są   

<<<<<<< HEAD
=======
  

>>>>>>> remotes/origin/master
otrzymałem taki link do wklejenia  

http://localhost:8888/?token=75735f695ba34f8251cd43b5d4c1cbce136ab41a41514795  

<<<<<<< HEAD
=======
    


>>>>>>> remotes/origin/master

 **A T R Y B U T Y**   

---
Gdy chcemy dostać się do atrybutu instancji, nasz program wykonuje nastęujące kroki:  

1.  sprawdza zakres **lokalny instancji**  
2.  nie znalazł, więc sprawdza zakres **lokalny klasy**  
3.  nie znalazł, więc otrzymamy **AttributeError**  
    

> W przeciwieństwie do funkcji, zakres lokalny klasy nie jest tworzony w czasie jej wywoływania, ale w czasie wykonania.  

> Każda **klasa ma** swój własny atrybut `__dict__`, który zawiera przestrzeń nazw, gdzie znajdują się atrybuty klasy  
  
> Każda **instancja ma** swój własny atrybut `__dict__`, który zawiera przestrzeń nazw, gdzie znajdują się atrybuty klasy  
 

**K L A S A**  
Aby w klasie mieć z metody dostęp do atrybutu klasy trzeba użyć notacji  

`NazwaKlasy.nazwa_atrybutu`
`Phone.__bases__` -> klasy, z których dziedziczy `Phone`

**atrybut klasy zdefiniowany przez użytkownika**       - wspólny dla wszystkich instancji klasy  
  
==odczyt==
`NazwaKlasy.__dict__['nazwa_klucza']` -> wartość  

`getattr(NazwaKlasy, nazwa_atrybutu, [opcjonalna wartość])` -> wartość,  
jeżeli atrybutu nie ma, zwraca `[opcjonalna wartość]`

==modyfikacja==
`NazwaKlasy.nazwa_atr = nowa_wartosc`
`setattr(Nazwa Klasy, nazwa_atrybutu, nowa_wartosc)`

mappingproxy jest niemodyfikowalny, więc ten kod nie zadziała
NazwaKlasy.__dict__[nazwa_atr]=nowa_wartosc  

zmiana w locie  

NazwaKlasy.nowy_arybut = nowa_wartosc
setattr(NazwaKlasy, nazwa_nowego_atr, value)  

USUWANIE atrybutow  

del NazwaKlasy.nazwa_atr

delattr(NazwaKlasy, nazwa_atrybutu)  
<<<<<<< HEAD
=======

  

>>>>>>> remotes/origin/master
  

WYŁOWYWALNE ATRYBUTY (funkcje)  

class Phone:
      atr1 = val
      atr2 = val

      def foo():
            print(f'{Phone.__name__} class.')

Phone.foo() -> 'Phone class.'
Phone.__dict__ -> ... foo: function  

<<<<<<< HEAD
getattr(Phone, foo)() -> wywoła funkcję foo  
  

METHOD RESOLUTION ORDER  
NazwaKlasy.__mro__  
kolejność przeszukiwania klasy, aby znaleść odpowiednią metodę  

--------------------------------------------------------------------------------------  

**INSTANCJA**  
=======
  

getattr(Phone, foo)() -> wywoła funkcję foo  

  

METHOD RESOLUTION ORDER  

NazwaKlasy.__mro__  

kolejność przeszukiwania klasy, aby znaleść odpowiednią metodę  

  

--------------------------------------------------------------------------------------  

**INSTANCJA**  

>>>>>>> remotes/origin/master
  

ATRUBUTY INSTANCJI  

<<<<<<< HEAD
=======
  

>>>>>>> remotes/origin/master
wbudowane atrybuty  

class Book:
      lang= 'ENG'

      def show():  

            print(Book.land)  

Book.__dict__ --> mappingproxy (atrybuty wbud. klasy)

book = Book()
book.__dict__  --> zwróci zwykły słownik  

# ale mamy dostęp do atrybutu klasy  

book.lang -> 'ENG'
  

<<<<<<< HEAD
Python napierw przeszukuje przestrzeń nazw instancji, a jeżeli nie znajdzie przechodzi do przestrzeni klasy.  
=======
  

  

Python napierw przeszukuje przestrzeń nazw instancji, a jeżeli nie znajdzie przechodzi do przestrzeni klasy.  

>>>>>>> remotes/origin/master
  

class Book:

      def foo():
            pass

#
Book.foo() -> ok
book=Book()
book.foo() -> error, bo wywołujemy metodę obiektu book, więc Python 
              automatycznie wstrzykuje argument _self_, a foo() nie przyjmuje
              żadnych argumentów
type(Book.foo) -> function
type(book.foo) -> method

  

  

metody klasy a atrybuty klasy  

class Book:  

      title = "Pan Tadeusz"  

        

      def show():  

            # print(f'title {title}')       -> error  

            print(f'title {Book.title}')    -> ok  

  

dostęp przez funkcję/metodę do:  

-   atrybutu instancji     _self.nazwa_atr_  
    
-   atrybutu klasy           NazwaKlasy.nazwa_atr  
    

brand = 'HP'

class Phone:

      brand = 'Apple'  

      r1 = [brand] * 2 # -> ['Apple', 'Apple']  

      r2 = [brand for i in range(2)] #-> ['HP', 'HP']  

#  

# list comprehension działa jak funkcja, więc 'brand' nie jest własnością klasy
# zminić: [Phone.brand for i in range(2)]

  

class