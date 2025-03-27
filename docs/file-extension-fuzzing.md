# FUZZING DE EXTENSIONES DE ARCHIVOS

!!! tip "Wordlist adecuada para fuzzing de extensiones de archivos"
    La wordlist de **seclists** llamada **web-extensions.txt** es una de las mejores para empezar este tipo de fuzzing.

El **fuzzing de extensiones de archivos** es una técnica empleada para descubrir qué tipos de archivos existen en un servidor, mediante la generación de múltiples solicitudes que varían la extensión del archivo.

Uno de los enfoques más comunes es realizar fuzzing sobre un nombre de archivo muy usado en aplicaciones web, como **index**. Por ejemplo, si el servidor utiliza el archivo index como entrada principal, es posible que existan variantes ocultas como **index.php**, **index.html**, etc.

!!! info "Nombres de archivos comunes"
    Aunque **index** es el nombre más común, es prudente ampliar el alcance del fuzzing utilizando otros nombres de archivos que también se emplean en aplicaciones web, por ejemplo: **default**, **home**, **main**, **portal**, **dashboard** o **app**.


## Fuzzing de extensiones de archivos con Ffuf
Para realizar este tipo de fuzzing en ffuf con el nombre de archivo **index** podemos usar el siguiente comando:

``` sh
ffuf -u http://TARGET_IP:PORT/indexFUZZ -w /usr/share/seclists/Discovery/Web-Content/web-extensions.txt:FUZZ
```

Esto realizara una busqueda de archivos como **index.php**, **index.html**, **index.*** utilizando las extensiones que tiene la wordlist.

Podemos utilizar dos wordlist para realizar un fuzzing a diferentes nombres de archivos con diferentes extensiones:

``` sh
ffuf -u http://TARGET_IP:PORT/NAMESEXT -w common_entry_names.txt:NAMES -w /usr/share/seclists/Discovery/web-extensions.txt:EXT
```

!!! warning "Placeholder de la wordlist"
    Es importante no olvidar asignar un placeholder a las dos wordlists y posicionarlas en la URL de la manera adecuada.


## Fuzzing de extensiones de archivos con Gobuster