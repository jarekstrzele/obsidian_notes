[[0 _ Vim wprowadzenie]]

# Section 7. Wyszukuj i podmieniaj ciągi znakowe  

**WYSZUKIWANIE**  
#vim/search
`f{znak}`      # wyszukiwanie po znakunp.fs  
`F{znak}`      # wyszukiwanie po znaku wstecz  

t{znak}      # wyszukiwanie po znaku - kursor przed  

T{znak}      # wyszukiwanie po znaku wstecz - kursor wstecz  

;            # do kolejnego wyniku wyszukiwania  

,            # do poprzedniego wyniku wyszukiwania  

  

**/{tekst} **    # wyszukiwanie tekstu np./Port  

**?{tekst}** # szukiwanie tekstu w stecz  

  

**n** # do kolejnego wyniku wyszukiwania  

**N** # fo poprzedniego wyniku wyszukiwania  

  

***** # wyszukiwanie słowa na którym aktualnie jest kursor  

**#**             # wyszukiwanie wstecz słowa na którym aktualnie jest kursor  

  

**PODMIENIANIE**  
#vim/replace 
  

:[zakres]/{aktualny tekst}/{nowy tekst}/[flaga]  

:%s/disabled/enabled/gg - wszystkie wystąpienia tekstu w linii (global))  

%s -we wszystkich liniach pliku  

:5s/disabled/enabled/g5s - w piątej linii  

:5,10s/disabled/enabled/g5,10s- od 5 do 10 linii  

**u**                  # wycofanie zmiany (undo)!!!!!!!!!!!!!  

**ctr + r**        # powrót do zmian(redo)!!!!!!!!!!!!!  

