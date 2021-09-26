+++
title = "The Twelve Factor App"
description = "Aplicaciones de doce Factores The Twleve Factor App"
tags = [
    "arquitectura",
    "desarrollo",
    "patrones",
]
date = 2021-09-26T02:13:50Z
author = "Jaime Hernandez"
+++

# Aplicaciones de doce Factores

## Introducción
En este post quisiera compartir lo que encuentro relevante de las apliaciones de 12 factores, aunque puedes encontrar su descripción completa en la pagina https://12factor.net/ (en mi caso lo tomo como apuntes y recordatorio de como se debiera estructurar una aplicación actualmente).

### Que significa una aplicación de 12 factores
* En la era moderna, el software se entrega comúnmente como un servicio: llamadas aplicaciones web o software como servicio . La aplicación de doce factores es una metodología para crear aplicaciones de software como servicio.

* La metodología de doce factores (12 Factor) fue creada en el año 2012 por varios desarrolladores de aplicaciones en Heroku y consiste en un enfoque o filosofía de trabajo en la que se deben considerar doce principios para desarrollar aplicaciones en la nube (Cloud Computing Apps). A través de estos 12 puntos clave se facilita la construcción correcta y el desarrollo óptimo de un servicio en la nube.


## Los Doce Factores 

### I. Base de código (Codebase)
*  Seguimiento de una base de código en el control de revisiones, muchas implementaciones
### II. Dependencias (Dependencies)
* Declarar y aislar dependencias explícitamente
### III. Configuración (Config)
* Almacenar la configuración en el entorno
### IV. Servicios de respaldo (Backing services)
* Trate los servicios de respaldo como recursos adjuntos
### V. Construir, lanzar, ejecutar (Build, release, run)
* Etapas de construcción y ejecución estrictamente separadas
### VI. Procesos (Process)
* Ejecute la aplicación como uno o más procesos sin estado
### VII. Enlace de puerto (Port binding)
* Exportar servicios a través de la vinculación de puertos
### VIII. Concurrencia (Concurrency)
* Escalar horizontalmente a través del modelo de proceso
### IX. Desechabilidad (Disposability)
* Maximice la solidez con un inicio rápido y un apagado elegante
### X. Paridad desarrollo / producción (Dev/prod parity)
* Mantenga el desarrollo, la puesta en escena y la producción lo más similar posible
### XI. Registros (Logs)
* Trate los registros como transmisiones de eventos
### XII. Procesos de administración (Admin processes)
* Ejecute tareas de administración / gestión como procesos únicos