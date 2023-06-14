
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
> - aby z niego skorzystać musisz utworzyć konto admina 
> 	- `python manage.py createsuperuser`
> 	- wprowadź nazwę użytkownika, opcjonalnie e-mai, hasło





5
5



















