---
title: Aplicación de Farmacias de turno con XamarinForms
description: >-
  En este nuevo post voy a realizar una aplicación de farmacias de turno, las
  farmacias de turno serán localizadas en mi aplicación por mi…
date: ''
categories: []
keywords: []
slug: ''
---

En este nuevo post voy a realizar una aplicación de farmacias de turno, las farmacias de turno serán localizadas en mi aplicación por mi posición georeferencial para desplegar las que me quedan más cercas a mi posición para esto empezamos con lo siguiente:

Api que consumiremos

[https://farmanet.minsal.cl/index.php/ws/getLocalesTurnos](https://farmanet.minsal.cl/index.php/ws/getLocalesTurnos)

Crearemos un nuevo proyecto llamado FarmaciasTurno

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__kynPiStJC0wYIW9N5DB__Xw.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__l1ySrYlmDy3__4NX7EuuvCg.png)

  

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__PfEu4b33aLgafam0zAwCGA.png)

  

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__J1Z6rGOLCd2YNyKgFsAUaA.png)

  

Para esto igual que en post anteriores crearemos nuestro Patrón MVVM he instalaremos xamarin.essentials

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__33G0jYmcyJZU__fUil__uA6A.png)

Dentro de model crearemos una nueva clase llamada FarmaciasData

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__oHJQwCWM5a__2WAjHARGIWw.png)

Eliminamos la clase dejando solo el namespace

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__m3tZfmRpyFaGSGpqcefc2w.png)

Seleccionamos todo el json de nuestra pagina de farmacias de turno (ctrl + A) y luego (ctrl + C) para copiar

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__WoYfd0MDb0AIbwp4oECB__A.png)

  

Luego nos vamos a Editar → Pegado especial → Pegar Json como clases

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__y6__f33W9h4t2HjSR09rqUg.png)

Nuestra clase deberá quedar de la siguiente manera

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__I4IlhT__dCwDGIsaJ2DOrAg.png)

Renombramos nuestra clase a FarmaciasData

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__IcFDeM7etZeMr8aQFWQ4lQ.png)

Luego crearemos en nuestro modelo la clase MainPageViewModel.cs 

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__osp1iDT2u5dGquNL9iy75A.png)

  

  

Debemos instalar este paquete nuGet

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__U1N6JlGirWFftegDM3GV8Q.png)

  

  

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__8tEfFr7eANV7hQNIcz__8hg.png)