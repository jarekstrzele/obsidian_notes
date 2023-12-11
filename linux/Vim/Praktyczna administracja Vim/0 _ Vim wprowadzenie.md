**Udemy Praktyczna Administracja Edytor Vim**   
**Łukasz Bartnicki**  

# Vim wprowadzenie   
[[rejestry]]
[[obiekty tekstowe]]
[[tryby]]
[[usun, dodaj, wstaw]]
[[wyszukaj i podmieniaj str]]


## Tryby pracy

1. _normal/command Mode_ Esc ( wpisujesz komendy, polecenia)
2. *insert mode* i (edytowanie treści pliku)  
3. *command-line Mode*                
	1. bardziej zapisywanie pliku, 
	2. wychodzenie z pliku metapolecenia 
4.  *Visual mode*  
5.  *Replace Mode*  
    
Vi ma alias do vim, więc pisząc vi uruchamiam vima  

`:q` wyjście z pliku bez zapisywania  
`:q!`    CHCĘ WYJŚĆ NIC NIE ZAPISUJ!!!!  
`:w`      write the content of the file  
`:wq`   zapisz i wyjdź  

**NAWIGACJA**  
#vim/nawigacja
	 
     k  
h       l  
     j  

  
**przerzucanie stron**:  
`ctr+f     ctr+bgg     # POCZĄTEK PLIKU ` 
`shift+g               # KONIEC PLIKU   `
`:1                    # do pierwszej linii:30 do 30 linii  `

  **słowa**  
`w   do przodu   `
`b   do tyłu  `

5w 4b   ileSłów  
bez znaków interpunkcyjnych:          shift+w               shift+b  
  

## [[rejestry]]

**Section 6. Dodwaj i łącz tekst**  

**DODAWANIE**  

**i**                     insert mode  
**shift+i**          od początku linii  

**a**                     append mode  
**shift+a**          od końca linii  
 

**liczniki** - wstawianie wielokrotnie  
**5i**           wpis słowa + esc -> słowo pojawi się pięć razy  

`o`                  pisanie w linii poniżej  

`shift+o`   pisanie w linii powyżej  

np. 5o '#' - wstawi w pięciu liniach znak '#'  

**PODMIANA**  
#vim/replace
**r**                      podmiana znaku  
**shft+r**             podmiana ciągła REPLACE MODE  

**cw**                  zmiana słowa change mode  
**3cw**                zamiana 3 słów  

**c0**                      zamiana do początku linii  
**c$**                      zamiana do końca linii  

  

**ZMIANA LITER**  
**~**                   zmiana litery z małych na duże i na odwrót  

`g~~`             zmiana do końca linii z małych na duże i na odwrót  
`gUU`             zmiana całej linii na duże litery  

`guu`             zmiana całej linii na małe litery  
`gwU`             zmiana słowa na duże litery  
`gwu`            zmiana słowa na małe litery  

  
==LINIE==
`shift + j`             złączenie linijek  
`shift + a`         dopisywania na końcu linii, w której znajduje się kursor  
`shift + i`           dopisywanie na początku linii, w której znajduje się kursor  

---
[[wyszukaj i podmieniaj str]]
  
[[tryby]]
[[obiekty tekstowe]]


[[Bufory i okna]]
  

---



---

  

  

**SECTION 12 Konfiguruj vim i użyj dokumentacji wbudowanej**  

  

  

HELP  

  

  

:helpwyjście :q  

  

  

:help [komenda]  

  

  

:help [początek komendy] + ctrl + d - podpowiedź komendy  

  

  

  

  

  

ctrl + ]= przejście opisu dla słowa aktualnie pod kursorem  

  

  

ctrl + i-przejście do przodu  

  

  

ctrl + o- przejście do  

  

  

  

  

  

Konviguracja set i vimrc  

  

  

.vimrc  

  

  

  

  

  

vim --version -wyświetla wersje Vim i ścieżkę do plików vimrc  

  

  

  

  

  

:set-aktualne ustawienia  

  

  

:set[ustawienie]?-pokazanie aktualnego ustawienia np. :set history?  

  

  

:set[ustawienie]!-zmiania ustawienia na przeciwne  

  

  

  

  

  

:set'[ustawienie]'-wyświetlenie manual dla opcji  

  

  

  

  

  

  

  

  

:help option-list -wyświetlanie spisu ustawień  

  

  

  

  

  

Ciekawe opcje-set:  

  

  

history-wielkość historii podpowiedzi  

  

  

expandtab-zamiana tabów na spacje  

  

  

showcmd-pokazywanie wpisywanych komend  

  

  

number-numerowanie linii  

  

  

hlsearch-podświetlanie wyników wyszukiwania  

  

  

backup-auto backup plików przed zmianą  

  

  

bex-backup extension-rozszerzenie dopisywane do nazwy pliku backup  

  

  

  

  

  

CONTROL + d - podpowiadanie opcji  

  

  

  

  

  

:set ruler!-linika  

  

  

  

  

  

w pliku .vmrc wpisujesz  

  

  

set [istawienie]  

  

  

ale  

  

  

set bex=.bck