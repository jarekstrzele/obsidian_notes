[[#Obiekty `HTTPRequest`, `HTTPResponse`]]
[[#Modele tworzenie, dodawanie, pobieranie, modyfikacja, komunikacja z DB]]
	[[#Komunikacja a DB `QuerySet`]]


01:33

1. Obiekty HTTPRequest, HTTPResponse [[#Obiekty `HTTPRequest`, `HTTPResponse`]]
2. Routing: urls.py i tworzenie url-i aplikacji [[#]]
3. modele: tworzenie dodawania, pobieranie modyfikacja danych, komunikacja z DB
4. manager .objects
5. interaktywan konsola Pythona w Django [[#]]
6. Relacje [[#Relacje]]
7. Funkcje i klasy widoków, GET, POST 
8. QueryDict [[#QueryDict]]
9. CSRF (bezpieczeństwo) [[#`CSRF`]]
10. Sesje, cookies [[#Sesje i ciasteczka]]

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
p1 = Post.objects.get(id=1)
p1.delete()
```


### Pobieranie
jeden obiekt
`Post.objets.get(attr=value)` 
`Post.objets.get(id=1)`

wszystkie
`Post.objects.all()`


----
## Komunikacja a DB `QuerySet`

Po utworzeniu modeli danych Django można skorzystać z bezpłatnego interfejsu API do interakcji z nimi

Obiekt `QuerySet` to zbiór zapytań do bazy danych słuzący do pobierania obiektów z DB.
Obiekt `QuerySet` umożliwia stosowanie filtró

https://docs.djangoproject.com/en/2.0/ref/models

### `filter()`
```python
Post.objects.filter(publish_year=2022)
Post.objects.filter(publish_year=2022, author_username='admin') # to jest równoznaczne z budowaniem obiektu `QuerySet, ktory łączy wiele fitrów`
```

### `exclude()`
wszystkie posty z 2022, które NIE zaczynają się od "Dlaczego"
```python
Post.objects.filter(publish_year=2022)
 .exclude(title_startswith='Dlaczego')
```


### `order_by()`
```python
Post.object.order_by('title') # porządek rosnący, domyślny

Post.object.order_by("-title") # w porządku malejącym
```


## Menedżer obiektów `Manager.object`
**menedżer** to interfejs, przez który operacje zapytań bazy danych są dostarczane do modeli Django

Dla każdego modelu w aplikacji Django istnieje  co najmniej jeden menedżer.
`Objects` to domyśłny menedżer każdego modelu, który pobiera wszystkie obiekty z bazy danych

można napisać **własny menedżer** -- DWA SPOSOBY:
- pierwsz polega dodaniu dodatkowych metod menedżera `Post.objects.my_manager()`
- drugi na modyfikacji początkowego menedżera kolekcji `QuerySet` -- `Post.my_manager.all()`

DODAWANIE własnego MENEDŻERA
plik `models.py` (pierwszy menedzęr staje się menedżerem domyślnym )

```python
class PublishedManager(models.Manager):
	def get_queryset(self):
		return super(PublishManager, self).get_queryset().filter(status='published')

class Post(models.Model)
	# ...........
	objects = models.Manager() # menedżer domyśłny
	published = PublishedManager() #  menedże nistandardowy
```


## Relacje 
relacje są definiowane na poziomie bazy danych, a nie tylko na poziomie aplikacji

- *wiele-do-jednego* (jeden użytkownik, wiele postów) (*many-to-one*)
wiele obiektów może odwoływać się do tego samego obiektu
```python
book = Book.objects.get(title="Django")
author = Book.author # pobierz autora książki

books.author.books_set.all() # pobierze wszystkie książki danego autora
```

a

- *wiele-do-wielu* (autorzy - książki, )
```python
class Author(models.Model):
	name = models.CharFIeld(max_length=100)
class Book(models.Model):
	title = models.CharField(max_length=100)
	authors = models.ManyToManyField(Author)
```
Pole `ManyToManyField` w celu obsługi relacji tworzy zupełnie nową tabelę, w której wykorzystywany jest znany już mechanizm kluczy obcych
```python
book = Book.objects.get(title="Python and Django")
authors = Book.authors_set.all() # pobierz wszytkich autorów książek
books = authors[2].book_set.all() # pobierz książki, których autorem jest trzeci z autorów
```


- *jeden-do-jednego* (identyfikator produktu, kod kreskowy produktu)
`OneToOneField`


#### KLUCZ GŁÓWNY
- pole, którego wartość w całej tabeli jest unikalna (w całym modelu ORM)
- często to pola automatycznie inkrementowane
- wszystkie modele niezawierające jawnie określonego klucza głównego otrzymują *atrybut*  `id` będący polem typu `AutoField)`

#### KLUCZ OBCY
klasa `ForeignKey` (podklas klasy `Field`)
pierwszy argument tej klasy stanowi klasę modelu, do którego należy się odwołać
```python
class Author(models.Model):
	name = models.CharFIeld(max_length=100)

class Book(models.Model):
	title = models.CharField(max_length=100)
	author models.ForeignKey("Author")


```

-------
## QueryDict
zmodyfikowany słownik zdolny przechowywać wiele wartości dla jednego klucza

atrybuty `request.GET` i `request.POST` są instancjami `django.http.QueryDict`

te `QueryDicts` domyślnie są niezmienne

Jeżeli sam tworzę  instancje `QurtyDict`, mogę sprawić, że będzie zmienny `mutable=True` w jego `__init__()`

Ma wszystkie metody słownikowe, plus swoje własne np.
- `getlist(key)` zwraca listę z wartościami przypisanymi dla danego klucza
- `lists()` zwraca w listach wszystkie wartości z żądania
```bash
>>> q = QueryDict('a=1&a=2&a=3')
>>> q.lists()
[('a',['1','2','3'])]
```


--------
## Funkcje i klasy widoków, GET i  POST
Django to zbiór **komponentów**:
- które przyjmują zapytania webowe
- które zwracają odpowiedź w postaci kodu HTML dla przeglądarki
- **punkt wejścia** - *zapytania URL*

**widok** to funkcja
- wykonywana zgodnie z żądaniem URL (jaki adres, taki widok)
- zwraca wartość jako odpowiedź na żądanie


#### widok funkcyjny
`views.py`
```python
def book_update_view(request):
	if request.method == 'GET':
		### ..
	if request.method == 'POST':
		# ....
```

`urls.py`
```python
urlpatterns = [
	path('update/<int:pk>', views.book_update_view, name='update')		   
]
```


#### widok klasowy
`views.py`
```python
from django.views import View

class BookUpdateView(View):
	def get(self, request, *args, **kwargs):
		# obsługa żądania GET
def post(self, request, *args, **kwargs):
	# obsługa żądania POST
```
klasa `VIew` ma metodę `dispatch()`, która zwiera logiką obsługi dla poszczególnych metod zapytań HTTP:
- żądanie metodą GET, wywoła metodę get
- żądanie metodą POST, wywoła metodę post
- ....


`urls.py`
```python
utelpatterns = [
	path('update/<int:pk>', view.BookUpdateView.as_view(), name='update')
]
```
`as_view()` opakowuje naszą klasę w funkcje i możemy przekazać ją do URL resolvera `path()`



--------
## GET vs POST

## GET
 dane wysyłane `GET` są dołączane do adresu URL i stanowią jego część (np. `http://www.google.com/search?q=django`,  pole `q` ma wartość `django`, czyli zostało wpisane do formularza , a formularz przesłał dane do skryptu wyszukującego to, co widać w adresie


### POST
dane przesyłane na standardowe wejście skryptu (nie potrzebuje adresu URL)
danych nie widać w adresie
ten sposób do przesyłania haseł, autoryzacji


------
# `CSRF`
#csrf
==Ochrona przed fałszowaniem żądań==
**CSRF** lub **XSRF** :
- atak jednym kliknięciem, jazda sesyjna, fałszowanie żądań między witrynami
- to złośliwe wykorzystanie strony internetowe, aby przesyłać nieautoryzowane od użytkownika polecenia, 

Aby włączyć ochronę CSRF należy dodać *CsrfViewMiddleware* do klasy w `settings.py` - domyśłnie jest włączone

- to oprogramowanie ustawia **token** w pliku **cookie** w odpowiedzi wychodzącej
- kiedy w przychodzącym żądaniu jest wykorzystywana niebezpieczna metoda (dowolna oprócz GET), plik cookie musi pasować do tokena, który jest wysyłany jako dane formularza `csrfmiddlewaretoken` lub jako nagłówek `X-CsrfToken` (=> klient inicjujący żądanie jest również właścicielem pliku cookie, a co za tym idzie sesji (uwierzytelnionej)  )

Formularze korzystające z metody POST powinny zawierać `token CSRF` w szablonie

`{% csrf_token %}` - wyświetli ukryte pole i zapewni, że plik cookie zostanie ustawiony w odpowiedzi


DEKORATOR wyłączający ochronę `@csrd_exempt`
```python

@csrf_exempt
def my_view(req):
	"""Allows unsafe methods without CSRF protection"""
	# ....
```


-------
# Sesje i ciasteczka
KORZYSTANIE Z SESJI:
`settings.py`:
- część `MIDDLEWARE_CLASSES` klasy `django.contrib.sessions.middleware.SessionMiddleware` (domyślnie już jest)
- części `INSTALLED_APPS` dodać `django.contrib.sessions`

teraz polecenia `python manage.py syncdb`

Gdy `SessionMiddleware` jest aktywne każdy obiekt `HttpRequest`(pierwszy argument każdej funkcji widoków) będzie miał atrybut **session**, który jest podobny do słownika

`request.session['klucz']='wartosc'`

`request.session.get('masz komentarz', False)`

`SESSION_COOKIE_AGE` czas ważności cookie sesji w sekunadch
`SESSION_COOKIE_SECURE`

CIASTECZKA
#cookie
- dane informatyczne (w szczególności pliki tekstowe), które są przechowywane w urządzeniu końcowym użytkownika strony
- służą do optymalizacji procesu korzystania ze stron WWW
- dzielą się na:
	- **sesyjne** ( tymczasowe) istnieją do momentu wylofowania się lub wyłączenia przeglądarki
	- **stałe** przechowywane przez zdefiniowany czas


ustawienia cookie
```python 
def view(request):
	response = HttpResponse("To co chcemy zwrócić")
	response.set_cookie("cookie_name", "cookie_value")
```

pobieranie cookie
```python
def view(req):
	if 'cookie_name' in req.COOKIES:gg
		value = req.COOKIES['cookie_name']
```










