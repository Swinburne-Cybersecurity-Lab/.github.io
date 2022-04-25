---
layout:     post
title:      "CyberSecurity Workshop - Part2-1"
subtitle:   " \"CyberSecurity\""
date:       2022-04-08 01:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Warning.jpg)
**WARNING:** <font  color=red> This program is for educational purposes only. If you attempt these techniques without authorization, you are very likely to get caught. If you are caught engaging in unauthorized hacking, most companies will fire you. Claiming that you were doing security research will not work as that is the first thing that all hackers claim. </font>.

___
## Part 2-1 Practices:

##### What is WebGoat?
WebGoat is a deliberately insecure application that allows interested developers just like you to test vulnerabilities commonly found in Java-based applications that use common and popular open-source components.

For us this is a good application to understand cybersecurity. We were able to practically see how a hacker could break into a website.


##### Preparation:
-   Computer with any operating system (Windows, Linux, MacOS)
-   [webgoat-server-8.2.2.jar](https://github.com/WebGoat/WebGoat/releases/download/v8.2.2/webgoat-server-8.2.2.jar)
-   [webwolf-8.2.2.jar](https://github.com/WebGoat/WebGoat/releases/download/v8.2.2/webwolf-8.2.2.jar)
-   [JAVA 17](https://www.oracle.com/java/technologies/downloads/)
-   Browser (Recommend using Chrome or FireFox)

##### Install environment (Locally)
Run in the terminal (For Windows, use cmd win+R (Not PowerShell)):
`java -Dfile.encoding=UTF-8 -Dserver.port=8080 -Dserver.address=localhost -Dhsqldb.port=9001 -jar webgoat-server-8.2.2.jar`

Run in other terminal:
`java -Dfile.encoding=UTF-8 -Dserver.port=9090 -Dserver.address=localhost -jar webwolf-8.2.2.jar`

Then you will see:
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture2.png)
Patiently waiting for the environment to start. 
When the terminal stops outputting messages, the environment is probably ready.  Let's continue.



##### Open WebGoat:
When you are done with the preparation part, you can type http://localhost:8080/WebGoat in your browser. Register an account according to your preferences. This will only be stored on your local computer.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture8.png)

Then login with the account you just registered. You will see the next picture. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture9.png)

___

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