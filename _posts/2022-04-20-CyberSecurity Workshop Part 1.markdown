---
layout:     post
title:      "Cybersecurity Workshop"
subtitle:   
date:       2022-04-20 14:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
catalog: true
tags:
---


## Workshop Summary

Our lives are closely linked to the world of the internet, mobile computing, and electronic media. Cybersecurity, the protection of systems, networks, and programs, is becoming a critical aspect of our every day lives. In this hands-on workshop you will discover how web-based vulnerabilities work, different types of cyber attacks and the impact they can have.


___


## Part 1 Introduction 
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




![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Warning.jpg)
**WARNING:** <font  color=red> This program is for educational purposes only. If you attempt these techniques without authorization, you are very likely to get caught. If you are caught engaging in unauthorized hacking, most companies will fire you. Claiming that you were doing security research will not work as that is the first thing that all hackers claim. </font>.

___

## Part 2 Practices

##### What is WebGoat?
WebGoat is a deliberately insecure application that allows interested developers just like you to test vulnerabilities commonly found in Java-based applications that use common and popular open-source components.

For us this is a good application to understand cybersecurity. We were able to practically see how a hacker could break into a website.


##### (Optional) Install environment (Locally) 
-   Computer with any operating system (Windows, Linux, MacOS)
-   [webgoat-server-8.2.2.jar](https://github.com/WebGoat/WebGoat/releases/download/v8.2.2/webgoat-server-8.2.2.jar)
-   [webwolf-8.2.2.jar](https://github.com/WebGoat/WebGoat/releases/download/v8.2.2/webwolf-8.2.2.jar)
-   [JAVA 17](https://www.oracle.com/java/technologies/downloads/)
-   Browser (Recommend using Chrome or FireFox)


Run in the terminal (For Windows, use cmd win+R (Not PowerShell)):
`java -Dfile.encoding=UTF-8 -Dserver.port=8080 -Dserver.address=localhost -Dhsqldb.port=9001 -jar webgoat-server-8.2.2.jar`

Run in other terminal:
`java -Dfile.encoding=UTF-8 -Dserver.port=9090 -Dserver.address=localhost -jar webwolf-8.2.2.jar`

Then you will see:
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture2.png)
Patiently waiting for the environment to start. 
When the terminal stops outputting messages, the environment is probably ready.  Let's continue.






##### Open WebGoat
When you are done with the preparation part, you can type http://localhost:8080/WebGoat in your browser. Register an account according to your preferences. This will only be stored on your local computer.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture8.png)

Then login with the account you just registered. You will see the next picture. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture9.png)

___

##### HTTP Basics 
The basics for understanding the transfer of data between the browser and the web application and how to trap a request/response.

HTTP is also called Hypertext Transfer Protocol. Officially, it is an application layer protocol in the Internet protocol suite model for distributed, collaborative, hypermedia information systems. Simply speaking. The web pages we use are based on this protocol.

Let's follow the page and explore.

If you are using Chrome, you can right click on the blank part of the page. Then select inspect to access the developer tools. 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture10.png)

**Elements(Inspector) Tab :** the HTML and CSS source code.

**Console tab:** We can see anything, which a loaded JavaScript file may have printed out to it. It is also possible for us to run our own line of JavaScript code.

**Sources tab:** all the HTML, CSS and JavaScript files that are used.

**Network tab:** Logs all network activity in the Network.

The Quiz: 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture11.png)
You can try any possible answer in the input box. Then click Go and submit your answer. At this time, the browser will send a request to the server. (Remember to open Developer Tools before you click the button to send the request so that it keeps track of your network activity.)

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture12.png)

Then you will see a name called attack2 appear in the window. Although there are many other activities, attack2 appears when we press the button. We click on it and more information will appear. Like request url, method. Here the method is POST. We can use it to answer the first question. When we click on payload, we can see which data is sent by that request. 

___


##### SQL Injection 
First let's learn some information about SQL.

SQL is a standardized programming language which is used for managing relational databases and performing various operations on the data in them. With using SQL you can use standard SQL commands to interact with relational databases. They are CREATE, SELECT, INSERT, UPDATE, DELETE and DROP.

A relational database is a type of database that stores and provides access to data points that are related to one another. Each row in a table is a record with a unique ID called the key. Columns of the table hold attributes of the data. Each record has a value for each attribute.

Motivation behind a SQL Injection attack is to gain access to data from a database, that the hacker is not authorised to see. With this attack they could gain personal information on people, gain passwords, usernames, credit details. Client list that companies have and sell it on the dark web for a certain value of money.

