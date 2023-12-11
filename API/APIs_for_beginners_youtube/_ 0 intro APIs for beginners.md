#youtube #api #beginner #freecodecamp 
#dennis_craig

https://www.youtube.com/watch?v=GZvSYJDk-us


----------
# Intro APIS for beginners

## Interface
- radio -> its interface allows us to change the volume, station, .... ; the magic that is happening is completely abstracted away from me and I'm still on control
- Graphical User Interface
- `button` is an  interface, it provides the developer the means of controlling its interactions while abstracting away how that actually works, implementation-wise

>[!interfaces]
>- they all define ways for us to interact or communicate with an object whether that object be physical or software
>- and as a user of the interface you don't need to understand the implementation (we don't need to understand how it works)
>- we only must know what we've been allowed to change or see
INTERFACES ABSTRACT AWAY THE IMPLEMENTATION!!!

==UI== User Interface is made for the user of the application
==API== is made for the application programmer to use and extend in their applications

## API
>[!API]
>it is a contract of sorts:
>  - it defines how it's expected to be used
>  - it defines what you can expect to receive by using it
>  - it is a set of tools

built-in functions are examples of API

Frameworks provide an API that allow you to extend what has been provided to make it your own

### remote API
- phones have not enough memory to all data, so thanks to remote API they can use remote data and algorithms (recognise a song, translating text that was taken a photo)
- REST Representational State Transfer was accepted by almost everybody -> it completely overtook the term API

----------------
# How the web works?
#http
a browser is a web client, it allows us to connect to a sever by putting a location in the address bar ([[URL]], [[URI]], [[_ 0 HTTP fundementals]])


- a client  --- sends HTTP request --->  a server
this request: URI, GET(this request will only receive data)
- The server receives the request, procees it and generate the resutling webpage
- the server --- sends HTTP response ---> the client:
	1. the most important part of that response is the body (for a webpage that contains the HTML) 
	2. the browser renders the page (thanks to this response)
HTTP was designed as a stateless protocol!!!
**If you want to keep some sort of state, your client will have to manage that itself!!!**

Responses and Request have HEADERS
#http/headers
IF you want to maintain state like your login details, you must send it with each, and ever request, and you'll do this using headers
<iframe src="https://en.wikipedia.org/wiki/List_of_HTTP_header_fields" height=600 width=700></iframe>

----
# REST
Representational State Transfer

rest constrains:
- Client-server Architecture
- Statelessness
- Layered System
- Cacheability
- Uniform Design
- Code on Demand

==resource== - abstract, it is an object, it can be anythink we build; you can CRUD on it























