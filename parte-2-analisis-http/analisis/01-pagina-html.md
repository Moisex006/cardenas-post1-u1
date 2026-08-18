# Análisis 1: Petición GET — example.com

## Información general
- URL: https://example.com/
- Método: GET
- Código de estado: 200 OK

## Headers de Request
| Header | Valor |
|--------|-------|
| Host (:authority) | example.com |
| User-Agent | Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/151.0.0.0 Safari/537.36 |
| Accept | text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8 |

## Headers de Response
| Header | Valor | Significado |
|--------|-------|-------------|
| Content-Type | text/html | Indica que el cuerpo de la respuesta es un documento HTML, por lo que el navegador debe interpretarlo y renderizarlo como una página web. |
| Cache-Control | (no presente en la respuesta) | No se envió este header explícitamente; en su lugar se observa `Age: 4333`, que indica que la respuesta llevaba 4333 segundos almacenada en la caché de Cloudflare (CDN) antes de ser entregada. |
| Cf-Cache-Status | HIT | Header específico de Cloudflare que confirma que la respuesta fue servida desde la caché del CDN, no generada en tiempo real por el servidor de origen. |
| Server | cloudflare | Indica que la infraestructura que sirve el sitio está detrás de una red de distribución de contenido (CDN) de Cloudflare. |

## Tiempos de carga
| Fase | Tiempo (ms) |
|------|------------|
| Queueing | 1.16 |
| Stalled (inicio de conexión) | 0.89 |
| Request sent | 0.23 |
| Waiting for server response (TTFB) | 323.38 |
| Content Download | 0.59 |
| **Total** | **326.25** |



## Conclusión
La petición GET a example.com obtuvo un código 200 OK, indicando que el recurso se entregó exitosamente. El header `Content-Type: text/html` confirma que se trata de un documento HTML estándar, mientras que la presencia de `Cf-Cache-Status: HIT` y `Server: cloudflare` revela que el sitio está protegido y acelerado por una CDN, lo cual reduce la carga en el servidor de origen. El tiempo total de la petición fue de 326.25 ms, dominado casi por completo por la fase "Waiting for server response" (TTFB) con 323.38 ms, mientras que la descarga del contenido fue prácticamente instantánea (0.59 ms), lo cual es consistente con el tamaño reducido del HTML de example.com. La ausencia de fases de DNS Lookup y SSL en el timing sugiere que el navegador reutilizó una conexión ya establecida con el servidor.