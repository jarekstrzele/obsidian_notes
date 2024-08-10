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

return <button onClick={handleClick}>Przyczyna efektu</button>; }
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















