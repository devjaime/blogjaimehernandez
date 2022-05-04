---
title: Flutter Cloud AWS articulo en español parte 1 de 3
description: >-
  Este articulo es parte de una serie de post sobre servicios Cloud y Flutter en
  el cual empezare con AWS e intentare ir documentando lo más…
date: '2019-07-17T02:59:10.424Z'
categories: []
keywords: []
slug: >-
  /@devjaime/flutter-cloud-aws-articulo-en-espa%C3%B1ol-parte-1-de-3-ec31304ed06c
---

Este articulo es parte de una serie de post sobre servicios Cloud y Flutter en el cual empezare con AWS e intentare ir documentando lo más posible como poder conectarnos a los servicios de la nube de AWS

La división de este articulo se centrara en conceptos y teoría. Como configuración del backend parte 1 y 2.

En la tercera parte revisaremos como conectarlos con el api rest de los servicios AWS dentro de flutter.

Este articulo empezó la semana del 16/07/2019 y pretendo terminar la tercera parte 31/07/2019 teniendo un articulo cada semana.

Cabe mencionar que soy muy nuevo en los servicios Cloud y mi intención es abordarlo del punto de vista del desarrollador y su implementación en casos medianamente reales.

La problemática

¿Qué pasa si nuestra organización no quiere usar Firebase? Hmmm

**Este artículo se infiltra en el mundo de Amazon, típicamente** [**AWS**](http://aws.amazon.com/) **…**

Para la programación de esta demo, hemos utilizado

1.  Amazon s3 Bucket
2.  Funciones de Amazon Lambda
3.  Obviamente Flutter.

Explicación de conceptos

¿Que es Amazon s3 Bucket?.

### Conceptos básicos de Amazon S3

Para sacar el máximo partido posible a Amazon S3, necesita conocer algunos conceptos básicos. Amazon S3 almacena datos a modo de objetos dentro de **buckets(cubo es lo mismo para el concepto)**. Un objeto se compone de un archivo y, de forma opcional, de cualquier metadato que describa dicho archivo.

Para almacenar un objeto en Amazon S3, debe cargar en un **bucket** el archivo que quiera almacenar. Al cargar un archivo, puede configurar permisos en el objeto y cualquier tipo de metadatos.

¿Que son los buckets?

Los **buckets** son contenedores de objetos. Puede tener uno o más buckets. Para cada bucket, podrá controlar el acceso (quién puede crear, eliminar y enumerar objetos del bucket), consultar los logs de acceso al bucket y sus objetos y elegir la región geográfica en la que Amazon S3 almacenará el bucket y su contenido.

¿Que son las funciones de Amazon Lambda?

AWS Lambda es un servicio informático que permite ejecutar código sin aprovisionar ni administrar servidores. **AWS Lambda** ejecuta el código solo cuando es necesario, y se escala de manera automática, pasando de pocas solicitudes al día a miles por segundo. Solo se paga el tiempo de computación que se consume; no hay ningún cargo mientras el código no se ejecuta. Con **AWS Lambda**, puede ejecutar código para prácticamente cualquier tipo de aplicación o servicio de backend, y sin que se requiera ningún tipo de administración. AWS Lambda ejecuta el código en una infraestructura informática de alta disponibilidad y ejecuta la administración integral de los recursos informáticos, incluido el mantenimiento del servidor y del sistema operativo, el aprovisionamiento de capacidad y el escalado automático, así como la monitorización y los registros. Lo único que tiene que hacer es suministrar el código en uno de los [lenguajes que admite AWS Lambda](https://docs.aws.amazon.com/es_es/lambda/latest/dg/lambda-runtimes.html).

#### Paso 1:

Crear cuenta en [**Amazon Developer Console**](https://aws.amazon.com/) **…**

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__S7L59CH0olEZQ5x2Lv__Z3g.png)

#### Paso 2:

Recomiendo crear una cuenta gratuita

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__Qrud9sQR7wEiFtJC63kTsQ.png)

Buscar **s3** en la **consola de administración …**

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__xvCaKziUlOamV191Pl2oeQ.png)

**Crea un cubo según tu elección …**

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__eU4NnV6m3OYKWw39DDTqlg.png)

> _Por defecto, el cubo no es público, así que tenemos que hacerlo …_

Para realizar esta acción debes desmarcar la casilla de verificación que se muestra en la imagen a continuación

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__58CKm7plyopZKeuyy8vf4Q.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__0gyH6ORcvqSalwdQlx6dVA.png)

A continuación, vaya a la **política de Bucket** … y pegar a continuación

{  
    "Version": "2012-10-17",  
    "Statement": \[  
        {  
            "Sid": "Stmt1405592139000",  
            "Effect": "Allow",  
            "Principal": "\*",  
            "Action": "s3:\*",  
            "Resource": \[  
                "arn:aws:s3:::nombredesucubo/\*",  
                "arn:aws:s3:::nombredesucubo"  
            \]  
        }  
    \]  
}

> _NOTA: Reemplace_ **_‘NOMBRE DE SU CUBO’_** _por su nombre de cubo …_

> Esto nos permite realizar operaciones de cualquier tipo en nuestro cubo …

Advertencia este es solo un caso de demostración donde si quieres realizar una implementación en producción deberás revisar tus políticas de seguridad.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__vOJYbSEolyx6zrsJU1nSLg.png)

#### Paso 3 :

Necesitamos hacer apis para realizar operaciones en el cubo.

Para hacer apis, AWS ofrece [**Lambda**](https://aws.amazon.com/lambda/) similar a [**Cloud Functions**](https://cloud.google.com/functions/) …

Vaya a la **consola de AWS** y busque **Lambda** ..

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__pA6eVKl06njlEI0RK1YG9Q.png)

