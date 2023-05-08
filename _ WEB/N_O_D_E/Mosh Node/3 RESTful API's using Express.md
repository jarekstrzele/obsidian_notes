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
		- CRUD  can be made by sending http re
- client can send a http request to that endpoint to talk to our service
	- 






