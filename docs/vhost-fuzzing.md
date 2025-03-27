# FUZZING DE VHOSTS

!!! tip "Wordlist adecuada para fuzzing de extensiones de archivos"
    La wordlist de **seclists** llamada **subdomains-top1million-20000.txt** es una de las mejores para empezar este tipo de fuzzing.

El **fuzzing de vhosts** se centra en detectar configuraciones de servidores web que utilizan **virtual hosting**. En este caso, un mismo servidor puede alojar múltiples sitios web, diferenciados por el valor del encabezado `Host` en las peticiones HTTP.

## Fuzzing de vhosts con Ffuf
A diferencia del fuzzing de subdominios, en el fuzzing de vhosts el fuzzing se va a realizar en el header `Host` en lugar de la URL. Para ello primero tenemos que pasar dicho header con ffuf.

* `Host: http://FUZZ.TARGET_IP:PORT`

``` sh
ffuf -u 'http://TARGET_IP:PORT' -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt:FUZZ -H 'Host: FUZZ.TARGET_IP'
```


## Fuzzing de vhosts con Gobuster
