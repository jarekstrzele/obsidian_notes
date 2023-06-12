#python #django 

Agenda
1. Wprowadzeni
2. Szablony
3. Konfiguracja silnika szblonów
4. kontekst i procesory kontekstu
5. język szablonów Django i Jinja2
6. pliki statyczne
7. formularze
8. formularze oparte na modelach
9. widgety
10. pola formularza
11. waliacja formularza
12. walidatory
13. obsługa błędów formularza
14. metaklasy i meadane formularzy
15. widoki generyczne

--------------
# **WZORZEC MTV** *Model-Template-View*
#django/mtv

MODEL - logika bazodanowa
SZABLON - określa wygląd (HTML)
WIDOK - spina razem model i szablon tworząc gotową stronę

# WIDOK:
- w pliku `view.py` 
- to funkcja, która przyjmuje co najmniej jeden argument - obiekt `request`, a zwraca odpowiedź za pomocą ==`render_to_response`== (z szablonem może przyjmować kilka argumentów: nazwa szablony, słownik ze zmiennymi szablonu, `RequestContext` (zmienne globalne dla wszystkich szablonów)

**wygląd strony www** = kod z `view.py` + kod z `index.html`

# SZABLON
#django/templates 
- plik tekstowy zawierający kod HTML, do którego możemy "wstrzykiwać" dodatkowe zmienne przekazane z widoku (dynamiczne renderowanie strony)
- może być generowany w dowolny formacie tekstowym (HTML< XML< CSV, ...)
- podstawowe elementy to `{{ content }}` symbole zastępcze, który wartości są generowane f=dynamicznie
- zaleca się tworzenie dla szablonów *przestrzeni nazw* (podfoldery z nazwą aplikacji), aby uniknąć błędów duplikowani, gdy w projekcie jest więcej aplikacji o takiej samej strukturze folderów
	- utwórz katalog `templates` w katalogu głównym aplikacji, czyli 
	- `project_directory` > `aplication_name` >`base.html` i folder `templates` > `aplication_name` > html files
przykład `application_name\templates\archive.html`
```html
{% extends "base.html" %}
{% block title %} Article for {{ year }} {% endblock %}

{% block content %}
<h1> Articles for {{ year }} </h1>

{% for article in article_list %}
	<p> {{ article.headline }} </p>
	<p> By {{ article.reporter.full_name}} </p>
{% endfor %}
{% enblock %}
```

*{% extends %}* informuje Django o konieczności dziedziczenia po szablonie `base.html`
bloki *title* i *content* wypełniane są treścią z przekazanych wartości zmiennych

`aplication_name\base.html`
```html
{% load static %}
<html>
<head>
	<title>{% title %} {% endblock %}</title>
</head>
<body>
	<img src="{% static 'images/sitelogo.png' %}" alt="Logo">
	{% block content %} {% endblock %}
</body>
<html>
```

*{% load static %}* umożliwia dołączanie plików statycznych, bo nakazuje Django wczytanie znaczników szablonu *static*

*{% block <nazwa_bloku> %}* informują Django, że chcemy zdefiniować blok we wskazanym miejscu ---> inne szablony, które będą dziedziczyć po tym szablonie będą mogły umieszczać treść we wspomnianych blokach

## Konfiguracja szablonu
Są konfigurowane za pomocą ustawień `TEMPLATES` zawartych w pliku `settings.py`
np. 
```python
TEMPLATES = [
{
	'BACKEND': 'django.template.backends.django.DjangoTemplate',
	'DIR':[],
	'APP_DIRS': True,
	'OTIONS': {
	# /////
	}
}
]
```
to są domyślne ustawienia, więc DjangoTemplates szuka podkatalogu `templates` (`'DIR': []`)

`BACKEND` to ścieżka Python dla klasy silnika szablonów implementującej API. Wbudowane backend to :
- `django.template.backends.django.DjangoTemplates`
- `django.template.backends.jinja2.Jinja2`

`DIRS` definiuje listę katalogów, w których silnik powinien szukać plików źródłowych szablonów w kolejności wyszukiwania

`APP_DIRS` mówi, czy silnik powinien szukać szablonów w zainstalowanych aplikacjach
przykład
```python
import os

TEMPLATES = [
{
...
'DIRS': [os.path.jin(BASE_DIR, 'templates)]
}
]
```
katalog szablonów będzie widoczny dla modułu ładującego szablony

#### konfiguracja dwóch silników na raz
```python
TEMPLATES = [
{
  'BACKEND':'django.template.backends.django.DjangoTemplates',
  'DIRS': [
    '/home/html/example.com',
    '/home/html/default',
  ],
},
{
 'BACKEND':'django.template.backends.jinja2.Jinja2',
 `DIRS`:[
	 '/home/html/jinja2',
 ]
}
]
```



## Kontekst i procesory konteksty
kontekst `django.template.Context` oprócz danych kontekstowych przechowuje pewne metadane. Jest przekazywany do `Template.render()` w celu renderowania `template.django.template.RequestContext`

podklasa `Context ` przechowuje bieżące `HttpRequest` i uruchamia procesory kontekstu szablonów

Dane kontekstowe są przekazywane w postaci zwykłego tekstu, a bieżące żądanie `HttpRequest` jest przekazywane osobno w razie potrzeby


>[!info] Procesory kontekstowe
>- obiekty wywoływalne, które przyjmują obiekt żądania jako argument i zwracają słownik elementów, które mają zostać włączone do kontekstu
>- to funkcje, które odbierają bieżące `HttpRequest` jako argument i zwracają wartości danych, które mają zostać dodane do kontekstu renderowania
>- ich głównym zastosowaniem jest dodawanie do kontekstu wspólnych danych udostępnianych przez wszystkie szablony bez powtarzania kodu w każdym widoku

np. `settings.py`
```python
TEMPLATES = [
{
'BACKEND' ..
'OPTIONS': {
	'context_processors': [
		'django.template.context_processors.debug',
		'django.template.context_processors.request',
		'django.contrib.auth.context_processors.auth',
		'django.contrib.messages.context_processors.messages'
	]
}
}
]
```

### składnia języka szablonów

#### zmienne
dostęp do zmiennych podanych kontekście widoku można uzyskać za pomocą notacji w podwójnym nawiastem klamrowym
```html
<h1>{{ user.username }} </h1>
<di class="email"> {{ user.email }} </div>
```

#### filtry
wykonują zazwyczaj różne operacje formatyujące tekstu, łamanie linii, zmieniają wielkość liter, parsują okreśrone tagi ....

`{{ zmienna | nazwa_filtru }}`
np,
`{{ zmienna | lower }}` wyświetla zmienną po przefiltrowaniu przez filtr, który konwertuje tekst na małe listery

`{{ zmienna | escape | linebreaks }}` stosowanie kilku filtrów, wychodzi z treści tekstu oraz łamie tekst w linii poleceniem `<p>` `


