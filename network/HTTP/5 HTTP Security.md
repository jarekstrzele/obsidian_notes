[[_ 0 HTTP fundementals]]


---

# HTTP Security
HTTp os designed as a ==stateless== protocol meaning each request response transactionis indempendent of any previous of future transaction [[_ 0 intro APIs for beginners#How the web works | also see]]

## saving state
- embed a state in the resources that are being transferred to the client 
- save a state  on the server or behind the server (that style is required for state that has to be around a long time; e.g. remember email address )
	- a user session (it may live in memory or in a database )
	- a session storage can have some impacts on scalability (a kind of request -to-> this one server only)
	- 

## cookies
Websites that want to track users often turn to cookies.
Cookies are defined by RFC 6265.
- cookies can identify a user  but they don't authenticate a user
- cookies give a user some unique identifier

WHen a Website wants to give a user a cookie:
- it uses a set cookie header (`Set-Cookie`) in an HTTP response
- there are three pieces of information (they are separated by `;`) in this particular cookie:
	- 1. collection of name value pairs and these name value
		- sometimes it is changed to `GUID=003029394324fs32...` (because it is a memory limitation and it is more secure)
	- 2. `domain...`
	- 3. `path=/...` helps to organize cookies when there is mutiple 



## Tracing Sessions and HttpOnly
#httponly
the flag `HttpOnly` in `Set-Cookie`  tells the browser the user agent, is that it should not allow script code toaccess this cookie


## Basic Authentication







