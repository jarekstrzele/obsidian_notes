[[_ 0 HTTP fundementals]]


---

# HTTP Resources
**resources** are things I want to interact with on the web (images, pages, files, videos, ... ); each resource will have a URL I can use to find it

My browser understands sytnax `http://www.food.com/` (this is [[URL]])
When it see a such address, it knows that it needs to make an HTTP request to a server named food.

## three parts of HTTP
`http://food.com/recipe/grilled-cauliflower`

1. `http:` this is  a ==URL Scheme== (it describe how to access a particular resource and in this case it tells the browser to use the Hypertext Transfer Protocol ); -> other:
	1. `ftp:`
	2. `mailto`
	3. 
2. `food.com` this is ==the host==: 
	1. this part tells my browser  which computer on  the Internet is hosting the resource
	2. my computer will use the domain name system to look up an address for food
		1. where is food.com?
		2. it's at IP address 204.78.50.82
3. `/recipe/grilled-cauliflower` this is a ==URL Path==
	1. sometime it can be the same path as on the hard drive
	2. sometime this URL Path is generated dynamically <- this is preferable way !!!


## Internet Information Services - IIS
windows


## Ports, Queries and Fragments

### Ports
`http://food.com:80/recipes/squash`

`80` this is the port that the host is going to use to listen for HTTP requests

> the default port number for HTTP is port `80`

### Query
#query_string

`http://bing.com/search?q=jaboticaba`

?`q=jaboticaba` everything after the question mark ist the QUERY or QUERY STIRNG 
#query_string 

It is usually key:value pairs

?`firstName=Scorr&lastName=Allen` this query string has two parameters:
	- the first one has the `firstName` with value `Scott`
	- the second one `lastName` with value `Allen` 
	- `&` is used to delimit parameters


### Fragment
`http://wikipedia.org/wiki/Jabutica#Description`

`#Description` this is a fragment; it is not process by the server; the fragment is only used on the client and it identifies a particular section of a resource that the client should navigate to or focus on

---
## URL Encoding
Safe character:
- `a-z` 
- `0-9`
- `A-Z`
- `$-_.+*'(),`

You can transmit unsafe character in a URL but they need to be:
- percent encoded or 
	- ASCII Character *space* -> *%20* URL-encoding (`http://ps.com/scott%20allen`)
	- *!* -> *%21* ....
- URL encoded.

---
## Content Type
What does it really mean when we enter a URL into the browser?
Typically it means we want to retrieve or view some resources

When a host responds to an HTTP request -> returns a resource and also specifies the **content type**/media type of resource 

The content type that a server will specify rely on the Multi-purpose Internet Mail Extensions or MIME standards (the browser doesn't look up the extension of file)
#mime
The browser rely on the MIME!!!
type/subtype | Description
--- | ---
application/json| JSON data
image/gif | GIF image
image/png|PNG image
video/mp4| MP4 video
text/xml | XML
text/html | HTML
text/plain | Just text
... | ...


## Content Negotiation

A resource that's identified by a single URL can have multiple representations (one recipe but many languages, but HTML, but pdf, but ...). SO which representation server should be used ->

the client makes an HTTP request to a server, the client can specify the media types that it will accept (for example "I want HTML and French recipe")


















