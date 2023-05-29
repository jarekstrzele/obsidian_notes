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








