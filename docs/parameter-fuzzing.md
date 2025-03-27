# FUZZING DE PARAMETROS Y VALORES

!!! tip "Wordlist adecuada para fuzzing de parámetros"
    La wordlist de **seclists** llamada **burp-parameter-names.txt** es una de las mejores para empezar este tipo de fuzzing.

El **fuzzing de parámetros** es una técnica utilizada para descubrir vulnerabilidades en una aplicación web probando múltiples valores en los parámetros de las peticiones HTTP.

## Fuzzing en peticiones GET con ffuf
Las peticiones GET en una aplicación web se pasan a través de la URL, indicadas de la forma `?param=key`. El fuzzing lo realizaremos al parámetro con cualquier valor, esto con el fin de identificar los parámetros válidos.

``` sh
ffuf -u 'http://TARGET_IP:PORT/admin.php?FUZZ=key' -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ 
```

## Fuzzing en peticiones POST con ffuf
A diferencia de las peticiones GET que se realizan en la URL, las peticiones POST se pasan en el cuerpo (body) de la petición POST.

Para realizar estas peticiones con ffuf debemos usar dos parámetros adicionales además de los básicos:

* `-d`: Indica que los datos se enviaran en el cuerpo (body) de la solicitud HTTP.

* `-X`: Especifica el método HTTP a usar.

``` sh 
ffuf -u 'http://TARGET_IP:PORT/admin.php' -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -X POST -d 'FUZZ=key'
```

En PHP, es importante que el header **Content-Type** sea de tipo **application/x-www-form-urlencoded** debido a que es el único que acepta en peticiones POST. Para evitar errores, podemos agregarlo explicitamente al fuzzing.

* `-H`: Añade cabeceras HTTP personalizadas.

``` sh
ffuf -u 'http://TARGET_IP:PORT/admin.php' -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded'
```

Al encontrar un parámetro válido, podemos verificar la respuesta usando la herramienta `curl`. Supongamos que el parámetro válido que encontramos es `ìd`:

``` sh 
curl 'http://TARGET_IP:PORT/admin.php' -X POST -d 'id=key' -H 'Content-Type: application/x-www-form-urlencoded'
```

## Fuzzing de valores de parámetros con ffuf
Dependiendo del tipo de parámetro que obtuvimos, se utilizará diferentes wordlists para el fuzzing. En el caso anterior, obtuvimos un parámetro `ìd``por lo que podemos crear una wordlist personalizada con los números de 1 al 10,000 para intentar obtener un id válido. 

``` sh
ffuf -u 'http://TARGET_IP:PORT/admin.php' -w custom_ids.txt:IDS -X POST -d 'id=IDS' -H 'Content-Type: application/x-www-form-urlencoded'
```

Y si obtenemos un id válido, podemos usar `curl` para obtener la respuesta. (Supongamos que el id válido es 73).

``` sh 
curl 'http://TARGET_IP:PORT/admin.php' -X POST -d 'id=73' -H 'Content-Type: application/x-www-form-urlencoded'
```