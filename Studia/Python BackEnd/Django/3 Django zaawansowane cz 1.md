#python #django 

Agenda
1. Wprowadzeni
2. Szablony
3. Konfiguracja silnika szblonów
4. kontekst i procesory kontekstu
5. język szablonów Django i Jinja2
6. pliki statyczne
7. formularze
8. formularze oparte na modelach
9. widgety
10. pola formularza
11. waliacja formularza
12. walidatory
13. obsługa błędów formularza
14. metaklasy i meadane formularzy
15. widoki generyczne

--------------
**WZORZEC MTV** *Model-Template-View*
#django/mtv

MODEL - logika bazodanowa
SZABLON - określa wygląd (HTML)
WIDOK - spina razem model i szablon tworząc gotową stronę

WIDOK:
- w pliku `view.py` 
- to funkcja, która przyjmuje co najmniej jeden argument - obiekt `request`, a zwraca odpowiedź za pomocą ==`render_to_response`== (z szablonem może przyjmować kilka argumentów: nazwa szablony, słownik ze zmiennymi szablonu, `RequestContext` (zmienne globalne dla wszystkich szablonów)

**wygląd strony www** = kod z `view.py` + kod z `index.html`

SZABLON
#django/templates 
- plik tekstowy zawierający kod HTML, do którego możemy "wstrzykiwać" dodatkowe zmienne przekazane z widoku (dynamiczne renderowanie strony)
- może być generowany w dowolny formacie tekstowym (HTML< XML< CSV, ...)
- podstawowe elementy to `{{ content }}` symbole zastępcze, który wartości są generowane f=dynamicznie
- zaleca się tworzenie dla szablonów *przestrzeni nazw* (podfoldery z nazwą aplikacji), aby uniknąć błędów duplikowani, gdy
- utwórz katalog `templates` w katalogu głównym aplikacji
- 





