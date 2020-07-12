+++
title = "Pipenv como entorno virtual de Python"
description = "Pipenv es una herramienta que apunta a traer todo lo mejor del mundo de empaquetado (bundler, composer, npm, yarn, etc.) al mundo de Python."
tags = [
    "python",
    "pyenv",
]
date = 2020-07-12T02:13:50Z
author = "Jaime Hernandez"
+++

Pipenv es una herramienta que apunta a traer todo lo mejor del mundo de empaquetado (bundler, composer, npm, cargo, yarn, etc.) al mundo de Python. 
[fuente] (https://pipenv-es.readthedocs.io/es/latest/)
* Pipenv es la manera recomendada de instalar paquetes en un proyecto y administrar un entorno virtual.

## Requerimeintos

Python 3.x
Puedes comprobar la instalación usando los siguientes comandos





```python 
$ python --version
$ pip --version
```

este último comando deberia mostrarte la ultima version de Python, que es la tres. Pero si estas en Linux o Mac, puede que tengas tanto python 2 como python 3, así que en esos casos puedes comprobalos de esta manera.

```python 
$ python3 --version
$ pip3 --version
```

##  Instalación
para instalar Pipenv puedes ejecutar el siguiente comando
```python 
 $ pip3 install pipenv
```

Una vez terminada la instalación, puedes comprobar los paquetes que tienes instalado en tu computador, o mejor dicho en tu entorno global (global environment) usando el comando freeze

```python 
$ pip3 freeze
```

Aqui puedes darte una idea, que no todas las bibliotecas son necesarias para todos tus proyectos. sino que dependen.

Para activar tu entorno con Pipenv.

```python 
$ pipenv shell
```

Esto configurará tu entorno virtual y creará un archivo llamado Pipfile. el cual servira para listar todos las bibliotecas necesarias para tu proyecto y proveer metainformación.

De hecho, debido a que estas utilizando tu entorno virtual, por defecto ya estas usando Python 3. compruebalo tipeando.

```python 
$ python --version
```

Verás que estas usando la version 3. Y si quieres ver desde donde esta obteniendo esto, puedes comprobarlo usando el interprete de python y el modulo sys.

```python 
import sys
sys.executable
```

Para salir del entorno virtual, puedes executar simplement exit, desde tu terminal.


```python 
$ exit
```

Esto desactivará el entorno y regresarás al entorno global. y en cuanto a volver activarlo tan solo vuelve a tipear pipenv shell.

Para instalar paquetes, puedes hacer usando Pip. por ejemplo instalemos un modulo para tener colores en la terminal.

```python 
$ pip install colorama
```

Esto creará un archivo llamado Pipfile.lock. el cual sirve para hacer un seguimiento de las versiones correctas de nuestros módulos. Pero en realidad, no es necesario y no deberiamos modificar ese archivo.

Para utilizar este modulo puedes simplemente ejecutar python y tipear lo siguiente.

```python 
from colorama import Fore, Style

print(Fore.RED + 'Text in red')
print(Style.RESET_ALL)
```

Y en caso quieres ver la lista de modulos instalados, puedes ejecutar

```python 
$ pipenv lock -r
```

Para desistalar un modulo puedes usar.

```python
$ pipenv uninstall colorama
```

Esto lo quita de tu archivo Pipfile y lo remueve de tu entorno. Puedes comprobarlo ejecutando denuevo pipenv lock.

Y en caso quieres intalar dependencias de desarrollo puedes hacerlo de la siguiente manera.

```python
$ pipenv install colorama --dev
```

Otra forma de instalar modulos es a traves de un archivo requirements.txt. Para hacerlo puedes probar usando Django.

Crea un archivo requirements.txt con el siguiente contenido

```python
Django==2.2
```
Luego, ejecuta el siguiente comando para instalarlo con Pipenv.

```python
$ pipenv install -r requirements.txt
```
Esta es otra forma de instalarlo. Para comprobarlo crea un nuevo proyecto con Django.

```python
$ django-admin startproject hello
$ cd hello
$ python manage.py runserver
```

Un vez hecho esto, ya puedes ir al http://localhost:8000. y ver tu aplicación creada.

Para ver vulnerabilidades puedes ejecutar el siguiente comando

```python
$ pipenv check
```
Y en caso necesites actualizar, tan solo cambia la version del paquete en Pipenv, y luego ejecuta

```python
$ pipenv install
```

Para ver el arbol de dependencias del proyecto
```python
$ pipenv graph
```

OK, en produccion

```python
$ pipenv lock
```

Y en caso quieres ignorar el archivo pipfile
```python
$ pipenv install --ignore-pipfile
```

para ejecutar el proyecto sin el entorno virtual
```python
$ pipenv run python
```
Finalmente para eliminar un environment ejecuta
```python
$ pipenv --rm
```

Fin