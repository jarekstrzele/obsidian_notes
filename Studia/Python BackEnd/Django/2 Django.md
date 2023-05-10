
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
- następnie Django ładuje odpowiedni widok , przekazując `HttpRequest` jako pierwszy rgument do funkcji widoku
- każdy widok to funkcja przyjmująca jeden obowiązkowyu parametr `request` i zwracająca obiekt `HttpRequest`
- Podczas wywoływania obiektu `HttpRequest`
	- konstruowany jest obiekt `Request`, który zostaje wysłany do serwera, aby zażądać albo wykonać zaputanie dotyczące jakiegoś zasobu
	- obiekt `Response`















