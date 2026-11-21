# tienda-api (PC02 - Despliegue de Aplicaciones)

API de ejemplo sin dependencias. Requiere Node.js 20 o superior.

    npm test            # ejecuta las pruebas
    npm run test:cov    # pruebas con cobertura
    npm start           # inicia el servidor en el puerto 3000
    node verificar.mjs  # autoverificación de la parte práctica
    npm run pipeline    # pruebas y notificación a Slack (requiere SLACK_WEBHOOK_URL)

Rutas actuales: `/productos` y `/total?ids=1,2&cupon=DESC10`.
Las instrucciones de la práctica están en el enunciado de la PC02.

## Rutas

- `/health` responde 200 con `{"status":"ok"}`.
- `/ready` responde 200 con `{"status":"listo"}`, o 503 si `BASE_DE_DATOS_OK=false`.
- Cada petición escribe una línea JSON en consola (`ts`, `level`, `msg`, `method`, `path`, `status`, `ms`).

## Notificación a Slack

    SLACK_WEBHOOK_URL=<webhook> node notificar.mjs exito
    SLACK_WEBHOOK_URL=<webhook> node notificar.mjs error "detalle"

El webhook se lee solo de la variable de entorno `SLACK_WEBHOOK_URL` (en CI, del secret del mismo nombre).

## Despliegue (T5)

- Plataforma: Render (Web Service, runtime Node, comando de inicio `npm start`; configuración en `render.yaml`).
- URL pública: https://aguilar-contreras-pc2.onrender.com (verificar `<URL>/health` responde 200 con `{"status":"ok"}`).
