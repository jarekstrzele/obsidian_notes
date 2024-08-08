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









