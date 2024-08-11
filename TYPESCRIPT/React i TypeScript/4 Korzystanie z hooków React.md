[[_ 0 React i TypeScript reaktywne tworzenie stron internetowych dla początkujących]]

# Zasady stosowania hooków

- `Hooki` można wywoływać jedynie na najwyższym poziomie funkcji komponentu, co oznacza, że nie można ich używać w pętlach czy zagnieżdżonych funkcjach, takich jak funkcje obsługujące zdarzenia.
- Nie można ich wywoływać warunkowo.
- Można je stosować tylko w komponentach funkcyjnych, czyli z wyłączeniem klas.

## błędne użycia
### hook w obsłudze zdarzenia
```javascript
export function AnotherComponent() { 

	function handleClick() {
		useEffect(() => { console.log("Jakiś efekt");
	}); }

	return <button onClick={handleClick}>Przyczyna efektu</button>; 
	
}
```

WERSJA POPRAWNA
```javascript
export function AnotherComponent() {
	const [clicked, setClicked] = useState(false); 
	useEffect(() => {
		if (clicked) { console.log("Jakiś efekt");
		} },
		[clicked]);

function handleClick() { setClicked(true);

}

	return <button onClick={handleClick}>Przyczyna efektu</button>; 

}
```

### hook błędnie użyty warunkowo
```javascript
function YetAnotherComponent({ someProp }) { 

	if (!someProp) { return null; }

	useEffect(() => { console.log("Jakiś efekt");

	}); 
	
	return ...
}
```

WERSJA POPRAWIONA
```javascript
function YetAnotherComponent({someProp}) { 

	useEffect(() => {
		if (someProp) { console.log("Jakiś efekt");
	} });

	if (!someProp) { return null }

	return ... }
```



# Hook efektów `useEffect`

## definicja
> ==Hook efektów== jest narzędziem do zarządzania skutkami ubocznymi komponentu. 
> ==Skutkiem ubocznym== komponentu może być na przykład żądanie wysłane do serwisu internetowego. 
> 
> Definiujemy go za pomocą funkcji `useEffect`, dostarczanej przez Reacta. 
> 
> W funkcji tej wyróżniamy dwa parametry:
> >  funkcję, która uruchamia dany efekt, wywoływaną przynajmniej każdorazowo podczas renderowania komponentu;
> >  opcjonalną listę zależności, które jeśli ulegną zmianie, powodują ponowne wywołanie funkcji.


## przykłady
```javascript
function SomeComponent() {

	function someEffect() { 
		console.log("Jakiś efekt");
	} 
	useEffect(someEffect); // wywołaj funkcję someEffect po każdym renderowaniu komponentu

	return ... 
}
```

```javascript
function SomeComponent() {

	useEffect(() => { 
		console.log("Jakiś efekt");
	}
	); 
	
	return ...
}
```

```javascript
function SomeOtherComponent({ search }) {

	useEffect(() => { 
		console.log("Efekt zależny od propsa search ", search); 
		}
		, [search]
	); // efekt zależy od propsa search, funkcja efektu będzie uruchamiana za każdym razem, gdy zmieni się wartość search

	return ...; 
}
```


## Czyszczenie po `useEffect`
- ten hook może zwracać funkcję, która będzie czyścić, gdy komponent będzie odmontowywany (nie będzie wycieku pamięci)
- 

```javascript
function ExampleComponent({ onClickAnywhere }) { 
	useEffect(() => {
		function handleClick() { onClickAnywhere(); }
		document.addEventListener("click", handleClick);
		
		return () => { 
			document.removeEventListener("click", handleClick);
		};

	});

	return ...; 
}
```

Jeżeli nie zwrócimy funkcji, to przy każdym uruchomieniu będzie dodawana kolejna funkcja do obsługi zdarzenia.


----------
# Nowy projekt React + TypeScript

`npm create vite <nazwaprojektu>` -> `React` -> `TypeScript` 

`SWC Speedy Web Compiler`

Zamień `App.jsx`
```typescript
function App() {

  return (
    <>
     <div className="App"></div>
    </>
  )
}
```

## pobieranie danych - `useEffect` - to jedno z głównych zastosowań tego hooka

### plik symulujący żądanie `getPerson.tsx`
```typescript

type Person = {
    name: string
}
 

export function getPerson(): Promise<Person>{

    return new Promise((resolve)=>
        setTimeout( () => resolve({name: "Bob"}), 1000)
    )
}
```


#promise 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
> Zwróć uwagę na adnotację dotyczącą zwracanego typu, czyli `Promise<Person>`.
> Typ `Promise` to reprezentacja `Promise` w `JavaScripcie`, czyli ==coś, co musi zostać spełnione w pewnym momencie==.


## komponent `PersonScore.tsx`

```typescript
import { useEffect } from 'react';
import { getPerson } from './getPerson';
  

export function PersonScore() {

    // useEffect( ()=> {
    //    getPerson().then(person => console.log(person))
    // }, [])
    useEffect(async ()=> {
	    const person = await  getPerson()
	    console.log(person)
    })

    return null;
}
```

> Efekt wzywa funkcję `getPerson` i wypisuje osoby zwrócone z tej funkcji w konsoli. 
> Efekt jest uruchamiany jedynie po pierwszym wyrenderowaniu komponentu, dlatego że **pusta tablica** została zdefiniowana jako zależności efektu, w drugim elemencie funkcji.

użyj komponentu `PersonScore` w `App.jsx`











