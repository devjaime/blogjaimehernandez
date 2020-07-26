+++
title = "Flask Python primera aproximación"
description = "Flask Python primera aproximación"
tags = [
    "python",
    "flask",
]
date = 2020-07-25T02:13:50Z
author = "Jaime Hernandez"
+++

# Video Primera aproximación con Flask
{{< youtube id="ghoN4haF5SI" >}} 

## Codigo fuente
Puedes encontrar el código fuente de este proyecto [aquí](https://github.com/devjaime/apiflaskproductos)
## Flask
Flask es un microframework web de Python construido con un núcleo pequeño y una filosofía fácil de ampliar.



## ¿Por qué Flask es una buena opción de marco web?

Flask se considera más [Pitónco] (https://blog.startifact.com/posts/older/what-is-pythonic.html) que el framework web Django porque en situaciones comunes la aplicación web Flask equivalente es más explícita. También es fácil comenzar con Flask como principiante porque hay un pequeño código repetitivo para poner en marcha una aplicación simple.

Por ejemplo, aquí hay un válido "¡Hola, mundo!" Aplicación web con Flask:
```python
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hola, mundo!'

if __name__ == '__main__':
    app.run()
```

* El código anterior muestra "¡Hola, mundo!" en el puerto localhost 5000 en un navegador web cuando se ejecuta con el python app.pycomando y la biblioteca Flask instalada.

* El equivalente "¡Hola, mundo!" La aplicación web que utiliza el marco web Django implicaría significativamente más código repetitivo.

* Flask también se escribió varios años después de Django y, por lo tanto, aprendió de las reacciones de la comunidad Python a medida que evolucionó el marco. Jökull Sólberg escribió una gran pieza que articula a este efecto en su [experiencia](http://web.archive.org/web/20160305145017/http://jokull.calepin.co/my-flask-to-django-experience.html) de cambio entre Flask y Django .


## Construyendo una pequeña ApiRest

### Paso 1
Crearemos 2 archivos dentro de un directorio llamado, product-restapi:
* 1-   app.py (este archivo contendra la logica de nuestra aplicación flask)
* 2-   products.py (este archivo simulara la información devuelta en un archivo con formato json a de nuestra apirest)


### Paso 2

Deberas instalar las dependencias de flask, pero antes que esto recomiendo que instales un entorno virtual para tu proyecto, en mi caso ocupo pipenv, (si desconoces caul es el procedimiento puedes seguirlo en el siguiente tutorial) [pipenventornovirtual](https://jaimehz.com/post/entornosvirtualespython/)

en la terminal deberas ingresar el siguiente comando:
```terminal
pipenv shell
```

despues de esta acción verifica que tu entorno este sobre la version 3.6.x, con el siguiente comando:
```terminal
python --version
```

* instalar dependencia de flask
```terminal
pip install flask
```

### Nota: si estas trabajando con vscode te recomiendo instalar [autopep8] y [pylink] que son las sugerencia de este editor de texto.

### Paso 3 agregando productos
En el archivo products.py que creamos debemos ingresar los siguientes datos:

```json
products = [
    {"name": "laptop","price":800,"quantity":4},
    {"name": "mouse","price":40,"quantity":10},
    {"name": "monitor","price":400,"quantity":3},
]
```
Esto sera la simulación de nuestra base de datos con los productos que puede tener esta.

### Paso 4 app.py Creando un CRUD a partir de nuestro archivo de productos

Realizaremos las siguientes importaciones a nuestro archivo app.py, Flask que corresponde a la dependencia del microframework, jsonify para convertir de formato a string a json valido y request que lo ocuparemos para los metodos de nuestro CRUD
```python
from flask import Flask, jsonify, request

app = Flask(__name__)
  
from products import products
```

* La primera ruta que manejaremos es para verificar que nuestras importaciones sean las correctas:

```python
# Testing Route
@app.route('/ping', methods=['GET'])
def ping():
    return jsonify({'response': 'pong!'})
```


@app.route indica la ruta donde se encontrara y el metodo que se ocupara sera GET con una respuesta 'pong' o que el servicio funciona correctamente.


* Nuestra segunda ruta devolvera los productos en un formato json valido a traves de nuestra función importada jsonify
```python
# Get Data Routes
@app.route('/products')
def getProducts():
    # return jsonify(products)
    return jsonify({'products': products})

```
* Nuestra tercera ruta devolvera un producto en particular buscando por el nombre dentro del archivo json y si no lo encuentra devolvera que el producto no existe.
```python
@app.route('/products/<string:product_name>')
def getProduct(product_name):
    productsFound = [
        product for product in products if product['name'] == product_name.lower()]
    if (len(productsFound) > 0):
        return jsonify({'product': productsFound[0]})
    return jsonify({'message': 'Product Not found'})
```

* Nuestra cuarta ruta devolvera un nuevo producto insertado en nuestro arreglo, (este arreglo esta en memoria y no es información persistente), pero servira para probar agregar nuevos registros a nuestro json devuelto.
```python
# Create Data Routes
@app.route('/products', methods=['POST'])
def addProduct():
    new_product = {
        'name': request.json['name'],
        'price': request.json['price'],
        'quantity': request.json['quantity']
    }
    products.append(new_product)
    return jsonify({'products': products})
```

* Nuestra quinta ruta devolvera la modificación de datos de un producto cuando este existe al buscarlo por nombre.
```python
# Update Data Route
@app.route('/products/<string:product_name>', methods=['PUT'])
def editProduct(product_name):
    productsFound = [product for product in products if product['name'] == product_name]
    if (len(productsFound) > 0):
        productsFound[0]['name'] = request.json['name']
        productsFound[0]['price'] = request.json['price']
        productsFound[0]['quantity'] = request.json['quantity']
        return jsonify({
            'message': 'Product Updated',
            'product': productsFound[0]
        })
    return jsonify({'message': 'Product Not found'})
```

* Nuestra sexta y última ruta devolvere la eliminación de un producto al buscarlo por nombre.
```python
# DELETE Data Route
@app.route('/products/<string:product_name>', methods=['DELETE'])
def deleteProduct(product_name):
    productsFound = [product for product in products if product['name'] == product_name]
    if len(productsFound) > 0:
        products.remove(productsFound[0])
        return jsonify({
            'message': 'Product Deleted',
            'products': products
        })
```

* Para que funcionen nuestras rutas y puedas ejecutar el programa debes realizar lo siguiente:

```python
if __name__ == '__main__':
    app.run(debug=True, port=4000)
```

* Esto disponibilizara el puerto de conexión modo debug, luego ejecuta lo siguiente en el terminal:

```terminal
python app.py
```
debes probar tus apis con postman o insomnia