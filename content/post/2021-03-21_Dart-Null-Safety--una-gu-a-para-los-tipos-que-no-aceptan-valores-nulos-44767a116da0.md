---
title: 'Dart Null Safety: una guía para los tipos que no aceptan valores nulos'
description: >-
  La introducción de Null Safety en Dart 2.9 marca un hito importante para el
  idioma. Null Safety(verificación de valores nulos en español)…
date: '2021-03-21T04:25:01.799Z'
categories: []
keywords: []
slug: >-
  /@devjaime/dart-null-safety-una-gu%C3%ADa-para-los-tipos-que-no-aceptan-valores-nulos-44767a116da0
---

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__jvllq9__b3Kp6oDGQ.png)

La introducción de Null Safety en Dart 2.9 marca un hito importante para el idioma. Null Safety(verificación de valores nulos en español) te ayuda a evitar toda una clase de problemas y permite algunas mejoras de rendimiento.

Este artículo describe los cambios y muestra cómo utilizar las nuevas funciones de Null Safety con un ejemplo.

_puedes probar Null Safety en_ [_nullsafety.dartpad.dev_](https://nullsafety.dartpad.dev/) _:_

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__nVq4aw9jq__k5DRUT.png)

Esto contiene un “¡Aprenda de los fragmentos!” menú desplegable con mini-ejercicios para familiarizarse con la nueva sintaxis.

### Tabla de contenido

*   Algo de contexto
*   Sistema de tipo dart
*   Dart Null Safety: Beneficios
*   Declaración de variables que no aceptan valores NULL
*   Declaración de variables que aceptan valores NULL
*   El operador de aserción
*   Análisis de flujo: promoción
*   Análisis de flujo: asignación definitiva
*   Usar variables que no aceptan valores NULL con clases
*   Argumentos posicionales y con nombre que no aceptan valores NULL
*   Operador de cascada con reconocimiento nulo
*   Operador de subíndice nulo
*   La palabra clave tardía
*   Variables estáticas y globales
*   Conclusión
*   Referencias

### Algo de contexto

Las referencias nulas se [introdujeron por primera vez](https://www.infoq.com/presentations/Null-References-The-Billion-Dollar-Mistake-Tony-Hoare/) en 1965 en el lenguaje de programación ALGOL y desde entonces han sido adoptadas por la mayoría de los lenguajes de programación convencionales.

Sin embargo, los errores nulos son tan comunes que las referencias nulas se han denominado el error del billón de dólares.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/0__xPVtP9__lEtpkmEj0.jpg)

Entonces, veamos qué ha cambiado en Dart para abordar esto.

### Sistema de tipo dart

Antes de abordar Null Safety, hablemos del sistema de tipo Dart.

Se dice que Dart tiene un **sistema de tipo sound** (sera por que a medida que escribe “**escucha**” tus cambios y te informa tus errores). Cuando escribimos código Dart, el **verificador de tipos** se asegura de que no podamos escribir algo como esto:

```
int age = "hello world"; // A value of type `String` can't be assigned to a variable of type `int`
```

Este código produce un error que nos dice que _“_ `_String_`_no se puede asignar un valor a una variable de tipo_ `_int_`_"_ .

De manera similar, cuando escribimos una función en Dart, podemos especificar un **tipo de** retorno :

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__FHXNjRdAEPAfhWfHq3hbCA.png)

Debido a la **seguridad** del **tipo** , Dart puede garantizar con un 100% de confianza que esta función **siempre** devuelve un `int`.

> _La seguridad de tipos nos ayuda a escribir programas más seguros y a razonar más fácilmente sobre el código._

Pero la seguridad de tipos por sí sola no puede garantizar que una variable (o un valor de retorno) no sea `null`.

Como resultado, este código se compila, pero genera una excepción **en tiempo de ejecución** :

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zFa0gW0JZmYXXPje7vsASQ.png)

En este ejemplo, es bastante fácil detectar el problema. Pero en bases de código grandes es difícil hacer un seguimiento de lo que puede y no puede ser `null`.

Las comprobaciones`null` en tiempo de ejecución pueden mitigar el problema, pero agregan más ruido:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Q6avbzvWGMKc__VUMAlKyUg.png)

Lo que realmente queremos aquí es decirle a Dart que el argumento`value` **nunca** debería ser `null`.

Se necesita una mejor solución, y ahora la tenemos. 😎

### Dart Null Safety: Beneficios

Dart 2.9 presenta **Sound Null Safety** como una función de lenguaje y aporta tres beneficios principales:

*   Podemos escribir código seguro para valores nulos con sólidas garantías de **tiempo de compilación** . Esto nos hace productivos porque Dart puede decirnos cuando estamos haciendo algo mal.
*   Podemos declarar más fácilmente nuestra **intención** . Esto conduce a una API que se autodocumentan y son fáciles de usar.
*   El compilador de Dart puede optimizar nuestro código, lo que resulta en programas más pequeños y rápidos.

Así que veamos cómo funciona la seguridad nula en la práctica.

