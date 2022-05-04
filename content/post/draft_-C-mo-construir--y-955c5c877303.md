---
title: ¿Cómo construir? y
description: 'La guía completa, paso a paso.'
date: ''
categories: []
keywords: []
slug: ''
---

###   

#### La guía completa, paso a paso.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__fxdQZZznPZuKV25O4hPn7Q.png)

  

### 1\. Crea el proyecto de la biblioteca.

Comenzamos como de costumbre, generando la configuración inicial con el `ng new`comando:

**ng nuevo** lib-demo --prefix ld

Con la versión 7de Angular CLI, el formato del archivo de configuración de manera bastante importante. `angular.json`Representa lo que ahora se llama un espacio de trabajo, posiblemente con múltiples **_proyectos_**  . De forma predeterminada, obteniendo `lib-demo`y los `lib-demo-e2e`proyectos se generan para nosotros, pero podemos agregar más con el `"ng generate application [my-app-name]"`comando.

Lo que también se puede generar en el lugar de la _aplicación_  , es una _biblioteca_  :

**ng g biblioteca** tvmaze --prefix tm

En cuanto a los indicadores para este comando, hay [varias opciones](https://github.com/angular/angular-cli/wiki/generate-library)  , pero configura el prefijo es el mínimo absoluto. Si no eliges el prefijo, el valor predeterminado será `lib-`.

El `generate`comando hizo varios cambios a nuestra aplicación:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__G7ayZlniVwbL__scvV__79LQ.png)

En particular, `"projects"`se creó un nuevo directorio, con la `"tvmaze"`carpeta dentro. Este nuevo _proyecto también_ está referenciado en nuestra `angular.json`configuración.

### 2\. Definir y proporcionar algunas interfaces.

Una solicitud de API se verá así: [https://api.tvmaze.com/shows/336](https://api.tvmaze.com/shows/336)  .   
Si sigue el enlace, no será tan complejo; sería una buena idea definir un conjunto de interfaces reutilizables y proporcionarlas a los usuarios de nuestra biblioteca. Puedes usar una herramienta maravillosa de [jsontots.com](http://www.jsontots.com/) para hacer lo primero:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__GbHAjzI4U3UEr1D4DcaKBA.gif)

Vamos a crear un archivo con todas las interfaces. Hay muchos de ellos y todos están bastante relacionados.`projects/tvmaze/src/lib/**tvmaze.models.ts**`

Para que los usuarios puedan utilizar esta biblioteca tengan acceso a nuestras interfaces, debemos proporcionarnos como una aplicación pública de la biblioteca tvmaze. Edite el archivo generado en el primer paso para que se vea así:`projects/tvmaze/src/**public_api.ts**`

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__qGsme__joFCtw3RH8BHbUcA.png)

### 3\. Crea un servicio en la biblioteca.

Nuestra tvmaze recién Creada Tiene Su propio `package.json`, `tsconfig.json`, `tslint.json`y `karma.conf.js`puesto m Que Tiene Que SENTIDO pueden requérir Una configuration diferente de la Aplicación directora. También tiene un componente de muestra, un módulo y un servicio generado para nosotros. También podemos agregar otros adicionales, que haremos en un momento.

Por ahora vamos a añadir algo de lógica a la`projects/tvmaze/src/lib/**tvmaze.service.ts**`

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____kSQNpCK__4oJ2f8GObbqrw.png)

No hay nada inusual En Este servicio Que No Sea La `provideIn: root`configuration en el `@Injectable`decorador. Es en realidad una nueva configuración agregada en Angular 6.

> `"provideIn: root"` Permitir un servicio sin registro explícito en ningún NgModule.

¿Por qué es útil? En el caso de los servicios de bibliotecas, no se puede utilizar el servicio.

### 4\. Crear un componente en la biblioteca.

Nuestra biblioteca mostrará un _póster_ del espectáculo dado. Al igual que con un proyecto Angular típico, no tiene que crear un componente a mano, es para lo que sirve la CLI:

**ng generar componente** cartel - **_proyecto_ = tvmaze**

Solo teníamos que decirle a la CLI que creara el póster dentro de nuestra biblioteca de _tvmaze_  .

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__kN3Quhhr6Vs4hOhT__mWpjg.png)

Para que el componente esté disponible fuera de las bibliotecas `tvmaze.module`, debemos agregarlo a la `exports`sección. Asegúrate de que se vea así:`projects/tvmaze/src/lib/**tvmaze.module.ts**`

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__tiAdG__MyhmrFyXBlGFs8nw.png)

