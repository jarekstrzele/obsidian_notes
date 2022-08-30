# Section 11 Otwieraj wiele plików przy pomocy BUFORÓW i OKIEN  
#vim/buffers

`:buffers`   `:ls`     listowanie aktualnie otwartych buforów  

**Otworzenie bufora:**  
`vim nazwaPliku  `

**Otworzenie wielu buforów:**  
`vim plik1 plik2 plik3 ...  `  

**Dodanie kolejnego bufora:**  
`:badd [plik]  `  

**Zamknięcie bufora**  
`:bd [numer]  `

**Przechodzenie do buforu**  
`:buffer [numer] `
chyba wystarczy `:b [numer]  `
`:bn`  do następnego bufora        next  
`:bp`  do porzedniego buforu       previous  
`:bf` do pierwszego                     first  
`:bl`  do ostatniego                      last  
`:b#`     przejście do ostatniego edytowanego  


**%a**       active otwarty i wyświetlany aktualnie  
**h**          hidden modyfikowany, nie zapisany nie wyświetlany  
**inactive**  nie modyfikowany, nie wyświetlany  

**:E**                  graficzny explorator plików  
 
---

# OKNA VIMa
#vim/windows

dzielenie na okna  
`:vs [bufor]` podzielenie ekranu w pionie (bufor opcjonalny)  

`:sp [bufor]`  podzielenie ekranu w poziomie  

==poruszanie się po oknach  ==
`ctrl + ww` przejście do następnego okna  
`ctrl + w + h/j/k/l` przejście do okna w konkretnym kierunku  
`ctrl + w + =`  wyrównanie wszystkich okien  

`ctr+ w + +`   powiększanie okna w pionie  
`ctr+ w + -`  pomniejszanie okna w pionie  

`ctr+ w + >` przesunięcie podzielnika okna w prawo  `ctr+ w + <` przesunięcie podzielnika okna w lewo  

`:on` zamknięcie wszystkich okien OPRÓCZ aktywnego  

---  

## WAŻNE  
> otworzenie jednego buforu a potem podzielenie okienka na wiele róznych okienek to wciąż będzie jeden bufor, więc zmiana w jednym buforze zmienia wszystkie okienka  
  
**Aby przyporządkować jeden bufor do jednego okienka!!!:**  
- mam otwarte jedno okienko z jednym plikiem    
- :vs nazwa_nowego pliku    

  