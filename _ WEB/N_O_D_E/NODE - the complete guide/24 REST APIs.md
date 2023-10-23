# What & Why?
- not every Frontend (UI) requires HTML Pages (mobile Apps)
- Single Page App
- service APIs (e.g. Google Maps API)

Frontend (UI) is decoupled from the backend (server)

>[!definition] REST
>- Representational State Transfer
>- Transfer Data instead of User Interfaces
>	- data format:
>		- HTML (Contains User Interface, but you need only data)
>		- Plain Text (No UI Assumptions, but it is difficult to parse)
>		- XML (No UI Assumptions, Machine-readable, XML-parser needed)
>		- ==JSON (No Ui Assumptions, Machine-readable, Can easilu be converted to JavaScript)==


>[!important]
>Only the response (and the request data) changes, NOT the general server-side logic!

# ROUTING
Requests would be sent from the client through, when working in the browser through asynchronous JavaScript (fetch API/ Ajax)

>[!definition] API endpoint
> the combination of :
> 	- a http method (like Post, Get) a
> 	- respective path

>[!info] Http method
>- GET
>	- get a Resource from the Server
>- POST
>	- Post a Resource to the Server:
>		- create Resource or
>		- append Resource
>- PUT
>	- Put a Resource onto the Server
>		- create a Resource
>		- overwrite a Resource
>- PATCH
>	- Update parts of an existing Resource on the Server
>- DELETE
>	- Delete a Resource on the Server
>- OPTIONS
>	- determine whether follow-up Request is allowed 


# REST Principle
1. Uniform Interface:
	1. clearly defined API endpoints with
		1. clearly defined 
			1. request + 
			2. response data structure
2. Stateless Interactions
	1. server and client don't store any connection history, every reques

















