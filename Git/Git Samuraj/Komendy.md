[[Repozytorium]]
[[0-Git wprowadzenie samuraj]]

---


# konfiguracja  

`git config --global user.name "jan nowak"`
`git config --global user.email` 
// bez --globalnie będą ustawienia lokalne  

`git config --unset --logbal user.email`  usunięcie  

`git config --global core.editor ` jaki edytor

`git config --global --list `


---
# inicjalizacja  
`git init`
`git init _path_`

`git init -h` // jakie parametry możemy użyć
`git init --help` // dokumentacj

`git clone http...`
`git clone kurs-git kopia-kurs-git ` 

---

# ADD  

git add // dodawanie aktualnej wersji plików 
            // do kat robo do staging area

Dodawanie wszystkich plików (modified and untracked)
git add -A  

git add --all
git add . //katalog bieżący z podkatalogami  

---

# COMMIT zaktualizowanie repo  
`git commit`

commit robi:  
-  tworzy obiekt commita w bazie  
-  tworzy obiekt tree w bazie  
- tworzy informacje o nowym commicie w gałęzi, w której jesteśmy  
- ustawia HEAD na najnowszą zmianę  
    

  

opis  `-m`
-  40-60 znaków,  
-  present simple   
- po pierwszej linii pusta linia i dopiero wtedy nowa treść  
   
przeniesienie do indeksu wszystkich śledzonych (tracked) plików z katalogu roboczego  
`git commit -a ( git commit --all)`

przeniesienie pliku z roboczego od razu do repo
`git commit plik.js`  
 
gdy coś poszło nie tak:  
// ?powrót do ostatniego commitu
`git commit --amend`

// zmiana tylko message
`git commit --amend -m "our new message`  

  ---

# LOG  
`git log`  // wychodzimy prze 'q'

`git log --oneline`
`git log --oneline 10`
`git log --since "2019"`
`git log --since="5.4.2019"`

wyszukiwanie konkretnych commitów
`git log --grep "plik.txt` wielkość liter ma znaczenie
			                       jeżeli w opisie występuje "plik.txt'

`git log --stat`  które pliki zmienilł commit w jaki spowób

---

``git show //szczegółowe zobaczenie zmian w danych komicie
`git show id_commitu`

---
`git diff` (porównanie) pokazuje domyślnie różnicę między plikami **kat.rob. a indeksem**

`git diff nazwa-pliku` konkretny plik

`git diff --cached`  pliki w indeksie vs pliki w repo (otatni commit)
to samo =>
`git diff --stage`

porównanie plików z różnymi commitami
git diff id_cimmit id_commit  

USUWANIE  

// usuwa pliki z kat.robo. i wersję z indeksu
// nie usuwa tego pliku z historii repo
**git rm plik**  

// trzeba potwierdzić commitem

// usunięcie tylko z katologu roboczego  

**rm plik**

// usuwanie pliku z indeksu, ale nie z kat.robo.  

// plik będzie untracked  

**git rm --cached plik**

  

rm file                    // usuwa z kat.robo.
git rm --cached file       // usuwa z indeksu  

git rm file                // usuwa z kat.robo i z indeksu  

  

git mv plik newNamedfile  

  

  

**C H E C K O U T**   

// wersja z kat.robo. jest usuwana  

// wersja z indeksu jest przywracana  

// jeżeli brak zmian w przechowalni, to przywracany stan z ostatniego commit
**git checkout plik**   

**lepsza wersja tej komendy**  

                        **git checkout -- plik**  

// bez kresek git może  

// nie wiedzieć, że parametr jest nazwą pliku// gdy chcemy przywrócić stan kat.robo. z ostatniego commit**git checkout HEAD -- plik**   

// przywrócić indeks ze stanu ostatniego commit
git checkout id_num_of_commit   

  

RESET  

**git reset / reset HEAD**  

-   usuwa pliki ze staging area  
    
-   pliki są nadal śledzone  
    
-   pliki pozostają w kat.robo.  
    
-   stan staging area taki jak po ostatnim commit  
    
-   HEAD - użcie tego jest czytelniejsze
    
    gdybyśmy chcieli z indeksu usunąć tylko konkretny plik/folder  
    

**git reset -- plik
gir reset HEAD plik**  

---

  

  

B R A N C H E S  

  

git branch      // na jakiej gałęzi jesteś
git branch nazwa-nowego-brancha  

git checkout nazwa-istniejącego brancha  // przełączanie się na inny branch  

git merge nazwa-brancha      // aktualną gałąż łączymy z nazwa-brancha  

**HEAD**  

-   określa, do której gałęzi się odnosimy,  
    
-   wskazuje na ostatni commit  
    
-   .git/HEAD/refs/master  
    

  

  

git P U S H  

przekazywanie zmian z local repo do remote repo  

  

git P U L L  

pobieranie zmian z remote repo do local repo




