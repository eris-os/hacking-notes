# INTRODUCCION AL FUZZING

El **fuzzing** es una técnica que consiste en inyectar datos aleatorios, inesperados o malformados en una aplicación para observar como reacciona. La idea es provocar errores, fallos de memoria, caídas o comportamientos no deseados que puedan revelar vulnerabilidades.

## Diferencia entre fuzzing y fuerza bruta
!!! info "Sobre la terminología"
    Es común que se mezcle la terminología y se le llame *fuzzing* a *técnicas de fuerza bruta*. Ejemplo de ello es en la búsqueda de directorios que existen en una página web, esto sería en teoría fuerza bruta pero se le suele llamar de igual manera fuzzing de directorios. En la practica no es tan importante saber usar exactamente la terminología, si no más bien saber cuando y cómo realizar las técnicas.

!!! note "Terminología en las notas"
    En todas las notas usaremos indiscriminadamente los términos fuzzing y fuerza bruta sin tomar demasiado en cuenta la terminología adecuada para la técnica.

Aunque ambos métodos implican enviar múltiples solicitudes o entradas a una aplicación, existen diferencias fundamentales:

* **Objetivo:**
    * *Fuzzing*: Busca provocar fallos o comportamientos inesperados inyectando datos variados, a menudo con el propósito de descubrir vulnerabilidades en el manejo de entradas.
    * *Fuerza bruta*: Se centra en probar todas las combinaciones posibles (por ejemplo, contraseñas o nombres de usuario) para adivinar credenciales o descubrir recursos.

* **Enfoque y Metodología:**
    * *Fuzzing*: Es un enfoque exploratorio y se usa para encontrar errores en la lógica o manejo de excepciones.
    * *Fuerza bruta*: Es un enfoque sistemático y repetitivo, orientado a agotar combinaciones conocidas para acceder a un recurso específico.

## Herramientas comunes
!!! note "Herramientas usadas en las notas"
    Si bien existen diversas herramientas que permiten realizar fuzzing, en estas notas los ejemplos serán exclusivamente con **ffuf** y **gobuster**.

Entre las herramientas que se suelen usar para el fuzzing existen: **ffuf**, **gobuster**, **dirsearch**, **wfuzz**, **burp suite intruder**, **zap fuzzer**, etc.




