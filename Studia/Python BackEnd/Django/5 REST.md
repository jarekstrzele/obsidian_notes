#rest 
#django 

[[5.1. Serwer JSON]]




# REST

>[!info] REST
> Representational State Transfer
> - rodzaj architektury opartej na określonych **regułach opisujących jak definiowane są zasoby**
> - umożliwia **dostęp** do zasobów 
> - powstał 2000 Roy T.Fielding
> - do komunikacji występuje **protokół HTTP**
> - niezależny od danej technologii

podczas tworzenia REST API do komunikacji wykorzystuje się **metody HTTP**


# API
>[!info] API
>Application Programming Interface
>- **interfejs** programowania aplikacji wykorzystywany do łączenia aplikacji
>- **metoda komunikacji** pomiędzy składnikami składnikami oprogramowania i aplikacji sieciowymi oraz wymiany danych między oddzielnymi systemami

- rozszerza funkcjonalności aplikacji sieciowych poprzez gromadzenie **danych ze źródeł zewnętrznych**
- umożliwia **dzielenie dużych systemów** na małe usługi 

## Elementy API
- *procedury* - (rutyny) odnoszą się do konkretnych zadań lub funkcji wykonywanych przez program
- *protokoły* - służy do wymiany danych pomiędzy aplikacjami
- *narzędzia* - segmenty, z których można tworzyć nowe programy

## ZALETY API
- *uniwersalność* - umożliwia stworzenie jednego API do różnych aplikacji
- *intuicyjny interfejs* - 
- *wykorzystanie formatu JSON* - lekki testowy format wymiany danych 
- uzyskiwanie danych z wielu źródeł
- odseparowanie warstwy klienta, od warstwy serwerowej
- łatwe testowanie endpointów


## działanie API
- klient tworzy zapytanie w postaci adresu (endpoint)
- klient wysyła zapytanie (*request*)
- serwer otrzymuje zapytanie klienta i przygotowuje odpowiedź (*response*)
- serwer zwraca odpowiedź na zapytanie klient
- klient otrzymuje i przetwarza odpowiedź


# zasady opisujące REST

## odseparowanie interfejsu użytkownika od operacji na serwerze
- klient po wydaniu zapytania nie może wpłynąć na działanie serwera
- umożliwia wykorzystani jednego REST API w wielu niezależnych od siebie aplikacjach, a dane pozostaną spójne

## Bezstanowość (*stateless*)
- każde zapytanie klienta musi zawierać komplet informacji
- serwer nie przechowuje stanu o sesji użytkownika


## Cacheability
06:00
- otrzymana odpowiedź z REST API musi być zdefiniowana jako cacheable czy non-cacheable
- ma to związek z danymi które często się zmieniają
- np. można podać dane pogodowe w ujęciu minotowym, które szybko się zmieniają

## endpoint
- adresy zasobów, powinny jednoznacznie wskazywać, do którego zasobu się odwołują
- dane otrzymana w API powinny być niezależne od schematu bazy danych, w której są przechowywane

## separacja warstw
- warstwa dostępu do danych powinna być oddzielona od logiki biznesowej oraz prezentacji
- oddziaływanie pomiędzy warstwami powinno być znikome lub żadne


## udostępnienie adapterów i skryptów użytkownikowi
opcjonalna reguła, mówiąca o tym, że jeżeli wiemy, że klient chce wykonać konkretne operacje na danych to można udostępnić gotowe rozwiązania


----
# Praca z REST API

## metody
do najpopularniejszych metod HTTP zaliczamy:
- GET - pobierać zasób
- POST - wysyłać/tworzyć nowy zasób (np. uzupełnianie formularza na stronie internetowej)
- PUT - aktualizuje zasób
- DELETE

## kody statusu
- praca z REST API wiąże się z otrzymywaniem komunikatów podczas odbioru i przetworzenia żądania HTTP
- w odpowiedzi znajduje się kod stanu HTTP
- kod zawiera informacje o wynikach żądania

`200` ok
`201` utworzono nowy zasób
`202` prośba została odebrana, ale nie wprowadzono jeszcze żadnych zmian
`204` żądanie powiodło się, ale odpowiedź nie zawiera treści


`400` żądanie było zniekształcone
`401`  klient nie ma uprawnień do wykonania żądanej akcji
`404` żądany zasób nie został znaleziony

## endpoint
- uzyskanie dostępu do zasobu jest realizowanie za pomocą udostępnionego zestawu publicznych adresów URL
- interfejs API REST udostępnia taki zestaw
- **adresy URL** w kontekście interfejsu API są nazywane **endpoints** punktami końcowymi


metoda http | endpoint | opis
---| --- | ----
get | /klienci | uzyskaj listę klientów
get | /klienci/klient_id | uzyskaj dostęp do klienta
post | /klienci | zaktualizuj dane klienta
delete | /klienci /klient_id / usuń klienta



-----