### Declaración de variables que no aceptan valores NULL

El cambio de lenguaje principal es que **de forma predeterminada** todos los tipos ahora no admiten nulos .

Esto significa que este código no se compila:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__1X07SFJIkQfInqUMGwR9Dg.png)

Al usar variables que no aceptan valores NULL, debemos seguir una regla importante:

> _Las variables que no aceptan valores NULL siempre deben inicializarse con valores que no sean nulos._

Si razona en este sentido, será más fácil comprender todos los nuevos cambios de sintaxis.

Repasemos este ejemplo:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__hpOuIYihEitiPttnPyT18g.png)

Aquí se **garantiza** que tanto el argumento como el valor de retorno no son `null`.

Como resultado, las comprobaciones `null` en **tiempo de** ejecución ya no son necesarias y este código ahora produce un error en **tiempo de compilación** :

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__zFa0gW0JZmYXXPje7vsASQ.png)

Pero si todos los tipos ahora **no aceptan valores NULL** de forma predeterminada, ¿cómo podemos declarar variables que **aceptan valores NULL** ?

### Declaración de variables que aceptan valores NULL

El símbolo`**?**` es lo que necesitamos:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ulEKWUQCzcJRx9IckHNWOg.png)

_Nota: no es necesario inicializar una variable que acepte valores NULL antes de usarla. Se inicializa_ `_null_`_de forma predeterminada._

Aquí hay algunas otras formas de declarar variables que aceptan valores NULL:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__i96n__zRcMQVGxh4GF2MPuA.png)

Las variables que aceptan valores NULL son una buena forma de expresar la **ausencia** de un valor y esto es útil en muchas API.

Cuando diseñe una API, pregúntese si una variable debe ser null o no, y declare en consecuencia.

Pero hay casos en los que sabemos que algo no puede ser `null`, pero no podemos **demostrárselo** al compilador. En estos casos, el operador de aserción puede ayudar.

### El operador de aserción

Podemos usar el operador de aserción `**!**`para asignar una expresión null a una variable no anulable:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__9l6QKqsMDl8km59Nkn8__4w.png)

Al hacer esto, le estamos **diciendo a** Dart que `maybeValue`no es `null`, y es seguro asignarlo a una variable que no acepta valores NULL.

Tenga en cuenta que la aplicación del operador de aserción a un `null`valor arrojará una excepción de tiempo de ejecución:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Adc7XC3Ta5q8mXMKwmxSIA.png)

_Cuando sus suposiciones son incorrectas, el_ `_!_`_operador genera excepciones en tiempo de ejecución_

A veces necesitamos trabajar con APIs que devuelven valores que aceptan valores NULL. Revisemos la función`lastName`:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__73mRztMJkydiAR8rpfn90Q.png)

Aquí el sistema de tipos no puede ayudar. Si nosotros **sabemos** que la función **va a** devolver un valor que no es`null` para un argumento dado, hay que asignarlo a una variable no anulable **tan pronto como sea posible** .

Esto se hace con el operador`!`:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__WAWz6l__5fj2sE4MiF__IJQQ.png)

En resumen:

*   Intente crear variables que no admitan valores NULL cuando sea posible, ya que se **garantizará** que no lo estén `null`en el **momento de la compilación** .
*   Si sabe que una expresión anulable no será `null`, puede asignarla a una variable no anulable con el `!`operador.

### Análisis de flujo: promoción

Dart puede facilitarle la vida al tener en cuenta las comprobaciones `null` de las variables que aceptan valores NULL:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__AoVFL0HJLEYeyZbmCm8dqw.png)

Aquí usamos una declaración`if` para regresar antes si el argumento`value` es `null`.

Más allá de ese punto, `value`no puede ser`null`y se trata (o **promociona** ) a un valor que no acepta valores NULL. Por lo tanto, podemos usar con seguridad en `value.abs()`lugar de `value?.abs()`(con el operador consciente de nulos).

De manera similar, podríamos lanzar una excepción si el valor es `null`:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__1z9RmH3fm__pN0o1nO1QZFg.png)

Una vez más, `value`se promueve a un valor que no acepta valores NULL y `?.`no se necesita el operador de reconocimiento de nulos .

En resumen:

*   Utilice verificaciones nulas **por adelantado** para devolver antes o lanzar excepciones
*   Después de las comprobaciones nulas, las variables que aceptan valores NULL se **promueven** para que no admitan valores NULL.

Y después de que una variable anulable se haya verificado como nula, Dart te permite usarla como una variable no anulable, lo cual es bastante bueno.

### Análisis de flujo: asignación definitiva

Dart sabe dónde se **asignan las** variables y dónde se **leen** .

Este ejemplo muestra cómo inicializar una variable que no acepta valores NULL **después de** verificar una condición:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__eK8BTupeVnw8C5KZcl____vQ.png)

Siempre que se le dé un valor a una variable que no acepta valores NULL **antes** de usarla, Dart no reclamara.

### Usar variables que no aceptan valores NULL con clases

