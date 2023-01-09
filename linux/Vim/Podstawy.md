VI(m)  
  

numerowanie wierzy 
` :set number `
wyłączyć:
`:set nonumber`
#vim/vmrc
na stałe w pliku *~/.vimrc* 
ustawić 'set number' 
instrukcja 
`echo -e '"wlaczenie numerowania linii\nset number' >> ~./vimrc  ``

włączenie terminala 
`:termin  `
  

### Na początku  
[[0 _ Vim wprowadzenie]]
```vim
:q! - wyjdź bez zapisywania zmian  
:wq - zapisz i wyjdź==:x  
:w - tylko zapisz  
```
   
`:syntax on  `   podświetlana składnia  

`dd `                    kasuje całą linię na której jest kursor  
 

### tryby
- tryb NORMAL - dokument do przeglądania, ale nie deytowania  
- tryb INSERT (esc) wyjście z tego trybu  
- tryb COMMAND-LINE  
  

**TRYB NORMAL**
#vim/normal
pozwala na bardziej złożone operacje na plikach,  
`YY`          kopiuje linijką
`P`            wkleja,
`6P`          sześć razy wkleja linijkę  

`DD`            usuwa linię
`4DD`          cztery linie  
  

**TRYB INSERT**  
#vim/insert
I - przejście do tego tryby w miejscu, gdzie jest kursor  
O - przejście do tego tryby w nowej linii  
A - przejście do tego tryby w następnym polu  
CW - przejście do tego tryby kasując słowo, na którym jest kursor  

kopiuj - wklej (zaznacz myszką lub visual block)  
crl+shift+c - kopiuje  

ctr + shift+v wkleja  


TRYB VISUAL BLOCK  
#vim/visual
 
pozwala zaznaczyć fragment(blok) tekstui wykonywać na nich operacje  
pozwala zaznaczać kolumny teksty  

1. z trybu normalnego CTRL V  
2. Poruszamy kursorem i zaznaczmy tekst  
3. D - usuwa zaznaczony tekst  
Y - kopiuje zaznaczony tekst  


## TRYB COMMAND_LINE 

- zastępowanie słów %s/słowo_do_zastąpienia/nowe_słowo/g  
- numeracja linii set number  
wiele innych  

  

Manual  

Ktoś może pomyśleć – „po co mi znajomość VIMa, przecież jest milion przyjaźniejszych dla użytkownika edytorów”. Zgodzę się, po części – jest wiele UNIX-owych edytorów tekstu posiadających interface dużo przyjaźniejszy jednak żaden z nich nie ma takich dużych możliwości jak stary poczciwy VIM, nie znam innego edytora, który z równie sprawnie i szybko edytuje pliki 200 megowe. Zresztą na niektórych serwerach (wierzcie mi, że są takie) VIM jest jedynym dostępnym edytorem tekstu.  

  
Jako, że kiedyś sam szukałem prostego manuala z podstawowymi komedami VIMa to może komuś się przyda:  

poruszanie się po dokumencie  
- przejście do następnej linii
- przejście do poprzedniej linii  
0 – przejście do początku linii  
^ – przejście do pierwszego znaku nie będącego znakiem białym w linii  
$ – przejście na koniec linii  
n| – przejście do kolumny n linii  

  

  

} – przejście do następnego paragrafu  

  

  

{ – przejście do poprzedniego paragrafu  

  

  

% – przejście do otwarcia / zamknięcia nawiasu (),[],<>,{}  

  

  

`G` – przejście na koniec dokumentu  
`nG` – przejście do linii 

### zapisywanie  
`:x` lub `:wq` – zapisywanie pliku i wyjście  
`:q!` – wyjście bez zapisania zmian  
`:w` plik – zapisanie w nowym pliku „plik”  

### wyszukiwanie  


`/ STRING` – szukanie do przodu  


? STRING – szukanie do tyłu  


n – przejście do następnego znalezionego elementu  

SHIFT+n przejście do poprzedniego znalezionego elementu  

### kasowanie tekstu  

`x` – kasowanie bieżącego znaku  
`nx` – kasowanie znaków  
`dw` – kasowanie bieżącego wyrazu  
`dd` – kasowanie bieżącej linii  
`ndd` – kasowanie linii  
`D` – kasowanie znaków od kursora do końca bieżącej lini  
`dG` – kasowanie wszystkiego od kursora do końca dokumentu  

### edycja tekstu    

`o` – wstawienie nowej linii poniżej bieżącej  
`O` – wstawienie nowej linii powyżej bieżącej  
`i` – rozpoczęcie edycji przed kursorem  
`I` – rozpoczęcie edycji na początku bieżącej linii  
`a` – rozpoczęcie edycji po kursorze  
`A` – rozpoczęcie edycji na końcu bieżącej linii  
`cw` – zastąpienie wyrazu (bieżący wyraz się kasuje, kursor ustawia się na jego początku)  
`cc` – zastąpienie linii (bieżąca linia się kasuje, kursor ustawia się na jej początku)  
 

### kopiowanie i wstawianie  
`yw` – kopiuj do schowka bieżący wyraz  
`yb` – kopiuj do schowka poprzedni wyraz  
`Y` – kopiuj do schowka bieżącą linię  
`nY` – kopiuj następne  linii  

`p` – wklej skopiowany tekst za kursorem  
`P` – wklej skopiowany tekst przed kursorem  
 

### inne  
`u` – cofnięcie ostatniej zmiany  
`U` – cofnięcie wszystkich zmian w bieżącej linii  
`.` – powtórzenie ostatniej komendy  
`SHIFT+#` – wyszukiwanie wyrażeń pasujących do zaznaczonego  
`SHIFT+%` – przejście do kolejnego nawiasu () lub {}  
`~` – zmiana litery z małej na dużą i na odwrót  


