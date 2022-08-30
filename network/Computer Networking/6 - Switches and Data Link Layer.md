[[network/Computer Networking/_ 0 Start]]


---
# Switches and Data link layer

**Switch** 
- operates on a physical (**BITs**) and data link layers (**FRAMEs**), it doesn't work on network or transport or app layers
- its responsiblility is to transfer frames between different devices  as fast as possible
- 

Ports in a switch:
- `Gi0/1  Gi0/2  Gi0/3 ...`
- `0` slot number
- `1 2 3`  port number

MAC address table:
- is in the switch memory
- maps port numbers to mac address of devices

----
## Ethernet Frame Header
==IEEE 802.3:==
1. 7 bytes PREAMBLE
2. 1 byte SFD (Start-of-frame Delimter)
3. 6 bytes (Destination MAC address)
4. 6 bytes (Source MAC address)
5. 4 bytes VLAN Tag
6. 2 bytes Type (each type of protocol is encapsulated next
-----------end of header
1. Data recieved from upper layers
2. CRC (FCS) Cyclic Redundancy Check (Frame Check Sequence) 4 bytes

> 26 bytes - minimum overhead in every frame

---

## Types of Communication

#### Unicast
a specific device wants to send data tp a single device


#### Mutlicast
one device wants to send data to a specific group


#### Broadcast
a single device communicates with all devices

---
## Types of MAC addresses

#### Unicast
MAC Address that is asigned to any network interface card (NIC)

#### Multicast
MAC adrresses that are used in multicast transmission
Sender sends one stream to multicast MAC address (starts with `01:00` ; this address only as a destination MAC address

#### Broadcast
`ff:ff:ff:ff:ff:ff` is only one 
if the switch recieved inf the this frame has to be send to this address, it will send it to all accecible ports in the same splot





