# INTRODUCCION A LOS WEB PROXIES

Un **web proxy** actúa como un intermediario entre el cliente (navegador web o aplicación) y el servidor de destino. En lugar de conectar directamente, la petición se redirige al proxy, que luego la reenvía al servidor. En hacking la habilidad de interceptar y modificar peticiones y respuestas es fundamental.

![proxy working](assets/proxy_working.png)

Los dos web proxies más comunes son **Burp Suite** y **Zed Attack Proxy (ZAP)**.


## Navegador web preconfigurado en Burp Suite
Tanto Burp Suite como ZAP vienen con un navegador preconfigurado con la configuración correspondiente del proxy y de los certificados CA.

Para acceder al navegador configurado de **Burp Suite** vamos a ir a la pestaña **Proxy > Intercept** y en la esquina superior derecha se encuentra un botón que dice **Open browser**.

![burp suite open browser](assets/burp_suite_open_browser.png)

Esto abrirá su navegador predeterminado que suele ser un **chromium**.

## Navegador web preconfigurado en ZAP

Para abrir el navegador web preconfigurado en ZAP buscaremos el icono de firefox, usualmente es el último o penúltimo de los iconos.

![zap browser button](assets/zap_browser_button.png)

Esto abrira su navegador preconfigurado y nos aparecerá un mensaje de bienvenida como el siguiente:

![zap welcome browser](assets/zap_welcome_browser.png)

## Uso del plugin Foxy Proxy (Burp Suite y ZAP)