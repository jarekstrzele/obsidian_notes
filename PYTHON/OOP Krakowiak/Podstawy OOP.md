### 4 filary OOP  
[[0-OOP wprowadzenie OOP Krawkowiak]]
  
**ABSTRAKCJA**        
-   ograniczenie cech obiektu ze świata rzeczywistego do cech istotnych z punktu wiedzenie programisty    
-   cel: uproszczenie rozwiązania i zwiększenie ogólności  
    

**HERMETYZACJA**  
-   ukrywanie implementacji przed użytkownikiem      
-   obiekt nie może zmieniać stanu wewnętrznego innych obiektów w nieoczekiwany sposób  
  

**DZIEDZICZENIE**  
#python/inheritance    

**POLIMORFIZM**
jedna nazwa metody wiele różnych zachowań  

**etapy**  
OOA      Object Oriented Analysis  
OOD      Object Oriented Design  
OOP      Object Oriented Programming  


> Klasa jest obiektem typu _type  
> więc ma
> 
>       - atrybuty    (__name__)   
>       - zachowania (modyfikują stan klasy)  
	> - jest wywoływalna (callable) -> jej wywołanie zwraca obiekt należący di tej klasy  
	> - są dynamiczne  
	> 
	
  

PascalCase   aby nazywać klasy.  
Klasy wbudowane nazwane są z małej litery: int, str, float, ...  

```py
class Phone:  

 pass

Phone.__name__ -> 'Phone'
Phone.__module__ -> '__main__'
Phone() -> object Phone  

phone = Phone()
type(phone)              ->      __main__.Phone
phone.__class__          ->      __main__.Phone
phone.__class__.__name__ ->      Phone
type(phone).__name__     ->      Phone  

id(object_name) -> the identity od an object  

id(phone) -> 2611052029504  

phone1 is phpn2
False  

phone = Phone() -> dwie metody wykonywane: __new__ oraz __init__
```

**ręcznie**
#python/__new__  #python/__init__ 
p2 = Phone.__new__(Phone) -> tworzy obiekt typu Phone (to samPython robi)
p2.__init__(args)                     -> inicjalizacja obiektu  



  