Here we have a sample database **(A1 SQL Injection (intro) subtask 2)**. A employees table. And we have userid, username, etc.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture13.png)

We can manipulate this table with some commands. Let’s try:
`Select department from employees where last_name='Franco'`

This command allows us to find the department whose last name is 'Franco' from the employees table. 

SQL injection is a common attack vector that uses malicious SQL code for backend database manipulation to access information that was not intended to be displayed. This information may include any number of items, including sensitive company data, user lists or private customer details.

It’s one of the most popular hacking techniques, but also one of the oldest. Nearly 20 years since its discovery, SQL injection news still relevant. For one, it’s used in an estimated two-thirds of web app attacks today.

In March 2022, A security vulnerability in e-learning platform Moodle could allow an attacker to take over a database and potentially obtain sensitive information. This information can be private information about the user.


![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture14.png)

Let's look at an example **(A1 SQL Injection (intro) subtask 10)**.
This is Numeric SQL injection. 
Suppose the following is a query statement from the server:
`"SELECT * FROM user_data WHERE login_count = " + Login_Count + " AND userid = "  + User_ID;`

If we just enter the query data normally, then there won't be any problem. But we must know what the **Login_Count** and **User_Id** are. 
Only one of these fields is susceptible to SQL Injection. 
Let’s try:
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture15.png)
Then click Get account info, you will get all user information. 
Let's use the input data to complete the SQL statement:
`SELECT * FROM user_data WHERE login_count = 123 AND userid = 1 or 1=1;`
It is easy to see that the last input of **‘or 1=1’** always works. We can also replace **‘1=1’** with true.  That's how Numeric SQL injection works.


___


##### Authentication Bypasses 
Authentication is the process of verifying whether someone or something is in fact who or what it is declared to be. This process prevents anyone or anything outside of a system they are not authorised to be in.

Motivation for hackers to bypass authentication systems. Is to gain access to system they do not have permission to. With this hackers can gain information, lock users out of their own systems. 


It happens in many ways, but usually take advantage of some flaw in the configuration or logic. Tampering to achieve the right conditions. 

Let’s try 2FA Password Reset **(A2 Authentication Bypasses subtask 2)**

When you forget your password, some applications often help you reset it by answering some questions to confirm your identity. As shown in the figure below.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture16.png)

When we enter some random data and click submit. In the sent packet, we can see that it has these fields. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture17.png)
We can guess that these fields are used by the server to determine if they are consistent with the stored answers. 
So we can go back to the Elements tab and change the name of the field. Just like the one shown in the figure below. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture18.png)
Then we submit our form, and we can successfully change our password. Even if we don't know the answer. 

___

## Part 3 Optional Task 

##### JWT tokens 

JSON Web Token is what JWT stands for, it defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed by using a secret or a public/private key pair using RSA.

Many applications use JWT to allow the client to indicate is identity for further exchange after authentication.
For example, if we log in to a website, the website may generate a JWT token for us to maintain our login status. Here is an example of a token.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture19.png)
The token is base64 encoded and consists of three parts: header, claims, signature.

Here is a basic sequence of getting a JWT token:
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture20.png)

We can use some decoding tools to decode the JWT token like online tools  https://jwt.io/  or https://token.dev/. We can also use WebWolf  http://localhost:9090/WebWolf/.

Then we can get the following decoded information:
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture21.png)

Let’s try JWT signing **(A2 JWT tokens subtask 5)**.
We can choose the role to vote for here. But there is no admin. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture22.png)
Let's try clicking on the trash can button. Only admin user can reset the votes. 
Then check the developer tools, network tab to see what's happening.
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture23.png)

We can see that we have sent our JWT token to the server, as shown in the red line above. Let's decode this data. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture24.png)
We change the algorithm to none, and the admin information in the data to true as shown below.
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture25.png)
Then replace the original JWT token with the generated JWT String. 
Remember to add the last dot. 
Like: eyJhbGciOiJub25lIn0.eyJpYXQiOjE2NDgxODU5NzIsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJUb20ifQ.
If you are using a Firefox browser, then you can modify the token information in the cookie field directly through the Edit and Resend buttons.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/20220426110141.png) 

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/20220426111207.png) 

Then send the message.

However, in chrome you can't do this directly. You can try to think of other solutions.

___

## Part 4 Optional Challenge 

**A1 Path traversal** Tab 2, 3.

**A2 JWT token** Tab 10. **password reset** Tab 4, 6.

**Challenges** 







