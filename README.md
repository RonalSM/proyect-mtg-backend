# MTGC Backend Server (Mesa Virtual de Commander MTG)

Servidor Fastify, motor de juego autoritativo en tiempo real por WebSocket, ORM Prisma y sincronización con Scryfall para la Mesa Virtual de Commander (MTG).

## 🚀 Despliegue en Render

Este repositorio está optimizado para ejecutarse en el tier gratuito de **Render** (o cualquier PaaS Node.js) con un consumo de memoria mínimo (< 100MB de RAM en compilación y ~80MB en ejecución).

### Configuración en Render:

- **Build Command**: `npm install && npm run build`
- **Start Command**: `npm start`
- **Health Check Path**: `/api/health`
- **Node Version**: 20.x o 22.x

### Variables de Entorno requeridas en Render:

| Variable              | Descripción                           | Ejemplo / Valor                                     |
| --------------------- | ------------------------------------- | --------------------------------------------------- |
| `NODE_ENV`            | Entorno de ejecución                  | `production`                                        |
| `PORT`                | Puerto asignado por Render            | `10000`                                             |
| `HOST`                | Interfaz de escucha                   | `0.0.0.0`                                           |
| `DATABASE_URL`        | Conexión PostgreSQL                   | Cadena generada por Render PostgreSQL o Supabase    |
| `SESSION_SECRET`      | Secreto para cookies cifradas         | Cadena aleatoria de al menos 32 caracteres          |
| `JWT_SECRET`          | Secreto para tokens JWT               | Cadena aleatoria de al menos 32 caracteres          |
| `SCRYFALL_USER_AGENT` | User-Agent según política de Scryfall | `MTGCommanderVirtualTable/1.0.0 (admin@mtgc.local)` |

---

## 💻 Desarrollo Local

### 1. Instalar dependencias

```bash
npm install
```

### 2. Generar cliente Prisma y compilar paquetes

```bash
npm run build
```

### 3. Ejecutar pruebas unitarias e integración (93 pruebas)

```bash
npm test
```

### 4. Iniciar en modo desarrollo con recarga automática

```bash
npm run dev
```

El servidor estará escuchando en `http://localhost:3001` con soporte completo de WebSockets en `ws://localhost:3001/ws/table/:roomCode`.
