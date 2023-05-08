#nod #restapi  #express 
[[_ 0 Node (Mosh)]]

---








---
http server
```js
const http = require('http') ;

const server = http.createServer( (req, res) => {
	if (req.url === '/') {
	    //...
	}
	
	if (req.url === '/api/courses') {
		//...
	}
});

server.listen(3000);

```


#express
>[!info]  Express
>it is a fast and light weight framework for building web applications
 


----
# RESTful Services
#restapi 

>[!info] Representational State Transfer ReST
> It is a convention for building http services

#crud
> we use simple http protocol principles to provide support to CRUD (Create, Read, Update, Delete)

- *endpoint* it is e.g. `http://vidly.com/api/customers`
	- `http` / `https`
	- `//vidly.com` domain of the application
	- `/api` convention to expose their RESTful services
	- `/customers` it refers to the collection of customers in our application (this is *resource* (in the REST world)) 
		- we can expose resources like: customers, movies, rentals, and various endpoints
		- CRUD  can be done by sending an http request to this endpoint
		- the kind of http requests determin the kind of operations
		- **every** http **request** has *a verb* or *a method* that determines its type or intention
		- HTTP METHOD 
			- `GET` for getting data
				- all custumers:
					- *request*  `GET /api/customers` 
					- *response* `[ {id: 1, name: '  '}, {id:2, name: '  '} ...]` 
				- one customer:
				- *request*  `GET /api/customers/1` 
				- *response* ` {id: 1, name: '  '}` 
			- `POST` for creating data
				- *request* `POST /ap/customers`  and in the **body** of the request add `{name: ' '} `
			- `PUT` for updating data
				- update one customer:
					- *request*  `PUT /api/customers/1` and in the **body** of the request add `{name: ' '} `
					- *response* `{id: 1, name: ' ' }`
			- `DELETE` for deleting data
- client can send a http request to that endpoint to talk to our service

```js
GET /api/customers
GET /api/customers/1
PUT /api/customers/1



```






