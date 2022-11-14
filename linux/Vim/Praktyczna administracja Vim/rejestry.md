[[0 _ Vim wprowadzenie]]
#vim/register

# REJESTRY
:reg    # spis rejestrów  
:reg 2  # pokaż zawartość drugiego rejestru  

## Typy

1. **liczbowy**  
-   w rejestrze zerowym      `"0` przechowywane jest ostatnie kopiowanie/yank      
-   w kolejnych rejetrach     `"1-"9` przechowywane 9 ostatnich kasowań/delete  

2. **literowy**
zarządzane przez użytkowanika  

## wstawianie
`"0 y2w yy 2yyy0 y$  `

`"1-"9 d2w dd 2dd d0 d$  `

np. `"a"ay2w "ayy "bdd:reg a:reg b  `

zmiana małej litery na dużą to *append*  
mała litera to *override*  
czylli  
`"ayw` - do rejestru  "a zapisz jedno słowo  
`"Ayw` - do rejestry "a dopisz jedno słowo  

 ## wyjmowanie
`"0 p shift+p ` 
`"1-"9"1p"1+shift+p  `

np. "a"ap"a+shift+p:reg a  
