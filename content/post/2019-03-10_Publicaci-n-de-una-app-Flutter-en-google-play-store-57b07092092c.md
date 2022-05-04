---
title: Publicación de una app Flutter en google play store
description: >-
  Hace un tiempo atrás compre una cuenta google play para publicar aplicaciones
  en la tienda de google play store, la finalidad al principio…
date: '2019-03-10T16:53:39.917Z'
categories: []
keywords: []
slug: >-
  /@devjaime/publicaci%C3%B3n-de-una-app-flutter-en-google-play-store-57b07092092c
---

Hace un tiempo atrás compre una cuenta google play para publicar aplicaciones en la tienda de google play store, la finalidad al principio es poder tener mi propio portafolio de aplicaciones para posteriormente poder vender alguna de estas aplicaciones en la misma tienda.

Dentro de estos pasos de publicación lo primero que realice fue inscribir este cuenta que tiene un valor de 25 USD en la pagina oficial, para este primer paso puedes ir a leer un poco sobre publicación de aplicaciones en el sitio oficial de android y posteriormente abrir play console.

Te dejo el link aquí: [https://developer.android.com/distribute/console/?hl=ES](https://developer.android.com/distribute/console/?hl=ES)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__JdJSLckFwpVBvOdNMQBL__g.png)

En la tienda debes tener presente 3 factores importantes

Contar con una cuenta de correo gmail, tener una tarjeta de crédito para adquirir los derechos de publicación y leer todos los tips para poder tener la mejor experiencia de publicación.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__UrXikJj0OqQXWTwEDV77bQ.png)

Una vez realizado este paso lo que realice fue ir a la pagina oficial de flutter para poder verificar los pasos de publicación.

