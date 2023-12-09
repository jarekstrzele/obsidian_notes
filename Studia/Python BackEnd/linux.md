Dwie warstwy:  
- kernel space   
- user space  
najniżej jest harware

  

KERNEL SPACE:  
- system calls (zmieniają się wraz ze zmiana jądra  
- frameworki (zapewniają dostęp z user space'a do warstwy sprzętowej w celu realizacji zadań: ALSA zapewnia API do sterownikakarty dźwiękowej)  
- subsystem (sieciowy, wirtualne pliki, process schudule)


Kernel napisany w języku C.  
  
USER SPACE:

- najniższa to warstwa bibliotek stand _C_ (ok 30 ) dają dostęp do funkcji w systemie użytkownikowi . Biblioteki są używane przez wszystkie programy , które są kompilowane i wymagają określonych funkcji ( preprocessing analiza kodu i szukanie deklaracji określonych funkcji i w te deklaracje wkleja odpowiednie implementacji)  
- _demony_ - programy, które realizują pewne zadania i są wykonywane w tle w nazwie na końcu mają _d_ np. _systemd_, _logind_, ..

PODRĘCZNIKI SYSTEMOWE:  
pokazują, jak używać określonych funkcji


------------
BIN - wykonywalne pliki binarne  
BOOT - wszystkie pliki startowe i kernel  
DEV - odwołania do urządzeń peryferyjnych (pliki o specjalnych właściwościach)  
ETC - wszystkie pliki konfiguracyjne (taki windowsowy kontrol panel)  
LIB - biblioterki (funkcjie i klasy z których korzystajć mogą wszystkie programy)  
LOST_NOTFOUND - pliki z uruchamiania/zamykania systemu (  
MEDIA - partycie, cdrom  
MNT - tymczasowo montowane dyski  
OPT - aplikacje zewnętrzne  
PROC - szereg wirtualnych plików (info o systemie `man proc`  
  `cat` wyświetlenie zawartości pliku na ekranie
`cat uptime`   
 > $ cat version
> > 
> > Linux version 5.15.74.2-microsoft-standard-WSL2 (oe-user@oe-host) (x86_64-msft-linux-gcc (GCC) 9.3.0, GNU ld (GNU Binutils) 2.34.0.20200220) #1 SMP Wed Nov 2 19:50:29 UTC 2022

SBIN - programy przeznaczone do działania systemu i administrowania systemem  
USR - biblioteki narzędzi programy dla wszystkich użytkowników systemu  
VAR - dane, które ulegają modyfikacji w czasie działania 


`touch nazwaPliku` utworzenie pliku

> cp source destination
> 
> rm fileName
> 
> mv fileName
> 
> rm -r folderName
> 
> tail -n 10 fileName - wyświetl 10 ostanich wierdzy pliku
> 
> head -d 10 file name 
> 
> less fileName - do wyświetlania pliku i scrollowanie

  

---

PRZEKIEROWANIE

> $ head nowy.txt > 22.txt (przekopiuj w nowym pliku 22.txt dziesięć pierwszych wierszy z pliku nowy.txt
> 
> $ cat nowy.txt 22.txt > 3.txt (połącz plik nowy z plikiem 22 i zawartość tego połączenia zapisz w nowym pliku 3.txt
> 
> jarek@DESKTOP-5DM5KMG:~/test$ wc 22.txt
> >  14  22 117 22.txt
> jarek@DESKTOP-5DM5KMG:~/test$ wc -c 22.txt (ilość bytów)
> > 117 22.txt
> 
> jarek@DESKTOP-5DM5KMG:~/test$ wc -l 22.txt (ilość linii)
> 
> 14 22.txt
> 
> jarek@DESKTOP-5DM5KMG:~/test$ wc -w 22.txt (ilość słów)
> 
> 22 22.txt
> 
> jarek@DESKTOP-5DM5KMG:~/test$ wc -m 22.txt (ilość liter)
> 
> 115 22.txt

  

--------

## WYSZUKIWANIE
`locate`
`pwd`
`find lokalizacja coMaBYćZnalezione` - znajdź plik w danej lokalizacji
> $ find ./ -name 22.txt
> ./test/22.tx

  

---

## POWIĄZANIA
ln -s fileName linkName - stwórz miękkie dowiązanie
ln fileName HardLinkName 
```bash
jarek@DESKTOP-5DM5KMG:~/test$ ln nowy.txt HARDlink_do_nowy
jarek@DESKTOP-5DM5KMG:~/test$ ls -lsail
67518 4 -rw-r--r-- 2 jarek jarek 1774 Dec 10 18:13 HARDlink_do_nowy
67516 0 lrwxrwxrwx 1 jarek jarek    8 Dec 11 12:54 link_do_nowy -> nowy.txt
67518 4 -rw-r--r-- 2 jarek jarek 1774 Dec 10 18:13 nowy.txt
```
-----

## PRAWA DOSTĘPU

czytanie -           4 lub r  
pisanie               2 lub w  
wykonyuwanie - 1 lub x
> -  zwykły plik
> d katalog
> l dowiązanie symboliczne
> s gniazdo
> c urządzenie znakowe
> b urządzenie blokowe
  

`chmod  777 file/folder`

----------

## MANAGER PROCESÓW  - `ps`

PID - process ID
TTY - z którego terminala pochodzi ten proces
TIME - ile czasu procesora zostało spożytkowane na działanie procesu
CMD - jaka komenda została użyta, aby ten proces wystartował

---

`grep` - wyszukiwanie określonych informacji wewnątrz pliku

$ grep -E few nowy.txt
fewf
`grep` (Global Regular Expression Print) jest to polecenie linuksowe, które pozwala na wyszukiwanie tekstu w plikach lub wyjściu innych komend.

Składnia komendy jest następująca:

`grep [opcje] wzorzec plik(i)`

-   `wzorzec` to ciąg znaków, który chcemy wyszukać
-   `plik(i)` to plik(i), w których chcemy przeszukać, jeśli nie podamy pliku komenda przeszuka wyjście pipe'a
-   `opcje` to opcjonalne argumenty, które pozwalają na kontrolowanie działania komendy.

Przykłady użycia:

-   `grep "example" file.txt` - wyszuka w pliku file.txt wszystkie linie zawierające ciąg znaków "example"
-   `ls -l | grep "root"` - wyszuka w wyjściu polecenia ls -l wszystkie linie zawierające ciąg znaków "root"
-   `grep -r "example" /etc` - rekursywnie przeszuka katalog /etc i jego podkatalogi w poszukiwaniu plików zawierających ciąg znaków "example".

Dzięki różnym opcjom, komenda grep jest bardzo elastyczna i pozwala na różnego rodzaju wyszukiwania.


 ----
 ## Piping `|` tworzenie nowych komend

`cat file | grep -E "r"` wyświetl/pobierz całą zawartość pliky `file` i wybierz z niego tylko te słowa, które zawierają `r` i tak przygotowane dane wyświel w konsoli

```bash
jarek@DESKTOP-2AAK5H9:~$ cat file.txt | grep -E "r"
sdvbdfr
rvfdfv
drsvdsvs
cdsvrew
saaefrsz
sdvbdfr
rvfdfv
drsvdsvs
cdsvrew
saaefrsz
```









  

  

  

  

  

  

  

  

  

  

  

  

  

>




