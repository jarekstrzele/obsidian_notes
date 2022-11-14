[[network/Computer Networking/_ 0 Start]]


----
# TCP/IP and OSI Model
##### How devices communicate in the computer network?


==WIRESHARKE==

==protocol== standard of communication that allows to talk some language between different devices
	gmail: Simple Mail Transfer Protocol **SMTP**
	chrome: Hypertext Transfer Protocol Secure **HTTPS**
	terminal: Secure SHell **SSH**
	filezilla: File Transfer Protocol **FTP**

![[TCP_IP_MODEL.excalidraw|700]]


models | standards
--- | ---
describes how devices <br>  communicate in computer network | describe actual communication

TCP - Transmission Control Protocol ( transport layer)
IP - (internet layer)


---
#### Application layer
these protocols are used by different applications
these protocols are used at the top level
purpose: transfer or receive some data and use resulting data in some apps

#### Transport layer
purpose: establish end-to-end communication and reliably deliver data
TCP (Transmission Control Protocol)
	- establishes end-to-end session between two different endpoints
	- reliably sends data (if some data was lost on the way fron one endpoint to anther, then TCP will attempt to retrasmit such data
	- terminate connection
UDP (User Dataground Protocol )
	- sends data from one point to another
	- is unreliable protocol


#### Internet
purpose: 
	- connect different networks, 
	- find optimal path between different networks
	- send packets from one network to another


#### Network Access
transmit data over the physical Media (ETHERNET)

### Layers are fully independent
One layer doesn't care about what happens on another layer


---
## Mapping captured packets data to TCP/IP model
Transmission Control Protocol -> TRANSPORT layer
Internet Protocol -> INTERNET layer
Ethernet -> Network Access
Frame -> NetworkAccess
Data -> Application layer
Domain Name System -> Application layer



----
# OSI Model
OPEN SYSTEMS INTERCONNECTION
is better for understading

![[OSI_Model.excalidraw| 800]]

`<meta charset'utf-8'>` presentation








