#rust #server 

-------
[[4.1 Struct]]
[[4.2 Strings]]




-------
# HTTP/1.1
- L7 Protocol
- sent over TCP (servers communicate by exchanging individual messages instead of streaming data)
- message based:
	- messages sent by the client (browser) are called **requests**
		- starts with: method (e.g. `GET`)
		- next path
		- next protocol (e.g. `HTTP`)
		- next a new line
		- and headers (`key:value` format)
		- next two new lines
	- messages sent by the server as an answer are called **responses**
		- starts with the protocol  and status code and reason fraus (`HTTP/1.1 200  OK`)
		- next line: list of headers 
		- next two new lines
		- and body (any format: html, json, js, ...)

REQUEST:
```
GET /search?name=abc HTTP/1.1 
Accept: text/html
```
RESPONSE:
```
HTTP/1.1 200 OK
Content-Type: text/html

<!DOCTYPE html>
<html land="en">
....
</html>
```

![[rust-server.excalidraw | 660]]


-------------


