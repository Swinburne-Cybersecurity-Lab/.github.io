---
layout:     post
title:      "CyberSecurity Workshop - Part1"
subtitle:   " \"CyberSecurity\""
date:       2022-04-08 00:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

![RUNOOB](https://raw.githubusercontent.com/NasTul/Diagrams/master/Picture1.png)


___
## Part 1 Introduction:
Now, we live in a digital world. Our work lives, personal lives, and finances have all linked to the world of the internet, mobile computing, and electronic media. Unfortunately, this widespread phenomenon makes us more vulnerable than ever to malicious attacks, invasions of privacy, fraud, and others. That’s why cybersecurity is such a vital part of a secure and well-ordered digital world. Cybersecurity keeps us safe from hackers, cyber criminals, and other agents of fraud.

A recent example is, for some reasons, some places are not convenient to access steam. A very famous game platform. Those hackers have downloaded and cracked all the games on steam into their web. This could be a disaster for game companies and players.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture4.png)
___
##### What is Cybersecurity?
The definition of Cybersecurity or IT security is the protection of systems, networks, and programs. The theft of or damage would be to their hardware, software, or electronic data. The cyberattacks could access, change, destroy the data.

However, your understanding of cybersecurity may still be vague right now. This is because cybersecurity is a very large concept. It includes Physical Security, Operating System Security, Malware, Network Security, Web Security, Cryptography, Web Application Security, Cloud Security and more… Is it more confusing? All of these are related to cybersecurity. Don't be afraid of them. Obviously, we can't be proficient at them all. We can use one of these sections as an entry point for understanding. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/2022040623255.png)
First, we need to learn some basic concepts that nicely summarize the key points of the above types of security. That is traditional security principal CIA. This stands for confidentiality, Integrity, and Availability. Next, we cover some basic concepts about what they are. Then some examples about attacks will be provided, with this you knowledge, you can figure out the answer to which security principle has been broken. 

   Confidentiality
-   Only those entitled to access the information can see it. 
-   Authorize, encrypt, access control, authenticate, restrict physical access.

   Integrity
-   Information cannot be altered, and changes are immediately detectable. 
-   Backup, checksum, hash, correction code

   Availability
-   Information is available (to read, write) to those who need it without interruption or onerous access restrictions. 
-   Redundant systems, data recovery, disaster planning, UPS, backup power systems, redundant network connections. 

Three examples of attack different attacks will now be covered. Three of them compromises the confidentiality, integrity, and availability. Not necessary in that order.


![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture27.png)

The first example is Packet Snifﬁng as shown in Fig. This is a type of network attack. The attacker captures the data packets in travel. If the data is captured and the network traffic is not encrypted, the attacker can collect the sensitive information like passwords or card numbers. The most widely used packet capture software is Wireshark.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture7.png)


This example is man-in-the-middle, another type of network attack. The attacker sits between two devices that are communicating, monitors their communication, and manipulate the data as it moves between them. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture61.png)

The last one is DoS (Denial of Service attacks): DOS Attack is a type of attack to a network server with large number or service requests that the target server cannot handle. In such case, DoS can crash the server and legitimate users are denied the service. DDoS (Distributed Denial of Service attacks): DDoS attack is a type of DoS attack, originating from many attacking computers from different geographical regions.

Now, packet sniffing, man-in-the-middle, and Denial-of-service attack. Can you answer which breaks confidentiality, which breaks integrity, and which breaks availability?

Answers are as follows, packet sniffing breaks the confidentiality, man-in-the-middle attack breaks the integrity, and DoS attack breaks the availability.

In addition to the classic C.I.A., there are several additional concepts that are also important in modern computer security applications. These concepts can be abbreviated as A.A.A., which in this context refers to assurance, authenticity, and anonymity. With the growth of the network, more and more concepts are being proposed. We need to keep learning to keep up with the times.

Let's go to the next part, Web Security. Let's use it as an entry point to see how cybersecurity practically works.