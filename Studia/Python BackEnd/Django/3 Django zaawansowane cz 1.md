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






