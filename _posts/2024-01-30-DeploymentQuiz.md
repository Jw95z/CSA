---
comments: true
layout: default
title: CSA Deployment quiz 
type: hacks
permalink: /deployQuiz
toc: true
courses: {'csa': {'week': 21}}
---
## Question 1 

1. Reverse Proxy, there is something called a server name and proxy pass. Describe server name and proxy pass definations in server file

![img](./images/question1.png)

### Sever Name
Server name is the address that people enter in their browsers to visit the site they want to visit. Just like a fingerprint, each particular website has its own unique domain name and the same name cannot be used on other web pages.

- The server_name directive is used to specify the domain name or names that should match this server block. 
- In this case, it is set to linkr.stu.nighthawkcodingsociety.com.
- When a request is received by NGINX, it checks the server_name directive to determine which server block's configuration should be used to handle the request.
- In the configuration you provided, the server block is responsible for handling requests for the domain linkr.stu.nighthawkcodingsociety.com.

![img](./images/servername.png)

### Proxy pass

Proxy pass defines the backend server or application to which NGINX should forward requests for processing. In your configuration, NGINX is set up to handle requests for linkr.stu.nighthawkcodingsociety.com and proxy them to a server running on localhost:8069.

- The proxy_pass directive is used to pass requests to a specified server and to enable dynamic loading of web applications.
- In this configuration, it is set to http://localhost:8069. This means that when NGINX receives a request, it will forward (or proxy) that request to the specified address (localhost:8069 in this case).
- The purpose of using proxy_pass in this context is likely to forward requests to a backend server or application running on the specified port 
- This is commonly used in reverse proxy setups where NGINX acts as an intermediary between the client and the actual web server, allowing for additional features such as load balancing, SSL termination, or serving static content.

![img](./images/proxypass.png)



## Question 2
2. Show JWT token login process. Split browser screen, to show that it needs authentication also decode the cookie.


![img](./images/cookie1.png)

## Question 3
3. Security Config: explain security config rules required for access in spring boot, provide request matcher that shows permit, and request matcher that shows authentication required

![img](./images/security.png)


## Question 4
4. POJO

![img](./images/pojo.png)
## Question 5
5. Describe the docker process for update of application. 0.9
![img](./images/pull.png)



