#git/repo

[[0-Git wprowadzenie samuraj]]
**REPOZYTORIUM      baza danych projektu**  

**repo** (czyt. ripo) historia stanów projektu objemująca:  
-   wszystkie commits  
-   stworzone w wyniku commits snapshots  
-   relacje między snapshotami (kolejność)   
    

**commit**  
#git/commit
-   zapisanie (zgłoszenie, wysłanie) w repo informacji zawartych w commit (pliki + metadane),  
-    utworzenie snapshota (kompletny zapis stanu projektu)  
    

Każdy commit jest obiektem w bazie danych repo Git .  

Commitowane (commit) jest to, co zawarte w przechowalni (staging area)   
 

**snapshot**  
#git/snapshot
(migawka, obiekt projektu, stopklatka, synonim commitu)  
-   zapisany stan indeksu (staging area) w chwili commitu  
-   zawiera:  
	-   kompletny projekt  
    -   metadane  
    -   referencje do plików, które się nie zmieniły  
    

**TRZY OBSZARY REPOZYTORIUM**  
-   working directory  
-   working tree  
-   nasze pliki i foldery + .git  
-   > to, na czym aktualnie pracujemy  
-   **staging area (index)** 
	-   poczekalnia, przechowywalnia, indeks  
	-   zawiera  
	-   pliku z aktualną zawartością (te zmienione)  
	-   pliki, które nie uległy zmianie 
	- zmiany, które chcemy zatwierdzić, inne niż  w repozytorium, ale też niekoniecznie aktualne (**czyli niekoniecznie te same co w katalogu roboczym**)  
    
-   **git folder (stricte repository)**  


OBIEKTY W REPOZYTORIUM  

> git przechowuje dane jako obiekty posiadające swój własny hash (identyfikator obiektu)   

*commits and files have hash*  
jeżeli pliki mają taką samą treść (nawet jeżeli nazwy plików są różne), to będą miały ten sam hash  
  

CZTERY STANY PLIKÓW W REPOZYTORIUM  
1.  **untracked** (nieśledzony)  
	1.  nowy plik w katalogu roboczym  
	2.  plik usunięty ze śledzonych  

2.  **tracked unmodified** (śledzony niezmodyfikowany) (po commit)  
	1.  pliki dodane do repo  
	2.  ale nie były modyfikowane  

3.  **tracked modified** (śledzony zmodyfikowany)  
	1. pliki już dodane do repo + uległy modyfikacji (aktualnie edytowane)  
4.  **tracked staged** (śledzony w poczekalni)  
   1.  plik w staging area + czekający na commit 

5. typ to plik ignorowany






