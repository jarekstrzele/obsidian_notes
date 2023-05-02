#django 
[[#WSTĘP]]
[[#MVC Model-Widok-Kontroler]]
[[#MTV - Django]]
[[#instalacja Django]]





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

Dane z bazy przekazywane dą do szablonów za pomocą Pythonowego słownika. Renderowanie polega na odszukaniu pliku szablonu, zastąpieniu przekazanych zmiennych danymi i odesłaniu całości (HTML + dane) do użytkownika.

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
`sudo apt update && sudo apt install python-django`

1. Intalacja Python
2. instalacja serwera Apache,  mod_wsgi (opcjonalnie),  - używanie Django na stronie produkcyjne w jednym zdwóch trybów:
	1. **tryb osadzony** osadza Python w Apache i ładuje kod Pythona do pamięci podczas uruchamiania serwera. Kod pozostaje w pamięci przez cały czas trwania procesu Apache, co prowardzi do znacznego wzrosu wydajności 
	2. **tryb demona** mod_wsgi tworzy niezależny proces demona, który obsługuje żadania. Proces demona może działą jako inny użytkowni niż serwer siecieowy, co prawdopodobnie prowadzi do poprawy bezpieczeństwa. Proces demona można zrestartować bez ponownego uruchamiania całego serwerwa WWW Apache
3. bazy danych (opcjonalnie, bo Django to ma) - 
	1. aby możliwe było użycie bazy danych w Django, należy ipewnić się, że serwer bazy danych działa i są zainstalowane odpowiednie wiązania bazodanowe Pythona
	2.  Django wspiera PostgreSQL, MariaDB, MySQL, Oracl, SQLIte
	3. 
4. instalacja Django:
	1. pip lub
	2. instalacja pakietu dystrybucji lub
	3. instalacja wersji deweloperskiej







