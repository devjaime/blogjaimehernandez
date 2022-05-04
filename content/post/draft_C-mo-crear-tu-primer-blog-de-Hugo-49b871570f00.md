---
title: Cómo crear tu primer blog de Hugo
description: >-
  Hugo es una gran herramienta para usar si quieres comenzar un blog. Hugo es
  uno de los generadores de sitios estáticos de código abierto…
date: ''
categories: []
keywords: []
slug: ''
---

Hugo es una gran herramienta para usar si quieres comenzar un blog. Hugo es uno de los generadores de sitios estáticos de código abierto más populares. Con su increíble velocidad y flexibilidad, Hugo hace que la creación de sitios web sea divertida nuevamente. \[Sitio oficial\] ([https://gohugo.io/](https://gohugo.io/))

Hugo es extremadamente sencillo, esto es algo muy positivo. Como desarrollador, estoy tentado a modificar las cosas aquí y allá todo el tiempo. No hay tecnología sofisticada subyacente a Hugo. Está construido con Go, pero eso no significa que quiera sumergirme en lo interno de Hugo y cambiar cómo funciona.

Y no muestra nada interesante o de próxima generación, como suelen hacer muchos frameworks de JavaScript.

Por lo tanto, me da mucho tiempo para hacer lo que es realmente útil cuando trabajo en un blog: escribir contenido . Me concentro en el contenido, no en el contenedor de contenido.

Dicho esto, Hugo es bastante flexible . Comencé mi propio blog con un tema de código abierto, luego lo cambié por completo. A veces quiero hacer cosas en mi sitio web que están fuera del alcance de un blog simple, y Hugo me permite crear esas cosas.

Finalmente, otra razón por la que ocupo Hugo es que es rápido . ¿Por qué? Primero, tiene Go en el núcleo, que se sabe que es un lenguaje muy rápido. Y en el ecosistema Go, no hay un concepto de dependencias de 100 megabytes. Las cosas están hechas para ser lo más rápido posible. Además, Hugo no necesita hacer algunas de las cosas sofisticadas que se necesitan al usar tecnología sofisticada.

De todos modos, basta de palabras.

Hugo es increíble, especialmente si eres un desarrollador y estás dispuesto a escribir en Markdown. Las personas no tecnológicas pueden simplemente negarse a usar Markdown, y es perfectamente comprensible.

Además, debe estar preparado para un flujo de trabajo centrado en Git para que las cosas realmente hagan clic.

Este es el proceso para escribir un blog:

*   escribe una publicación usando Markdown,
*   luego confirme sus cambios en un repositorio de Git, más comúnmente en GitHub,
*   y luego, alguna tecnología de despliegue automatico implementa los cambios en el servidor que aloja el sitio.

### Hospedar un sitio web de Hugo

###   

Un blog de Hugo es completamente estático . Esto significa que no necesita alojar su propio servidor o utilizar un servicio especial para ello.

Netlify, Now y GitHub Pages son tres excelentes lugares donde puedes alojar un blog de Hugo de forma gratuita.

El único costo es el que debe pagar por el nombre de dominio..

Para el ejemplo en cuestión ocuparemos Netlify.

### Instalar Hugo

###   

Para instalar Hugo en macOS, ejecute desde su terminal

```
brew install hugo
```

  

Copy

Para Windows y Linux, consulte la guía de instalación oficial por tener mac esta guía esta realizada en este entorno.

Crea un sitio Hugo Una vez que Hugo esté instalado, puede crear un sitio Hugo ejecutando

```
hugo new site myblog
```

  

Copy

Este comando debe ser creado en la carpeta raiz ya que el subdirectorio quedara como myblog que es donde ejecutara los comandos de hugo.

subire video explicativo