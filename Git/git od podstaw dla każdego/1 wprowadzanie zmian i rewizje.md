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





