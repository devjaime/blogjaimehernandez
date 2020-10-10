+++
title = "Paradigmas de base de datos"
description = "Paradigmas de base de datos existentes y su utilización actual"
tags = [
    "BASEDATOS",
    "Paradigmas",
]
date = 2020-10-09T02:13:50Z
author = "Jaime Hernandez"
+++
# Paradigamas de base de datos

## Bases de datos clave-valor: Redis, Memcached

* Redis: que significa Remote Dictionary Server (Servidor de diccionario remto), es un rápido almacén de datos clave-valor en memoria de código abierto que se puede utilizar como base de datos, caché, agente de mensajes y cola.

## ¿Cómo funciona Redis?
* Todos los datos de Redis residen en la memoria, a diferencia de las bases de datos que almacenan datos en discos o SSD. Como no hay ninguna necesidad de obtener acceso al disco, los almacenes de datos en memoria, como Redis, evitan los retrasos y pueden obtener acceso a los datos en cuestión de milisegundos. Redis incluye estructuras de datos versátiles, alta disponiblidad, datos geoespaciales, scripts Lua, transacciones, persistencia en disco y soporte de clúster, lo que simplica la creación de aplicaciones a escala de internet en tiempo real.

## Algunos casos de uso de Redis

* Teniendo en cuenta la naturaleza de Redis para ofrecer alto rendimiento y baja latencia en las operaciones de escritura, y princiaplmente de lectura, es normal encontrarlo en las diferentes implementaciones de sistemas siendo utilizado para almacenamiento principal, caché de alta velocidad y Broker de mensajes.

* Almacenamiento princiap: en este caso, Redis se convierte e na fuente de verdad para muchas aplicaciones que requieren responder muy rápidamente en las solicitudes que reciben, tales como ingestión de datos en tiempo real, monitorea de la operación de un sistema y extraer datos para realizar procedimientos analíticos.

* Caché de alta velocidad: es el uso más popular para lo que se utiliza Redis, con lo que podemos construir aplicaciones con mejores capacidades de responsividad y escalibilidad al contar con los datos mucho más cerca de las aplicaciones, reducioendo a su vez el tráfico hacia las fuentes de datos. Cuando la aplicación recibe una petición para obtener un recurso, como por ejemplo obtener las listas de las ciudades principales de un país, la aplicación busca primero si la información está en Redis, si no la encuentra, hace la consulta a la fuente de datos, y almacena los datos en Redis para entregar la respuesta rápidamente en próximas peticiones.
* Broker de mensajes: redis puede usuarse para comunicar diferentes procesos en un sistema distribuido, haciendo uso de la estructura de datos de listas y las peraciones que soporta. se puede implementar un sistema de colas sencillo en el que un productor envía valores a la lista, mientras que un consumidor los va retirando y procesando.

### ¿Qué es Memcached?

* Memcached es un almacén de datos en la memoria de alto rendimiento y fácil de usar. Ofrece una solución de código abierto, escalable y completamente desarrollada con tiempos de respuesta inferiores a un milisegundo, muy útil para el almacenamiento en caché o los almacenes de sesión. Memcached es una opción muy común para impulsar las aplicaciones en tiempo real en la Web, aplicaciones móviles, juegos, tecnología publicitaria y comercio electrónico.

### ¿Cómo funciona Memcached?
* A diferencia de las bases de datos que almacenan datos en el disco o en tarjetas SSD, Memcached guarda sus datos en la memoria. Como no hay ninguna necesidad de acceder al disco, los almacenes de clave-valor como Memcached evitan los retrasos y pueden acceder a los datos en cuestión de milisegundos. Memcached también funciona con el modelo distribuido, lo que significa que es fácil de escalar con el agregado de nuevos nodos. Además, como Memcached es multiproceso, puede escalar la capacidad de computación. Como resultado de su velocidad y escalabilidad, así como su diseño simple, su eficaz gestión de memorias y la compatibilidad de la API con los idiomas más populares, Memcached es una opción común para almacenamientos en caché a gran escala y de alto rendimiento.

