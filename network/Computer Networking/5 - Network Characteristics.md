[[network/Computer Networking/_ 0 Start]]




---
# Network Characteristics
## Bandwidth
(szerokość pasma, przepustowość)
>[!bandwidth]
>maximum amount of bits that could be transmitted over the link in specific amount of time
>is a phisical characteristic

5Mbps - 5 Megabits per second
1Kb = 1 000 bits
1Mb = 1 000 000 bits
1Gb = 1 000 000 000 bits

max 100 Gb
the slowest link of the net is the borrleneck , so it determins the speed of enire net



## Throughput
wydajność
It actual amount of data that could be transmitted
Its value depends e.ie. from TCi/IP Model layers.

Throughput will always be lower (10%) than bandwidth

When you use i.e. "Speedtest" you will see a throughput value


## Latency
czas oczekiwania
> 
> - (one-way delay) it's data transfer time from one device to another
> - it is appied to application layer 
> 
> Latency is very important when we talk, for example, about real time applications (i.e. videa)

What forms latency?
- queueing delay
- processing delay
- transmission delay
- propagation delay (how much time it takes to travel for a single bit of data from one end point to another)


## Ping
Round-trip Time (RTT)
Time required to send data from one device to another and back
from computer to server = 25ms
from server to computer = 30ms
RTT                                =  55ms

### Measuring RTT using Ping utility
```shell
~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=113 time=94.3 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=113 time=177 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=113 time=32.6 ms
...
^C
--- 8.8.8.8 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6009ms
rtt min/avg/max/mdev = 28.628/80.850/177.225/48.950 ms

```
`time=94.3` (request from my computer to google server)

> Evert IP packet is treated by network devices independently from the other packets

---
## Jitter
Jitter happens when different packets have different one-way delays

I.E.
- order at the sender: 1, 2, 3 (packets)
- order at the receiver: 3, 1, 2(packets)
- so server has to place them in the same order at in the sender -> it happens to Jitter
- Jitter is a variable latency for differen packets 
- if Jitter is very high, some packets wi be lost or  discarded by the reveiver


## packet loss rate
has impact to 







