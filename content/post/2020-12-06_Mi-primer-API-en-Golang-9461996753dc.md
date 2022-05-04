---
title: Mi primer API en Golang
description: >-
  Realice una primer “API” en golang muy simple la cual me gustaría compartir
  (lo más probable es que no cuente con las mejores practicas…
date: '2020-12-06T08:16:47.893Z'
categories: []
keywords: []
slug: /@devjaime/mi-primer-api-en-golang-9461996753dc
---

Realice una primer “API” en golang muy simple la cual me gustaría compartir (lo más probable es que no cuente con las mejores practicas pero por lo menos tiene los requisitos mínimos para escalar en algo más evolucionado).

Código fuente

[https://github.com/devjaime/golangrest](https://github.com/devjaime/golangrest)

Lo primero que quería era listar los requerimientos de mi API para que sea completamente funcional para lo que necesitaba.

1.  \- Debía ser capaz de conectarse a través de un ORM a la base de datos ya que lo más probable es que esta cambie en un futuro ( de referencia es azure sql en este momento).
2.  \- Debe ser capaz de levantar en un contenedor y pasar por un proceso de integración continua para estar como una api publica
3.  .- Debe ser escalable en el tiempo en cuanto a cantidad de usuario y peticiones concurrentes.

Diagrama de diseño de la API

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__V1mFb0wgIRT2RYPjATAk4Q.png)

No quisiera entrar más en detalles pero eso es todo lo que quería implementar para la API

Lo primero que investigue fue la documentación de Golang [https://golang.org/](https://golang.org/) donde lo primero es seguir muy bien las instrucciones de instalación de golang en tu maquina ya sea windows o mac [https://golang.org/dl/](https://golang.org/dl/)

En mi caso cuento con mac y lo que realice fue ver si existía instalación a traves de homebrew y lo realice siguiendo unos pasos muy simples, sacados del siguiente tutorial

[**Install Go on Mac (with homebrew)**  
_Install Brew (skip if you already did)_medium.com](https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5 "https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5")[](https://medium.com/@jimkang/install-go-on-mac-with-homebrew-5fa421fc55f5)

Con go versión pueden ver si realmente funciono la instalación y que versión tienen de go

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____YhAHN1PmULyEre102HmGg.png)

Otro recurso practico que me ayudo para levantar mi primer API fue este

[**FaztWeb| Curso Completo de Golang REST API CRUD desde cero, para principiantes**  
_En este ejemplo práctico de Go aprenderemos a crear una REST API desde cero usando Mux y conceptos basicos de este…_www.faztweb.com](https://www.faztweb.com/curso/golang-restapi-crud "https://www.faztweb.com/curso/golang-restapi-crud")[](https://www.faztweb.com/curso/golang-restapi-crud)

Sin embargo faltaban conceptos como ocupar un ORM y que ORM maneja Golang

De estos “googleando” llegue a [https://gorm.io/index.html](https://gorm.io/index.html) que parecía una muy buena opción.

Instalación en tu proyecto

go get -u gorm.io/gorm

Ahora dependiendo de la base de datos a ocupar, deberas buscar un dialecto

Puedes ver las distintas conexiones en

[**Connecting to a Database**  
_GORM officially supports databases MySQL, PostgreSQL, SQLite, SQL Server NOTE: To handle time.Time correctly, you need…_gorm.io](https://gorm.io/docs/connecting_to_the_database.html "https://gorm.io/docs/connecting_to_the_database.html")[](https://gorm.io/docs/connecting_to_the_database.html)

Otra dependencia importante de instalar es Fiber

**Fiber** es un **marco web** inspirado en [Express](https://github.com/expressjs/express) construido sobre [Fasthttp](https://github.com/valyala/fasthttp) , el motor HTTP **más rápido** para [Go](https://golang.org/doc/) . Diseñado para **facilitar las** cosas para **un** desarrollo **rápido** con **cero asignación de memoria** y **rendimiento** en mente.

instalación

go get github.com/gofiber/fiber/v2

Luego de eso te explicare mi estructura simple de la api

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__77RNJT1iD47BLWOJo0kqrg.png)

En donde la carpeta circleci, es la integración continua y los pasos para poder subir mi api a un servidor.

Puedes ver este video para darte una idea de lo que realizo en ese archivo

El resultado es algo como esto

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zM95A78YHlxViOvqzgVwEA.png)

En .ssh están las claves privadas y publicas para subir el proyecto, que es algo como esto.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__CTgAtWP__hnOUcWVfUrzycw.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__DS8vVnf__sF5g0ctDISP2yg.png)

Por supuesto debes crear las tuyas

Terminal (también en el video de referencia aparece muy bien explicado)

ssh-keygen -t rsa

*   En database el archivo database.go contiene el paquete de conexión

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__k8D57u1zeEacXbR5nnL7qQ.png)

y product es el modelo que consultara la base de datos con sus respectivos verbos.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__dvAX0hrOgSDHdXCX__33Pkg.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__XDFp7H0mEsgvwo2WGLf0kQ.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__mETS9kOSupjsNKH3oh4__gA.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__JP5NiWUOm9Kmf9MbBRaCKA.png)

el archivo .envexample debes reemplazarlo por .env donde estarán las variables de entorno con las tuyas.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__mQEPeGA0htmG__xgRZey__jg.png)

El archivo docker-compose.yml puede ser reemplazado para que el orquestador sea kubernetes (de forma local es más practico orquestar la API de esta forma)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__7mHcaxT7wQ__j0A9OIHkQIw.png)

El archivo dockerfile es lo mínimo que requiere la api para funcionar y como se ve son pasos muy sencillos facil de replicar

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Wa7C69fzYlknnHxOOsUxJA.png)

El archivo main.go contiene la mayor cantidad de lógica de la aplicación

Dependencias

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zgmWcPQk7pmVo__81z5WTPw.png)

Revisa la existencia de un archivo .env para las variables de entorno.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Pup96T1el8LEywyhDNn__LA.png)

Seteo de las variables de entorno

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__y8r6rIfryA6vsmaMi__I7vw.png)

rutas de la api

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__LVb2Rrw0m49lCHQZ2zFgIg.png)

inicialización de la base de datos

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__NGDUqx9e4bTPM6xFmTpCzg.png)

función principal

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__F0P5XdjC8__xs__S6b732Aqg.png)

Código fuente

[**devjaime/golangrest**  
_GitHub is home to over 50 million developers working together to host and review code, manage projects, and build…_github.com](https://github.com/devjaime/golangrest "https://github.com/devjaime/golangrest")[](https://github.com/devjaime/golangrest)

Espero este primer acercamiento te sirva en tus proyectos. (y en el futuro intentare realizar un video más detallado). Cualquier duda intentare contestar más seguido inclusive se que en post antiguos existen preguntas que no he contestado por lo cual intentare ponerme al día.

[**Donate to devjaime**  
_Help support devjaime by donating or sharing with your friends._www.paypal.com](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S "https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S")[](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S)