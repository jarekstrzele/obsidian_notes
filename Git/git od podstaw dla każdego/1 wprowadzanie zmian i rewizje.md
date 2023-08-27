[[_ git od podstaw]]

`git status` - sprawdzanie stanu (pokazywanie różnic między przestrzeniami): 
	- *working tree*, 
	- *staging area*, 
	- *local repository*

*no commits yet* - w *local repository* brak commitów/ rewizji

*nothing to commit* - w *staging area* brak zmian, które mogłyby zostać dodane do kolejnej rewizji


-----
# Pliki nieśledzone `untracked files `
to te, które są w katalogu roboczym, a nie znajdują się w *index*

`git add <file_name>` (przenosi plik z nieśledzonych do poczekalni) (czyli ten plik jest w *working tree* oraz w *staging area*)

Jeżeli wprowadzę zmiany w pliku, to nie są one automatycznie zapisywane w *staging area*


# Commit - rewizja
`git commit -m "some message"`

`git show` pokazuje, jaki informacje niesie ze sobą rewizja

`git show <idcommit>`


# Funkcja skrótu
Git jej używa w wielu miejscach `SHA1` - tej funkcji używa GIT

>[!info] funkcja skrótu
> na ==wejściu== przyjmuje pewne dane (np. łańcuch znaków)
> na ==wyjściu== zwraca jakąś liczbę , która charakteryzuje te dane
>

dobra funkcja skrótu powinna:
- dla danego tekstu zawsze  mieć tę samą liczbę na wyjściu
- być nieodwracalną, czyli z danej liczby nie można uzyskać zakodowanego tekstu
- liczba na wyjściu nie może się powtarzać

`index` GITa  to słownik `klucz:plik`, gdzie kluczem jest skrót tego pliku

funkcji skrótu używa GIT jako identyfikatorów rewizji