### Casos de uso destacados de Memcached
#### Almacenamiento en caché
* Memcached es una excelente opción para implementar un alto rendimiento del almacenamiento en caché en la memoria para disminuir la latencia de acceso a los datos, aumentar la capacidad y aligerar la carga de sus sistemas de backend. Memcached puede servir elementos en caché en menos de un milisegundo y le permite realizar escaladas fácilmente y de forma rentable en cargas mayores. Memcached está pensado para el almacenamiento en caché de resultados de consultas de bases de datos, de sesiones, de API y de elementos como imágenes, archivos y metadatos.

### Almacén de sesiones
* Memcached es una opción para el almacenamiento de datos en la memoria muy utilizada entre los desarrolladores de aplicaciones y que sirve para almacenar y gestionar datos de sesiones para aplicaciones de Internet en los casos en los que la persistencia no es algo fundamental. Memcached está diseñado para proporcionar escalas y latencias inferiores a un milisegundo requeridas para la gestión de datos de sesión, como perfiles de usuario, credenciales y estados de sesión.

### Redis vs. Memcached
* Redis y Memcached son dos de los más conocimos almacenamientos de datos en memoria de clave valor. Memcached está diseñado para la simplicidad mientras que Redis ofrece un conjunto enriquecido de características que lo hacen efectivo para una amplia gama de casos de uso.


## Wide-Column Databases(o almacenes de registros extensibles): Cassandra, Apache HBase
* Son bases de datos NoSQL que almacenan datos en registros con la capacidad de contener un gran número de columnas dinámicas. Las columnas pueden contener valores nulos y datos con diferentes tipos de datos. Además, los datos se almacenan en celdas agrupadas en columnas de datos en lugar de filas de datos. Las columnas se agrupan lógicamente en familias de columnas. Las familias de columnas pueden contener un número virtualmente ilimitado de columnas que se pueden crear en tiempo de ejecución o mientras se define el esquema. Y las familias de columnas son grupos de datos similares a los que normalmente se accede de forma conjunta. Además, las familias de columnas se pueden agrupar como superfamilias de columnas.

### Cassandra

### Historia y orígenes
* El desarrollo inicial de Cassandra tiene su origen en Facebook, que lo diseñó para potenciar la funcionalidad de búsqueda en el inbox. En 2008 fue liberado como proyecto open source y en febrero de 2010 se convirtió en un proyecto top-level de la fundación Apache.

Está inspirado e influenciado por los papers de Amazon Dynamo de 2007 y de Google BigTable de 2006. Hoy en día está mantenido y desarrollado por la compañía Datastax.

Su nombre está inspirado por la sacerdotisa Cassandra de la mitología griega, que tenía el don de la profecía, y predijo el engaño del Caballo de Troya.

### Arquitectura y características
* Cassandra nos proporciona tolerancia a particiones y disponibilidad, pero a cambio de ser eventualmente consistente, tal y como define el teorema CAP. El nivel de consistencia puede ser configurado, según nos interese, incluso a nivel de query.

* Es distribuida, lo quiere decir que la información está repartida a lo largo de los nodos del cluster. Además ofrece alta disponibilidad, de manera que si alguno de los nodos se cae el servicio no se degradará.

* Escala linealmente, lo que quiere decir que el rendimiento de forma lineal respecto al número de nodos que añadamos. Por ejemplo, si con 2 nodos soportamos 100.000 operaciones por segundo, con 4 nodos soportaremos 200.000. Esto da mucha predictibilidad a nuestros sistemas.

* Escala de forma horizontal, lo que quiere decir que podemos escalar nuestro sistema añadiendo nuevos nodos basados en hardware commodity de bajo coste.
* Implementa una arquitectura Peer-to-Peer, lo que elimina los puntos de fallo único y no sigue patrones maestro-esclavo como otros sistemas de almacenamiento. De esta manera cualquiera de los nodos puede tomar el rol de coordinador de una query. Será el driver el que decida qué nodo quiere que sea el coordinador.
Los datos son repartidos a lo largo del cluster en base a un token único calculado para cada fila por una función hash.

* Los nodos se reparten equitativamente el rango de tokens que va de -263 a 263, esto define el nodo primario. Internamente Cassandra replicará los datos entre los nodos con la política que le definamos, por ejemplo definiendo el factor de replicación.

