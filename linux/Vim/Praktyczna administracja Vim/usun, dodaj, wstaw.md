[[_ Intoduction]]
[[0 _ Vim wprowadzenie]]

**USUWANIE tekstu**  
#vim/delete
```vim
x                  # delete char  == dl 
d                  # Delete  

w                  # Word  
2dw                # Two Word Delete  
d2w                # Delete Two Word  
 

0             # początek  
$             # koniec  
d0            # delete do początku linii  
d$            # delete do końca linii  

shift+d       # delete do końca linii  
dd            # usunięcie linii  
2dd           # usunięcie dwóch linii  

```  

powtarzanie czynności  

      k  

h   d   l  

      j  

  

**KOPIOWANIE tekstu**  
#vim/copy
>
>	cut       -->      **Delete** (czyli usuwanie przez wycinanie go do schowka)  
>	copy    -->      **Yank** (szarpać, wyrwać, czyli jego kopię umieścić w schowku)  
>	paste   -->      **Put**  

**delete**  
#vim/delete
	linia:        dd                  2dd  
	słowo:     dw                 2dw  
	znak:       x                    2xpp  
  

**yank**  
#vim/yank
	linia:         yy           2yyy0y$  
	słowo:      yw          2yw  
	znak:            ----  
  
**put**  
#vim/put 
linia:   |  
słowo:| --> p              wkleja po kursorze albo pod linią
znak:  |  -> shift+p    wkleja przed kursorem albo nad linią

  