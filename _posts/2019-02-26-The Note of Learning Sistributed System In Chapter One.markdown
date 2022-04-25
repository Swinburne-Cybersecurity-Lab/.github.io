---
layout:     post
title:      "The Note of Learning Distributed System In Chapter One"
subtitle:   " \"CHARACTERIZATION OF 
DISTRIBUTED SYSTEMS \""
date:       2019-02-26 20:12:00
author:     "Nastul"
header-img: "img/dshead1.png"
tags:
    - Distributed System
---
> “Note. ”
> 
Update -26/02/2019 

This is note from Distributed System-concept and design

## **1.Introduction** <br>
**definition:**<br> 
A distributed system is one in which components located at networked computers communicate and coordinate their actions only by passing messages.

**characteristics of distributed systems:**<br>concurrency of components, lack of a global clock and independent failures of 
components.



- Concurrency:In a network of computers, concurrent program execution is the norm. I can do my work on my computer while you do your work on yours, sharing resources such as web pages or files when necessary. The capacity of the system to handle shared resources can be increased by adding more resources (for example. computers) to the network. We will describe ways in which this extra capacity can be usefully deployed at many points in this book. The coordination of concurrently executing programs that share resources is also an important and recurring topic.


- No global clock: When programs need to cooperate they coordinate their actions by exchanging messages. Close coordination often depends on a shared idea of the time at which the programs’ actions occur. But it turns out that there are limits to the accuracy with which the computers in a network can synchronize their clocks– there is no single global notion of the correct time. This is a direct consequence of the fact that the only communication is by sending messages through a network.


- Independent failures: All computer systems can fail, and it is the responsibility of system designers to plan for the consequences of possible failures. Distributed systems can fail in new ways. Faults in the network result in the isolation of the computers that are connected to it, but that doesn’t mean that they stop running. In fact, the programs on them may not be able to detect whether the network has failed or has become unusually slow. Similarly, the failure of a computer, or the unexpected termination of 
a program somewhere in the system (a crash), is not immediately made known to the other components with which it communicates. Each component of the system can fail independently, leaving the others still running. The consequences of this characteristic of distributed systems will be a recurring theme throughout the book.

<br><br>
**Examples of distributed systems**

- **Web search**
- **Massively multiplayer online games (MMOGs)**
-  **Financial trading**



<br><br>

**Trends in distributed systems**<br>
influential trends:
<br>


- the emergence of pervasive networking technology;
- the emergence of ubiquitous computing coupled with the desire to support user mobility in distributed systems;
- the increasing demand for multimedia services;
- the view of distributed systems as a utility.

**Pervasive networking and the modern Internet**<br>
![](http://ww1.sinaimg.cn/large/a75df9b2ly1g0jzuchdnrj20ve0ilwgw.jpg)
**Mobile and ubiquitous computing**<br>
• Laptop computers.<br>
• Handheld devices, including mobile phones, smart phones, GPS-enabled devices, pagers, personal digital assistants (PDAs), video cameras and digital cameras.<br>
• Wearable devices, such as smart watches with functionality similar to a PDA.<br>
• Devices embedded in appliances such as washing machines, hi-fi systems, cars 
and refrigerators.
![](http://ww1.sinaimg.cn/large/a75df9b2ly1g0jzz5wgedj20wi0g5gn3.jpg)
**Distributed computing as a utility**<br>
**Focus on resource sharing**<br>



<br><br><br>
# **Challenges**<br> #
**Heterogeneity**<br>
• networks;<br>
• computer hardware;<br>
• operating systems;<br>
• programming languages;<br>
• implementations by different developers.




**Openness**<br>
**Security**<br>
**Scalability**<br>
**Failure handling**<br>

 Consider the following examples: <br>
1. There should always be at least two different routes between any two routers in the Internet. <br>
2. In the Domain Name System, every name table is replicated in at least two 
different servers. <br>
3. A database may be replicated in several servers to ensure that the data remains 
accessible after the failure of any single server; the servers can be designed to 
detect faults in their peers; when a fault is detected in one server, clients are 
redirected to the remaining servers.<br>

**Concurrency**<br>

**Transparency**<br>

**Quality of service**<br>
![](http://ww1.sinaimg.cn/large/a75df9b2ly1g0k0bh76wyj20wt0emwgk.jpg)


<br><br><br>
# Summary #
The construction of distributed systems produces many challenges: <br>
**Heterogeneity:** They must be constructed from a variety of different networks, 
operating systems, computer hardware and programming languages. The Internet 
communication protocols mask the difference in networks, and middleware can deal 
with the other differences.<br>
**Openness:**Distributed systems should be extensible – the first step is to publish the 
interfaces of the components, but the integration of components written by different 
programmers is a real challenge.<br>
**Security:** Encryption can be used to provide adequate protection of shared resources 
and to keep sensitive information secret when it is transmitted in messages over a 
network. Denial of service attacks are still a problem.<br>
**Scalability:** A distributed system is scalable if the cost of adding a user is a constant amount in terms of the resources that must be added. The algorithms used to access shared data should avoid performance bottlenecks and data should be structured 
hierarchically to get the best access times. Frequently accessed data can be replicated.<br>
**Failure handling:** Any process, computer or network may fail independently of the 
others. Therefore each component needs to be aware of the possible ways in which 
34 CHAPTER 1 CHARACTERIZATION OF DISTRIBUTED SYSTEMS
the components it depends on may fail and be designed to deal with each of those 
failures appropriately.<br>
**Concurrency:** The presence of multiple users in a distributed system is a source of 
concurrent requests to its resources. Each resource must be designed to be safe in a 
concurrent environment.<br>
**Transparency:** The aim is to make certain aspects of distribution invisible to the application programmer so that they need only be concerned with the design of their particular application. For example, they need not be concerned with its location or the details of how its operations are accessed by other components, or whether it will be replicated or migrated. Even failures of networks and processes can be presented to application programmers in the form of exceptions – but they must be handled.<br>
**Quality of service：** It is not sufficient to provide access to services in distributed systems. In particular, it is also important to provide guarantees regarding the qualities associated with such service access. Examples of such qualities include parameters related to performance, security and reliability.




# reference #
Dollimore, J., Kindberg, T., & Coulouris, G. (2005). Distributed systems: Concepts and design