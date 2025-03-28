# INTERCEPTAR RESPUESTAS WEB

Interceptar las respuestas web significa capturar y analizar los datos que el servidor devuelve al cliente y tener la posibilidad de modificarlos. Esto nos permite modificar como luce la página web, como habilitar o deshabilitar ciertos campos ocultos.

## Interceptar respuestas web en Burp Suite
En Burp Suite tenemos que habilitar la intercepción de respuestas, para ello iremos a la pestaña de **Proxy > Intercept > Proxy Settings**.

![burp suite proxy settings](assets/burp_suite_proxy_settings.png)

Y en **Tools > Proxy** buscaremos el apartado que diga **Response interception rules** habilitando la opción `Intercept responses based on the following rules`. En este apartado podemos también modificar las reglas de intercepción de respuestas web.

![burp_suite_response_interception](assets/burp_suite_response_interception.png)

Ahora podemos interceptar las respuestas del servidor y modificarlas antes de que lleguen al cliente.

![burp suite response hentaila](assets/burp_suite_response_hentaila.png)

![burp suite response dom](assets/burp_suite_response_dom.png)

Y como podemos ver, ahora cuando damos **Forward** aparece con el título que hemos modificado en la respuesta.

![burp suite intercepted response](assets/burp_suite_intercepted_response.png)

## Interceptar respuestas web en ZAP