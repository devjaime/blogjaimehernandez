---
title: Día 4 Geolocation XamarinForms con Api XamarinEssentials
description: >-
  La clase de Geolocalización proporciona un API para recuperar las coordenadas
  actuales de geolocalización del dispositivo.
date: '2019-04-20T23:38:12.317Z'
categories: []
keywords: []
slug: >-
  /@devjaime/d%C3%ADa-4-geolocation-xamarinforms-con-api-xamarinessentials-fe79dbb3c9e5
---

La clase de Geolocalización proporciona un API para recuperar las coordenadas actuales de geolocalización del dispositivo.

Para empezar con este proyecto abriremos nuestro Visual Studio

Crearemos un nuevo proyecto

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__jXlA4RMUKE2z12HPR26IWg.png)

Seleccionaremos Aplicación Móvil (Xamarin.Forms)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__O6mfYAuUqbLhJg9h5eb__Tw.png)

Crearemos nuestra solución Geolocalización

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ngxma5dj2s__7nSOZFK7RoQ.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__4f__RyNU3__qDvQj__YTwRczw.png)

Una vez creado nuestro proyecto, agregaremos el paquete nuGet Xamarin.Essentials como se muestra a continuación.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__AF2Klsyd5g2adCQfkJh__5g.png)

El link de nuestro patrón de diseño y al igual que en post anteriores lo dejare acá

[**MVVM.rar**  
_Edit description_drive.google.com](https://drive.google.com/open?id=1QwNzT8fc5O8d8X2gmyvD45kRRdzB8eMA "https://drive.google.com/open?id=1QwNzT8fc5O8d8X2gmyvD45kRRdzB8eMA")[](https://drive.google.com/open?id=1QwNzT8fc5O8d8X2gmyvD45kRRdzB8eMA)

Solo deben copiarlo al proyecto como se muestra a continuación.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__XWb__39kJfThyMgss9__mvCw.png)

Una vez realizado esto crearemos un page llamado GeolocationPage.xaml, (esto en nuestra carpeta View).

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__CIK7QoZCE7ktsGIX4xjjZw.png)

Luego en nuestra carpeta ViewModel crearemos la clase GeolocationViewModel

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__bdZ10oasX7J1mF__We6LhMg.png)

Nuestra Vista GeolocationPage.xaml tendrá el siguiente código

Donde la información obtenida sera la siguiente:

Última ubicación conocida.

Ubicación actual.

La exactitud

Nuestra clase de la vista tendrá el siguiente código

y nuestro ViewModel tendrá el siguiente código.

También debemos considerar los permisos para nuestra plataforma de destino en este caso Android

Archivo AndroidManifiest

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__YaOJViOdUbnAX4tUSGfLvA.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__WRhAEb5OCgjxNEX1vrRsng.png)

A continuación los permisos para que los incluyas.

en nuestro app.xaml.cs apunta a nuestra pagina creada de la siguiente forma.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__3PS9TQ9QqwNAS7AQfjuW8g.png)

Ahora podrás ejecutar la aplicación, como veras te aparecerán las coordenadas de tu ubicación actual (en este caso aparecen las de mi casa).

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__06RbuyXBzWdVkHixaE2izQ.png)

En el próximo post y debido a las cosas que se pueden hacer con esta librería intentare realizar algo más llamativo relacionado con mapas.

Se me olvidaba!! el código fuente de la app lo pueden descargar desde

[**devjaime/geolocalizacion**  
_obtiene la localización actual en xamarin forms con Xamarin Essentials - devjaime/geolocalizacion_github.com](https://github.com/devjaime/geolocalizacion "https://github.com/devjaime/geolocalizacion")[](https://github.com/devjaime/geolocalizacion)