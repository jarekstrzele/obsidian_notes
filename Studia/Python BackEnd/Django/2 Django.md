01:33

1. Obiekty HTTPRequest, HTTPResponse
2. Routing: urls.py i tworzenie url-i aplikacji
3. modele: tworzenie dodawania, pobieranie modyfikacja danych, komunikacja z DB
4. manager .objects
5. interaktywan konsola Pythona w Django
6. Relacje
7. Funkcje i klasy widoków, GET, POST
8. QueryDict
9. CSRF (bezpieczeństwo)
10. Sesje, cookies

---------
# Obiekty `HTTPRequest`, `HTTPResponse`

- Django używa `HttpRequest` i `HttpResponse do przekazywania stanu przez system`
- gdy żądana jest strona, Django tworzy obiekt `HttpRequest`, który zawiera metadane dotyczące żądania
- następnie Django ładuje odpowiedni widok , przekazując `HttpRequest` jako pierwszy argument do funkcji widoku
- każdy widok to funkcja przyjmująca jeden obowiązkowyu parametr `request` i zwracająca obiekt `HttpRequest`
- Podczas wywoływania obiektu `HttpRequest`
	- konstruowany jest obiekt `Request`, który zostaje wysłany do serwera, aby zażądać albo wykonać zapytanie dotyczące jakiegoś zasobu
	- obiekt `Response` jest generowany, kiedy `requests` otrzymuje odpowiedź od serwera
	- obiekt `Response` zawiera wszystkie informacje zwrócone przez serwer oraz oryginalny obiekt `Request`


**przykład**
`hello/views.py`
```python
from django.http import HttpResponse

def hello(request):
	return HttpResponse('Hello, world')
```

`hello/urls/py`
```python
from django.conf.urls import url
from django.contrib import admin
from hello import views

urlpatterns = [
	url(r'^admin/', admin.site.urls),
	url(r'^$', view.hello)
]
```


![[obiekty_req_res_django.excalidraw| 700]]



## parametr `request`
zawiera wiele przydatnych danych - m.in. :
- `path` łańcuch reprezentujący ścieżkę do żądanej strony bez domeny (np.`/music.bands/the_beatles`)
- `scheme` ciąg reprezentujący schemat żadania (zwykle http lub https)
- `method` łańcuch okreśłający metodę żądania srony (GET albo POST)
- `cookies` słownik zwierający dane ciasteczek (klucze i wartości są łańcuchami)
- `meta` słownik zwierający nagłówki HTTP (np. CONTENT_LENGTH, ...)
- `files` obiekt zwierający dane o wysyłanych plikach (przez firmularz), kluczem jest nazwa pola formularza a wartościa słownik zawierający trzy klucze
	- `filename`
	- `content-type` typ mime pliku
- `user` obiekt rozpoznający zalogowanego użytkownika lub nie zalogowanego użytkownika
- `session` dane sesji, odczytywany jest obiekt reprezentujący bieżącą sesję 

**wszystkie atrybuty poza `session` powinny być używanie w trybie "tylko do odczytu"**


---
## Jak Django obsługuje żądanie?
Django obsługuje żądanie, kierując ścieżkę przychodzącego adresu URL do funkcji widoku.

**Funkcja widoku** odpowiada za zwrócenie odpowiedzi klientowi wysyłającemu żądanie. Różne adresy URL są zwykle obsługiwane przez różne funkcje widoku.

Aby skierować żądanie do określonej funkcji widoku, Django sprawdza konfigurację adresu URL (lub w skrócie **URLconf**).

Domyślony szablon projektu definiuje **URLconf** w `<myproject>/urls.py`
przykład - `urls.py`
```python
from django.conf.urls import url
from myapp.view import home, about, blog_detaill

urlpatterns = [
	url(r'^$', home, name="home"),			   
	url(r'^about/$', about, name="about"),			   
	url(r'^blog/(?P<id>\d+)/$', blig_detail, name="blog-detail"),			   
]

```

`^` kotwica początku
`$` kotwica końca


-------
# Modele: tworzenie, dodawanie, pobieranie, modyfikacja, komunikacja z DB

**ORM** (*object-relational mapper*) - mechanizm mapowania obiektowo-relacyjnego
- jest kompatybilny z MySQL, PostrgreSQL, SQLite, Oracle
- `settings.py` - definiowanie baz danych używaną w projekcie w ustawieniach `DATABASES`
- ten mechanizm bazuje na obiektach `QuerySet` 
- *QuerySet*
	- to zbiór zapytań do bazy danych służący do pobierania obiektów z bazy danych
	- umożliwia stosowanie filtrów pozwalających na zawężenie wynikow kwerendy na podstawie podanych parametrów

*KLASA <-> TABELA*
Klasa modelu reprezentuje tabelę w bazie danych 

*OBIEKT<->REKORD*
Intancj klasy reprezentuje pojedynczy rekord w tabeli bazy danych 


### Tworzenie
**Przykład**
```python
from ankiety.models import Quetions
b = Questions(id=1, question_text="Czy znasz polecenia SQL?", pub_date=2022-01-31)
b.save()
```
Python wykonuje instrukcje `SQL INSERT`.
Python połączy się z bazą dopiero, gdy wywołana będzie metoda `save()` (ta metoda nie zwraca żadnej wartości)



**Przykład**
```python
from django.contrib.auth.models import User
from blog.models import Post

user = User.objects.get(username='admin')
post = Post(title="inny Post", slug="another-post", body="content of post", author=user)
post.save()
```
- najpierw **pobieramy** obiekt `user`
- **tworzymy** egzemplarz klasy `Post`
- **zapisujemy** obiekt `Post` w bazie danych (`save()`)

można też ==stworzyć== obiekt  i ==zapisać== go w bazie danych za pomocą pojedynczej operacji (`create()`)
```python
Post.objects.create(title="some tile", slug="one-more-post", body="body of post", author=user) ;
```

### Aktualizowanie
```python
post.title = "Nowy tytuł"
post.save()
```
metoda `save()` wykona instrukcję `SQL UPDATE`

### Usuwanie 
```python
all_posts = Post.objects.all()
```

```python

```


### Pobieranie
jeden obiekt
`Post.objets.get(attr=value)` 
`Post.objets.get(id=1)`

wszystkie
`Post.objects.all()`









