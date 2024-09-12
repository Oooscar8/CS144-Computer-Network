[toc]



# CS144 Computer Network



---

## Networked Applications

### Byte Stream Model

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072253739.png" alt="image-20240907225315456" style="zoom:25%;" />

### World Wide Web (HTTP)

HTTP: hypertext transfer protocol

Client - Server

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072256179.png" alt="image-20240907225651919" style="zoom:25%;" />

### BitTorrent

> Break files into "pieces"

> Clients join and leave "swarms"

> Tracker keeps track of what clients are the members of "swarms"

<img src="../../../../../AppData/Roaming/Typora/typora-user-images/image-20240907232107668.png" alt="image-20240907232107668" style="zoom:25%;" />

### Skype

* Both clients

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072312668.png" alt="image-20240907231236456" style="zoom: 25%;" />

* NAT

B can connect to A, but not vice versa

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072313146.png" alt="image-20240907231350022" style="zoom: 25%;" />

* reverse connection

> Client A requests a connection to Client B

> A sends a message to Rendezvous, Rendezvous sends the request from A to B,

> Then B requests a connection to A

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072315333.png" alt="image-20240907231539117" style="zoom:25%;" />

* NATs

Two clients both behind NAT connect via Relay:

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072332986.png" alt="image-20240907233224830" style="zoom:25%;" />

---

## The 4 Layer Internet Model

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409080944938.png" alt="image-20240908094404690" style="zoom:50%;" />

### Link Layer

`Ethernet, WiFi, DSL, 3G`…

Deliver data over a single link between an end host and router, or between routers

### Network Layer

Deliver datagrams end-to-end

Provide an unreliable datagram delivery service (Must use IP)

* Packets

The Network Layer has the job of breaking data into packets, each with the correct destination address

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409080953960.png" alt="image-20240908095345699" style="zoom: 33%;" />

* IP

IP makes a best-effort attempt to deliver out datagrams to the other end **with no promises**

### Transport Layer

* TCP (Transmission Control Protocol)

Guarantee **correct**, **in-order** delivery of data, running **on top of the Network Layer**

* UDP (User Datagram Protocol)

Offers no delivery guarantees

### Application Layer

Bi-directional reliable byte stream between two applications, using application-specific semantics (e.g. http, bit-torrent)

'Get' is one of the commands of the HTTP:

![image-20240908101622139](https://gitee.com/OooAlex/study_note/raw/master/img/202409081016474.png)

### Summary

Each layer communicates with its peer layer

![image-20240908102313899](https://gitee.com/OooAlex/study_note/raw/master/img/202409081023310.png)

![image-20240908102846069](https://gitee.com/OooAlex/study_note/raw/master/img/202409081028454.png)

* IP is the "thin waist"

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409081034973.png" alt="image-20240908103439737" style="zoom: 33%;" />

* The 7-layer OSI Model

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409081037610.png" alt="image-20240908103716298" style="zoom:33%;" />

---

## The Network Layer (The IP service Model)

### Property

![image-20240908105323264](https://gitee.com/OooAlex/study_note/raw/master/img/202409081053674.png)

### Why is the IP service so simple?

![image-20240908110807536](https://gitee.com/OooAlex/study_note/raw/master/img/202409081108816.png)

### Features

![image-20240908111534425](https://gitee.com/OooAlex/study_note/raw/master/img/202409081115713.png)

### IPv4 Datagram

**`Checksum`** reduce chances of delivering datagram to wrong destination

**`TTL`** prevents infinite loop

**`Protocol ID`** tells destination how to deal with the data (e.g. TCP)

**`Type of Service`** gives a hint of how important the packet is

**`Packet ID`,`Flags`,`Fragment Offset`** help routers fragment IP packets into smaller datagrams

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409081120372.png" alt="image-20240908112017126" style="zoom: 33%;" />

---

## Life of a Packet

### TCP Byte Stream

* **3-way handshake** ("SYN, SYN/ACK, ACK")

1. The Client synchronize to the Server
2. The Server synchronize and acknowledge
3. The Client acknowledge the synchronize

![image-20240908140438966](https://gitee.com/OooAlex/study_note/raw/master/img/202409081404047.png)

IP address shows which computer the data goes to

TCP port shows which application the data goes to

IP packets have TCP segments, indicating which application the data goes to 

![image-20240908140747838](https://gitee.com/OooAlex/study_note/raw/master/img/202409081407899.png)

### Inside the Stream

The packets need to go through a series of **hops** to arrive the destination

![image-20240908141047907](https://gitee.com/OooAlex/study_note/raw/master/img/202409081410972.png)

### Inside Each Hop

Routers using a forwarding table

When a packet arrives, the router checks which forwarding entries pattern best matches the packet, it forwards the packet along that entries link 

![](https://gitee.com/OooAlex/study_note/raw/master/img/202409081415377.png)

---

## Packet Switching

#### Principle

A switch has a table of destination addresses and the next hop

When it receives a packet, it looks up the address in the table and sends the packet to the appropriate next hop

Each packet holds the destination address

Using this address, each switch can make the right decision

#### Flow

A collection of datagrams belonging to the same end-to-end communication, e.g. a TCP connection

---

## Layering Principle

### Definition

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409121602687.png" alt="image-20240912160236553" style="zoom: 50%;" />

### Examples of Layering

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409121608792.png" alt="image-20240912160830671" style="zoom:50%;" />

---

## Encapsulation Principle

### Principle

The lower layer, encapsulating the higher layer, and is the payload of the even lower layer

Encapsulation is how we take protocol layers and assemble them into packets

### An example

Your web browser generates an HTTP GET request

This HTTP GET request is the payload of a TCP segment

The TCP segment, encapsulating the HTTP GET, is the payload of an IP packet

This IP packet, encapsulating the TCP segment and the HTTP GET, is the payload of a `WiFi` frame

### VPN 

A more flexible encapsulation

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409121637063.png" alt="image-20240912163704943" style="zoom: 67%;" />

