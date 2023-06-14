
Agenda
1. Django Admin
2. Kontrola dostępu i sesje
	1. Django Session Framework
	2. Django User Framework


>[!info] Django
>- narzędzie **tworzenia interaktywnych stron** internetowych
>	- dodawania i obsługa elementów projektu (widoki)
>	- projektowanie szablonów, formularzy, testowanie i obsługa błędów
>- **narzędzie do tworzenia modeli danych** i wykonywanie migracji do baz danych (za pomocą formularzy i szablonów)
>- **oddziela**:
>	- "wydawców treści" (managerowie korzystają z systemu, aby dodać nowe informacje)
>	- "publicznej treści-witryny" (te nowe informacje: artykuły, wpisy, produkty jest wyświetlana na publicznej witrynie)

ważne komendy
##### `django-admin`
##### `manage.py`

`python manage.py makemigrations <nazwaApp>` poinformuje Django o zmianach w strukturze danych
`python manage.py migrate` utworzy nowe modele w bazie danych



>[!info] panel administracyjny
> - Narzędzie, które całkowicie automatyzuje tworzenie interfejsu administracyjnego i pozwala na bardzo szybkie i intuicyjne zarządzanie danymi w bazie
> - nie jest przeznaczony przez odwiedzających stronę, jest narzędziem dla menadżerów witryny
> - jednolity interfejs dla administratorów witryn do edycji treści

==pracujemy na istniejącym projekcie po zrobieniu migracji==

aby skorzystać z panelu admin  musisz utworzyć konto admina 
> 	- `python manage.py createsuperuser`
> 	- wprowadź nazwę użytkownika, opcjonalnie e-mai, hasło
> 	- `python manage.py runserver`
> 	- `http://127.0.0.1:8000/admin` (nazwa `admin` to nazwa użytkownika podana wcześniej)
> 	- nazwa użytkownika i hasło, jak podane wcześniej

po zalogowaniu mamy dostęp do struktury zarządzania grupami i użytkownikami


## Dodanie modelu aplikacji do panelu administracyjnego

Przykładowa aplikacja ma `Question`, `Choice`. Aby dodać te obiekty do strruktury utworzonej w pliku `model.py` należy zmodyfikować zawartość pliku `ankiety/admin.py` (`an`)




5
5



















