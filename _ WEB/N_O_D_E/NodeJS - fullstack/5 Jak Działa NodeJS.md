[[_ 0 NodeJS - zostań fullstack]]


# Jednowątkowa pętla zdarzeń

## Proces
>[!info] Proces
>To isntancja uruchomionego programu, której system operacyjny przydzielił zasoby takie jak czas procesora, pamięć operacyją, dostęp do urządzeń I/O, pliki

**Każdy nowo uruchomiony proces posiada własną niezależną przestrzeń adresową**

np. uruchamiasz Photoshopa, to taki uruchomiony proces jest procesem Photoshopa
np. `cmd` > `tasklist`


# Wątek
#node/thread

>[!info] Wątek (*thread*)
>część programu wykonywana współbieżnie, uruchomiona przez procesor. Proces może uruchamiać wiele wątków. Wątek tym różni się od procesu, że współdzieli z innymi wątkami zasoby przydzielone dla procesu

- Wątki wymagają mniej zasobów do działania, a także są szybciej tworzone. 
- Mogą przekazywać pomiędzy sobą dowolną ilość danych bez ich kopiowania, jedynie przekazując sobie wskaźniki w pamięci operacyjnej.
- aby otrzymać wrażenie współbieżności, procesor przełącza się pomiędzy wątkamiw którkich odstępach czasu


## Wielowątkowy Node.js i jednowątkowa pętla zdarzeń

>  Node to:
>>  - silnik V8 (interpreter języka JS)
>> 	 - jest jednowątkowy
>>  - C++ (dodatkowe biblioteki C++) (NodeJS APIs)






# Bloki budulcowe Node.js






