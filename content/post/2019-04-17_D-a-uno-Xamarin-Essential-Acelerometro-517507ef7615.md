---
title: Día uno Xamarin Essential Acelerometro
description: Para empezar el día de hoy debemos considerar lo siguiente
date: '2019-04-17T05:29:27.865Z'
categories: []
keywords: []
slug: /@devjaime/d%C3%ADa-uno-xamarin-essential-acelerometro-517507ef7615
---

Para empezar el día de hoy debemos considerar lo siguiente

Crear nuestro proyecto Xamarin, este proyecto sera creada en la nueva versión de Visual Studio 2019 si aun no lo tienen lo pueden descargar desde el siguiente link

[**Descargas | IDE, Code y Team Foundation Server | Visual Studio**  
_Descargas Descarga gratuita Descargar versión preliminar Evaluación gratuita Descargar versión preliminar Evaluación…_visualstudio.microsoft.com](https://visualstudio.microsoft.com/es/downloads/ "https://visualstudio.microsoft.com/es/downloads/")[](https://visualstudio.microsoft.com/es/downloads/)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__f3yOSezBo__HI1mi0KXqX7w.png)

Luego de lo anterior selecciona Xamarin Forms que es la solución múltiplataforma que implementaremos

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__cRfPXghdFdLTCY2oU8isjQ.png)

Identifica un nombre de solución y selecciona el botón Crear

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ToMebxjzhF2v1OB664MH5Q.png)

Para este ejemplo seleccionaremos una plantilla en blanco y seleccionaremos como plataforma de destino Android y IOS

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__4W0hsJNoen__hZU3WXDkiEg.png)

Realizaremos click derecho en la solución para abrir administración de paquetes nuGet, en donde seleccionaremos Xamarin.Essentials, este instalaremos la versión estable más reciente.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__fdVW__kg__IZbsudXUfFnhAw.png)

Confirmaremos los paquetes nuGet instalados.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__XTj9cLbczi1q8lhSK1gSVg.png)

En nuestra solución crearemos 3 carpetas para nuestro patrón MVVM

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__tcOBbqorqLTpvqaTB4pJyw.png)

Crearemos una pagina de contenido llamada AccelerometerPage.xaml

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__txh7FiyfawOncD7LoNf60Q.png)

En la carpeta ViewModel deberás crear una clase llamada AccelerometerViewModel.cs

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zBPyk__rjk8Nv7X0uzvU59g.png)

También agregaremos la clase base llamada BaseViewModel.cs

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__OI42I1EvdzQSiDjQhhz11Q.png)

y la clase ObservableObjet que nos servirá para notificar nuestras propiedades a la vista.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__AQdjghuAmvjonwkAMG8GJg.png)

Las 3 clases creadas a continuación para que copien su código dentro de ellas

AcelerómetroViewModel.cs

BaseViewModel.cs

ObservableObject.cs

Crearemos una vista llamada BasePage.cs

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__BwWV2i0bY6nCKm7G77Ofkg.png)

El código de este a continuación

Nuestro xaml tendrá la siguiente estructura

Una vez implementado esta vista probaremos nuestra aplicación.

Para esto ocupo un dispositivo Android (Dispositivo físico) .

La visualización final de esta parte a continuación

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__D4Ws2ceJOrkyKjC4QXHedQ.png)

El código de esta aplicación lo puedes encontrar en:

[**devjaime / acelerometro acelerometro**  
_Xamarin Forms Utilizando Xamarin Essentials — devjaime / Acelerometro_ github.com](https://github.com/devjaime/Acelerometro "https://github.com/devjaime/Acelerometro")[](https://github.com/devjaime/Acelerometro)