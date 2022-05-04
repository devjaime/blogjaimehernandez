---
title: 'Día 3: Arquitectura Flutter y configuración del proyecto'
description: >-
  Bienvenido al día 3, donde aprenderas sobre la arquitectura del marco Flutter
  y verá cómo configurar un proyecto Flutter con algunas…
date: '2021-03-23T12:03:09.639Z'
categories: []
keywords: []
slug: >-
  /@devjaime/d%C3%ADa-3-arquitectura-flutter-y-configuraci%C3%B3n-del-proyecto-9307aa98b4fe
---

Bienvenido al día 3, donde aprenderas sobre la arquitectura del marco Flutter y verá cómo configurar un proyecto Flutter con algunas buenas reglas de linter.

### Arquitectura Flutter

Ya sea que haya creado una aplicación Flutter antes o no, es útil obtener una descripción general de alto nivel de la arquitectura Flutter desde un punto de vista conceptual.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__Zne8__v9BhEYBuQNy.jpg)

Flutter usa su propio motor de renderizado llamado Skia. Está escrito en C/C ++ y proporciona API de bajo nivel para renderizado. Cuando escribes aplicaciones en Flutter, su código no llama directamente a las API del motor Flutter. Más bien, utiliza un conjunto de API de alto nivel proporcionadas por el **marco** Flutter .

Por diseño, **Flutter controla cada píxel que se dibuja en la pantalla** . El framework de Flutter ofrece un amplio conjunto de componentes de IU (llamados widgets) que se asemejan mucho a los controles de IU nativos en iOS y Android.

### Modelo de programación declarativa

Flutter usa un modelo de programación declarativo.

Los widgets de Flutter definen su IU anulando el método **build()** , que es una función que convierte el estado en IU:

**UI = f(state)**

Los widgets pequeños y de un solo propósito se **componen** juntos para crear otros más complejos y especializados que representan la interfaz de usuario de su aplicación. Por lo tanto, toda la aplicación está representada por un **árbol de widgets** .

Por ejemplo, así es como se ve el árbol de widgets para la aplicación de contador Flutter predeterminada:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__iAmiW7__uEolAjGJm.jpg)

​

En la próxima lección sobre gestión de estados, hablaremos sobre cómo reconstruir la interfaz de usuario cuando algunos estados **cambian** y qué técnicas están disponibles para hacerlo.

Pero por ahora esta es toda la teoría que necesita. Y si quieres una explicación más detallada de la arquitectura de Flutter, no hay mejor lugar que la documentación oficial:

*   [Descripción de la arquitectura flutter](https://flutter.dev/docs/resources/architectural-overview)

Esta es una lectura larga, pero vale la pena si quieres entender cómo funciona Flutter bajo el capó.

Pasemos a algo más práctico.

### Configuración del proyecto

Cuando creas un nuevo proyecto de Flutter, se generarán algunos archivos y carpetas.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__ruKZk537QYa7g2F0.jpg)

​

El archivo más importante se llama **pubspec.yaml** . Este se usa para especificar las **dependencias de** su aplicación . Estos recursos explican cómo funciona este archivo y cómo usarlo para instalar paquetes:

*   [El archivo pubspec](https://dart.dev/tools/pub/pubspec)
*   [El uso de paquetes](https://flutter.dev/docs/development/packages-and-plugins/using-packages)

Además de esto, recomiendo encarecidamente agregar un archivo **analysis\_options.yaml** . Esto se puede usar para especificar **reglas de linter** y habilitar advertencias y errores adicionales para su proyecto. Aquí hay una guía detallada al respecto:

*   [Primeros pasos: Creación de su proyecto](https://dash-overflow.net/articles/getting_started/) implementando reglas de linter

En particular, lea la sección “Cómo administrar sus reglas de linter fácilmente” al final. Esto explica cómo crear un conjunto de reglas limpias y fáciles de mantener que puede modificar en sus aplicaciones.

Puede descargar un archivo **analysis\_options.yaml** “oficial” [desde aquí](https://dart-lang.github.io/linter/lints/options/options.html) y también ver una [lista de todas las reglas admitidas con explicaciones](https://dart-lang.github.io/linter/lints/index.html).

### Reto diario

Agregue un archivo **analysis\_options.yaml** a su proyecto y escribe un tweet al respecto.

[**Donate to devjaime**  
_Help support devjaime by donating or sharing with your friends._www.paypal.com](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S "https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S")[](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__AoPJYe3CEt6kH81S.jpg)