---

---

---
En esta clase trabajamos con un escenario en el que se ha implementado una defensa basada en lista blanca para mitigar ataques SSRF. A pesar de esta protección, conseguimos acceder a un endpoint interno aprovechando cómo el servidor interpreta las URLs con credenciales embebidas.

Comenzamos probando distintas variantes del parámetro ‘**stockApi**‘, observando cómo la aplicación extrae y valida el hostname. Tras verificar que se aceptan URLs con formato de usuario, utilizamos técnicas de doble codificación para manipular el valor del hostname y hacer que el servidor interprete la URL de forma diferente a como lo hace la validación.

Gracias a esto, logramos redirigir la petición al endpoint de administración alojado en ‘**localhost**‘, y ejecutamos la acción de eliminar al usuario objetivo. Esta clase muestra cómo se pueden eludir filtros aparentemente robustos manipulando los componentes de una URL.