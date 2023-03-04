

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










