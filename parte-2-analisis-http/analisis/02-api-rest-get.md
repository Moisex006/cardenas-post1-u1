# Análisis 2: Petición GET — API REST (jsonplaceholder.typicode.com)

## Caso 1: Recurso existente (200 OK)

### Información general
- URL: https://jsonplaceholder.typicode.com/posts/1
- Método: GET
- Código de estado: 200 OK

### Headers de Request
| Header | Valor |
|--------|-------|
| Host (:authority) | jsonplaceholder.typicode.com |
| User-Agent | Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/151.0.0.0 Safari/537.36 |
| Accept | text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8 |

### Headers de Response
| Header | Valor | Significado |
|--------|-------|-------------|
| Content-Type | application/json; charset=utf-8 | Indica que el cuerpo de la respuesta es un objeto JSON, no HTML — el cliente debe parsearlo como datos, no renderizarlo. |
| Cache-Control | max-age=43200 | El recurso puede almacenarse en caché hasta por 43200 segundos (12 horas) antes de considerarse obsoleto. |
| Cf-Cache-Status | HIT | La respuesta fue servida desde la caché de Cloudflare. |
| X-Powered-By | Express | Revela que el backend está construido con el framework Express (Node.js). |
| X-Ratelimit-Limit / Remaining | 1000 / 999 | Headers de límite de peticiones (rate limiting): la API permite 1000 peticiones en la ventana actual, de las cuales quedan 999 disponibles. |

### Respuesta (Response)
Objeto JSON con los campos `userId`, `id`, `title` y `body` correspondientes al post con id 1.

---

## Caso 2: Recurso inexistente (404 Not Found)

### Información general
- URL: https://jsonplaceholder.typicode.com/posts/999
- Método: GET
- Código de estado: 404 Not Found

### Headers relevantes
| Header | Valor |
|--------|-------|
| Content-Type | application/json; charset=utf-8 |
| Content-Length | 2 |
| Cf-Cache-Status | HIT |

El cuerpo de la respuesta es un objeto JSON vacío (`{}`, de ahí el Content-Length de solo 2 bytes), ya que el recurso solicitado no existe en la base de datos de la API.

---

## Comparación: Petición HTML vs API REST

| Aspecto | example.com (Paso 7) | jsonplaceholder API |
|---|---|---|
| Content-Type | text/html | application/json |
| Formato del cuerpo | Documento HTML completo | Objeto/estructura de datos JSON |
| Propósito | Ser renderizado visualmente por el navegador | Ser consumido/parseado por código (frontend, apps, scripts) |
| Headers adicionales | Ninguno específico de API | Rate limiting (X-Ratelimit-*), framework backend (X-Powered-By) |

## Conclusión
La comparación entre ambas peticiones GET evidencia una diferencia fundamental en el `Content-Type`: mientras example.com devuelve `text/html` para ser interpretado visualmente por el navegador, la API REST responde con `application/json`, un formato pensado para ser consumido programáticamente. El caso del recurso inexistente (`/posts/999`) demuestra el comportamiento estándar de una API REST bien diseñada: en lugar de fallar silenciosamente, devuelve un código `404 Not Found` explícito junto con un cuerpo JSON vacío, permitiendo que el cliente maneje el error de forma predecible. Además, los headers `X-Ratelimit-*` presentes solo en la API reflejan una práctica común para proteger recursos de backend contra abuso, algo que no aplica a una página estática como example.com. En ambos casos Cloudflare actuó como capa de caché (`Cf-Cache-Status: HIT`), reduciendo la carga sobre el servidor de origen incluso para respuestas de error como el 404.