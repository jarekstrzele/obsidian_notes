

 **SECTION 14 Widoczność zmiennych**   
 #python/widocznosc_zmiennych
-   publiczne                  var  
-   chronione                 _var  
-   prywatne                 _ _var  

```py
class Phone:  

      var1 = 'xxx'
      _var2 = 'varrr'
      __var3 = '123'

Phone.var1 -> 'xxx'  

Phone._var2 -> 'varrr'
Phone._Phone__var3 -> '123'
Phone.__var2 -> Attribute Error  
```

> Do prywatnych atrybutów klasy (własności lub metod)   
> 
> - z zewnątrz klasy:  NazwaKlasy._NazwaKlasy__atrybut
> - z wnętrza klasy: NazwaKlasy.__atrybut   

> Tak samo jest z prywatnymi atrybutami (własnościami i metodami) instancji  
> 
> - z zewnątrz:   nazwa_obiektu._NazwaKlast__atrybut  
> 
> - z wnętrza:  nazwa_obiektu.__atrybut  

---

  
