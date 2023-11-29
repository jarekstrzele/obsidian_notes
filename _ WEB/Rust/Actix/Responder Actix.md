
#### `Responder`
- jest używany do reprezentowania typów, które mogą być zamieniane na odpowiedzi HTTP
- każdy *handler* **musi** zwracać typ implementujący trait `Responder` . Dzięki temu, biblioteka może automatycznie przekształcać wartości zwracane przez handlery na odpowiednie odpowiedzi HTTP
- definiuje metodę `respond_to`, która jest odpowiedzialna za przekształcenie wartości na odpowiedzi HTTP
- przykładowe typy, które implementują trait `Responder`:
	- `String` zwrócenie tekstu jako odpowiedź
	- `&str` zwrócenie referencję do napisu jako odpowiedź
	- `Vec<u8>` zwrócenie wektora bajtów jako odpowiedź
	- `HttpResponse` można zwrócić gotową strukturę `HttpResponse` z odpowiednimi nagłówkami, statusem i treścią