* Además soporta el concepto de data center para agrupar los nodos lógicamente y tener los datos más cerca del usuario.

### Conclusión
* Cassandra es una solución brillante para muchos casos de uso que podemos encontrar en el mundo Big Data. Sin embargo, no es adecuada para alojar un data warehouse convencional.

* Lo ideal es tener claro desde el principio el caso de uso y el tipo de consultas que haremos para diseñar la base de datos coherentemente, de esta manera podremos manejar grandes volúmenes de datos y aprovecharnos de las ventajas de esta potente base de datos distribuida.



### Apache HBase

* HBase es una base de datos distribuida no relacional de código abierto modelada a partir de Google BigTable y escrita en Java. Su desarrollo forma parte del proyecto Hadoop de la Fundación de Software Apache y se ejecuta sobre HDFS (el sistema de archivos distribuidos de Hadoop), proporcionando capacidades al estilos de BigTable para Hadoop. Es decir, proporciona una forma tolerante a fallos de almacenar grandes cantidades de datos dispersos (pequeñas cantidades de información inmersas dentro de una gran colección de datos inexistentes o poco significativos, tales como la búsqueda de los 50 mayores elementos en un grupo de 2 mil millones de registros, o la búsqueda de elementos distintos de cero que representan menos del 0,1% de una enorme colección).

* HBase incluye operaciones de compresión en memoria, y filtro de Bloom sobre la base de cada columna como se propone en el artículo original sobre BigTable.1​ Las tablas en HBase pueden servir como entrada o salida para tareas MapReduce en Hadoop, y se puede acceder a través del API en Java, como servicio REST, o con los API de conexión Avro y Thrift. Hbase es un almacén de datos orientado a columnas de tipo clave-valor y basado en Hadoop y HDFS. HBase se ejecuta sobre HDFS y es adecuado para acelerar operaciones de lectura y escritura en los grandes conjuntos de datos con un alto rendimiento y una baja latencia de entrada/salida.2​

* HBase no remplaza las bases de datos SQL clásicas, sin embargo el proyecto Apache Phoenix proporciona una capa de SQL para Hbase así como acceso vía el API JDBC que puede ser integrado con diversas herramientas de analítica de datos e inteligencia de negocios. El proyecto Apache Trafodion proporciona un motor de consulta SQL con drivers ODBC y JDBC y protección de transacciones ACID distribuidas a través de múltiples consultas, tablas y filas utilizando HBase como motor de almacenamiento.

* Actualmente, Hbase se utiliza en sitios web orientados a datos,3​ incluyendo la plataforma de mensajería de Facebook.4​5​ A diferencia de las bases de datos relacionales tradicionales, HBase no da soporte a consultas SQL sino a scripts escritos en Java que emplean un motor de cálculo similar a MapReduce.

## Document Databases: MongoDB, Firestore, CouchDB
* Una base de datos de documentos es un tipo de base de datos no relacional que ha sido diseñada para almacenar y consultar datos como documentos de tipo JSON. Las bases de datos de documentos facilitan a los desarrolladores el almacenamiento y la consulta de datos en una base de datos mediante el mismo formato de modelo de documentos que emplean en el código de aplicación. La naturaleza flexible, semiestructurada y jerárquica de los documentos y las bases de datos de documentos permite que evolucionen según las necesidades de las aplicaciones. El modelo de documentos funciona bien con casos de uso como catálogos, perfiles de usuario y sistemas de administración de contenido en los que cada documento es único y evoluciona con el tiempo. Las bases de datos de documentos permiten una indexación fácil, potentes consultas ad hoc y análisis de colecciones de documentos.

### MongoDB
* Dentro de las bases de datos NoSQL, probablemente una de las más famosas sea MongoDB. Con un concepto muy diferente al de las bases de datos relacionales, se está convirtiendo en una interesante alternativa.

* Pero cuándo uno se inicia en MongoDB se puede sentir perdido. No tenemos tablas, no tenemos registros y lo que es más importante, no tenemos SQL. Aun así, MongoDB es una seria candidata para almacenar los datos de nuestras aplicaciones.

