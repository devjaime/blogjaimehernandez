---
title: Diseño y desarrollo unidos en una herramienta para Flutter una idea genial!
description: >-
  Antes de empezar quisiera mencionar al autor de este proyecto Aloïs Deniel
  quien es desarrollador Flutter y Xamarin.
date: '2018-08-04T07:01:23.449Z'
categories: []
keywords: []
slug: >-
  /@devjaime/dise%C3%B1o-y-desarrollo-unidos-en-una-herramienta-para-flutter-una-idea-genial-706fb5977d7c
---

Antes de empezar quisiera mencionar al autor de este proyecto [Aloïs Deniel](https://twitter.com/aloisdeniel) quien es desarrollador Flutter y Xamarin.

y la idea original la pueden encontrar en:

[**From design to code, let's think about it**  
_If you know me a little you already know that I always think on how we could be more productive as a whole software…_aloisdeniel.github.io](https://aloisdeniel.github.io/introducing-figma-to-flutter/ "https://aloisdeniel.github.io/introducing-figma-to-flutter/")[](https://aloisdeniel.github.io/introducing-figma-to-flutter/)

Este es una difusión de su idea para las comunidad en español.

Todos los desarrolladores de software estamos constantemente pensando en como ser más productivos como equipo de software completo (con ayuda de toda nuestro equipo de trabajo). Cuando el diseñador se reúne con el desarrollador siempre existe un limite de ideas que el desarrollador puede llevar a cabo en sus proyectos y existe situaciones en que el trabajo del diseñador se pierde en la etapa de implementación del desarrollador.

Este proceso se centra en el flujo de trabajo del diseñador UI / UX hasta el desarrollador.

### Un proceso típico de desarrollo móvil hoy

El diseñador crea el contenido visual y lo exporta para los desarrolladores. Para cada plataforma, el desarrollador estudiará los recursos de diseño y los adaptará a su plataforma favorita, con las herramientas que conoce. Cada vez que el diseñador produce contenido nuevo (o modifica uno existente), cada desarrollador deberá aplicarlo a su plataforma.

Con respecto a la lógica comercial, los desarrolladores deberán asegurarse de tener especificaciones claras para no presentar comportamientos diferentes.

### Desarrollo unificado

Un primer paso natural sería unificar las ramas específicas de la plataforma. Para lograr esto, puede apostar por una solución multiplataforma.

De acuerdo, ahora tenemos una cadena de herramientas mucho menos específica y menos problemas específicos potenciales: un proceso general global más simple. ¡Estupendo!

### Y si … ?

Pero estoy seguro de que notó que las primeras tareas del desarrollador son adaptar los recursos del diseñador a su plataforma. Esas son tareas realmente largas en las que el desarrollador debe comprender lo que pensó el diseñador cuando creó el contenido.

Solo imagine si los desarrolladores pueden usar directamente el contenido del diseñador como componentes en su código.

### Presentando Figma a Flutter

Figma es una herramienta de diseño ([Figma](http://www.figma.com/) ) funciona en todas partes, es simple, colaborativa.

El software se basa en tecnologías web modernas (¡WebAssembly!) Y, como bonificación, ofrece API abierta para cualquiera.

### La creacion de [Aloïs Deniel](https://twitter.com/aloisdeniel) Figma a Flutter

Alois Deniel trabaja en el desarrollo de una pequeña herramienta que convierte archivos Figma en widgets Flutter (código Dart). Lo cual une la parte principal **del flujo de trabajo del diseñador UI / UX hasta el desarrollador.**

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__6XyWxlfBimWqiqJy.png)

Aún está en desarrollo activo, pero pueden probarlo en su navegador aquí: [Figma-to-Flutter](http://aloisdeniel.github.com/figma-to-flutter) .

### Aún muy experimental

> Todo esto esta en etapa de “idea” experimental y en desarrollo activo. El autor enfatiza “Si tuviera acceso al código fuente del renderizado de Figma, hubiera sido mucho más fácil y rápido ( **si un empleado de Figma lo leyera y pudiera compartir el algoritmo, ¡sería increíble!** ), Pero tenga en cuenta que toda la lógica de renderizado tiene ingeniería inversa , ¡entonces experimentarás muchas inconsistencias!”