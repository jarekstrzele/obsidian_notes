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

[[4.1. `useEffect`]]



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








