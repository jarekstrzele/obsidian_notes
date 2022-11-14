# Praktyczny kurs

## StackBlitz

[https://stackblitz.com/](https://stackblitz.com/ "https://stackblitz.com/")  

tworzenie projektów online   
Mam projekt na githubie. Kopiuję linkt bez '[https://github.com](https://github.com "https://github.com/")',  
czyli zamiast '[https://github.com/ZacznijProgramowac/todo-list-udemy](https://github.com/ZacznijProgramowac/todo-list-udemy "https://github.com/ZacznijProgramowac/todo-list-udemy")' jedynie  
jedynie  *ZacznijProgramowac/todo-list-udemy*

przechodzę do stackblitza:  
- do strony 'stackblitz.com' dopisuję '/github'  
- doklejam '/ZacznijProgramowac/todo-list-udemy' i naciskam enter --> otworzy projekt github w stackblitz  
https://stackblitz.com/**github/**ZacznijProgramowac/todo-list-udemy**  
branch tak samo doklejamy i możemy je przechowywać w stackblitz  

instalacja  
- nodejs  
- npm install -g @angular/cli            ( -g  globalna instalacja)  
- visual studio code   (or webstorm)  

## LINKI  
Na koniec garść linków, które możesz potrzebować:  

Środowisko programistyczne  
**Node.js**: [https://nodejs.org/](https://nodejs.org/ "https://nodejs.org/")  
**Starsze wydania node.js:** [https://nodejs.org/en/download/releases/](https://nodejs.org/en/download/releases/ "https://nodejs.org/en/download/releases/")  
**NPM:** [https://www.npmjs.com/get-npm](https://www.npmjs.com/get-npm "https://www.npmjs.com/get-npm")  

**Angular CLI:** [https://github.com/angular/angular-cli/blob/master/packages/angular/cli/README.md](https://github.com/angular/angular-cli/blob/master/packages/angular/cli/README.md "https://github.com/angular/angular-cli/blob/master/packages/angular/cli/README.md")  

**Wymagania Angulara**: [https://angular.io/guide/setup-local](https://angular.io/guide/setup-local "https://angular.io/guide/setup-local")  

Edytory kodu:  
**Edytor online Stackblitz:** [https://stackblitz.com/](https://stackblitz.com/ "https://stackblitz.com/")  
**Visual Studio Code:** [https://code.visualstudio.com/](https://code.visualstudio.com/ "https://code.visualstudio.com/")  
**Webstorm:** [https://www.jetbrains.com/webstorm/](https://www.jetbrains.com/webstorm/ "https://www.jetbrains.com/webstorm/")  

---

**angular-cli**  to narzędzie linii komend, 
				  aby łatwo zarządzać rozbudowywać, tworzyć projekty   

  
## GENEROWANIE NOWEGO PROJEKTU  

`ng new progetct_Name`

`ng new first-project`  
 // no routing, yest CSS  

## URUCHAMIANIE PROJEKTU  

`ng serve  `      // w konsoli edytora  

aplikacja jest w trybie developent, czyli coś zmieniam w pliku i od razu widać zmianę  

np. src> app > app.component.html
	usuń zawartość i napisz `
` <h1> heloM </h2> `

angular-cli przebuduje projekt i go odśwież  
  

jeżeli pojawią się problemy w Power Shellu:  

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser  
  

#### Dokumentacja na GitHub  
[https://github.com/angular/angular-cli/wiki](https://github.com/angular/angular-cli/wiki "https://github.com/angular/angular-cli/wiki")  
 
#### Angularowa dokumentacja  
[https://angular.io/cli](https://angular.io/cli "https://angular.io/cli")  

  
Główny projekt aplikacji (tu to jest 'first-project') to workspace, globalne ustawienia   

## KATALOGI  
**e2e**         
	do tworzenia testów end to end  

**node_modules**
	zawiera wszystkie zależności potrzebne do tworzenia aplikacji  
        te zależności dodatkowo można ustawiać w _package.json_  

**src**:  
      tu jest cała nasza aplikacja  

## PLIKI  
*.editorconfig*                 plik uniwersalne konfiguracji dla edytorów  
*angular.json*                  główny plik konfiguracyjny dla projektu 
								   (budowanie, testowanie, ...)  
*browserlist*                    opisuje wspierane przeglądarki dla narzędzi  
*karma.conf.js*                 do pisania testów  
*package.json*                 konfigurujemy zależności, 
									podstawowe komendy do uruchamiania skryptu prze npm, ...  
*package-lock.json*       tworzony automatycznie, 
									gdy wystartujemy npm install w naszym projekcie  
*tsconfig.app.json*         konfiguracja typescripta dla aplikacji  
*tsconfig.json*                 konfiguracja typescripta dla naszego workspacea  
*tsconfig.spec.json*       do konfig testów  
*tslint.json*                      do sprawdzania poprawności naszego kodu  


### PLIK   *A N G U L A R . J S O N*
tu definiujemy konfigurację dla całego workspace'a i swojej aplikacji (bądź szeregu aplikacji)  

"projects"                       konfiguracja wszystkich projektów  
"projectType"                jaki rodzaj projektu tworzymy (application, library)  
"sourceRoot"                 katalog naszej aplikacji  
	"prefix" (!!!)  
	...
	"style" : [ "src/style.css"],   
	"scripts"  : []                  skrypty JS uruchamiane w
									globalnym kontekście aplikacji  

## KATALOG   **S R C**  
*src*                        reprezentuje jedną aplikację  
	app   
       assets              tu umieszczamy statyczne pliki
					        (czcionki, grafiki,  svg...)  
      index.html      angular automatycznie dociąga 
						  do tego pliku wszystkie skrypty JS i pliki CSS  
      main.ts            TO PUNKT STARTOWY DLA ANGULARA  
      style.css           w całej aplikacji   
  

Linki  
#### Konfiguracja TypeScript  
[https://www.typescriptlang.org/docs/handbook/compiler-options.html](https://www.typescriptlang.org/docs/handbook/compiler-options.html "https://www.typescriptlang.org/docs/handbook/compiler-options.html")  

#### Worskpace Angulara w szczegółach  
[https://angular.io/guide/workspace-config](https://angular.io/guide/workspace-config "https://angular.io/guide/workspace-config")  
