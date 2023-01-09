[[_ 0 HTTP fundementals]]


---

# HTTP Messages
signal transmitted, message received

>[! HTTP/1 specification]
>it defines the language that everyone on the Web (all clients and all severs can understand each other)

<mark style="background: #FF5582A6;"></mark> 
**There are two types of messages**:
1. client ==HTTP request msg== 
	1. that's what the client sends to the server (this msg has to be correctly formatted)
	2. it's just a command in plain ASCII text and it's formatted to the HTTP specification
	

2. server ==HTTP response== (this msg has to be correctly formatted)

==a single HTTP transaction== = request + response


<mark style="background: #FFB8EBA6;">A MANUAL REQUEST</mark> 
```shell
3. see 'TelNet' -> *a manual request* (`80` is a port)

$ telnet odetocode.com 80
Trying 168.62.48.183...
Connected to odetocode.com.
Escape character is '^]'.
//we are connected
Can I have? // this is not correct HTTP request

// response
HTTP/1.1 400 Bad Request
Content-Length: 0
Connection: close
Date: Tue, 19 Jul 2022 12:11:46 GMT

Connection closed by foreign host.
*************
// a correct manual request 
$ telnet odetocode.com 80
Trying 168.62.48.183...
Connected to odetocode.com.
Escape character is '^]'.
// this is a REQUEST
GET /odetocode.jpg HTTP/1.1
Host: www.odetocode.com
// push 2 x enter

// RESPONSE
HTTP/1.1 301 Moved Permanently
Content-Length: 158
Content-Type: text/html; charset=utf-8
Date: Tue, 19 Jul 2022 12:14:14 GMT
Server: Microsoft-IIS/10.0
Location: https://odetocode.com/odetocode.jpg
X-Powered-By: ASP.NET

```

## HTTP Request Method
Methods tells the server what the request wants to do

Method | Description
----| ----
**GET** | Retrieve a resource
**POST** | Update a resurce
PUT | store a resource
DELETE | Remove a resource
HEAD | Retrieve the headers for a resource

## `GET` and `POST`
**safe** Methods that allows us to read and view resources from a Web server ->  `GET` method (i.e. to get images, ...)

**unsafe** methods let you change resources on a Web server -> `POST` (e.g. to process a credit card transaction, ...) ==in a post operation, the inputs don't go into the URL, they go into the HTTP message

### POST/Redirect/GET - PRG
#prg
It is a programming pattern  to avoid a worring if the user tries to refresh the result of a post operation
in  a html file there is a forme, and a PRG pattern:
```html
 
<body>
<!-- ... -->
@if(IsPost){
  Session["firstName"]=Request.form["firstName"];
  Session["lastName"]=Request.Form["lastName"];
  Response.Redirect("signedup.cshtml")
  }
</body>
</html>
```

in the HTML forms you can use `GET` or `POST` method


## Request Messages
are ASCII text with three parts:
[method]  [URL]  [version]
[headers]
[body]

body may be from form key:value pairs

## Response Message
[ version ]    [ status ]   [ reason ]
[ headers ]
[ body ]

body - might be HTML, image content, ...

## Status Codes
range     | category        | examples
--------- | --------------- | ------
   100-199   |   informational | x
200-299   |   successful    | 200 OK
300-399   |   redirection   | 301 resource moved permanently
400-499   |   client error  | 400 Bad Request, 403 Forbbiden, 404 NotFound
500-599   |   server error  | 500 Internal Server Error, 503 Service Unavailable


## HTTP Fiddler
a free tool (Windows) , intercepts all the HTTP traffic betweem your machine and some [distant] server





