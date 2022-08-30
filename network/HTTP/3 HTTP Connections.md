[[_ 0 HTTP fundementals]]


---

# HTTP  Connections
very lower perception

## Layers
Network communictaion protocol, the things that move information around the internet, are most buisness application, they consist of LAYERS
==each layer== in a communications stack is responsible for a specific and very limited number of responsibilities

==HTTP is what we call an application layer protocol== - it allows two apps to communicate over the network

==Application layer - HTTP==
	- two apps communicate 
==Transport layer   - TCP== (transmission Control Protocol):
	- the browser read scheme, host, port and open TCP socket by specifying that server address, and starts writing data into the socket
	- TCP accepts that data and cope with lost or duplcate data (TCP automatically resends any information that might get lost in transit; application doesn't worry about it)
	- TCP is reliable and UDP (User Datagram Protocol) is unreliable
	- TCP: error detection, flow control
==Network layer - IP==:
	- takes pieces of information and moving them through all the switches, routers, gateways, repeaters, ...
	- IP wokrs very hard to deliver the data at the destination,  but doesn't garantee
	- IP breaks data into packets/datagrams

==Data Link - ETHERNET==
	- media


## Programming Sockets
`URI`  Uniform Resource Identifier -> more generic than a URL because it can identify a resource by either name or location (but URL is a URI)

>Gniazdo (ang. socket) – pojęcie abstrakcyjne reprezentujące dwukierunkowy punkt końcowy połączenia. Dwukierunkowość oznacza możliwość wysyłania i odbierania danych. Wykorzystywane jest przez aplikacje do komunikowania się przez sieć w ramach komunikacji międzyprocesowej.

## Parallel Connections
Browsers can make parallel connections (2-6 ...)


## Persistent Connections
default type of connection in HTTP 1.

It stays open  after the completion  of one request response transaction (a browser can make many requests without overhead of opening  a new socket)

Persistent connections also avoid the slow start strategy that is part of TCP congestion control 

Persistent connections reduce memory usage, reduce CPU usage , reduce network congestion, reduce latency

Servers can close this connection and users too (Wireshark allows to see these processes)

Share servers forbid persitent connections 








