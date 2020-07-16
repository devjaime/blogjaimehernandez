+++
title = "Continuación de NestJS como Framework de desarrollo Backend"
description = "En este articulo se abordara la teoria de inyección de dependencias, los aspectos importantes de autenticación y ORM para acceder a las base de datos."
tags = [
    "nestjs",
    "nodejs",
    "backend",
]
date = 2020-07-16T02:13:50Z
author = "Jaime Hernandez"
+++
## Inyección de dependencia
La inyección de dependencia es la técnica de suministrar un objeto dependiente, como un módulo o componente, con una dependencia o como un servicio, inyectándolo en el constructor del componente. Más adelante abordaremos un ejemplo de esto. 

```typescript
@Injectable()
export class UsuarioService implements IUsusuarioService {
    constructor(@Inject('UsurioRepositoro') private readonly UsuarioRepositorio: typeof Usuario) { }
    ...
}
```

Aquí estamos inyectando el [UsuarioRespositorio] en el constructor de [UsuarioService], proporcionando así acceso al repositorio de la base de datos del usuario desde el interior del [UsuarioServicecomponents].
A su vez, esto UsuarioService se inyectará en el UsuarioController en el src/usuario/usuario.controller.ts archivo, que proporcionará acceso a UsuarioService y las rutas que apuntan a este controlador.

## Autenticación
La autenticación es uno de los aspectos más importantes del desarrollo. Como desarrolladores, siempre queremos asegurarnos de que los usuarios solo puedan acceder a los recursos para los que tienen permiso de acceso. La autenticación puede tomar muchas formas, desde mostrar su licencia de conducir o pasaporte hasta proporcionar un nombre de usuario y contraseña para un portal de inicio de sesión. En los últimos años, estos métodos de autenticación se han ampliado para volverse más complicados, pero aún necesitamos la misma lógica del lado del servidor para asegurarnos de que estos usuarios autenticados sean siempre quienes dicen ser y persisten en esta autenticación para que no tengan que volver a autenticarse por cada llamada a una API REST o Websocket porque eso proporcionaría una experiencia de usuario bastante terrible. 
Irónicamente, la biblioteca elegida para esto también se llama Passport, y es muy conocida y utilizada en el ecosistema Node.js. Cuando se integra en Nest, utiliza una estrategia JWT (JSON Web Token). Passport es un middleware por el que se pasa la llamada HTTP antes de llegar al punto final en el controlador. 

```typescript
@Injectable()  
export class AuthenticationMiddleware implements NestMiddleware {  
   constructor(private usuarioService: UsuarioService) { }  

   async resolve(strategy: string): Promise<ExpressMiddleware> {  
       return async (req, res, next) => {  
           return passport.authenticate(strategy, async (/*...*/args: any[]) => {  
               const [, payload, err] = args;  
                if (err) {  
                    return res.status(HttpStatus.BAD_REQUEST).send('El usuario no se pudo conectar.');  
                }  

               const usuario = await this.usuarioService.findOne({
                    where: { email: payload.email }
               });  
                req.usuario = usuario;  
                return next();  
            })(req, res, next);  
        };  
    }  
}
```
Nest también implementa Guards, que están decorados con los mismos @Injectable() que otros proveedores. Los guards restringen ciertos puntos finales en función de a qué tiene acceso el usuario autenticado. 

## ORM
Un ORM es un mapeo relacional de objetos y es uno de los conceptos más importantes cuando se trata de la comunicación entre un servidor y una base de datos. Un ORM proporciona una correspondencia entre los objetos en la memoria (clases definidas tales como [User] o [Comment]) y las tablas relacionales en una base de datos. Esto le permite crear un Objeto de transferencia de datos que sabe cómo escribir objetos almacenados en la memoria en una base de datos, y leer los resultados de una consulta SQL u otro lenguaje de consulta, nuevamente en la memoria. Por lo general para futuros ejemplos intentare demostrar  el uso de TypeORM. Que es uno de los ORM más maduros y populares para Node.js y, por lo tanto, tiene un conjunto de características muy amplio. También es uno de los paquetes para los que Nest proporciona sus propios paquetes:@nestjs/typeorm. Es increíblemente poderoso y tiene soporte para muchas bases de datos como MySQL, PostgreSQL, MariaDB, SQLite, MS SQL Server, Oracle y WebSQL. Junto con TypeORM, Sequelize es también otro ORM para datos relacionales.

Si TypeORM es uno de los ORM más populares, entonces Sequelize es EL más popular en el mundo de Node.js. Está escrito en JavaScript simple pero tiene enlaces TypeScript a través de los paquetes sequelize-typescripty @types/sequelize. Sequelize cuenta con un sólido soporte de transacciones, relaciones, replicación de lectura y muchas más funciones. 



