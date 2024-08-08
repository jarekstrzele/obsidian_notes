#react 

> Wąski zakres działania Reacta oznacza, że może być on włączony do istniejącej aplikacji, nawet jeśli korzysta ona z innego frameworka. To dlatego, że nie musi on kontrolować całej aplikacji, aby działać; zadowoli się byciem częścią frontendu aplikacji.


>[!important] JSX
> `JSX` to składnia używana w komponencie Reacta do określenia tego, co ma być wyświetlane.
> `JSX` to skrót od JavaScript XML, co daje nam pewne pojęcie, czym to jest.
> nie jest bezpośrednio wykonywany w przeklądarce - napierw musi być przetłumaczony *transpiled* na JavaScript

```javascript
function App() { 

	return (
		<div className="App">
			<Alert type="information" heading="Sukces"> Wszystko jest naprawdę dobrze!
			</Alert> 
		</div>

); }
```


Otwórz przeglądarkę, wejdź na stronę https://babeljs.io/repl i wprowadź
poniższy kod w JSX w lewym oknie strony:
`<span>O nie!</span>` W prawym oknie strony pojawi się kod, na który został przekształcony JSX: `React.createElement("span", null, "O nie!");`

```
const title = "O nie!"; 
<div className="title">
	<span>{title ? title : "Coś ważnego"}</span> 
</div>
```

-------

# Tworzenie komponentu
- NARZĘDZIE ONLINE: https://codesandbox.io 
- wybierz `React` , punktem wejścia będzie  `index.js`

## `index.js`
```javascript
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App";


const rootElement = document.getElementById("root");
const root = createRoot(rootElement);

root.render(
	<StrictMode>
		<App />
	</StrictMode>
);
```
- Pierwsza instrukcja importuje komponent StrictMode z Reacta. Oznacza to, że komponent `StrictMode` z biblioteki react będzie używany później w tym pliku.
- Druga instrukcja importuje funkcję `createRoot` z Reacta.
- Trzecia instrukcja importuje komponent `App` z pliku `App.js` w projekcie.
- Następnie zmienna `rootElement` jest przypisywana do elementu DOM o identyfikatorze root.
- Funkcja `createRoot` w Reaccie przyjmuje element DOM i zwraca zmienną, która może być używana do wyświetlania drzewa komponentów Reacta. Zmienna `rootElement` jest następnie przekazywana do `createRoot`, a wynik jest przypisywany do zmiennej `root`.
- Funkcja `render` jest wywoływana na zmiennej root, przekazując JSX zawierający komponent `StrictMode` z komponentem App umieszczonym w środku. Funkcja `render` wyświetla komponenty Reacta na stronie. Ten proces jest nazywany renderowaniem.

## Drzewo komponentów Reacta
Komponenty w Reaccie mogą być umieszczane w innych komponentach.
aplikacja jest ustrukturyzowana w drzewo zawierające komponenty Reactowe i elementy DOM.

`App.js`
```javascript
<div className="App"> 
	<h1>Hello CodeSandbox</h1>
	<h2>Start editing to see some magic happen!</h2> 
	</div>
```

```
StrictMode
	|--App
		|--div
			|--h1
				|--h2
```

## tworzenie komponentu `alertu`
Nazwa komponentu musi zaczynać się Z DUŻEJ LITERY.

`Alert.js`
```javascript
function Alert() { 
	return (
		<div> 
			<div>
				<span role="img" aria-label="Ostrzeżenie">⚠</span> <span>O nie!</span>
			</div>
		<div>Coś jest nie tak ...</div> </div>
); }
```


## `import`, `export`
Instrukcje `import` i `eksport` pozwalają organizować napisany w JavaScripcie kod w moduły.

- Funkcje i zmienne w module są izolowane, dzięki czemu funkcje o tych samych nazwach nie będą ze sobą kolidowały. 
- Taka organizacja kodu jest szeroko stosowana w aplikacjach Reacta, ponieważ jest znacznie bezpieczniejsza.

## definiowanie modułów
>[!definition] moduł
> - Moduł to plik z co najmniej jednym poleceniem `export`. 
> - Polecenie to wskazuje, które elementy są dostępne dla innych modułów. 
> - Pomyśl o tym jak o publicznych elementach. Element może być 
> 	- funkcją, 
> 	- klasą lub 
> 	- zmienną w pliku. 
> - Jeśli element nie jest zawarty w instrukcji `eksport`, oznacza to, że jest prywatny i nie jest dostępny poza modułem.

### eksport
#### eksport nazwany
```javascript
function myFunc1() { ...

}

function myFunc2() { ...

}

function myFunc3() { ...

}

export { myFunc1, myFunc3 };
```

`myFunc2` - jest prywatna

alternatywnie:
```javascript
export function myFunc1() { ...

}

function myFunc2() { ...

}

export function myFunc3() { ...

}

```


#### eksport domyślny
można użyć do eksportowania pojedynczego, publicznego elementu.
```javascript
export default myFunc1; 
// lub 
export default function myFunc1() { ...

}
```



### import 
Za pomocą instrukcji import można używać publicznych elementów z modułu. 

#### import nazwany
`import { myFunc1, myFunc3 } from './myModule'`

#### import domyślny
==Import domyślny może zostać użyty tylko w odniesieniu do eksportu domyślnego.==

`import myFunc1 from './myModule';`



## dodawanie komponentu
- komponent `Alert` musi być wyeksportowany: `export function Alert()`
- dobra praktyka: **jeden komponent, jeden plik**
- import `import { Alert} from './Alert'`
- użycie `<Alert />`


--------

# Korzystanie z propsów

>[!definition] props
>Słowo props to skrócona forma angielskiego słowa *properties*, które oznacza „właściwości”. 
>W środowisku osób pracujących z Reactem jest ono powszechnie używane, więc również w tej książce będziemy posługiwać się tym terminem.










