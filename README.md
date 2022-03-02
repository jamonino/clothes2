<br />
<div align="center">
  
  <h1 align="center">CLOTHES 2</h3>

  <p align="left">
    La valoración total del examen es de <b>10 puntos</b>.
    <br />
    <br />
    Lenguajes: Java, SQL y PHP
    ·
    Motor BBDD: PostgreSQL
  </p>
</div>

    
## RESUMEN:   
Ampliar la API REST/JSON del proyecto "Clothes" tanto en <a href="https://github.com/jamonino/clothes1">JAVA</a> como en <a href="https://github.com/jamonino/clothes-PHP">PHP</a>

* Limpieza y estructura de código **1P**

### 3P Ejercicio 1 (JAVA): 

Queremos almacenar nuestras marcas de ropa (Por ejemplo Chanel , Prada y Gucci) de manera que podamos obtener un listado de productos con nombre, stock, precio y género de una determinada marca haciendo un GET en la ruta admin/brand/{id}. 

El parámetro {id} sería un número entero identificador de la marca. Las marcas tienen un nombre y un país de origen.

Actualmente los elementos de la tabla products no están relacionados con ninguna marca por lo que hay que inventar al menos tres marcas y relacionar cada uno de los productos manualmente de forma aleatoria con ellas.

**Archivo DB.sql**

* Archivo DB.sql con las modificaciones correctas **1P**

**admin/brand/{id}**
    
* GET - Lista   **2P**

<-- RESPONSE
```js
{
  "responseCode":1,
  "products":[
    {
      "id":1,
      "name":"corbata",
      "price":2900,
      "stock":8,
      "gender":1,
      "brand":{
        "id":3
      }
    },
    {
      "id":2,
      "name":"bufanda",
      "price":1200,
      "stock":4,
      "gender":2,
      "brand":{
        "id":3
      }
    }
  ]
}
```

NOTA1: Si alguien no sabe cómo modificar el archivo DB.sql podrá pedirlo al profesor por <a href="mailto:joseantonio.monino@murciaeduca.es">email</a> perdiendo el punto correspondiente.

NOTA2: Modificar el archivo DB.sql no tiene ningún efecto sobre la bbdd. Para aplicar los cambios habrá que ejecutar su contenido en la misma tal y como se detallaba en el ANEXO BBDD.

### 3P Ejercicio 2 (PHP): 

**/brand**

* POST Crear un Web service de tipo POST en la ruta brand/ para insertar nuevas marcas en la bbdd. **3P**

Si se hace en JAVA en lugar de usar PHP **1P**

--> REQUEST 
```js
{
  "name":"Nike",
  "origin":"USA"
}
```
<-- RESPONSE
```js
{
  "responseCode":1
}
```


### 2P Ejercicio 3 (JAVA): 

**/user/{gender}** 

* GET - Lista **2P**

Modificar el Web service /user/{gender} para que a la información devuelta a cada producto le añada información sobre la marca a la que pertenece

<-- RESPONSE
```js
{
  "responseCode":1,
  "products":[
    {
      "id":1,
      "name":"zapatillas",
      "price":2900,
      "stock":8,
      "gender":1,
      "brand":{
        "name":"Nike",
        "origin":"USA"
      }
    },
    {
      "id":2,
      "name":"bufanda",
      "price":1200,
      "stock":4,
      "gender":1,
      "brand":{
        "name":"Gucci",
        "origin":"Italia"
      }
    }
  ]
}
```


### 1P Ejercicio 4 (PHP): 

**brand/{id}**

* PUT - Edición

Crear un Web service de tipo PUT en la ruta brand/ para editar una marca.

--> REQUEST 
```js
{
  "name":"Adidas",
  "origin":"Alemania"
}
```
<-- RESPONSE
```js
{
  "responseCode":1
}
```


## ANEXO BBDD

Entramos en consola SQL de la BBDD creada
```sh
psql clothes_db
```

Ahora copiar y pegar el código DB.sql modificado. El original sin modificar es el siguiente:

```sql

DROP TABLE IF EXISTS products CASCADE;
CREATE TABLE products (
"id" integer GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
"name" character varying(100),
"price" integer,
"stock" integer,
"gender" integer
);

REVOKE ALL ON SCHEMA public FROM PUBLIC;
GRANT ALL ON SCHEMA public TO clothes_user;

REVOKE ALL ON products FROM public;
GRANT ALL ON products TO clothes_user;

INSERT INTO products (name, price, stock, gender) VALUES ('pantalones', 2000, 6, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('camiseta', 2200, 4, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('chaqueta', 1000, 1, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('camisa', 3300, 7, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('calcetines', 500, 0, 1);
INSERT INTO products (name, price, stock, gender) VALUES ('blusa', 1800, 1, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('vestido', 4500, 4, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('falda', 3000, 2, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('medias', 1000, 0, 2);
INSERT INTO products (name, price, stock, gender) VALUES ('zapatos de tacón', 3400, 3, 2);
```

## EXCEPCIONES

En todos los web services, en caso de excepción se debe devolver un objeto Response con responseCode = 0.


<br />
<div align="center">
  <h1 align="center">¡Mucho ánimo!</h3>
</div>




