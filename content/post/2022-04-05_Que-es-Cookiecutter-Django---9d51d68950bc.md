---
title: "Que es Cookiecutter Django\_?"
description: >-
  Este pequeña introducción es tanto para recordarme a “mi mismo” que existe
  esta herramienta. Como para compartir esta forma fácil y bonita…
date: '2022-04-05T05:47:34.849Z'
categories: []
keywords: []
slug: /@devjaime/que-es-cookiecutter-django-9d51d68950bc
---

![](/Users/devjaime/Documents/blog/posts/md_1651648785637/img/1__e51KT42qJ__PWbMwcVa7yyA.png)

Este pequeña introducción es tanto para recordarme a “mi mismo” que existe esta herramienta. Como para compartir esta forma fácil y bonita de empezar un proyecto en django backend.

Que es un Cookiecutter? : Dada la definición técnica

> es una utilidad de línea de comandos que crea proyectos a partir de una plantilla (plantillas de proyectos), por ejemplo, crear un proyecto de paquete de Python a partir de una plantilla de proyecto de paquete de Python. La gracia de estás plantillas es que vienen con todo lo necesario para empezar un buen proyecto, por ejemplo de Backend.

#### Aquí un repositorio de configuración con una guía rápida

[**GitHub - cookiecutter/cookiecutter-django: Cookiecutter Django is a framework for jumpstarting…**  
_Powered by Cookiecutter, Cookiecutter Django is a framework for jumpstarting production-ready Django projects quickly…_github.com](https://github.com/cookiecutter/cookiecutter-django "https://github.com/cookiecutter/cookiecutter-django")[](https://github.com/cookiecutter/cookiecutter-django)

[**Deployment with Docker - Cookiecutter Django 2022.14.2 documentation**  
_If you are deploying to AWS, you can use the IAM role to substitute AWS credentials, after which it's safe to remove…_cookiecutter-django.readthedocs.io](https://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html "https://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html")[](https://cookiecutter-django.readthedocs.io/en/latest/deployment-with-docker.html)

### Características

*   Para Django 3.2
*   Funciona con Phyton 3.9
*   Renderiza proyectos de Django con una cobertura de prueba inicial del 100 %
*   Twitter [Bootstrap](https://github.com/twbs/bootstrap) v5
*   Configuraciones basadas en [12 factores a través](http://12factor.net/) [de django-environ](https://github.com/joke2k/django-environ)
*   Seguro por defecto. Creemos en SSL.
*   Configuraciones de desarrollo y producción optimizadas
*   Registro a través [de django-allauth](https://github.com/pennersr/django-allauth)
*   Viene con un modelo de usuario personalizado listo para usar
*   Configuración ASGI básica opcional para Websockets
*   Construcción estática personalizada opcional usando Gulp y livereload
*   Envíe correos electrónicos a través [de Anymail](https://github.com/anymail/django-anymail) (usando [Mailgun](http://www.mailgun.com/) de forma predeterminada o Amazon SES si AWS es el proveedor de la nube seleccionado, pero se puede cambiar)
*   Almacenamiento multimedia con Amazon S3 o Google Cloud Storage
*   Compatibilidad con Docker mediante [docker-compose](https://github.com/docker/compose) para desarrollo y producción (utilizando [Traefik](https://traefik.io/) con compatibilidad con [LetsEncrypt](https://letsencrypt.org/) )
*   [Perfil](https://devcenter.heroku.com/articles/procfile) para implementar en Heroku
*   Instrucciones para implementar en [PythonAnywhere](https://www.pythonanywhere.com/)
*   Ejecutar pruebas con unittest o pytest
*   Versión personalizable de PostgreSQL
*   Integración predeterminada con [compromiso previo](https://github.com/pre-commit/pre-commit) para identificar problemas simples antes de enviarlos a revisión de código

_Espero sea de utilidad para alguien más_

Dejo un video de configuración (pero es siempre bueno ver la documentación oficial del proyecto en el caso de que algo cambiara)