### Cómo escribir y desplegar Lambdas …

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__qBsj7DrmQ7F1Fjm3UbuoIQ.png)

1.  Instalar [**s**](https://www.npmjs.com/package/serverless)**erverless :** este es un paquete nodeJS que nos ayuda a escribir Lambdas e implementarlas en AWS-

npm install -g serverless

nota si no estas seguro de tener instalado node en tu maquina local verificarlo a través del siguiente comando node — version.

Si la consola dice que no reconoce el comando es dado que no lo tienes instalado y debes proceder a instalar node.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1____FvPdpESGPy2Ak1C0XZ9IQ.png)

Nota importante intenta siempre instalar la versión estable LTS recomendada para la mayoría, debido a que esta tiene características probadas.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__eBUi3pwfy8Bfaw5WaAZQSA.png)

una vez instalado debiera aparecer la versión correspondiente con node — version

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__D5S5g5y39poNV____DwI0rdw.png)

npm install -g serverless

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__kwvDLR2lPcnfCq3u5CGmjA.png)

**2\. Configure sus credenciales de AWS**

Lo primero deben irse a gestión de identidad y acceso “IAM”

¿Que es IAM?

**AWS** Identity and Access Management (**IAM**) es un servicio web que le ayuda a controlar de forma segura el acceso a los recursos de **AWS**. Utilice **IAM** para controlar quién está autenticado (ha iniciado sesión) y autorizado (tiene permisos) para utilizar recursos.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__OW9V5I0jx__AyXsVRBx__YXw.png)

Una vez dentro dirigirte al menú de usuario

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__q4MzMDYvoEzBFQ6JsGMxJw.png)

En donde crearemos un nuevo usuario.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__pmcvP3FWsWPwdaAoJvK64Q.png)

Como vemos en la imagen otorgaremos un nombre de usuario y en tipo de acceso, solo marcaremos “Acceso mediante programación” el cual nos otorgara una clave de acceso secreta.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__AbSF2jn2b1erQsIXTuOl7g.png)

En el wizard nos fijaremos en lo siguiente otorgar permisos de Administrador para efectos de prueba de recurso y en establecer un limite de permisos

“Crear “user” sin un limite de permisos.

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__i3BeXglhZlvQNzWd__1KVpw.png)

Al crear el usuario podrás ver la clave de acceso secreta de 2 formas, descargando el archivo .csv y teniéndolo localmente en tu PC. (recuerda mantenerlos a mano ya que lo ocuparemos dentro de poco).

**3\. Configure sus credenciales de AWS en su pc local con npm serverless**

una vez en tu equipo local debes ejecutar el siguiente comando en la terminal

serverless config credentials --provider aws --key 'AWS Key publica' --secret 'AWS Key privada'

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__lfq6Eb4qWiyAz__uU53JnYw.png)

**3\. Crea un proyecto (sin servidor)**

Recordemos los requisitos antes de continuar

### Pre-requisitos

1.  Node.js `v6.5.0 o posterior`.
2.  CLI serverless `v1.9.0`o posterior. Puede ejecutar `npm install -g serverless`para instalarlo.
3.  Una cuenta de AWS. Si aún no tiene uno, puede inscribirse para una [prueba gratuita](https://aws.amazon.com/s/dm/optimization/server-side-test/free-tier/free_np/) que incluye 1 millón de solicitudes Lambda gratuitas por mes.
4.  Configure sus [credenciales de proveedor](https://serverless.com/framework/docs/providers/aws/guide/credentials) -> [Vea el video sobre la configuración de credenciales](https://www.youtube.com/watch?v=KngM5bfpttA)

### Crear un nuevo servicio

Cree un nuevo servicio utilizando la plantilla Node.js, especificando un nombre único y una ruta opcional para su servicio.

\#   Cree un nuevo servicio / proyecto

serverless create --template aws-nodejs

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__IVscuHxJHKWyPpQ5h__Zmkg.png)

`handler.js ->` Donde escribes tu lógica`...`

`serverless.yml ->` Donde describe tu deploy`...`

functions:  
  
  getAllFiles:  
    handler: handler.getAllFiles  
    events:  
     - http:  
         path: /getAllFiles  
         method: get         
  
  uploadFile:  
    handler: handler.uploadFile  
    events:  
     - http:  
         path: /uploadFile  
         method: post

> _Por ejemplo,_ **_obtener_** _y_ **_publicar los_** _puntos finales de url …_

En el archivo handler.js …

_Lógica para obtener todos los archivos, desde el almacenamiento de AWS ._

module.exports.getAllFiles = async (event, context) => {

let files = \[\];

let params = {   
 Bucket: process.env.BUCKET, / \* required \* /   
 Prefix: ‘upload’   
 };

let result = await s3.listObjectsV2 (params) .promise ();

dejar datos = resultado. contenido;   
 Object.keys (data) .forEach ((key, index) => {

let fileObject = data \[key\];

files.push (\`https: // $ {result.Name} .s3.us-east-2.amazonaws .com / $ {fileObject.Key} \`);   
 });

return {   
 statusCode: 200,   
 body: JSON.stringify ({   
 files: files,   
 bucketName: \`$ {result.Name}\`,   
 subFolder: \`$ {result.Prefix}\`,   
 }, null, 2),   
 };   
};

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__3guQ0UUU__LnLucPOWws8dw.png)
![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__aaqdsXnJA5A4PeO8bPfivA.png)

Espero sea de su interés hasta este momento.

[**Donate to devjaime**  
_Help support devjaime by donating or sharing with your friends._www.paypal.com](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S "https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S")[](https://www.paypal.com/donate/?hosted_button_id=AHPZLS6ZR2A7S)