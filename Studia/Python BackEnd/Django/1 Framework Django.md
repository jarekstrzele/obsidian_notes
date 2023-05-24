#django 
[[#WSTĘP]]
[[#MVC Model-Widok-Kontroler]]
[[#MTV - Django]]
[[#instalacja Django]]
[[#projekt vs aplikacja]]
[[#tworzenie projektu]]
[[#tworzenie pierwszego widoku aplikacji]]
[[#`django-admin i manage.py`]]
[[#`setting.py`]]
[[#Migracje]]
[[#MODELE]]


----
Aby rozpocząc pracę z frameworkiem Django:
1. zainstalować is konfigurować Python i Django
2. uruchomić serwer `python3 manage.py runserver`
3. utworzyć projekt `django-admin startproject <projectname>`
4. dodać aplikację i skonfigurować adresy URL w plikach `urls.py`
5. skonfigurować ustawienia aplikacji w pliku `settings.py`
6. utworzyć widok `view.py`
7. zaprojektować modele danych za pomoacą OMR (mapowanie opobiektowo-relacyjne) w pliku `models.py`
8. wykonać migracje w bazie danych





----



# WSTĘP
>[!info]  Django (dżango) 
>TO darmowy i open-source'owy framwork do tworzenia aplikacji webowych napisnaych w pYthonie
>- 2003 Lawrence Journal-World
>- 2005 licencja BSD
>- 2008 funcdacja Django Software Foundation
>
>Django:
>- upraszcza projektowanie serwisów
>	- już ma uwierzytalnianie użytkowników
>	- panel zarządzania stroną,
>	- formularzez
>	- przysyłanie plików
>- oferuje środowisko testowe (deweloperski serwer WWW , nie trzeba instalować dodatkowych narzędzi typu LAMP/WAMP)



>[!info] FRAMEWORK , platforma programistyczna
>- szkielet do budowy aplikacji (ogólna struktura aplikacji i ogólne mechanizmy działania aplikacji )
>- zestaw komponentów i bibliotek ogónego przeznaczenia do wykonywania okreśłonych zdań
>- to taki "dodatek" do języka programowania, dzięki któremu można w szybszy sposób kodowac nowe rzeczy



-----
## MVC Model-Widok-Kontroler

wzorzec projektowania aplikacji rozdzielający dane(model) od sposoby ich prezentacji(widok) i zarządzania ich przepływem(kontroler)

**kontroler** działa jako interfejs między Widokiem a Modelem, przechwytuje wszystkie przychodzące żądania
**model** reprezentuje stan aplikacji, czyli dane, może mieć również logike biznesową
**widok** reprezentuje prezentację, th UI (interfejs użytwownika)


### w Django
**MODEL** reprezentuje źródło informacji; to klasy opisujące pojedyncze tabele w bazie danych zorientowane obiektowo (ORM):
- atrybuty klasy to pola tabeli
- instancja klasy  to rekord danch
- modele są definiowane w pliku *models.py*

**ORM** (ang. Object-Relational Mapping) - mapowanie obiektowo-relacyjne, oprogramowanie odwzorowujące strukturę relacyjnej bazy danych na obiekty danego języka programowania


**WIDOK** (00:27) to funkcja lub klasa Pythona, która odpowiada na żądania WWW, np. zwraca kod HTML generowany w szablonie (*template*), jakiś dokument, obrazek lub przekerowuje na inny adres; jest definiowany w pliku *views.py*
Django zawiera wiele widoków wbudowanych (*generic views*), w tym opartych na klasach opisujących modele, umożliwiających
	- przeglądanie (np. ListView, DetailView,)
	- edycję danych (np. CreateView, UpdateView)
Każda funkcja pełniąca rolę widoku jako pierwszy argument otrzymuje obiekt `HttpRequest` zawierający informacje o 
- żądaniu typu `GET`  lub `POST`, 
- nazwę użytkownika, 
- dane przesłane do serwera

OBIEKT `request` jest słownikiem. Widok musi zwrócić jakąś odpowiedź. W Django jest to obiekt typu `HttpResponse`

Widoki wykonują jakieś operacje po stronie serwera w odpowiedzi na żądania klienta. Widoki powiązane są z określonymi adresami url.

Dane z bazy przekazywane do szablonów za pomocą Pythonowego słownika. Renderowanie polega na odszukaniu pliku szablonu, zastąpieniu przekazanych zmiennych danymi i odesłaniu całości (HTML + dane) do użytkownika.

W Django szblony zapisywane są w podkatalogu `templates/nazwa_aplikacji`


**KONTROLER** (00:29) mechanizm kierujący kolejne żądania do odpowiedniuch widoków na podstawie wzorców adresów URL
W Django adresy wiążemy z widokami w pliku *urls.py* ->
np. `url(r'^loguj/$', views.loguj, name='loguj')`
- `r'loguj/$` to wyrażenie regularne `regex`
	- `r` początek, `$` koniec
	- `^` dopasowuje początek ciągu lub nowj linii
	- `.` dowolny pojedynczy znak
	- `\d` lub `[0-9]` pojedyncza cyfra dzięsiętna
	- `[a-z]`, `[A-Z]`, `[a-zA-Z]`
	- `+` jedno lub więcej wystąpień poprzedniego wyrażenia `\d+`
	- `?` zero lub jednp wystąpienie poprzedniego wyrażenia
	- `*`  zero lub więcej wystąpień poprzedniego wyrażenia
	- `{1,3}` od 1 do 3 wystąpień poprzedniego wyrażenia `\d{1,3}`


#  MTV - Django
(00:30)
model MODEL
szablon TEMPLATE
widok  VIEW

Widoki są powiązane z adresami URL i same decydują, o tym, co zostanie zwrócone i pełnią w ten spoób rolę kontrolera
Szablony decydują o tym, jak to zostanie zaprezentowane użytkownikowi, a więc pełnią rolę widoków w sensie MVC





---
# instalacja Django
`sudo apt update && sudo apt install Django`
https://docs.djangoproject.com/pl/4.0/topics/install/

1. Intalacja Python
2. instalacja serwera Apache,  mod_wsgi (opcjonalnie),  - używanie Django na stronie produkcyjne w jednym zdwóch trybów:
	1. **tryb osadzony** osadza Python w Apache i ładuje kod Pythona do pamięci podczas uruchamiania serwera. Kod pozostaje w pamięci przez cały czas trwania procesu Apache, co prowardzi do znacznego wzrosu wydajności 
	2. **tryb demona** mod_wsgi tworzy niezależny proces demona, który obsługuje żadania. Proces demona może działą jako inny użytkowni niż serwer siecieowy, co prawdopodobnie prowadzi do poprawy bezpieczeństwa. Proces demona można zrestartować bez ponownego uruchamiania całego serwerwa WWW Apache
3. bazy danych (opcjonalnie, bo Django to ma) - 
	1. aby możliwe było użycie bazy danych w Django, należy ipewnić się, że serwer bazy danych działa i są zainstalowane odpowiednie wiązania bazodanowe Pythona
	2.  Django wspiera PostgreSQL, MariaDB, MySQL, Oracl, SQLIte
	3.  https://docs.djangoproject.com/pl/4.0/topics/install/
4. instalacja Django:
	1. pip lub
	2. instalacja pakietu dystrybucji lub
	3. instalacja wersji deweloperskiej

----
# projekt vs aplikacja
(00:44)
#django/app 
**APLIKACJA** aplikacja webowa, która coś robi, ma konktretne przeznaczenie, może być nią np. blog, sklep, ankieta, czat, baza danych publicznych
aplikacje moga być przechowywane i uruchamian gdziekolwiek na ścieżce pythona. W praktyce najczęściej tworzony jest główny projekt, w którym konfiguowany jest adres URL i serwer i w ramch którego może funkcjonować wiele aplikacji. Wówaczas palikacje te są tworzone jako podmoduły głównego projektu
#### `python manage.py startapp nazwaAplikacji`
generuje podstawową strukturę katalogów aplikacji

#django/project
**PROJEKT** zbiór konfiguracji i palikacji dla konkretnej wutryby. Projekt może zawierać wiele aplikacji. Aplikacja może być w wielu projektach
###  `django-admin startproject mysite` 

---
# tworzenie projektu
#django/project 
- zaplanuj nazwę projektu
	- unikaj nazw komponentów wbudowanych w Python luib Django 
- zaplanuj miejsce przechowywania plików projektu
	- nie umieszczaj plików w głównym katalogu serwera WWW (np/ /var/www)

### `django-admin startproject mysite` 
utworzony zostanie katalog mysite w bieżącym katalogu z podkatolaogiem ustawień projekto o takiej samej nazwie zawierający pliki o konkretnej strukturze

`mysite/` katalog główny, który jest pojemnikiem projektu
`manage.py` skrypt Python, narzędzie liniii koment do zarządzania projektem
`db.sqlite3` baza danych w domyśłnym formacie SQLite3
`__init__.py` pusty plik, który mówi Pythonowi, że ten katalog jest modułem
`settings.py` ustawienia dla projektu Django
`urls.py` list obsługiwanych adresów URL
`asgi.py` plik konfiguracyjny wykorzystywany przez serwry WWW
`wsgi.py` plik konfiguracyjny wykorzystywany przez serwry WWW


### `python manage.py runserver`

- domyślnie `runserver`  otwiera port `8000`
- `python manage.py runserver 8080`
- `python manage.py ruserver 0:8000` - `0` jest skrótem `0.0.0.0` umożliwia nasłuchiwanie na wszystkich dostęþnych publicznych IP
- w większości przypadku serwer Django sam się przeładowuje po wprowadzeniu zmian (oprócz dodawania nowych plików do projektu)

------
# tworzenie pierwszego widoku aplikacji
### `python manage.py startapp ankiety`

1. otwórz plik `ankiety/views.py`
```python
from django.http import HttpResponse

def index(request):
	return HttpResponse("Działa. Jesteśmy wpierwszej aplikacji Django-ankiety")
```

2. zmapuj ten plik na adres URL, więc `URLconf`
	-  w katalogu aplikacji `ankiety` utwórz plik o nazwie `urls.py`
```python
from django.urls import path
from . import views

urlpatterns = [path('', views.index, name='index')]
```



- w pliku projektu `mysite` folder główny zmodyfikuj `urls.py`
	- dodaj `include` do biblioteki `django.urls` wstawiając include() na listę url patterns
	- uzyskamy wskazanie w podstawowej konfiguracji adresu URL na moduł `ankiety.urls`
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
	path('ankiety/', include('ankiety.urls'))
	path('admin/', admin.site.urls),
]
```

`python manage.py runserver`

## rejestrowanie aplikacji w projekcie
`mysite/settings.py`

```python
# ...
INSTALLED_APPS = [
	'ankiety.apps.AnkietyConfig', # rejestracja aplikacji
	'django.contrib.admin',
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.messages',
	'django.contrib.staticfiles',
]
# ...

LANGUAGE_CODE = 'pl'
TIME_ZONE = 'Europe/Warsaw'
```
#django/include
*include()* 
- pozwala na odniesienia do innych adresów `URLconf`
- należy używać, gdy stosowane są inne wzorce URL (oprócz `admin.site.urls`)

------
# `django-admin i manage.py`
**django-admin** narzędzie wiersza poleceń do zadań administracyjnych

**manage.py** robi to samo co w/w ale również ustawia *zmienną środowiskową* `DJANGO_SETTINGS_MODULE` tak, aby wskazywała na plik `settings.py` projektu

------
# `settings.py`
standardowy moduł Python ze zminnymi na poziomie moduły reprezentującymi ustawienia DJango
`INSTALLED_APPS`  nazwy wszystkich aplikacji, które są aktywowane w danej instancji Django
	- `django.contrib.admin` panel administracyjny
	- `django.contrib.auth` syste uwierzytelniania
	- `django.contrib.contenttypes` framework dla typów treśco
	- `django.contrib.sessions` framework dla sesji
	- `django.contrib.messages` frame work powiadomień
	- `django.contrib.staticfiles` framework do zarządzania plikami statycznymi

Aplikacje mogą być używane w wielu projektach i można je pakować i udostępniać innym do użytku w ich  projektach

---
# Migracje

#django/migrate
#### `migrate` uruchomi migracje tylko dla aplikacji w `INSTALLED_APPS`
Niektóre z tych aplikacji używają przynajmniej jednej tabeli w bazie danych, więc należy stworzyć tabele w bazie danych zanim będzie można je użyć
Aby to zrobić należy uruchomić komendę:
##### `python manage.py migrate`

Aby **utworzyć bazę danych** wystarczy wpisać komendę:
#### `python manage.py makemigrations <nazwa_app>`
`python3 manage.py makemigrations ankiety`
(za pierwszym razem zostaną utworzone tabele do obsługi np, użytkowników, walidacji,  ...)

**Zatwierdzić migrację** - utworzono standardowe grupy i użytkownicy
#### `python3 manage.py migrate`

**Migracja**
- to sposób w jaki Django przechowuje zmiany modeli i przez to również zmiany schematu baz danych
- migracje są po prostu plikami na dysku
- django tworzy migracje automatycznie, ale można modyfikować je ręcznie lub po porstu sprawdzać jak zostały zapisane zmiany dotyczące baz danych

znajduje się w np. `ankiety/migrations/0001_inital.py`

## Uruchomienie migracji
- po utworzeniu nowych modeli (np. *Question i Choice*) należy poinformaować Django o zmianach w strukturze danych tak, aby zostały przechowane jako migracja:
##### `python3 manage.py makemigrations ankiety`

- następnie URUCHAMIAMY migrację, aby utworzyć nowe modele w bazie
##### `python3 manage.py migrate`
(jeżeli nie tworzymy nowej struktury, ale np, dodajemy dane, wystarczy tylko uruchomić migrację)
w wyniku tej komenty kod Python ==> kod SQL (`python3 manage.py sqlmigrate <nazwa migracji>` => podgląd kodu SQL, np, `python manage.py sqlmigrate ankiety 0001`)

PODSUMOWANIE trzy kroki do tworzenia zmian w modelach:
1. Modyfikacja modeli w `models.py`
2. uruchomienie w `makemigrations`, aby stworzyć migracje dla zmian
3. uruchomienie `migrate`, aby zastosować te zmiany na bazie danych



----

# MODELE
#django/modele
>[!info] Model
>To pojedyncze, pełne źródło informacji o danych.
>Zawiera podstawowe pola i zachowania danych, które są przechowywane.

**Właściwości**
- każdy model odpowiada jednej **tabeli** w bazie danych (zazwyczaj)
- każdy model to **klasaPythona**, która dziedziczy z `django.db.models.Mode`
- każdy **atrybut** modelu reprezentuje **pole** w tabeli
- Django daje możliwość automatycznego generowania API dostępu do baz danych
- Migracje pochodzą z pliku modeli i jest to sposób w jaki Django przechowuje zmiany i akrtualizuje schemat baz danych, tak by był zgodny z bieżącymi modelami

### Przykład:
Zdefinujemy modele wykorzystywane do zbudowania aplikacji ankiety

W Aplikacji ankiety, stworzymy dwa modele(dwie tabele):
- *Question* (pole pytanie, pole data publikacji)
- *Choice* (pole treść wybory, pole podsumowanie głosów)
Każdy element Choice jest związany z elementem z Question

**Strukturę modeli** opisujemy w pliku `ankiety/modeles.py` :
```python
from django.db import models

class Question(models.Model):
	question_text = models.CharField(max_length=200)
	pub_date = models.DateTimeField('date published')

class Choice(models.Model):
	question = models.ForeignKey(Question, on_delete=models.CASCADE)
	choice_text = models.CharField(max_length=200)
	votes = models.IntegerField(default=0)	


```

- każde pole jest reprezentowane przez instalcję klasy `Field`
- każdy model jest reprezentowany przez klasę, ktora dziedziczy po djangk.db.models
- każdy model ma kilka zmiennych klasowych, z których każda reprezentuje pole bazy danych w modelu