El link es el siguiente: [https://flutter.dev/docs/deployment/android](https://flutter.dev/docs/deployment/android)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__wrxCK0__5emwaW8ax__VuYaw.png)

Una buena alternativa (aunque se actualiza con un cierto desfase) es ingresar a la traducción realizada por la comunidad cuyo link seria el siguiente:

[**Preparando para release una app Android**  
_Durante el ciclo de desarrollo típico, probarás una aplicación usando \`flutter run\` en la línea de comando, los botones…_flutter-es.io](https://flutter-es.io/docs/deployment/android "https://flutter-es.io/docs/deployment/android")[](https://flutter-es.io/docs/deployment/android)

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__nSo4hPS2vArZztwOGe__R5A.png)

Cabe mencionar que este proyecto de traducción es un gran aporte al cual podrías integrarte sin ningún problema bifucardo su proyecto y apoyando en la traducción, la comunidad te lo agradecería mucho.

Link

[**Flutter ES**  
_Comunidad de desarrolladores de Flutter de habla hispana. - Flutter ES_github.com](https://github.com/flutter-es "https://github.com/flutter-es")[](https://github.com/flutter-es)

Entonces para esta demostración ocupare una aplicación que lo único que realiza es la conversión de monedas de un país en otro la cual pueden revisarla del siguiente repositorio:

[**devjaime/FlutterConversor**  
_Simple conversor de monedas para mostrar publicación en la google play store - devjaime/FlutterConversor_github.com](https://github.com/devjaime/FlutterConversor "https://github.com/devjaime/FlutterConversor")[](https://github.com/devjaime/FlutterConversor)

Entonces el primer paso segun la guia oficial de flutter es revisar App Manifest de Android el cual se encuentra en esta dirección <app dir>/android/app/src/main

De este apartado dado que nuestra aplicación se conecta a un api obtiene los datos del valor de cada moneda desde internet dejaremos activo el permiso correspondiente a este, si su app no se conecta a internet no es necesario que activen este permiso.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__95Fm22DcfHZVvN7Cctjp3w.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____ZCz5Csn8__fw7chKYjhfIw.png)

Revisando la configuración de compilación

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__QgYB2JSSCL9x__IvzQxthww.png)

Este archivo al principio me costo identificarlo ya que existen varios del mismo nombre por lo cual creo que una captura de pantalla de la aplicación y ver en que lugar se encuentra aclarara esto.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__F0rSLiShkOS1mUghtpqXng.png)

### Añadiendo un icono para el Launcher

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__LzJC9ukRiKH6BNSXZ5Y1dQ.png)

Los distintos iconos que van a aparecer en nuestra app siempre son un tema (ya que existen distintas medidas el como generarlos y donde colocarlos)

Para los que no saben de que se trata esto les dejo una captura de pantalla:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__OWgVOr1ADxblrHauveOpgw.png)

Para la generación de los distintos tamaños de estos iconos tenemos varias formas de realizarlo, la que mas aconsejo yo (debido a que no soy un diseñador gráfico) es ocupar un programa que haga el trabajo por nosotros

[**App Icon Generator**  
_Generate icons and images for mobile apps, android and iOS. No need to upload or download. Works on your browser_appicon.co](https://appicon.co/ "https://appicon.co/")[](https://appicon.co/)

Con este generador de iconos solo debemos pegar una imagen con la sufiente densidad (densidad mas alta) y generara todos los iconos necesarios).

Ahora simplemente debemos copiar y reemplazar los iconos y carpetas generadas a nuestra carpeta de assets generados.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__GaiHw8GY6BpCKUItTRMA__w.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__c41V__T6DQhJ9Lru34HsyzA.png)

Firmado de la app

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__70enG2ea54XpKrKdlBqIHg.png)

El firmado de la app fue una de las cosas que más me costo entender y existen varios vídeos y tutoriales de cual es la mejor forma de realizarlo y todas son distintas, por lo cual lo que intente fue realizar la forma más simple posible.

Lo primero que realice fue ejecutar flutter doctor -v en la terminal para ver donde estaba instalado el jdk de java que ejecuta flutter:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__xEYfgD9gtW__uauXJB3I__LQ.png)

Si se van al explorador encontraran una ruta como la siguiente

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__dSgdgEaucWTJRb__w7F1deg.png)

Entonces desde la ventana cmd me muevo a la misma ruta

Nota importante deben abrir la ventana cmd en modo administrador

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__N2P01JleA3NYmUGDLmEf7w.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__4or2OCSZxXWMKaoXLPrSKA.png)

Luego de lo anterior pegas el comando siguiente:

keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key

en mi derivación de este comando para windows lo que realice fue cambiar la ruta “~/key.jks” a “c:\\key.jks” también podrías cambiar el alias o el nombre del archivo si lo deseas.

como se muestra a continuación.

keytool -genkey -v -keystore c:\\keyapp.jks -keyalg RSA -keysize 2048 -validity 10000 -alias keyapp

la razón por la que dejo el archivo en la raiz de c: es solo como demostración

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__AueF2x5P96P0J232dXZI2g.png)

y en esta ejecuto el comando anteriormente descrito

al presionar enter se te ira preguntando los datos necesarios para identificar la clave de publicación

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__8jd0X7Da1oCP6CMkUQIsAQ.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ajUPaeawYcPG1YnFK5__kmA.png)

Al presionar enter te pedirá confirmar si ocuparas la misma clave de almacén en mi caso recomiendo presionar INTRO para ocupar la misma.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____NweF4__BglRVQAybBfRAfQ.png)

Si todo sale bien tus claves fueron generadas exitosamente en el path que otorgaste.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__bEnOUHQl7kZl9L2tHJHtCw.png)

Referencia al keyStore desde la app

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__yLDDGTQHvtOx2____tvQEzag.png)

Una vez creado el archivo, debes generar una referencia desde la app para esto debes ir al directorio de la aplicación y modificar el archivo key.properties

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__qeDy992JQTYQowCwaIsnmg.png)

ingresa los datos anteriormente puestos como son las password el keyalias y la ruta donde se encuentra el archivo.

Configurar la firma en Gradle

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__pRxGjCCr__LYDBOm9iR0q2w.png)

Tal como aparece en la gua oficial solo debes reemplazar la información del archivo por la descrita en este apartado quedando de la siguiente forma.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__9Zg__oJyXZJrDTRmeb8d__Vw.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__WMoVdHX0Cn6mixv8sLTqdA.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__qm7ufdRaFO3Pfe__3xrt8FA.png)

Para construir la release debes ejecutar el comando tal como aparece y verificar la salida de este

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__8I6GBnBHfnX8TKVwK6et7w.png)

luego de ejecutar flutter build apk

debes ejecutar el comando flutter install si quieres instalar y probar tu aplicación

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__DsaDi0hnbqGq1i6g__oa__Jw.png)

en este caso la instalo directamente en el dispositivo de prueba.

Ahora solo nos queda publicar nuestra app con google play console

Recomiendo crear la ficha de play store y completar los datos correspondientes

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Oi1vpZrXhgBb1kXVFdlqeg.png)

Crear los iconos e imágenes

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__d55zW2MlVaosURDj5vTJRg.png)

Para crear las imágenes recomiendo este link en donde a traces de una captura de pantalla puedes generar los distintos iconos de la aplicación para visualizarlos en la tienda.

[**App Screenshot Generator for App Store & Google Play**  
_AppLaunchpad is an android & ios screenshot generator to create customized App Store & Google Play images for your app…_theapplaunchpad.com](https://theapplaunchpad.com/ "https://theapplaunchpad.com/")[](https://theapplaunchpad.com/)

Seleccionas la plataforma

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____BxMM__9g30xbHEw3eWqFJA.png)

El template

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__oOjb9oHPUY5EII8Pc3eQYA.png)

y por último subes tu captura de pantalla

Luego de lo anterior sube tu apk y realiza distintas pruebas tienes distintos ambientes, lo recomendable es que realices varias pruebas internas antes de subir a producción puedes realizar pruebas abiertas y pruebas cerradas, verificar los dispositivos y los países en los que se distribuira tu aplicación, te deseo mucho éxito en tu camino a la publicación de tu nueva aplicación de flutter

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__bkHWUldwtq0EVHpLnIrRYQ.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__okt__cMHs1ltWGZs11Hd3Kg.png)