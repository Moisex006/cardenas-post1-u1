### Headers relevantes de la respuesta
| Header | Valor observado | Significado |
|--------|-------|-------------|
| Content-Type | application/json; charset=utf-8 | El cuerpo de la respuesta es un objeto JSON. |
| Location | https://jsonplaceholder.typicode.com/posts/101 | Header estándar de una respuesta 201 Created: apunta a la URL del nuevo recurso creado (el post con id 101). |
| X-Powered-By | Express | El backend está construido con el framework Express (Node.js). |
| Cf-Cache-Status | DYNAMIC | A diferencia de las peticiones GET anteriores (que mostraban HIT), esta respuesta no se sirvió desde caché — Cloudflare la marca como dinámica porque las peticiones POST no son cacheables al modificar el estado del servidor. |
| Cache-Control | no-cache | Confirma que esta respuesta no debe almacenarse en caché, coherente con tratarse de una operación de creación. |