https://pl.reactjs.org/tutorial/tutorial.html
#react 


# React Docs - Samouczek
**REACT** to:
- biblioteka javascriptowa
	- deklaratywna
	- wydajna
	- elastyczna
- budowanie interfejsów użytkowanika przy użyciu odizolowalny od siebie kawałków kodu, zwanych "komponentami"

>[!important] Komponent
> - Pozwala wytłumaczyć Reactowi, co chemy ujrzeć na ekranie
> - gdy zmieniają się nasze dane, React w sposób efekwtywny aktualizuje i ponownie wyrenderuje komponenty
> - każdy komponent w Reakcie jest enkapsulowany

## Reactowy komponent klasowy
```javascript
class Przestepca extends React.Component {
 render() {
  return (
   <div className="views">
    <h1>{this.props.name} poszukiwany przez</h1>
     <ul>
      <li>ABW</li>
      <li>BBC</li>
      <li>ZSRR</li>
     </ul>
   </div>
    );
  }
}
```

Przykład użycia: `<ShoppingList name="Marek" />`

`<div />`  jest przekształcany w `React.createElement('div')`

Powyższa składnia JSX jest przekształcana na
```jsx
 return ( React.createElement('div', {className: 'views'},
 React.createElement('h1', /* ... h1 children ... */),
 React.createElement('ul', /* ... ul children ... */)
);
```
Na **wejściu** komponent przyjmuje parametry (atrybuty/*props*. *properties*).
Na **wyjściu** przy pomocy metody  [[React render |  `render`]] zwraca strukturę widoków do wyświetlenia.


-----
# TIC TAC TOE

```javascript
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {/* TODO */}
      </button>
    );
  }
}

class Board extends React.Component {
  renderSquare(i) {
    return <Square />;
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}

class Game extends React.Component {
  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}

// ========================================

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<Game />);

```

W powyższym kodzie mamy trzy komponenty:
- Square (pole na planszy)
- Board (plansza)
- Game (gra)
- 