### ¿Dónde se puede utilizar MongoDB?
* Aunque se suele decir que las bases de datos NoSQL tienen un ámbito de aplicación reducido, MongoDB se puede utilizar en muchos de los proyectos que desarrollamos en la actualidad.

* Cualquier aplicación que necesite almacenar datos semi estructurados puede usar MongoDB. Es el caso de las típicas aplicaciones CRUD o de muchos de los desarrollos web actuales.

* Eso sí, aunque las colecciones de MongoDB no necesitan definir une esquema, es importante que diseñemos nuestra aplicación para seguir uno. Tendremos que pensar si necesitamos normalizar los datos, denormalizarlos o utilizar una aproximación híbrida. Estas decisiones pueden afectar al rendimiento de nuestra aplicación. En definitiva el esquema lo definen las consultas que vayamos a realizar con más frecuencia.

* MongoDB es especialmente útil en entornos que requieran escalabilidad. Con sus opciones de replicación y sharding, que son muy sencillas de configurar, podemos conseguir un sistema que escale horizontalmente sin demasiados problemas.

### ¿Dónde no se debe usar MongoDB?
* En esta base de datos no existen las transacciones. Aunque nuestra aplicación puede utilizar alguna técnica para simular las transacciones, MongoDB no tiene esta capacidad. Solo garantiza operaciones atómicas a nivel de documento. Si las transacciones son algo indispensable en nuestro desarrollo, deberemos pensar en otro sistema.

* Tampoco existen los JOINS. Para consultar datos relacionados en dos o más colecciones, tenemos que hacer más de una consulta. En general, si nuestros datos pueden ser estructurados en tablas, y necesitamos las relaciones, es mejor que optemos por un RDBMS clásico.

* Y para finalizar, están las consultas de agregación. MongoDB tiene un framework para realizar consultas de este tipo llamado Aggregation Framework. También puede usar Map Reduce. Aún así, estos métodos no llegan a la potencia de un sistema relacional. Si vamos a necesitar explotar informes complejos, deberemos pensar en utilizar otro sistema. Eso sí, esta es una brecha que MongoDB va recortando con cada versión. En poco tiempo esto podría dejar de ser un problema.

## Firestore

* Cloud Firestore es la base de datos más reciente de Firebase para el desarrollo de apps para dispositivos móviles. Es una solución eficiente y de baja latencia destinada a las apps para dispositivos móviles que necesitan estados sincronizados entre los clientes en tiempo real.

### ¿Como funciona?
* Cloud Firestore almacena en caché datos que usa tu app de forma activa, por lo que la app puede escribir, leer, escuchar y consultar datos, aunque el dispositivo se encuentre sin conexión. Cuando el dispositivo vuelve a estar en línea, Cloud Firestore sincroniza todos los cambios locales de vuelta a Cloud Firestore.

## CouuchDB
CouchDB es una base de datos NoSQL de código abierto basada en estándares comunes para facilitar la accesibilidad y compatibilidad web con una diversidad de dispositivos.

## Relational Databases: MySQL, Postgres, SQL Server, CockroachDB

* Una base de datos relacional es un tipo de base de datos que almacena y proporciona acceso a puntos de datos relacionados entre sí. Las bases de datos relacionales se basan en el modelo relacional, una forma intuitiva y directa de representar datos en tablas. En una base de datos relacional, cada fila de la tabla es un registro con un ID único llamado clave. Las columnas de la tabla contienen atributos de los datos, y cada registro generalmente tiene un valor para cada atributo, lo que facilita el establecimiento de las relaciones entre los puntos de datos.

### ¿Qué es MySQL?
* MySQL es un sistema de gestión de bases de datos relacionales de código abierto (RDBMS, por sus siglas en inglés) con un modelo cliente-servidor. RDBMS es un software o servicio utilizado para crear y administrar bases de datos basadas en un modelo relacional. Ahora, echemos un vistazo más de cerca a cada término:

