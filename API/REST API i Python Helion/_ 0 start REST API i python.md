#helion 
#api  #restapi #python #fastapi  #pytest #mongodb 
#wybierek_dawid

---
# Rest Api w Pythonie - start
[[2.1 Hello world]]
[[2.2 Modele Pydantic]]
[[2.3 MongoDB]]
[[3 - Struktura projektu]]
[[4 - testy]]


>[!important] API Application Programming Interface
>zbiór reguł ściśle opisujący, w jaki sposób programy lub podprogramy komunikują się ze sobą
> 


>[!important] REST 
>REpresentational State Transfer i/lub styl architektoniczny dla rozproszonych systemów hipermedialnych (Roy Fielding 2000)
>
>Interfejs API seici WEB (lub usługa sieci Web) zgodny ze stylem architektownicznym REST to interfejs REST API


 KLIENT - aplikacja/usługa uzyskująca dostęp do zasobów 
SERWER - aplikacja/usługa, w której znajdują się zasoby (np. SOAP serwer api nie jest rest, narzuca bardzo określone struktury)

## 6 zasad Rest
ograniczenia architektoniczne
1. ==Jednolity interfejs==
	1. wszystkie żądanie o pewien zasób powinny być takie same, niezależnie skąd 
	2. jeden element danych (np. imię, nazwisko, email użytkownika <-> jeden URi)
2. ==Rozdzielenie klienta i serwera==
	1. client app powinna dysponować wyłącznie informacja o `uri` żądanego zasobu, nie może wchodzić w interakcje z serwerem w żaden inny sposób
	2. server app nie powinna modyfikować client app, a tylko przekazywać zasób przy użyciu protokołu http
3. ==Bezstanowość==
	1. każde żądanie musi zawierać wszystkie informacje niezbędne do jego przetworzenia 
	2. aplikacje serwera nie mogą przechowywać żadnych danych związanych z żądanie klienta
4. ==Możliwość buforowania==
	1. klient musi mieć informacje o możliwości buforowania danego zasobu
	2. odpowiedzi srwera muszą zawierać info o możliwości buforowania zasobu
5. ==Warstwowa architektura systemu==
	1. wywołania i odpowiedzi przechodzą przez różne warstwy
	2. ani serwer ani klient nie powinni wiedzieć, czy komunikują się z elementem pośredniczącą czy aplikacją końcową
6. kod na żądanie (opcjonalnie)
	1. kod wykonywalny tylko na żądani
		
---
## HTTP
Hypertext Transfer Protocol
protokół bezstanowy: ani serwer ani klient nie przechowuje informacji o tym, jakie były wcześniej zapytania, nie ma też stanów wewnętrznych
==>
KAŻDE ZAPYTANIE DO SERWERA JEST JAKBY NOWE!

tą bezstanowość obchodzi się przy użyciu ciasteczek (cookies)

### metody HTTP
służą do rozgraniczania róznych czynność, które mamy zamiar wykonać, pomagają także w projektowaniu przeglądarek internetowych i obsłudze zapytań
Najpopularniejsze:
- GET
- POST (tworzenie zasobu)
- PUT (aktualizacja zasobu)
- DELETE


### kody odpowiedzi HTTP
statusy
- *1xx*  rzadkie, dotyczą środowiska (np. 111 serwer odrzucił połączenie)
- *2xx* - zapytanie się powiodło
- *3xx* - przekierowanie, zapytania należy kierować pod inny adres
- *4xx* błąd aplikacji psowodowany działaniem użytkowanika
	- 404 nie znaleziono
	- 304 brak dostępu
	- 400 niepoprawne zapytanie
- *5xx* błąd serwera (np. nieobsłużonych wyjątek wkodzie)


-------
## VS CODE
#vscode
extentions:
- python
- autoDocstring
- 

## środowisko wirtualne
`python3 -m venv venv_api`
warto podłączyć z automatu to środowisk
```shell
$ source  venv_api/bin/activate
(venv_api) (base) jarek@jarek-Lenovo-G700:~/MEGAsync/PROG/API/rest_api$ 
```








































