[[network/Computer Networking/_ 0 Start]]


---
# Ethernet
This protocol (very popular) is used to transfer data using wired  or wireless media

TCP/IP model:
- `TCP` is a protocol on the transport layer and
- `IP` is a protocol on the network layer
- `Ethernet ` is used on the Data Link and Physical Layer (the Nerwork Accerss layer)
	- it's not a single protocol
	- it's a set of different protocols that define communication between different devices on data lina and physical layer

==IEEE 802.3== a standard that defines the communication between devices (wire media)
==IEEE 802.11== (a,b, c) (wireless media)


---
## Cooper, Fiber and Wireless media
cooper - bednarz, twórca/naprawiacz beczek
fiber - włókno, struktura

==cooper cable==  physical cable that consists of eight different wires that are actually combined into four pairs   connector = RJ-45 (distance = 100m)

==fiber cable== for long distance transmission, you could transmitt the data using light 
 


----
## NIC Network Interface Card
or network interface controller
different devices have different controllers

---
## MAC Address 
Media Acces Control is built into everi NIC by manufacturer

MAC address is unique hardware address
It is data link address
It is wrote in hexadecimal

Each Ethernet NIC must have MAC Address

### MAC Address Structure
1 octet = 8 bits
6 octets = 48 bits

every Mac address consists of 48 bits or 6 octets
3 octets: OUI Organizationally Unique Idenifier
	CC:46:D6 - Cisco
	3C:5A:B4 - Google, Inc.
3 octets: Network Interface Controller specific


---
## Binary vs Hexadecimal (4 bits)

0 - 0000
5 - 0101
A - 1010
B - 1011
E - 1110
F - 1111

---





