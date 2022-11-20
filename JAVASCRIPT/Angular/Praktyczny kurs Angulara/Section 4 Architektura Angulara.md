[[JAVASCRIPT/Angular/Praktyczny kurs Angulara/0 Podstawy Angular]]


---

# SECTION 4 ARCHITEKTURA ANGULARA
**Angular**  
- został napisany w Typescripcie jako kompleksowym framework  
- bardzo często stosowany do budowy aplikacji enterprise (bankowe, ...)      
-   typowy podział :  
	- moduł:  
	    - serwis  
	    - komponent  
		    - dyrektywa  
		    - pipe  
    
- w app angulara są moduły, a zawsze jest moduł główny  
- moduł może również zawierać inne moduły  
 ---
 
## CO TO SĄ MODUŁY?  
#angular/moduł
- każda aplikacja napisana w angularze ma przynajmniej jeden moduł,      
- src.app.app.module.ts -> główny moduł nazywa się AppModule; ma on wiedzę o :
	- komponentach  
	- serwisach   
	- innych modułach  

- główny moduł jest punktem startowym całej aplikacji  
- główny moduł może posiadać settings  
- wszystko w głównym module jest przygotowane do kompilacji i z tego powstaje nasza aplikacja  
    
- `AppModul` to zwykła klasa, ale ma specjalny dekorator `@NgModule`  
- `@NgModule`:
	-  declaration: [   ]  
		- miejsce deklarowania komponentów a także dyrektyw i pipe  
		- jeżeli stworzymy nowy komponent i chcemy go użyć, to tutaj musimy go zadeklarować  
	- imports: [  ]  
		- tu importujemy moduły własne lub już gotowe (zrobione przez kogoś innego wbudowane w angulara  
	- providers: [  ] to miejsce, w którym informujemy app o serwisach  
	- bootstrap: [  Appstartowa ]   
    
---

## CO TO SĄ KOMPONENTY?  
#angular/component
- komponent to klasa posiadająca `@Component` 
- `@Component` zajmuje się wyświetlaniem widoków html i obsługą zdarzeń, jakie może wywołać użytkownik  
- komponent, który ma inny komonent jest RODZICEM (**PARENT**), a ten, który jest zawarty to **CHILD**
- drzewo komponentów (aplikację dzielimy na wiele komponentów)  
- każdy komponent musi być zadeklarowany w module, bo inaczej aplikacja nic nie będzie wiedziała o tym komponencie     
- komponent służy do wyświetlania danych i komunikacji z użytkownikiem  

---


## CO TO JEST SERWIS?  
#angular/service
- serwis to taki backend aplikacji     
- serwis to klasa z dekoratorem `@Injectable`   
- głównym celem serwisu jest wykonywanie zadań dla komponentu      
- komponent zajmuje się wyświetlaniem danych, serwis te dane dostarcza, te dane analizuje i przetwarza  
- komponenty najlepiej skomunikować ze sobą za pomocą serwisu  
- serwisy powinny być odpowidzialne za protokoły HTTP, logowanie błędów, dzielenie danych pomiędzy komponentami  
- aby serwis działał powinien być umieszczony  
	- w tablicy _providers_ w module (jego widoczność w całej applikacji jako singleton)  
	- w tablicy _providers_ w dekoratorze komponentu (widoczność tylko w tym komponencie)  
-   w tablicy _providers_ w module  
    

**POSUMOWANIE**
> **moduł** splata elementy Angulara w jedną całość  

  
>  **komponent**   część aplikacji, która komunikuje się z użytkownikiem, w tym miejscu powstaje to co widać na ekranie  


> **serwis**  to zaplecze naszej aplikacji. Dostarcza dane, zajmuje się ich przekształcanie, wykonuje zapytania HTTP, sprawdzania uprawnienia, obsługuje komunikację między komponentami  




