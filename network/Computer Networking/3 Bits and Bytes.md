[[network/Computer Networking/_ 0 Start]]


---
# Bits and Bytes
1 bit (Binary Digit) Basic unit of information
1 byte - 8 bit 
	1 byte is also colled Octet
	10100101
	1 byte encodes one character in UNICODE



## PDUs Protocol Data Units
the smallest piece of information that is related to specific layer in the same model [[2 -  TCP IP OSI Models]]

| Layers | OSI          | PDUs     | description                                   |
|--------|--------------|----------|-----------------------------------------------|
| Host   | Application  | Data     | Interaction with end-user(HTTP,FTP)           |
| Host   | Presentation | Data     | Data representation (JEPG, UTF-8)             |
| Host   | Session      | Data     | Establishes and controls session (L2TO, h.245 |
| Host   | Transport    | Segments | end-toend connections(TCP and UDP)            |
| Media  | Network      | Packets  | Logical addressing and ROuting (IPv4, v6)     |
| Media  | Data Link    | Frames   | Physical addressing (Ethernet)                |
| Media  | Physical     | Bits     | Transmission of the data (Ethernet, WiFi,...) |

**frame** PDU for Data Link is the smallest piece of information on data link layer,
**packets** the smallest piece of information on network layer
**Segments** the smallest piece of information on the transport layer (TCP segments or UDP segments)
**data** the smallest peice of information on session or presentation or application


-----
## OSI vs TCP/IP
TCP (application) 
   / \
	|
   \\ /
OSI(application, presentation, session)
because app(e.i. Chrome) is responsible for all operations that happen on app, presentation, session layers


TCP(Transport) <-> OSI (Transport)
TCP(Internet) <-> OSI(Network) -> delivery of the packets from source to destination

TCP(Network Access)
  / \
   |
 \\ /
 OSI(Data link, Physical)
   
----
## Encapsulation and Decapsulation

### encapsulation
>[!encapsulation]
>it's a process of formatting data
>this process **adds** some additional overhead(==header==) on each layer

E.I.
1. you have an email ready to send (data in the ==app layer==)
2. this data goes to ==Transport layer== and  this layer adds `Segment header` (segment is the Protocol Data Unit PDU)
3. this extended data goes to ==Network layer== and this layer adds a new header `Packet Header` (packet is PDU for Network layer, so you have now `data + segment header + packet header`
4. this complex data are going to ==Data Link== layer and on this layer we add one more header `Frame Header` and  after data ad `Frame trailer` (error handeling)
5. finally, this data, along with all added, headers is transmitted over the ==physical== media (`BITS`)

```
1. DATA
2. segmentHeader+DATA
3. packetHeader+segmentHeader+DATA
4. frameHeader+packetHeader+segmentHeader+DATA+frameTrailer
5. BITS
```

### Decapulation
a reverse process
1. from physical `BIT` to Data Link (read only Frame Header and Frame trailer)
2. the Network layer reads only Packet header and removes it
3. the Transport layer reads only Segment header and removes it
4. the Application layer reads `DATA`



















