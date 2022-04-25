---
layout:     post
title:      "CyberSecurity Workshop - Part2-JWT tokens"
subtitle:   " \"CyberSecurity\""
date:       2022-04-09 14:47:00
author:     "Nastul"
header-img: "img/data-featured-image-1.jpg"
tags:
    - InformationSecurity  
---

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







