
# _ React Bob Ziroll
#react    #bob_ziroll  #youtube  

https://scrimba.com/learn/learnreact/welcome-to-an-introduction-to-react-coaaf455789c2a9addc20dd24

https://www.youtube.com/watch?v=bMknfKXIFA8

---
Pojawiają się błędy. Aby je rozwiązać:
- install chrome extension React
- run `index.html` not directly by by the server( _VS CODE_ live server)

---

To start React just past into `index.html` in the header two libraries:
```html
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
```
so now we have an access to a global variable `ReactDOM`

and Bable:
`<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

`
and in `index.js`:
```js
ReactDOM.render(<h1> Hello, every one </h1>, document.getElementById("root"))
```




