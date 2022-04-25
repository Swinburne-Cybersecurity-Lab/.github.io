---
layout:     post
title:      "CyberSecurity Workshop - Part2-2"
subtitle:   " \"CyberSecurity\""
date:       2022-04-08 10:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

![RUNOOB](https://raw.githubusercontent.com/NasTul/Diagrams/master/Picture1.png)


___
## Part 2-2 Practices:
___
##### SQL Injection:
First let's learn some information about SQL.

SQL is a standardized programming language which is used for managing relational databases and performing various operations on the data in them. With using SQL you can use standard SQL commands to interact with relational databases. They are CREATE, SELECT, INSERT, UPDATE, DELETE and DROP.

A relational database is a type of database that stores and provides access to data points that are related to one another. Each row in a table is a record with a unique ID called the key. Columns of the table hold attributes of the data. Each record has a value for each attribute.

Motivation behind a SQL Injection attack is to gain access to data from a database, that the hacker is not authorised to see. With this attack they could gain personal information on people, gain passwords, usernames, credit details. Client list that companies have and sell it on the dark web for a certain value of money.

Here we have a sample database. A employees table. And we have userid, username, etc.

![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture13.png)

We can manipulate this table with some commands. Let’s try:
`Select department from employees where last_name='Franco'`

This command allows us to find the department whose last name is 'Franco' from the employees table. 

SQL injection is a common attack vector that uses malicious SQL code for backend database manipulation to access information that was not intended to be displayed. This information may include any number of items, including sensitive company data, user lists or private customer details.

It’s one of the most popular hacking techniques, but also one of the oldest. Nearly 20 years since its discovery, SQL injection news still relevant. For one, it’s used in an estimated two-thirds of web app attacks today.

In March 2022, A security vulnerability in e-learning platform Moodle could allow an attacker to take over a database and potentially obtain sensitive information. This information can be private information about the user.


![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture14.png)

Let's look at an example (A1 subtask 10).
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

___
##### JWT tokens:

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

Let’s try JWT signing.
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
However, in chrome you can't do this directly. 
![RUNOOB](https://raw.githubusercontent.com/NasTul/COS80013_Lab/main/Picture26.png)
You can do this by right clicking on the network activity and chose the way you want to, for example if you want to send a request using windows terminal, you can choose PowerShell. Then edit the corresponding cookie information in a text editor. Finally, type in the terminal.

___
## Tasks

Now is your turn to try it.

**A1 Path traversal** Tab 2, 3.

**A2 JWT token** Tab 10. **password reset** Tab 4, 6.

**Client side** HTML tempering. 

**Challenges** 







