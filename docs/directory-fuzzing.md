# FUZZING DE DIRECTORIOS

!!! tip "Wordlist adecuada para fuzzing de directorios"
    La wordlist de **seclists** llamada **directory-list-2.3-medium.txt** es una de las mejores para empezar este tipo de fuzzing.

## Fuzzing de directorios con Ffuf
!!! note "Parámetro -ic"
    El parámetro **-ic** nos permite evitar que los comentarios en una wordlist se tomen como parte de la lista.

Para listar directorios debemos especificar dos parámetros:

- `-u`: Especifica la URL del objetivo.
- `-w`: Define la wordlist que se usará para el fuzzing.


!!! note "Placeholder / Palabra clave"
    Por defecto la palabra que utiliza ffuf es **FUZZ**, aún si no le asignamos algún placeholder a la wordlist, se puede usar esta palabra para realizar la operación de fuzzing.

Además a la wordlist le podemos asignar un placeholder (palabra clave) para identificarla con el formato `wordlist_path:placeholder`.

``` sh
ffuf -u http://TARGET_IP:PORT/FUZZ -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt:FUZZ -ic
```

Además podemos utilizar los siguientes parámetros para realizar un fuzzing más eficiente:

- `t`: Número de hilos (threads). Usado para aumentar o disminuir la velocidad del fuzzing (40 por defecto).
- `timeout`: Tiempo máximo de espera por petición en segundos (10 por defecto).
- `v`: Muestra información detallada (verbose).
- `o`: Permite guardar la salida en un archivo.
- `of`: El formato de archivo usado para guardarlo.
- `recursion`: Activa el modo recursivo.
- `recursion-depth`: Limita la profundidad de la recursión.

El comando completo para un fuzzing de directorios suelen ser como el siguiente:

``` sh
ffuf -u http://TARGET_IP:PORT/FUZZ -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt:FUZZ -ic -t 200 -timeout 5 --recursion --recursion-depth 2 -v -o nombre_archivo.html -of html
```

## Fuzzing de directorios con Gobuster


## Fuzzing de directorios con Burp Intruder


## Fuzzing de directorios con ZAP Fuzzer