### zastępowanie  


Można używać wyrażeń regularnych PERL- kompatybilnych  

  

  

zastąpienie stringu OLD stringiem NEW  

  

  

:s/OLD/NEW – pierwszego wystąpienia w bieżącej linii  

  

  

:s/OLD/NEW/g – każdego wystąpienia w linii  

  

  

:#,#s/OLD/NEW/g – pomiędzy liniami # i #  

  

  

:%s/OLD/NEW/g – w całym dokumencie  

  

  

:%s/\([0-9]\+\) OLD/\1 NEW/g – w całym dokumencie z użyciem backreferencji (trzeba poprzez „\” wyescapować znaki specjalne, następnie poprzez „\1” wstawić wyciągnięte dane)  

  

  

praca z danymi zewnętrznymi  

  

  

Vim umożliwia wywołanie dowolnej komendy z poziomu edytora, można także odczytywać efekt jej działania  

  

  

:! komenda – wywołanie 'komenda’ w shellu i wyświetlenie jej wyniku, komenda może być każde polecenie unixowe  

  

  

:r ! komenda – wywołanie 'komenda’ w shellu i wczytanie wyniku jej działania do edytora  

  

  

:r ! last | grep user – na wywoływanych komendach można robić dowolne operacje przed wczytaniem do edytora  

  

  

:r textfile – wczytanie źródła pliku 'textfile’ do edytora  

  

  

:r ! w3m http://en.wikipedia.org/wiki/Vi -dump – wczytanie do edytora zawartości strony internetowej  

  

  

Praca z zakładkami  

  

  

:tabs – wyświetlenie informacjie o aktualnie otwartych zakładkach  

  

  

:tabnew – otwarcie pustej zakładki  

  

  

:tabnew FILE – otwarcie pliku FILE w nowej zakładce  

  

  

:tabf FILE – otwarcie pliku w nowej zakładce  

  

  

:tabn – przejście do następnej zakładki  

  

  

gt – przejście do następnej zakładki (działa w trybie NORMAL)  

  

  

gT – przejście do poprzedniej zakładki (działa w trybie NORMAL)  

  

  

n gt – przejście do zakładki o numerze n (działa w trybie NORMAL)  

  

  

n gT – cofnięcie się do zakładki znajdującej się w odległości n od aktualnej (działa w trybie NORMAL)  

  

  

:tabp – przejście do poprzedniej zakładki  

  

  

:tabl – przejście do ostatniej zakładki  

  

  

:tabc – zamknięcie aktualnej zakładki, gdy jest jedna karta, to nie będzie zamknięta  

  

  

:tabo – zamknięcie wszystkich zakładek oprócz tej która jest aktualnie używana  

  

  

:tabd KOMENDA – wykonuje komendę na wszystkich otwartych zakładkach  

  

  

i  

  

  

Możliwe problemy i ich rozwiązania  

  

  

Jeżeli przy wklejaniu do konsoli kodu z tabulacjami/spacjami tworzą się niechciane wcięcia należy użyć polecenia „:set paste” następnie wkleić kod i ponownie ustawić „:set nopaste”, więcej o wklejaniu na w tym temacie stackoverflow