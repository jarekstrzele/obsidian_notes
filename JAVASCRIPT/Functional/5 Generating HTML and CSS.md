[[0- Intro functional programming (beginner udemy)]]

[[5 - HTML and CSS]]
[[5 Transforming Data to HTML]]



---
# Generating HTML and CSS

## tachyons
`mw5` -max width 5 (table)
`center w-100` center 100% width
`stripe-dark` alternate the background color for each row between white and gray
`tr` text right in column
`tl` text left class in column


## transformation
to transform data into other data use function 

---
`<script src="https://cdn.rawgit.com/knowthen/d90da7fbbcc3222252d2845eef2adc38/raw/6099003c3102daf281681cd92b7158477a1bc5f4/hyperscript-browser.js"></script>`
### Hyperscript
### Hyperscript helpers
-  provides functions for every type of HTML tag
-   `div('hi') // <div> hi </div>`
-   `p('hola)' // <p> hola </p>`
-  `h1('guttentag') // <h1> guttentag </h2>`

```javascript
const myHeading = tags.h1("Hey");
console.log(myHEading.outerHTML); //->"<h1> Hey </h1>"

// destructuring
// const { h1 } = tags;
// you can simply add: const {h1, p, ...}
// const myHeading = h1("Hey");


const node = document.getElementById("app");
node.appendChild(myHeading);
```


```javascript
// 1. using destructuring, create a constant named
// p, which is a function that will create paragraph tags
// Remember, you'll need to use the "tags" namespace
// to destructure from
const { p } = tags;

// 2. create a constant named myParagraph by using the
// p function you coded in step 1.  The paragraph should
// contain a sentence of your choosing.

const myParagraph = p('Lorem ipsum dolor sit amet.');

// 3. create a constant named node, that references 
// the dom node where the id is 'app'.

const node = document.getElementById('app');

// 4. add your 'myParagraph' to the dom node you 
// coded in step 3

node.appendChild(myParagraph);
```

----




















