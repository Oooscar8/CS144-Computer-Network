[toc]



# CS144 Computer Network



---

## Networked Applications

### Byte Stream Model

<img src="https://gitee.com/OooAlex/study_note/raw/master/img/202409072253739.png" alt="image-20240907225315456" style="zoom:25%;" />

### World Wide Web (HTTP)

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

