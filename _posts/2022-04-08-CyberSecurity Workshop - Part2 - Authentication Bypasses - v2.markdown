---
layout:     post
title:      "CyberSecurity Workshop - Part2-Authentication Bypasses"
subtitle:   " \"CyberSecurity\""
date:       2022-04-09 11:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

##### Authentication Bypasses:
Authentication is the process of verifying whether someone or something is in fact who or what it is declared to be. This process prevents anyone or anything outside of a system they are not authorised to be in.

Motivation for hackers to bypass authentication systems. Is to gain access to system they do not have permission to. With this hackers can gain information, lock users out of their own systems. 


It happens in many ways, but usually take advantage of some flaw in the configuration or logic. Tampering to achieve the right conditions. 

Let’s try 2FA Password Reset (A2 Authentication Bypasses)

When you forget your password, some applications often help you reset it by answering some questions to confirm your identity. As shown in the figure below.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture16.png)

When we enter some random data and click submit. In the sent packet, we can see that it has these fields. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture17.png)
We can guess that these fields are used by the server to determine if they are consistent with the stored answers. 
So we can go back to the Elements tab and change the name of the field. Just like the one shown in the figure below. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture18.png)
Then we submit our form, and we can successfully change our password. Even if we don't know the answer. 









