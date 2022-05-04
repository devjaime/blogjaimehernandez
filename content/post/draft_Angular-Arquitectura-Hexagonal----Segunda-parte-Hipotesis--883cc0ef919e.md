---
title: 'Angular Arquitectura Hexagonal : {Segunda parte Hipotesis}'
description: >-
  Después de haber visto en teoría cómo se puede estructurar un proyecto de
  aplicación web según la Arquitectura Limpia, veamos cómo podemos…
date: ''
categories: []
keywords: []
slug: ''
---

Después de haber visto en teoría cómo se puede estructurar un proyecto de aplicación web según la Arquitectura Limpia, veamos cómo podemos implementar este patrón en la práctica. Si te lshas perdido el artículo de introducción, [puede encontrarlo aquí](https://devjaime.medium.com/angular-arquitectura-hexagonal-hipotesis-a2cfa0b94a07) . Revisaremos todas las capas y veremos qué se implementa allí. Encontrarás el **código completo** [**aquí**](https://github.com/im-a-giraffe/angular-clean-architecture) **.**

La aplicación de muestra es un calendario de cumpleaños para elefantes. Se mantiene muy simple para aclarar el uso de Arquitectura limpia. Toma datos de una API o un MockRepository incluido dentro de la aplicación y muestra todos los elefantes y sus cumpleaños en una tabla.

### Estructura del proyecto

Un proyecto Angular podría estructurarse de la siguiente manera, partiendo de la estructura conocida generada por el angular-cli.