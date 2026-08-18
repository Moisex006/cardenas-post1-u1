# Post-contenido — Unidad 1: Fundamentos de la Web

## Descripción
Repositorio del laboratorio de la Unidad 1 de Programación Web —
Séptimo Semestre. Contiene dos partes: configuración del entorno
de desarrollo (parte-1-entorno/) y análisis de peticiones HTTP con
Chrome DevTools y Postman (parte-2-analisis-http/).

## Parte 1 — Entorno de desarrollo
Página HTML básica (header, main, footer y dos secciones) con estilos
CSS y script JS, inspeccionada con Chrome DevTools (paneles Elements,
Styles y Console). Incluye un efecto hover agregado con transición CSS.
Ver `parte-1-entorno/`.


## Parte 2 — Análisis de peticiones HTTP
| # | Tipo | URL | Código |
|---|------|-----|--------|
| 1 | GET HTML | https://example.com | 200 OK |
| 2 | GET JSON (exitoso) | /posts/1 | 200 OK |
| 3 | GET JSON (fallido) | /posts/999 | 404 Not Found |
| 4 | POST JSON | /posts | 201 Created |


## Herramientas utilizadas
- VS Code, Git, GitHub
- Google Chrome + DevTools (paneles Elements, Console, Network, Timing)
- Postman (petición POST con tests automatizados)

## Conclusiones
Este laboratorio permitió comprender de forma práctica cómo funciona el ciclo de vida
de una petición HTTP, desde la solicitud de un documento HTML estático hasta el consumo
y creación de recursos en una API REST. Se identificaron diferencias clave entre los
métodos GET y POST, entre respuestas exitosas y de error (200/404 vs 201), y entre
contenido HTML y JSON a través del header Content-Type. El uso combinado de Chrome
DevTools y Postman demostró ser fundamental para depurar aplicaciones web: DevTools
permite inspeccionar peticiones reales del navegador con todo detalle de tiempos y
headers, mientras que Postman facilita construir, probar y automatizar peticiones
personalizadas mediante tests. En conjunto, estas herramientas son esenciales para
cualquier desarrollador que necesite diseñar, consumir o depurar comunicaciones
cliente-servidor.