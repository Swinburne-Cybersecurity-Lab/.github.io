---
layout:     post
title:      "CyberSecurity Workshop - Part2-SQL Injection"
subtitle:   " \"CyberSecurity\""
date:       2022-04-09 10:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

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