También se añadido `HttpClientModule`la dependencia, ya Que NECESITAMOS `HttpClient`es `TvMazeService`, Y `CommonModule`Porque es Donde `async`la tubería y `ngIf`la directiva (Que El _cártel_ se definen Componente utilizació).

### 5\. ¡Construye el tiempo!

Antes de que podamos usar nuestra biblioteca, necesitamos construirla. Una vez más, CLI angular ayuda con eso. Ahora podemos decirle que construya un proyecto específico:

**ng construir** tvmaze

### 6\. Usa la biblioteca

Para probar nuestra biblioteca, debemos hacer lo que siempre haríamos con una extensión de terceros: definir como una dependencia en la `imports`sección del módulo de la aplicación:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__iaB9ljriE5R0EpmlSi8Xlw.png)

Lo que hay que tener en cuenta aquí es que no importamos la clase mediante una ruta relativa al directorio de televisión, sino que lo hacemos como si ya está en `node_modules`. ¿En realidad está ahí? No

Entonces, ¿cómo funciona esto?

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__7v16hkl0A51G0Rhwg2cYWQ.png)

Cuando generamos la biblioteca ( `ng generate library tvmaze`), la CLI angular modificó `tsconfig.json`la raíz de nuestro proyecto agregándola `tvmaze`a la `paths`entrada.

Esto significa que siempre que está en su código de TypeScript que usted va a ser algo de `"tvmaze"`él, en realidad se está importando desde el `dist/tvmaze`directorio, donde se guardó la compilación de nuestra biblioteca.

Eso es realmente conveniente, porque una vez que publique la biblioteca en el repositorio npm real y que desee comenzar a usar esa versión, no tendrá que cambiar la importación en el origen de la aplicación, solo elimine esa `paths`entrada.

Ahora vamos a mostrar algo.

Vamos a modificar el valor predeterminado `src/app/app.component.ts`para que se vea así:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Y__IhzTF3GazFuyb7fUgvqA.png)

Aquí estamos usando todo lo que nuestro `tvmaze`servicio proporciona:    
la `Show`interfaz, `TvmazeService`y `<tm-poster>`. Una vez que iniciemos la aplicación, esto debería ser un resultado:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__NhUx7qBFMnb5QTGCKPRfRQ.png)

### 7\. Publicar la biblioteca

Para que la biblioteca esté disponible en npm, todo lo que necesita hacer es crear una compilación de producción y ejecutar el `npm publish`comando desde el directorio dist del proyecto:

**ng build** tvmaze --prod   
**cd** dist / tvmaze   
**npm publish**

Si no ha publicado nada antes, primero debe crear una cuenta npm e iniciar sesión ( [consulte los detalles en la documentación](https://docs.npmjs.com/getting-started/publishing-npm-packages) ), pero de lo contrario ...    
eso es todo :-)

### Epílogo

Lo que no cubrimos en la guía es probar, en sí mismo es un tema en sí mismo, pero aparte de ejecutar el `ng test tvmaze`comando en lugar de `ng test`hacerlo, es como probar cualquier otra aplicación Angular.

Una cosa que falta a la perfección en la configuración actual es un poco mejor que la automatización: por ahora, cada vez que usted quiera en su aplicación los cambios que introdujeron en la biblioteca, deben reconstruir la biblioteca y, a menudo, reiniciar el servidor de la aplicación principal. . El equipo angular está trabajando para hacer que esto sea más ágil, pero mientras tanto, lo que puedo sugerir es hacer un guión para que se asigne un enlace de clave en su IDE (por ejemplo, usar las [_tareas de_](https://code.visualstudio.com/docs/editor/tasks) Visual Studio Code). Eso es lo que estoy haciendo.

Dicho esto, el proceso actual es una **gran experiencia de desarrollo** que solo estoy esperando a que aparezcan nuevas bibliotecas en todo el ecosistema :-)

Por cierto como siempre, puede consultar el código terminado que se usa en este artículo en [GitHub](https://github.com/sulco/angular-lib-demo)  . Y asegúrese de leer la [entrada de](https://github.com/angular/angular-cli/wiki/stories-create-library) la [wiki](https://github.com/angular/angular-cli/wiki/stories-create-library) en el repositorio de CLI para obtener información adicional, como el razonamiento detrás de ciertas opciones arquitectónicas.