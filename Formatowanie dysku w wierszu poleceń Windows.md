
# Jak sformatować dysk USB za pomocą wiersza polecenia w systemie Windows

https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html

- 80
- [1](https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html# "Bezużyteczny")
- [2](https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html# "Ubogi")
- [3](https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html# "Targi")
- [4](https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html# "Dobry")
- [5](https://soundartifacts.com/pl/how-to/134-how-to-format-usb-drive-using-command-prompt-in-windows.html# "Doskonały")

Aby sformatować dowolny dysk pamięci w systemie Windows, wystarczykliknij prawym przyciskiem myszy dysk i wybierz opcję Format. To prosta sprawa. Bez głębokich menu, bez niczego. Ale będą chwile, gdy proces ten nie sformatuje dysku USB i wygeneruje dziwne błędy, takie jak niemożność sformatowania, niemożność przypisania litery dysku itp.

W takich sytuacjach możesz spróbować sformatować dysk USB z wiersza polecenia. Poniżej znajdują się **kroki potrzebne do sformatowania dysku USB z wiersza polecenia**. Podążaj za nimi jeden po drugim, a za kilka sekund sformatowany dysk.

**Ostrzeżenie:** przed sformatowaniem napędu USB wykonaj kopię zapasową dowolnej daty. Formatowanie dysku powoduje nieodwracalne usunięcie z niego wszystkich danych.

Poniższa metoda działa w systemach Windows XP, Vista, 7 i 8.

## Sformatuj USB za pomocą CMD

Formatowanie dysku USB za pomocą wiersza polecenia jest znacznie łatwiejsze niż myślisz. Wszystko, co musisz zrobić, to wybrać dysk i wykonać określone polecenie formatu.

1. Po pierwsze **podłącz napęd USB**.

2. Wyszukaj **cmd** w menu Start kliknij prawym przyciskiem myszy Wiersz polecenia i wybierz „**Uruchom jako administrator**. ”

3. Aby sformatować dysk USB, musimy skorzystać z narzędzia Diskpart. Więc wykonaj `diskpart` dowództwo.

4. Będziesz teraz w narzędziu Diskpart. Wykonać `list disk` polecenie, aby wyświetlić listę wszystkich dysków w systemie.

![Sformatuj dysk listy cmd napędu USB](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows.jpg "Sformatuj dysk listy cmd napędu USB")

5. Z powyższej listy zidentyfikuj dysk USB. Ogólnie dysk USB można zidentyfikować na podstawie jego rozmiaru. Na przykład podłączyłem pendrive 4 GB. Mój dysk USB jest reprezentowany jako „Dysk 2” o pojemności 3818 MB.

6. Po zidentyfikowaniu dysku USB na liście dysków wpisz poniższe polecenie i naciśnij klawisz Enter, aby wykonać polecenie. **Zamień <numer dysku> na rzeczywisty numer dysku**.

select disk <diskNumber>

Po zastąpieniu powyższego polecenia faktycznym numerem dysku, polecenie będzie wyglądać mniej więcej tak.

select disk 2

![Sformatuj dysk USB cmd wybierz dysk USB](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows_2.jpg "Sformatuj dysk USB cmd wybierz dysk USB")

7. Po wybraniu dysku musisz go wyczyścić. Wykonaj poniższe polecenie, aby wyczyścić dysk USB.

clean

8. Po wyczyszczeniu dysku czas utworzyć partycję podstawową. W tym celu wykonaj poniższe polecenie

create partition primary

9. Teraz możemy sformatować dysk. Wykonaj poniższe polecenie, aby sformatować dysk USB w systemie plików NTFS. Ogólnie dyski Windows są sformatowane jako NTFS. **Jeśli chcesz system plików FAT32** następnie wymień `ntfs` z `fat32` w poniższym poleceniu. „Szybka” część polecenia sygnalizuje systemowi wykonanie szybkiego formatowania. Zobaczysz to jako pole wyboru podczas próby sformatowania dysków z Eksploratora plików.

format fs=ntfs quick

![Sformatuj polecenie cmd format napędu USB](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows_3.jpg "Sformatuj polecenie cmd format napędu USB")

10 Nawet po sformatowaniu dysk USB nie będzie widoczny w Eksploratorze plików. Wynika to z faktu, że system Windows nie przypisał żadnej litery dysku do nowo sformatowanego dysku. Musisz wyraźnie powiedzieć systemowi Windows, aby przypisał literę dysku. Wykonaj poniższe polecenie, aby przypisać literę dysku do napędu USB.

assign

![Sformatuj dysk USB cmd przypisz literę dysku](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows_4.jpg "Sformatuj dysk USB cmd przypisz literę dysku")

11. To jest koniec formatowania dysku USB z wiersza polecenia. Pamiętaj, że jesteśmy w narzędziu Diskpart. Aby się z tego wydostać, wykonaj `exit` dowództwo.

![Sformatuj dysk USB cmd exit diskpart](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows_5.jpg "Sformatuj dysk USB cmd exit diskpart")

12. Następnie możesz zamknąć wiersz polecenia systemu Windows, klikając przycisk „X” na pasku tytułu lub wpisując `exit` jeszcze raz.

13. Po otwarciu Eksploratora plików możesz zobaczyć, że dysk jest sformatowany i uporządkowany.

![Sformatuj dysk USB cmd sformatowany](https://soundartifacts.com/images/how-to/how-to-format-usb-drive-using-command-prompt-in-windows_6.jpg "Sformatuj dysk USB cmd sformatowany")

Widzisz, formatowanie dysku USB z wiersza polecenia nie jest trudne. Skomentuj poniżej, dzieląc się swoimi doświadczeniami lub problemami, które napotkasz podczas formatowania dysku USB z wiersza polecenia.

Jeśli chcesz, możesz także podzielić dysk USB na partycje, aby lepiej zarządzać przechowywanymi danymi.

Jeśli podoba Ci się ten artykuł, sprawdź, jak powiększać i pomniejszać w wierszu polecenia i programie PowerShell, a także jak w wierszu polecenia lub w rozmiarze, kolorze i kształcie kursora PowerShell.
