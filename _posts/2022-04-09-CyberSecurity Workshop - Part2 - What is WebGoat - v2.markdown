---
layout:     post
title:      "CyberSecurity Workshop - Part2- What is WebGoat"
subtitle:   " \"CyberSecurity\""
date:       2022-04-09 02:47:00
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