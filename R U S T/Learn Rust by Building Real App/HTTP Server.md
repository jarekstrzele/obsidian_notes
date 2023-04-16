#rust #server 

# HTTP/1.1
- L7 Protocol
- sent over TCP (servers communicate by exchanging individual messages instead of streaming data)
- message based:
	- messages sent by the client (browser) are called **requests**
	- messages sent by the server as an answer are called **responses**

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
<html land="en"
```






