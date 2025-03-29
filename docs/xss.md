# INTRODUCCION AL CROSS-SITE SCRIPTING (XSS)

El **Cross-Site Scripting (XSS)** es una vulnerabilidad de seguridad que afecta a aplicaciones web, permitiendo a atacantes inyectar y ejecutar código malicioso en el navegador de la víctima utilizando inputs no sanitizados. Esto se traduce en una vía para robar cookies, redirigir a usuarios, manipular contenido, y en general, comprometer la integridad y privacidad de la sesión.

Existen tres tipos principales de vulnerabilidades XSS:

* **XSS Almacenado (Persistente)**: Es el tipo más crítico de XSS. El payload se almacena en el servidor y cada vez que un usuario accede a la información almacenada, el script se ejecuta en su navegador.

* **XSS Reflejado (No-persistente)**: Este tipo se da cuando el payload se envía en la solicitud HTTP (por ejemplo, en un parámetro GET o POST) y es reflejado en la respuesta del servidor. No se almacena, sino que se ejecuta en el momento en que la víctima accede a un enlace manipulado.

* **XSS DOM (No persistente)**: El ataque se ejecuta enteramente en el lado del cliente. La vulnerabilidad radica en cómo el JavaScript del sitio manipula el Document Object Model (DOM). El atacante inyecta un payload que modifica el DOM de forma inesperada, sin que el servidor intervenga directamente.