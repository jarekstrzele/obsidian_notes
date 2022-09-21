[[_ 0 w3school React]]

---
# JSX
#jsx 

JSX stands for JavaScript XML.
JSX allows us to write HTML in React.
JSX makes it easier to write and add HTML in React.

JSX converts HTML tags into react elements

JSX | React
---- | ----
`const myEle = <h1> I'am </h1>;` | `const myEle = React.createElement('h1', {}, 'I am');`


##  Expressions in JSX
With JSX you can write expressions inside curly braces `{ }`
```JSX
const myElem = <h1> React is {5+5} times better with JSX </h1>;
```

## Inserting a Large Block of HTML
To write HTML on multiple lines, put the HTML inside parentheses:
```jsx
const myElement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);
```

## One Top Level Element
The HTM code must be wrapped in ONE top level element
```jsx
const myElement = (
  <div>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </div>
);
```

Instead of `<div> </div>` you can use `<> </>`


## Element must be Closed
`const myEle = <input type="text" />`


## Attribute class = `className`
```jsx
const myElement = <h1 className="myclass">Hello World</h1>;
```


## Conditions
### `If`
```jsx
const x = 5;
let text = "Goodbye";
if (x < 10) {
  text = "Hello";
}

const myElement = <h1>{text}</h1>;
```

### ternary expression `? : `
```jsx
const x = 5;
const myElement = <h1>{(x) < 10 ? "Hello" : "Goodbye"}</h1>;
```





























