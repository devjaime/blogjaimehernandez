---
title: Día 3 Geocoding XamarinForms con Api XamarinEssentials
description: >-
  En este tercer día y siguiendo los artículos anteriores, comentare mi
  experiencia con Geocoding de XamarinEssentials.
date: '2019-04-19T13:48:22.659Z'
categories: []
keywords: []
slug: >-
  /@devjaime/d%C3%ADa-3-geocoding-xamarinforms-con-api-xamarinessentials-f8b8b8f37c5d
---

En este tercer día y siguiendo los artículos anteriores, comentare mi experiencia con Geocoding de XamarinEssentials.

La clase Geocoding proporciona una API para geocodificar una dirección de posición en coordenadas posicionales y revertir las coordenadas de geocodificación en una dirección de posición.

Tal como en los 2 post anteriores abriremos nuestro Visual Studio y crearemos un nuevo proyecto de tipo XamarinForms llamado “Geocodificacion”

Seleccionaremos una plantilla en blanco, seleccionaremos nuestras plataformas de destino y presionamos el botón crear.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__5FvGAXXBR5mxgTXXx6m7JA.png)

Luego de lo anterior seleccionaremos Administración de paquetes Nuget y y presionamos en instalar Xamarin.Essentials.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__kMQm00o6XfpRDvdRZr__bng.png)

Luego de lo anterior crearas las siguientes carpetas para conservar nuestro patrón de diseño MVVM, (Si has visto los post anteriores te darás cuenta que es exactamente la misma estructura) por lo cual te dejo un enlace con las carpetas para que puedas copiar este modelo y así no tengas que crear una por una.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__7shj5AupIi7S2tAwtn90yw.png)

[**Geocodificacion.rar**  
_EMMVM Geocodingn_drive.google.com](https://drive.google.com/open?id=1Y5J6wtQoc0PTgtXVMf3fU8ptkuAxXih8 "https://drive.google.com/open?id=1Y5J6wtQoc0PTgtXVMf3fU8ptkuAxXih8")[](https://drive.google.com/open?id=1Y5J6wtQoc0PTgtXVMf3fU8ptkuAxXih8)

Luego en nuestra carpeta View creamos una nueva Page llamada “GeocodingPage.xaml”

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__7f0FJYnMO8MC53Vnk8k0zA.png)

y en nuestra carpeta ViewModel creamos en el enlace llamado “GeocodingViewModel”

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__9__6FzQGoQqFU7SCXvRu6tA.png)

El código de nuestra View “GeocodingPage.xaml” sera el siguiente.

En la clase deberás copiar lo siguiente.

En nuestro ViewModel deberes escribir el siguiente código.

y por ultimo deberás fijarte que inicializas vista desde el app principal

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__VgZ2LBPRPbgLxavhQkfpWQ.png)

Una cosa importante es siempre fijarte en los permisos dependiendo de nuestro dispositivo, en este caso como estoy probando con un dispositivo Android, deberás realizar lo siguiente.

En el archivo AndroidManifiest de nuestro proyecto Android agrega lo siguiente

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zvGiKzCEPPTjApwQ1twMsA.png)

y en el assambly que esta en la misma parte agrega el siguiente código

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__1Y4ttFo4O9J__C7RjrwCs__Q.png)

El diseño final de nuestra aplicación sera el siguiente, si vez coincidí perfectamente con la dirección buscada en google maps

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__J__gVSAEnrTHG6ETmKXchlw.png)

El código de la app lo puedes descargar del siguiente repositorio.

[**devjaime/Geocodificacion**  
_Repositorio XamarinForms donde se explica el sensor geocoding para obtener información de una ubicación en particular …_github.com](https://github.com/devjaime/Geocodificacion "https://github.com/devjaime/Geocodificacion")[](https://github.com/devjaime/Geocodificacion)