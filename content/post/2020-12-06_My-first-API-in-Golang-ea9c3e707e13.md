---
title: My first API in Golang
description: >-
  I made a very simple first “API” in golang which I would like to share (most
  likely it does not have the best practices but at least it…
date: '2020-12-06T08:42:12.908Z'
categories: []
keywords: []
slug: /@devjaime/my-first-api-in-golang-ea9c3e707e13
---

I made a very simple first “API” in golang which I would like to share (most likely it does not have the best practices but at least it has the minimum requirements to scale into something more evolved).

Source Code

[**devjaime/golangrest**  
_GitHub is home to over 50 million developers working together to host and review code, manage projects, and build…_github.com](https://github.com/devjaime/golangrest "https://github.com/devjaime/golangrest")[](https://github.com/devjaime/golangrest)

The first thing I wanted was to list the requirements of my API so that it is fully functional for what I needed.  
\- It should be able to connect through an ORM to the database since it will most likely change in the future (reference is azure sql at this time).  
\- Must be able to lift into a container and go through a continuous integration process to be like a public api  
.- It must be scalable in time in terms of number of users and concurrent requests.  
API design diagram

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Zs__G00mmVB59U2JCzV7p__w.png)

The first thing I investigated was the Golang documentation [https://golang.org/](https://golang.org/) where the first thing is to follow the golang installation instructions very well on your machine either windows or mac [https://golang.org/dl/](https://golang.org/dl/)

In my case I have a mac and what I did was to see if there was an installation through homebrew and I did it by following some very simple steps, taken from the following tutorial.

[**Install Go on Mac (with homebrew)**  
_Install Brew (skip if you already did)_medium.com](https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5 "https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5")[](https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5)

With “go version” you can see if the installation really works and what version of go you have

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__h84GdWMh0SUjwzV9.png)

Another practical resource that helped me to build my first API was this:

However, concepts such as occupying an ORM and what ORM handles Golang are missing. From these “googling” I got to [https://gorm.io/index.html](https://gorm.io/index.html) which seemed like a very good option. Installation in your project

go get -u gorm.io/gorm

Now depending on the database to occupy, you should look for a dialect

You can see the different connections in

[**Connecting to a Database**  
_GORM officially supports databases MySQL, PostgreSQL, SQLite, SQL Server NOTE: To handle time.Time correctly, you need…_gorm.io](https://gorm.io/docs/connecting_to_the_database.html "https://gorm.io/docs/connecting_to_the_database.html")[](https://gorm.io/docs/connecting_to_the_database.html)

Another important dependency to install is Fiber  
Fiber is an Express-inspired web framework built on top of Fasthttp, the fastest HTTP engine for Go. Designed to make things easy for rapid development with zero memory allocation and performance in mind.

installation

go get github.com/gofiber/fiber/v2

After that I will explain my simple API structure

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__MF5__21RMvEFqRRr4.png)

Where the folder circleci, is the continuous integration and the steps to upload my api to a server.  
You can watch this video to get an idea of what I do in that file

The result is something like this:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__L1__Tlc__6ybdgnMWv.png)

In .ssh are the private and public keys to upload the project, which is something like this.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__Dg74ucmro77pgk__p.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__9FzSlr91__l4dkBBH.png)

Of course you must create your own  
Terminal (also in the reference video it appears very well explained)  
ssh-keygen -t rsa  
In database the file database.go contains the connection package

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__QkFcmZT70ELrEk1T.png)

and product is the model that will query the database with its respective verbs.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__RLHca__V____KMa8ahl.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__CTscLEU__osCaStMS.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__J8Tk1UrTxkDN5LhL.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__szWyQmccUrvL2v6J.png)

the file .env example you must replace it with .env where the environment variables are with yours.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__pSx0mQ7FGW8j3RjM.png)

The docker-compose.yml file can be replaced so that the orchestrator is kubernetes (locally it is more practical to orchestrate the API this way)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__zTqX6A__AoEspRzxp.png)

The dockerfile file is the minimum that the api requires to work and as you can see, they are very simple steps easy to replicate.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0____YbrjslYvct8HrfA.png)

The main.go file contains the largest amount of application logic  
Dependencies

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__nJ7iVZhWY4JXjdp__.png)

Check for an .env file for environment variables.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__AjpRGd71TeMeox6c.png)

Setting the environment variables

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__HESc__DVtTGtA4FoH.png)

api routes

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__tDjSbEcgxcV4uuPy.png)

database initialization

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__IqmAHZJreiAeIOn2.png)

principal function

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__zgz8Uvjgp7s__pEiz.png)

Source Code

[**devjaime/golangrest**  
_GitHub is home to over 50 million developers working together to host and review code, manage projects, and build…_github.com](https://github.com/devjaime/golangrest "https://github.com/devjaime/golangrest")[](https://github.com/devjaime/golangrest)

I hope this first approach helps you in your projects. (and in the future I will try to make a more detailed video). Any questions I will try to answer more often I even know that in old posts there are questions that I have not answered so I will try to update myself.

[**Donate to devjaime**  
_Help support devjaime by donating or sharing with your friends._www.paypal.com](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S "https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S")[](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S)