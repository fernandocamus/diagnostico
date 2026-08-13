# Mini Help Desk

Registro y seguimiento de incidencias técnicas. Stack: React 19 + Vite
(frontend), Java 21 + Spring Boot 4 (backend), PostgreSQL 16 y Docker Compose.

## Puesta en marcha

Requiere únicamente Docker (y Docker Compose). No instala Java, Node ni
PostgreSQL: las imágenes se construyen a partir de los `Dockerfile` de `backend/`
y `mi-app/`.

```bash
docker compose up --build
```

La aplicación queda disponible en <http://localhost:5173>.

- La API se publica en el mismo origen bajo `/api` (Nginx reenvía al backend);
  el backend no expone puerto en el host.
- La primera compilación descarga las dependencias de Maven y npm y puede tardar
  varios minutos; las siguientes son mucho más rápidas por el cacheo de capas.

## Configuración

Los valores de conexión, credenciales y el puerto del frontend se definen en un
archivo `.env` en la raíz. Copie `.env.example` como `.env` y ajuste lo que
necesite. Los datos se guardan en el volumen `postgres_data` y sobreviven a
`docker compose down`; solo `docker compose down -v` los elimina.

## Documentación

- [`docs/requerimientos.md`](mi-app/docs/requerimientos.md) — levantamiento de requerimientos, reglas de negocio y criterios de aceptación.
- [`docs/arquitectura.md`](mi-app/docs/arquitectura.md) — arquitectura, modelo de datos y contrato de la API.
- [`docs/decisiones.md`](mi-app/docs/decisiones.md) — decisiones técnicas y sus alternativas.
- [`docs/verificacion.md`](mi-app/docs/verificacion.md) — guía paso a paso para comprobar la solución.
