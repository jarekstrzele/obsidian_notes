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


>[!info]  Express
>it is a fast and light weight framework for building web applications
 














