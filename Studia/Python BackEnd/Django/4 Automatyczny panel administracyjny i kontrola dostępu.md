
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

Przykładowa aplikacja ma `Question`, `Choice`. Aby dodać te obiekty do strruktury utworzonej w pliku `model.py` należy zmodyfikować zawartość pliku `ankiety/admin.py` (`ankiety` - to nazwa projektu)
```python
from .models import Question

admin.site.register(Question)

from .models import Choice

admin.site.register(Choice)
```

po ponownym uruchomieniu w panelu pojawi się projekt `ankiety` z `Choices` i `Questions` -> teraz na tych obiektach można wykonywać CRUD



# Sesje
- HTTP jest protokołem bezstanowym
	- *bezstanowy* komunikaty między klientem a serwerem są od siebie całkowicie niezależne, nie ma pojęcia "sekwencji" ani zachowania opartego na poprzednich komunikatach
- Komunikacja między przeglądarką a serwerem odbywa się za pomocą protokołu HTTP

zatem jeżeli chcemy mieć witrynę, która śledzi bieżące relacje z klientem, musimy to wdrożyć samodzielnie

>[!info] sesje
>mechanizm używany przez Django (i większość narzędzi Internetu) do śledzenia "stanu" między witryną a daną przeglądarką

- sesje umożliwiają przechowywanie dowolnych danych dla każdej przeglądarki i udostępnianie tych danych witrynie za każdym razem, gdy przeglądarka  połączy się ze stroną 
- 
### cookie
Django używa pliki cookie zawierające specjalny **identyfikator sesji** , aby zidentyfikować każdą przeglądarkę i powiązaną z nią sesję w witryną

rzeczywiste dane sesji są domyślnie przechowywane w bazie danych witryny (jest to bezpieczniejsze niż przechowywanie danych w pliku cookie, gdzie są bardzie podatne na złośliwych użytkowników)

### włączanie sesji
w `settings.py` powinny być zdefiniowane:
- w `MIDDLEWARE_CLASSES` klasa `django.contrib.sessions.middleware.SessionMiddleware`
- w `INSTALLED_APPS` aplikacja `django.contrib.sessions`

to oprogramowanie jest dodawane domyśłnie podczas tworzenia nowego projektu za pomocą polecenia `startproject`

gdy `SessionMiddleware`  jest aktywne każdy obiekt `HttpRequest` (pierwszy argument każdej funkcji widoków) będzie miał atrybut `session`,  który jest podobny do słownika

### ustawienia sesji
`Middleware` można konfigurować z poziomu `settings.py`

`SESSION_ENGINE` pozwala na zdefiniowanie miejsca przeznaczonego do przechowywania sesji (domyślnie sesja jest przechowywana w bazie danych - model Session `django.contrib.sessions`)

##### opcje przechowywania sesji
- **sesje oparte na bazie danych** (domyślni silnik sesji)
- **sesje oparte na plikach** - dane sesji przechowywane w systemie plików
- **sesje buforowane** dane sesji są przechowywane w buforze (opcja CACHES można wskazać mechanizm buforowania - najlepsza wydajność)
- **buforowane sesje oparte na bazie danych** - dane sesji są przechowywane w buforze operacji zapisu i bazie danych. Odczyt danych następuje z bazy danych tylko wtedy, gdy dane nie znajdują się już w buforze
- **buforowane sesje oparte na mechanizmie cookies** dane sesji są przechowywane w plikach cookies wysyłanych do przeglądarki internetowej
- 
#### pozostałe opcje `Middleware`
- `SESSION_COOKIE_AGE` czas ważności cookie sesji w sekundach
- `SESSION_COOKIE_DOMAIN` domena ciasteczka pozwala na ustawienie dowolnej domeny tak by uzyskać dostęp do ciasteczka w obrębie całej domeny i subdomeny, wartość 'None' pozwala na standardowe ustawienia ciasteczka dla bieżącej domeny
- `SESSION_COOKIE_NAME` nazwa ciasteczka dla sesji, domyślnie sessionid
- `SESSION_COOKIE_SECURE` - jeżeli ustawione na `TRUE` ciasteczko będzie przesyłane tylko przez połączenia `HTTPS`
- `SESSION_EXPIRE_AT_BROWSER_CLOSE` jężeli ustawione na `True` sesja wygaśnie po zamknięciu przeglądarki

atrybuty sesji
```python
# ustawiamy sesję o nazwie "moj_wybor"
request.session['moj_wybor'] = 'wybor1'

request.session.get('moj_wybor')

del request.session['moj_wybor']
```

domyślnie Django zapisuje tyl






