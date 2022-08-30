[[Komendy]]
[[Repozytorium]]
  
---

# Pojęcia podstawowe
#git
#samuraj_programowania
#udemy 



**git to rozproszony system kontrolii wersji**  
-   **VCS** version control system służy do zarządzania projektem w czasie.  
-   Tworzy historię projektu,  
-   pozwala na współpracę wielu osób i łączenie ich pracy  
-   pomaga śledzić zmiany i łączyć kod wielu osób pracujących nad projektem  
-   pozwala podróżować  w czasie (do poprzednich wersji projektu)  między różnymi światami (przełączanie między branch'ami)  
    
 **repozytorium** to pojęcie obejmujące  : 
-   pliki projektu oraz  
-   zapis historii zmian  
    

 **rozprosozny**:  
-   każdy użytkowani danego repo ma własne kompletne repo na swoim komputerze (**repo lokalne**),  
-   lokalne repo nie musi być podłączone do sieci,  
-   lokalne może być aktualizowane o zmiany w globalnym repo  
-   repo lokalne może być łączone z repo głównym  
-   najczęściej istnieje repo główne/zdaln  
    

# JAK DZIAŁA GIT?  
-   git robi snapshoty i zapisuje je w obiektach repozytorium projektu  
-   **commit** - zapisanie w repo aktualnego stanu projektu (stopklatka, save, snapshot, migawka),  
-   **snapshot** zawiera kompletny stan projektu   
-   **historia** projektu to ciąg snapshotów  
    

## GITHUB  
serwis internetowy na którym możemy przechowywać nasze repo  


# WIERSZ POLECEŃ  
git - możńa pracować w wierszu poleceń jak i w interfejsie graficznym  
CLI - Command Line Interface  

## powłoki tekstowe:  
-   Bash,   
-   PowerShell (windows)  
-   CMD (windows)  
-   GitBush (na windowsa)  
  

## GIT ogólnie  
-   napisany w C  
-   2005, Linus Torvald  
-   używa algorytmu SHA1 (=> git jest bardzo bezpieczny (integralność danych))  
-   robi kopię całego projektu a nie tylko zmian  

---
  

 # SECTION 2 INSTALACJA i wiersz poleceń   

cls - powershell  
clear git bushh  
cd.. powershell  
cd .. gitbush powershell  
mkdrir       -   bash power  
dir - kistowanie  
touch - tworzenie pliku  
nazwa - tworzenie pliku  

`echo "jakiś tekst" >> about.html `  stworzy plik about z treścią  

Visual Studio Code --> View --> Command Pallet--> select default shell  

---
# section 3 REPOZYTORIUM

**.git            repozytorium**  

konfiguracja gita (pilk konfiguracyjy znajduje się w **.git jako .gitconfig**  

`git config`  global user.name "userName"  

`git config`  global user.email "emaul@cos.pl"  

`git config`  global core.editor   

`git config user.name = "username"`
to będa dane lokalne, tylko dla danego projektu  

`git config --global --unset user.email`
kasuje wartość user.email   

## PROJEKT KSIĄŻKI  
git init --help       // dokumentacja  

git init -h            // o parametrach  

_ls -a_            a       w      windowsie                  _dir -h_  

   
mamy trzy obszary:
-   katalog robczy  
-   katalog .git ( czyli katalog z repo)  
-   index, przechowalnia, stage             pomiędzy coś oczekujące na dodanie  
    
`git add fileName  
`git commit -m "initial commit"  
`git log  
`git log --oneline  

> 4 stany plików w repo GIT  
> 
> 1.  plik nieśledzony  
> 2.  plik śledzony  
	> 1.  niezmodyfikowany  
	>  2.  zmodyfikowany  
>    > 3.  w indeksie  
>     

  
Mamy plik śledzony.  
Zmodyfikowaliśmy ten plik.  
Plik ma status zmodyfikowany.  
Aby powrócić do stanu przed modyfikacją:  
#git/checkout
`git checkout nazwaPliku`

ale git podpowiada, że   
`git restore nazwaPliku
ta komenda przywóci plik do ostatniego commit

`git add --all`      `git add -A`        `git add .`  


JEDEN PLIK W DWÓCH STANACH:  
1. dodałem plik do stage area.  
2. plik ten potem zmodyfikowałem  
3. ==> nasz plik jest w dwóch wersjach:  

                 -   w stage area (1.)                    
                 -   po modyfikacji (2.)  


zmieniamy nazwę pliku z chapter2 na chapter4  
`$ git mv chapter2.txt chapter4.txt   

  
1. mam plik `xx.txt` i jest on tracked  
2. dodaję do niego nową treść, ale nie dodaję tego pliku do staging area  
3. `git checkout -- xx.txt`  # spowoduje powrót do stanu pliku bez dodanej nowej treści, czyli do punktu.  

## USUWANIE PLIKU  
Chcemy usunąć pli `intro.txt`  
#git/deleting
`rm intro.txt`  

`git status` informuje nas, że plik został usunięty,
**ALE MUSIMY GO JESZCZE USUNĄĆ Z REPOZYTORIUM!!!!!!!!!!!!!!!**  
```bash
git add .
git commit -m "dew"  
```
ale dopóki nie zrobimy git add, commit łatwo przywrócimy ten plik pisząc  
```bash
git checkout -- nazwa_skasowanego_pliku
git checkout -- info.txt  
```
  
_aby jednocześnie USNUNĄĆ+USUNĄĆ_z_REPO_:  
`git rm nazwa_pliku  

na zielono otrzymujemy komunikat, że plik skasowano  
```bash
$ git status   

On branch master  

Changes to be committed:  

  (use "git restore --staged <file>..." to unstage)  

        deleted:    intro.txt  
```

teraz chcemy przywrócić ten plik do folderu i staging are  

choć w/w `git restore -stage ....`,
to w kursie proponują git reset, czyli przywróć stan staging area przed wykonaniem komendy git rm nazwa_pliku  


pokazuje mi, że (na czerwono) że ten plik jest skasowany)  

w kursie proponują `git checkout -- nazwa=pliku  

ale mi się wyświetla inna podpowiedź, aby użyć komendy `restor  
```bash

$ git status   

On branch master  

Changes not staged for commit:  

  (use "git add/rm <file>..." to update what will be committed)  

  (use "git restore <file>..." to discard changes in working directory)  
```
rozwiązanie z kursu też działa  

## CLONE
#git/clone
                               `git clone  

klonowanie lokalne  
*git clone   skąd     dokąd*

`git clone  nazwaFolderuDosklonowania  NazwaSklonowanegoRepo  

remotely  
`git clone https://adres_danego_repo  

---------------  

zrobiliśmy commit z błędnym komentarzem, aby móc ten komentarz edytować piszemy  

`git commit --amend  

WYLUCZENIE PLIKÓW I FOLDERÓW -.gitignore  

`# komentarz
`tegoplikuNieuwzględniaj.txt
`# tego katalogu też nie uwzględniaj
``/katalog_nigdy_nieśledzony  

  
Może się zdarzyć, że mimo zainstalowania Gita Twój VSC nie pokazuje informacji o stanie repozytorium (czyli na przykład nie widzisz listy plików w zakładce Source Control czy literek przy plikach). Sprawdź wtedy czy w swoich ustawieniach nie masz włączonych opcji, które sprawiają, że VSC ignoruje Gita.File -> Preferences -> Settings -> Open Settings JSON (ikonka w prawym górnym rogu). Jeśli masz takie właściwości i wartości, to je usuń lub zakomentuj.  

1.  "git.enabled": false,  
2.  "git.autorefresh": false,  
    

W folderze `.git/objects`   GIT przechowuje informacje o plikach w repo  

git cat-file -p tu_numer(dwie pierwsze cyfry folderu ,reszta cyfr z nazwy pliku)
-p   pokaż zawartość  

-t    pokaż typ (blob, commit, tree, ...)

git cat-file -p tu_numerHash

  

git hash-object uset.txt
git hash-object name.txt

git hash-object nazwa_pliku => hash tego pliku  

git log --oneline => pierwszy cyfr hasha