---
title: Día 2 Bateria En Xamarin Forms con Xamarin Essentials
description: >-
  En este articulo cubriré la experiencia con el segundo sensor a probar en este
  caso es la batería de nuestro dispositivo.
date: '2019-04-19T04:25:21.088Z'
categories: []
keywords: []
slug: >-
  /@devjaime/d%C3%ADa-2-bateria-en-xamarin-forms-con-xamarin-essentials-4d4f0ae8133
---

En este articulo cubriré la experiencia con el segundo sensor a probar en este caso es la batería de nuestro dispositivo.

La Api que captura el sensor de Batería permite verificar la información de esta y monitorear los cambios, proporciona información sobre el estado de ahorro de energía del dispositivo, que indica si el dispositivo se está ejecutando en un modo de bajo consumo.

Un ejemplo de uso seria el siguiente:

Las aplicaciones deben evitar el procesamiento en segundo plano si el estado de ahorro de energía del dispositivo está activado.

Para esto debemos comenzar de la siguiente forma:

Creamos un nuevo proyecto en visual studio

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__vVren6nk6s4y4jYa9tj1rQ.png)

Seleccionamos una plantilla de Xamarin.Form multiplataforma.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__7OQvoRukg6h3sZcIlUhQkA.png)

Elegimos el nombre de nuestra Solución

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__lojCSObhbHrzk__zhTO95kQ.png)

Seleccionamos una plantilla en blanco con nuestras plataformas de destino, en este caso Android / IOS

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__APIH6o54MdmLHqGUQM3EHQ.png)

y creamos nuestra solución.

Damos Click derecho sobre nuestra solución y agregamos el package nuGet xamarin.essentials, lo agregamos en nuestra solución para los proyectos involucrados

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__juy6Pq8MsiJmJTEZ3xqPeg.png)

Crearemos la siguiente estructura de carpetas en nuestra aplicación (Si ya vienes del primer post te darás cuenta que es la misma estructura de carpetas y puedes copiarlas directamente del repositorio). Esto solo es para que nuestro patrón de diseño MVVM funcione correctamente.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__sBY979qvtTTXwex__2iJAww.png)

En nuestra vista carpeta View agregaremos una nueva page llamada BatteryPage

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__R__TaMw1p67zeeLHnvCKFYQ.png)

y en nuestro ViewModel agregaremos una clase llamada BatteryViewModel.cs

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__oB9pwRkoUTUEOSqMyIgdCw.png)

En nuestra vista xaml debemos agregar el siguiente código

En la clase de nuestra vista debemos agregar el siguiente código.

En nuestro viewmodel debemos agregar lo siguiente:

Tambien debes agregar los permisos en el proyecto Android para que esto funcione

AssemblyInfo.cs

\[assembly: UsesPermission(Android.Manifest.Permission.BatteryStats)\]

AndroidManifest.xml

<uses-permission android:name=”android.permission.BATTERY\_STATS” />

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__fxREiDRru0AHrFevX4PGtg.png)

El resultado final de nuestra app sera el siguiente:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__C__7EnEA10KKiqSadOu8zVw.png)

Puedes descargar el código fuente de esta app desde:

[**devjaime/Bateria**  
_Sensor de bateria con Xamarin Essentials Xamarin Forms - devjaime/Bateria_github.com](https://github.com/devjaime/Bateria "https://github.com/devjaime/Bateria")[](https://github.com/devjaime/Bateria)