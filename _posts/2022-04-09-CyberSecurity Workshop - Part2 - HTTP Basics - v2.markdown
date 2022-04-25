---
layout:     post
title:      "CyberSecurity Workshop - Part2-HTTP Basics"
subtitle:   " \"CyberSecurity\""
date:       2022-04-09 03:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---


##### HTTP Basics:
The basics for understanding the transfer of data between the browser and the web application and how to trap a request/response.

HTTP is also called Hypertext Transfer Protocol. Officially, it is an application layer protocol in the Internet protocol suite model for distributed, collaborative, hypermedia information systems. Simply speaking. The web pages we use are based on this protocol.

Let's follow the page and explore.

If you are using Chrome, you can right click on the blank part of the page. Then select inspect to access the developer tools. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture10.png)

**Elements Tab:** the HTML and CSS source code.

**Console tab:** We can see anything, which a loaded JavaScript file may have printed out to it. It is also possible for us to run our own line of JavaScript code.

**Sources tab:** all the HTML, CSS and JavaScript files that are used.

**Network tab:** Logs all network activity in the Network.

The Quiz: 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture11.png)
You can try any possible answer in the input box. Then click Go and submit your answer. At this time, the browser will send a request to the server. (Remember to open Developer Tools before you click the button to send the request so that it keeps track of your network activity.)

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture12.png)

Then you will see a name called attack2 appear in the window. Although there are many other activities, attack2 appears when we press the button. We click on it and more information will appear. Like request url, method. Here the method is POST. We can use it to answer the first question. When we click on payload, we can see which data is sent by that request. 