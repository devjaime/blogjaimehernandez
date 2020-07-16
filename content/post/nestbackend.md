+++
title = "Primera aproximación NestJS como Framework de desarrollo Backend"
description = "Este es una serie de post sobre Nest.js, Nest.js es un Framework web moderno construido en un servidor Node.js Express.(aunque tambien se puede cambiar) Con este puede dar a sus aplicaciones una base de código organizada y una estructura bien definida para trabajar en grupos de desarrollo medianos utilizando buenas prácticas de codificación."
tags = [
    "nestjs",
    "nodejs",
    "backend",
]
date = 2020-07-15T02:13:50Z
author = "Jaime Hernandez"
+++

Nest.js es un Framework web moderno construido en un servidor Node.js Express.(aunque tambien se puede cambiar) Con este puede dar a sus aplicaciones una base de código organizada y una estructura bien definida para trabajar en grupos de desarrollo medianos utilizando buenas prácticas de codificación. 
[Sitio Oficial] (https://nestjs.com/)
* Nest (NestJS) es un framework para crear aplicaciones del lado del servidor Node.js escalables y eficientes. Utiliza JavaScript, es totalmente compatible con TypeScript (aún permite a los desarrolladores codificar en JavaScript puro o como lo llaman vanilla javascript) y combina elementos de OOP (Programación Orientada a Objetos), FP (Programación Funcional) y FRP (Programación Reactiva Funcional).

1.- Programación orientada a objetos (OOP): un modelo que se basa en objetos en lugar de acciones y reutilización en lugar de funcionalidad de nicho.

2.- Programación funcional (FP): El diseño de una funcionalidad determinada que no depende de estados globales, es decir. una función f (x) devuelve el mismo resultado cada vez para algunos parámetros establecidos que no cambian.

3.- Programación funcional reactiva (FRP): una extensión de FP desde arriba y programación reactiva. La programación funcional reactiva es, en esencia, la programación funcional que representa un flujo a través del tiempo. Es útil en aplicaciones como UI, simulaciones, robótica y otras aplicaciones donde la respuesta exacta para un período de tiempo específico puede diferir de la de otro período de tiempo.
* En otra ocación abordare sobre estos conceptos.

## Instalación

Puede instalar a traves de los siguientes comandos

```terminal 
npm install -g @nestjs/cli
```
O a traves de docker

```terminal 
docker pull nestjs/cli:[version]
```

Se puede generar un nuevo proyecto Nest con el comando:

```terminal 
nest new [nombre-proyecto]
```

Este proceso creará el proyecto a partir de un typescript-starter y le pedirá el nombre, descripcion, version (por defecto 0.0.0), y autor(esto sería tu nombre). Una vez finalizado este proceso, tendrá un proyecto Nest completamente configurado con las dependencias instaladas en su node_modules (carpeta). El comando [new] también le preguntará qué gestor de paquetes desea utilizar,  [yarn] o [npm].

El comando más utilizado desde la CLI será el [generate] (g), esto le permitirá crear nuevos controllers, modules, services o cualquier otro componente que soporta Nest. La lista de componentes disponibles es:

1. class (cl)
2. controller (co)
3. decorator (d)
4. exception (e)
5. filter (f)
6. gateway (ga)
7. guard (gu)
8. interceptor (i)
9. middleware (mi)
10. module (mo)
11. pipe (pi)
12. provider (pr)
13. service (s)

Tenga en cuenta que la cadena entre paréntesis es el alias de ese comando específico. Esto significa que en lugar de escribir:
```terminal 
nest generate service [nombre-servicio]
```
En su consola, puede ingresar:
```terminal
nest g s [nombre-servicio]
```

Por último, Nest CLI proporciona el comando info (i) para mostrar información sobre su proyecto. Este comando generará información similar a la siguiente:

{{< figure src="/img/nestinfo.png" alt="nest info">}}

# Continuara.....