### Código abierto
* Código abierto significa que eres libre de usarlo y modificarlo. Cualquiera puede instalar el software. También puedes aprender y personalizar el código fuente para que se adapte mejor a tus necesidades. Sin embargo, la GPL (licencia pública de GNU) determina lo que puedes hacer según las condiciones. La versión con licencia comercial está disponible si necesitas una propiedad más flexible y un soporte avanzado.

### Modelo cliente-servidor
* Las computadoras que tienen instalado y ejecutan el software RDBMS se llaman clientes. Siempre que necesitan acceder a los datos, se conectan al servidor RDBMS. Esa es la parte «cliente-servidor».

* MySQL es una de las muchas opciones de software RDBMS. Suele pensarse que RDBMS y MySQL son lo mismo debido a la popularidad de MySQL. Para nombrar algunas aplicaciones web grandes como Facebook, Twitter, YouTube, Google y Yahoo!, todas usan MySQL para el almacenamiento de datos. Aunque inicialmente se creó para un uso limitado, ahora es compatible con muchas plataformas de computación importantes como Linux, macOS, Microsoft Windows y Ubuntu.


## PostgreSQL
* PostgreSQL es una de las opciones más interesantes en bases de datos relacionales open-source. Michael Stonebraker inició el proyecto bajo el nombre Post Ingres a mediados de los 80’s con la idea de solucionar problemas existentes en las bases de datos en esa época. MySQL fue por mucho tiempo el motor más popular; pero hoy es propiedad de Oracle y esto limita su evolución.
* Es gratuito y libre, además de que hoy nos ofrece una gran cantidad de opciones avanzadas. De hecho, es considerado el motor de base de datos más avanzado en la actualidad.
* Una característica interesante de PostgreSQL es el control de concurrencias multiversión; o MVCC por sus siglas en inglés. Este método agrega una imagen del estado de la base de datos a cada transacción. Esto nos permite hacer transacciones eventualmente consistentes, ofreciéndonos grandes ventajas en el rendimiento.
* En Postgres no se requiere usar bloqueos de lectura al realizar una transacción lo que nos brinda una mayor escalabilidad. También PostgreSQL tiene Hot-Standby. Este permite que los clientes hagan búsquedas (sólo de lectura) en los servidores mientras están en modo de recuperación o espera. Así podemos hacer tareas de mantenimiento o recuperación sin bloquear completamente el sistema.

## Sql Server
* Los servidores SQL Server suelen presentar como principal característica una alta disponibilidad al permitir un gran tiempo de actividad y una conmutación más rápida. Todo esto sin sacrificar los recursos de memoria del sistema. Gracias a las funciones de memoria integradas directamente en los motores de base de datos SQL Server y de análisis, mejora la flexibilidad y se facilita el uso. Pero quizá su característica más destacada es que ofrece una solución robusta que se integra a la perfección con la familia de servidores Microsoft Server.
* Características de Microsoft SQL Server :

*  Soporte de transacciones.
* Escalabilidad, estabilidad y seguridad.
* Soporte de procedimientos almacenados.
* Incluye también un potente entorno gráfico de administración, que permite el
* uso de comandos DDL y DML gráficamente.
* Permite trabajar en modo cliente-servidor, donde la información y datos se alojan en el servidor y las terminales o clientes de la red solo acceden a la información.
* Permite administrar información de otros servidores de datos. 

## CockroachDB
* CockroachDB es nativo de la nube y está diseñado para implementarse en Kubernetes

## Graph Databases: Neo4j, DGraph, Janus Graph
* Una base de datos de gráficos es una base de datos diseñada para tratar las relaciones entre los datos como igualmente importantes para los datos en sí. Está destinado a contener datos sin restringirlos a un modelo predefinido. En cambio, los datos se almacenan como los sacamos primero, mostrando cómo cada entidad individual se conecta o se relaciona con otras.
### ¿Por qué graficar bases de datos?

* Vivimos en un mundo conectado! No hay información aislada, sino dominios ricos y conectados a nuestro alrededor. Solo una base de datos que adopte relaciones de forma nativa es capaz de almacenar, procesar y consultar conexiones de manera eficiente. Mientras que otras bases de datos calculan relaciones en el momento de la consulta a través de costosas operaciones JOIN, una base de datos de gráficos almacena conexiones junto con los datos en el modelo.

