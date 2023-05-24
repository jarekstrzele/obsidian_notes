
#udemy #web_app  #fullstack #stashchuk_bogdan 

- VS Code 
	- Bracker Air Colorizer
	- Prettier - Code formatter
	- Cobalt2 Them Official
	- Material Icon Theme

-----------
[[1 React]]





----

# Frontend vs Backend

## frontend
- client side
- everything user sees ot directly interacts with (e.g. buttons, menu, ...)
- mutliple frontend apps can interact with the same backend
- frontend building **blocks**:
	- HTML
	- CSS
	- JavaScript
- **anatomy** of the frontend app
	- clients (screen desktop, mobile, table...)
	- server (to host files like HTML, CSS, JS)
	- communication between clients and server
- **communication** between clients and servers
	- they communicate in the form of  requests-and-responses
	- e.g.
		1. user opens a web app -- init --> request to the server
		2. the server immediatly response (sends css files) or requests other server for data (login) and the responses 
	- ==for the server it matters only a structure of the request that is received from the client==
	- most popular protocol HTTPS
	- REST API is an application programming interface that conforms to the requirements of the rest architectural style  and allows for interaction with restful web services 
		- API server exposes mutiple endpoints with different methods enabled for them (GET, POST, DELETE)
	- other popular language is GraphQL
		- there is just single endpoint on the server side
		- and clients make consolidated requests for data using such a single endpoint
	- REST API and GraphQL work over HTTPS

- **responsive layout**
	- layout of the frontend app that smoothly adjusts itself depending on the screen size and other device parameters
	- layout should be also adjusted depending on the device orientation
	- how to make it:
		- mobile first design
		- CSS Media Queries
		- Elements sizing in relative units (REM Sizing of the elements relative to the root element)
		- CSS FlexBox (position)
		- Separate CSS files for mobile and desktop
		- subdomain for mobile application



## backend
- server side
- hidden from the user
- contains data and application logic
- **technologies**:
	- **building APIs and backend logic**
		- NodeJs
		- Java
		- Python
		- C#
		- PHP
	- **Infrastructure services**
		- AWS
		- Docker
		- ELK
		- Apach kafka
	- **databases**
		- MongoDB
		- Redis
		- MySQL

## FULLSTACK = FRONTEND + BACKEND




