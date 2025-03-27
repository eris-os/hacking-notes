# FUZZING DE SUBDOMINIOS

!!! tip "Wordlist adecuada para fuzzing de extensiones de archivos"
    La wordlist de **seclists** llamada **subdomains-top1million-20000.txt** es una de las mejores para empezar este tipo de fuzzing.

El **fuzzing de subdominios** busca descubrir nombres de subdominios asociados a un dominio principal. Esto se hace probando combinaciones de palabras (como `admin`, `dev`, `test`, `blog`, etc.) y verificando si existen entradas DNS válidas o si resuelven una dirección IP.

## Fuzzing de subdominios con Ffuf
Para realizar fuzzing de subdominios con ffuf utilizamos el siguiente comando:

``` sh
ffuf -u http://FUZZ.TARGET_IP:PORT/ -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt:FUZZ
```

## Fuzzing de vhosts con Gobuster
