
#### `App` 
- główny komponent, który służy do konfigurowania aplikacji serwera HTTP
- jego struktura reprezentuje aplikację serwera HTTP i jest używana do definiowania tras (routing) oraz konfiguracji obsługi żądań
- umożliwia definiowanie ścieżek URL i przypisywania im funkcje obsługi *handler* (funkcja wywoływana w momencie otrzymania żądania)
- przykładowe metody:
	- `route()` umożliwia zdefiniowanie konkretnejścieżki URL i metody HTTP, która ma być obsługiwana przez określony handler
	- `service()` rejestruje *handler* jako obsługę okreśłonej ścieżki URL. Można zarejestrować wielokrotnie różne handlery dla tej samej ścieżki, obsługujące różne metody HTTP
	- `data()` przechowuje dane aplikacji,  które będą dostępne dla wszystkich handlerów w ramach aplikacji
	- `wrap()` dodaje  [[middleware]] do aplikacji, który jest wywoływany przed osbłygą żądań przez handlery. 


