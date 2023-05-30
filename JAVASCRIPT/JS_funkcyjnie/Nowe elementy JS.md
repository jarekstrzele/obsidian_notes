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





----
# Destrukturyzacja