* Acceder a los nodos y las relaciones en una base de datos de gráficos nativa es una operación eficiente, en tiempo constante y le permite atravesar rápidamente millones de conexiones por segundo por núcleo.

* Independientemente del tamaño total de su conjunto de datos, las bases de datos de gráficos se destacan en la gestión de datos altamente conectados y consultas complejas. Con solo un patrón y un conjunto de puntos de partida, las bases de datos de gráficos exploran los datos vecinos alrededor de esos puntos de partida iniciales, recopilando y agregando información de millones de nodos y relaciones, y dejando intactos los datos fuera del perímetro de búsqueda.

## Neo4j
* Neo4j es una base de datos de gráficos nativa NoSQL de código abierto que proporciona un backend transaccional compatible con ACID para sus aplicaciones. El desarrollo inicial comenzó en 2003, pero ha estado disponible públicamente desde 2007. El código fuente, escrito en Java y Scala, está disponible de forma gratuita en GitHub o como descarga de una aplicación de escritorio fácil de usar . Neo4j tiene una edición comunitaria y una edición empresarial de la base de datos. Enterprise Edition incluye todo lo que Community Edition tiene para ofrecer, además de requisitos empresariales adicionales como copias de seguridad, agrupación en clústeres y capacidades de conmutación por error.

* Neo4j se conoce como una base de datos de gráficos nativa porque implementa de manera eficiente el modelo de gráficos de propiedades hasta el nivel de almacenamiento. Esto significa que los datos se almacenan exactamente como los escribe en la pizarra y la base de datos utiliza punteros para navegar y recorrer el gráfico. A diferencia del procesamiento de gráficos o las bibliotecas en memoria, Neo4j también proporciona características de base de datos completas, incluido el cumplimiento de transacciones ACID, el soporte de clústeres y la conmutación por error en tiempo de ejecución, lo que lo hace adecuado para usar gráficos para datos en escenarios de producción.

* Caso de uso Walmart utiliza recomendaciones de usuario en tiempo real utlizando este modelo de base de datos.

## Dgraph
* Dgraph es la base de datos GraphQL nativa con un backend gráfico. Es de código abierto, escalable, distribuido, altamente disponible y ultrarrápido.

* Neo4j es la base de datos de gráficos más popular según db-engines.com y existe desde 2007. Dgraph es una base de datos de gráficos mucho más nueva creada para escalar a la escala web de Google y para un uso de producción serio como base de datos principal.

* Neo4j se ejecuta en un solo servidor. La versión empresarial de Neo4j solo ejecuta réplicas de datos universales. A medida que los datos escalan, esto requiere que el usuario escale verticalmente sus servidores. El escalado vertical es caro.

* Dgraph tiene una arquitectura distribuida. Puede dividir sus datos entre muchos servidores Dgraph para distribuirlos horizontalmente. A medida que agrega más datos, puede agregar más hardware básico para servirlos. Dgraph incorpora más funciones de rendimiento, como reducir las llamadas de red en un clúster y una ejecución de consultas muy concurrente, para lograr un alto rendimiento de consultas. Dgraph realiza una replicación consistente de cada fragmento, lo que lo hace resistente a fallas y protege a los usuarios del tiempo de inactividad del servidor.

## JanusGraph
* JanusGraph es una base de datos de gráficos escalable optimizada para almacenar y consultar gráficos que contienen cientos de miles de millones de vértices y bordes distribuidos en un clúster de varias máquinas.

* JanusGraph es un proyecto de The Linux Foundation e incluye participantes de Expero, Google, GRAKN.AI, Hortonworks, IBM y Amazon.

## Search Databases: ElasticSearch, Algolia, MeiliSearch
## ElasticSearch
* Elasticsearch es un motor de analítica y análisis distribuido y open source para todos los tipos de datos, incluidos textuales, numéricos, geoespaciales, estructurados y desestructurados. Elasticsearch está desarrollado en Apache Lucene y fue presentado por primera vez en 2010 por Elasticsearch N.V. (ahora conocido como Elastic). Conocido por sus API REST simples, naturaleza distribuida, velocidad y escalabilidad, Elasticsearch es el componente principal del Elastic Stack, un conjunto de herramientas open source para la ingesta, el enriquecimiento, el almacenamiento, el análisis y la visualización de datos. Comúnmente referido como el ELK Stack (por Elasticsearch, Logstash y Kibana), el Elastic Stack ahora incluye una gran colección de agentes de envío conocidos como Beats para enviar los datos a Elasticsearch.