Las variables de instancia en las clases deben inicializarse si no aceptan valores NULL:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Y59vP__rqo2__MHe2__PjEN5w.png)

Si una variable de instancia que no acepta valores NULL no se puede inicializar con un valor predeterminado, configúrelo con un constructor:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__QdlJQ5GrcqxW1zq3dzI1lA.png)

Argumentos posicionales y con nombre que no aceptan valores NULL

Con Null Safety, los argumentos con **nombre que** no aceptan **valores** NULL siempre deben ser **obligatorios** o tener un **valor predeterminado** .

Esto se aplica tanto a los métodos regulares como a los constructores de clases:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__CIHCJ3fXaY4KTcawF9FSXA.png)

Podemos arreglar el código anterior con el nuevo `required` **modificador** , que reemplaza la `@required` **anotación anterior** :

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__IW1Mi7g__kFC4QRK9kLSg9Q.png)

Y cuando usamos las API anteriores, Dart puede decirnos si estamos haciendo algo mal:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ZFA2149BBJNmRN2K6MQ3iQ.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__N1na7CkT0r8q0LTUT__kqmw.png)

Los parámetros **posicionales** están sujetos a las mismas reglas:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__cQeQ7JMxZVwtmnDI2hF__Dg.png)

_Entre variables null y no null, argumentos con nombre y posicionales, valores obligatorios y predeterminados, hay mucho que asimilar. Si está confundido, recuerde la regla de oro:_

> _Las variables que no aceptan valores NULL siempre deben inicializarse con valores que no sean nulos._

_Para comprender completamente todas las funciones de seguridad nula, practique su uso con_ [_Dartpad_](https://dartpad.dev/?null_safety=true)_. Dart le dirá si está haciendo algo mal, así que lea los mensajes de error con atención._ 🔍

### Operador de cascada con reconocimiento nulo

Para hacer frente a Null Safety, el operador en cascada ahora adquiere una nuevos valores `null ?..`. Ejemplo:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__3a__ni6coMxemLuSgzkclLg.png)

Las operaciones en cascada anteriores solo se ejecutarán si `path`no es así `null`.

El operador de cascada con detección de nulos puede **provocar un cortocircuito** , por lo que solo `?..`se necesita un operador al comienzo de la secuencia.

### Operador de subíndice nulo

Hasta ahora, verificar si una colección era `null`antes de usar el operador de subíndice era detallado:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__lsntZAufevn7E__AQLoPB0w.png)

Dart 2.9 presenta al `null`operador `?[]`, lo que hace que esto sea mucho más fácil:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__PUDgdjxpeFhPSPnD8PUNeg.png)

### La palabra clave late

Utilice la palabra `late` clave para inicializar una variable cuando se **lee por primera vez** , en lugar de cuando se **crea** .

Un buen ejemplo es al inicializar variables en `initState()`:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__NOFIr5bh7smBQRDTfyBIYg.png)

Aún mejor, `initState()`se puede eliminar por completo:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__mPQSU8bJ4eLT3qmz11rFMQ.png)

Es común usar `late`en combinación con `final`, para **diferir** la creación de variables de **solo lectura** hasta el momento en que se leen por primera vez.

Esto es ideal cuando se crean variables cuyo inicializador hace un trabajo pesado:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__82jm8t12bJ1Frm__IkQqC1g.png)

Cuando se usa dentro de un cuerpo de función, `late`y `final`se puede usar así:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____hUI5LOLN7KHQRVcPIRJVQ.png)

Aunque no recomiendo el uso de variables late de esta manera. Porque este estilo puede resultar en errores de ejecución no obvios. Ejemplo:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__6FJZdB8r6n8zNusRFbI9jA.png)

Al declarar una variable`late` que no acepta valores NULL , **prometemos** que no será nula en tiempo de ejecución, y Dart nos ayuda con algunas garantías de tiempo de compilación.

Pero recomiendo usar solo `late con`moderación y siempre inicializar las variables `late` cuando se declaran.

### Variables estáticas y globales

Todas las variables globales **ahora deben inicializarse cuando se declaran, a** menos que sean `late`:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__ODg745f__lNXbRuqr1jEavA.png)

Lo mismo se aplica a las variables de clase estáticas:

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__gDF7CmUZ77QGVvKWTnoZ0g.png)

Pero como dije antes, no recomiendo usar `late de esta`forma, ya que puede provocar errores de tiempo de ejecución.

### Conclusión

Null Safety es un cambio importante para el lenguaje Dart y se ha introducido para ayudarte a escribir un código mejor y más seguro.

Pero al final del día, Null Safety es solo una herramienta, y es su trabajo usarla correctamente.

Cada vez que declare una variable en Dart, piense si debería ser null o no. Esto puede parecer un trabajo adicional, pero conducirá a un mejor código y Dart puede ayudarlo en el camino.

[**Donate to devjaime**  
_Help support devjaime by donating or sharing with your friends._www.paypal.com](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S "https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S")[](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S)