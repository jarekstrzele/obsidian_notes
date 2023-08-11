[[_ git od podstaw]]

#git/commit 

# katalogi w GITcie
GITa nie interesują katalogi, bo git pracuje na plikach, więc dodanie nowego katalogu nic nie zmienia w repo

Katalogi są zapamiętywane jako ścieżka dostępu do pliku, więc dodanie pliku do folderu sprawi, że folder zostanie zapamiętany

- `git add *`
- `git commit -m "druga rewizja"`


rewizja_1 <---- rewizja_2


# Usuwanie plików

1. skasować plik
2. `git add <filename>`

`git commit -m "..."`


---
# rewizje gita

`git log` lista rewizji

`git log --graph` graf rewizji
`git log --graph --oneline`
`git log --graph --oneline --all` --- można zrobić alias do tego polecenia

## alias
#git/alias

```bash
$ git config --global alias.gr "log --graph --oneline --all"
```

```
jarek@jarek-legion:~/Desktop/git_test$ git gr
* 386d257 (HEAD -> main) add and delete sec.txt
* 18ec335 drugi commit
* 5c71221 first commit

```


---------
# porównywanie plików `git diff`
#git/diff

scenariusz:
- dodajemy nowy plik txt z zawartością
- `add`, `commit`
- modyfikujemy ten plik i `add` (czyli  w repo i w indeksie są dwa te pliki o różnej zawartości )
- jeszcze raz go modyfikujemy, ale bez `add`


`git diff` porównywania plików między przestrzeniami:
- `working tree` a `staging area`

`git diff --staged` porównywanie plików miedzy przestrzeniami:
- `staging area` a `local repository`