### ¿Para qué se usa Elasticsearch?
* La velocidad y escalabilidad de Elasticsearch y su capacidad de indexar muchos tipos de contenido significan que puede usarse para una variedad de casos de uso:

* Búsqueda de aplicaciones
* Búsqueda de sitio web
* Búsqueda Empresarial
* Logging y analíticas de log
* Métricas de infraestructura y monitoreo de contenedores
* Monitoreo de rendimiento de aplicaciones
* Análisis y visualización de datos geoespaciales
* Analítica de Seguridad
* Analítica de Negocios

### ¿Cómo funciona Elasticsearch?
* Los datos sin procesar fluyen hacia Elasticsearch desde una variedad de fuentes, incluidos logs, métricas de sistema y aplicaciones web. La ingesta de datos es el proceso mediante el cual estos datos son parseados, normalizados y enriquecidos antes de su indexación en Elasticsearch. Una vez indexados en Elasticsearch, los usuarios pueden ejecutar consultas complejas sobre sus datos y usar agregaciones para recuperar resúmenes complejos de sus datos. Desde Kibana, los usuarios crean visualizaciones poderosas de sus datos, comparten dashboards y gestionan el Elastic Stack.


## Algolia
* Algolia es un motor de búsqueda alojado accesible vía una potente API la cual se puede integrar en webs y aplicaciones móviles. El motor se centra en ofrecer resultados de manera rápida y aplicando la relevancia en los posibles productos a mostrar en una búsqueda según las configuraciones que realicemos para ello y así ofrecer la mejor experiencia al usuario.

### Search engine 
* Es el cerebro de Algolia construido y optimizado para poder ofrecer lo mejor a los clientes, especializado en búsquedas basadas en texto y con datos estructurado. Por ejemplo es apto para buscar un producto en un e-commerce, una canción en una plataforma de streaming, artículos en medios de prensa digital. Al final todo esta información sobre los productos está almacenada en una tabla de una base de datos con sus atributos y valores. 

* La clave es que con el motor de Algolia puede buscar específicamente en esos atributos pudiendo llegar a nivel de granularidad mayor a la hora de realizar una búsqueda, incluso se pueden utilizar estos atributos como filtros


## MeliSearch
* API de búsqueda de próxima generación
* Un motor de búsqueda de código abierto, increíblemente rápido e hiperelevante que mejorará su experiencia de búsqueda.

* MeiliSearch tiene como objetivo ser su backend de búsqueda de referencia cuando desee crear una excelente experiencia de búsqueda para sus usuarios finales.
* MeiliSearch está diseñado para la búsqueda de usuarios finales en una colección de datos no tan grande (<10 millones de documentos).
* MeiliSearch está hecho para escribir a medida que busca y buscar prefijos.

## Multi-model Databases: FaunaDB, CosmosDB
## FaunaDB
* FaunaDB es una base de datos global sin servidor que reconsidera la relación cliente-servidor . Con una interfaz GraphQL nativa de la web que admite lógica empresarial personalizada, una estructura de datos y computación coherente con seguridad moderna y total libertad de las operaciones de la base de datos, FaunaDB le permite simplificar el código, reducir costos y enviar más rápido. 

## CosmosDB
* Azure Cosmos DB es un servicio de base de datos NoSQL totalmente administrado para el desarrollo de aplicaciones modernas. Obtenga tiempos de respuesta inferiores a diez milisegundos y una disponibilidad del 99,999 % garantizados, respaldados con acuerdos de nivel de servicio, escalabilidad automática e inmediata y API de código abierto para MongoDB y Cassandra. Disfrute de operaciones de escritura y lectura rápidas en cualquier parte del mundo gracias a la distribución global de la arquitectura multimaestro llave en mano.