[[_ JavaScript funkcyjnie]]

---
[[#Lambda]]
[[#Spread/rest]]
[[#Destrukturyzacja]]


---

# Lambda
#javascript/lambda

```js
const product = {
	id: 1,
	name: "Product #1",
	price: 100,
	category: "Category #1"
}

const getName = product => product.name ;
const productName = getName(product)
console.log(productName) ;

const getliteralObiektu = (prod) => ({id: prod.id, name: prod.name})
console.log(getliteralObiektu(product)) ;
```

----
# Spread/rest
## rest
```js
const product = {

id: 1,

name: "Product #1",

price: 100,

category: "Category #1"

}

  
  

const {name, price, category} = product ;

console.log(name, price, category) ;

  

const getName = ({id, name, ...rest }) => ({ id, name, rest })

console.log(getName(product)) ;
```

```bash
Product #1 100 Category #1
{
  id: 1,
  name: 'Product #1',
  rest: { price: 100, category: 'Category #1' }
}
```


częściowe wykonanie funkcji
```js
const addition = (a,b) => a + b ;

const operation = fn => (x, y) => fn(x,y) ;

// częściowe wywołanie funkcji
const add = operation(addition) ;
const result = add(5,0) ;

console.log(result) ; // 0
```

częściowe wykonanie funkcji
```js
const addition = (a,b) => a + b ;

const operation = fn => x => y => fn(x,y) ;

// częściowe wywołanie funkcji
const add = operation(addition) ;
const result = add(5)(10) ;

console.log(result) ; // 15
```






