# Panel Gastos Logísticos

Panel de gastos operativos y logísticos, conectado a Supabase. Es una app de **un solo archivo** (`index.html`) — no necesita build ni dependencias: usa Chart.js, SheetJS y Supabase por CDN.

## Funcionalidades
- Métricas, dona, evolución mensual y comparativa por categoría.
- Resumen por mes (respeta el filtro de categoría) y conteo de envíos.
- Alta manual de gastos y borrado.
- **Carga masiva** desde CSV / Excel con perfiles por sector:
  - **AMBA Flex** → Envíos Flex ML (anti-duplicados por ID Cardinal).
  - **Tiendas** → ICBC, Frávega, Megatone, OnCity (por `# Venta`).
  - **Distribución ARGC** → multi-hoja: CORP, Retiro Proveedores, Spot, Distribución.
- **Exportar a Excel** eligiendo categoría y rango de fechas.

## Configuración
En el `<script>` de `index.html` se completan:
```js
const SUPABASE_URL = '...';
const SUPABASE_ANON_KEY = '...';
```

## Base de datos (Supabase)
- Tabla `gastos`: agregados diarios que muestra el panel.
- Tabla `envios`: un registro por envío/remito (anti-duplicados), desde la que se regeneran los totales diarios.

## Deploy
Sitio estático. Se publica en Vercel apuntando a este repo (sin configuración de build).
