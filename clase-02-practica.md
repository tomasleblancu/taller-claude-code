# Clase 2 — Práctica: Casos de uso reales con Claude Code

**Duración:** 2 horas
**Requisito:** Tener Claude Code instalado y funcionando (Clase 1).
**Objetivo:** Usar Claude Code para resolver tareas reales de tu trabajo: analizar datos, redactar contenido, consultar bases de datos, y automatizar tareas repetitivas.

---

## Parte 1 — Repaso y setup (15 min)

### Verificar que todo funciona

```bash
cd ~/Desktop/taller-claude
claude
```

Si alguien tiene problemas, resolverlos ahora.

### Repaso express de la Clase 1

- Claude Code vive en la terminal y tiene acceso a tus archivos
- Siempre pide permiso antes de actuar
- **Estático** (archivos locales): instrucciones, reglas, templates
- **Dinámico** (base de datos en la nube): clientes, ventas, métricas
- Se invoca con `claude` dentro de una carpeta

---

## Parte 2 — Caso 1: Analizar datos de un archivo (25 min)

### El escenario

Tienes un archivo CSV con las ventas del trimestre y necesitas sacar conclusiones rápidas para una reunión.

### Paso a paso

**1. Crear datos de ejemplo:**

```
> Crea un archivo ventas-q1-2025.csv con 30 filas de datos ficticios de ventas.
> Columnas: fecha, vendedor, cliente, producto, cantidad, monto_clp.
> Que haya 4 vendedores distintos, 8 clientes distintos, y 5 productos.
> Los montos deben ser realistas (entre 50.000 y 5.000.000 CLP).
```

**2. Pedir análisis:**

```
> Analiza ventas-q1-2025.csv y dame un resumen ejecutivo para presentar en la reunión de equipo.
> Incluye: total vendido, mejor vendedor, mejor producto, tendencia mensual.
```

**3. Profundizar:**

```
> ¿Qué vendedor tiene el ticket promedio más alto?
```

```
> ¿Hay algún cliente que haya comprado solo una vez? Podrían ser oportunidades de seguimiento.
```

**4. Generar un reporte:**

```
> Crea un archivo reporte-q1.md con un reporte ejecutivo completo.
> Incluye tablas, rankings y recomendaciones de acción para el equipo.
```

### Lo que aprendemos aquí
- Claude Code lee archivos CSV directamente — sin copiar ni pegar
- Puede hacer análisis complejos y presentarlos como quieras
- Puede generar reportes listos para compartir

---

## Parte 3 — Caso 2: Redacción y comunicación (20 min)

### El escenario

Necesitas redactar distintos tipos de comunicación para tu trabajo diario.

### Ejercicios

**1. Email de seguimiento:**

```
> Redacta un email de seguimiento para un cliente llamado Rodrigo Fuentes de la empresa TechCorp.
> Le enviamos una propuesta hace 5 días y no ha respondido.
> Tono: profesional pero cercano. No agresivo.
```

**2. Iterar sobre el tono:**

```
> Hazlo más corto, máximo 4 líneas. Va para WhatsApp, no email.
```

**3. Propuesta comercial:**

```
> Crea una propuesta comercial en formato markdown para el cliente TechCorp.
> Ofrecemos: plan de software por 500.000 CLP/mes, incluye soporte 24/7 y 5 licencias.
> La propuesta debe tener: resumen ejecutivo, detalle del servicio, precios, y próximos pasos.
```

**4. Comunicación interna:**

```
> Redacta un mensaje para Slack avisando al equipo que cerramos la venta con TechCorp.
> Incluye el monto y agradece al equipo de operaciones por el apoyo.
```

### Lo que aprendemos aquí
- Claude Code puede adaptar tono y formato según el canal (email, WhatsApp, Slack)
- Puedes iterar rápidamente pidiendo cambios
- Los archivos generados quedan guardados en tu carpeta para reusar

---

## Parte 4 — Caso 3: Base de datos con Neon (30 min)

### ¿Por qué una base de datos?

En la Clase 1 aprendimos que los datos dinámicos (clientes, ventas, etc.) no deben vivir en archivos locales. Ahora vamos a usar **Neon** — una base de datos en la nube que Claude Code puede consultar directamente.

### Configuración de Neon

**1. Crear cuenta en Neon:**

1. Ve a [neon.tech](https://neon.tech) y crea una cuenta gratuita
2. Crea un nuevo proyecto (ponle un nombre como "taller-ventas")
3. Neon te dará una URL de conexión — la necesitaremos en un momento

**2. Conectar Claude Code con Neon:**

Claude Code se conecta a Neon a través de MCP. La configuración se hace una vez y queda lista para siempre.

> **Nota para el instructor:** Mostrar en pantalla cómo configurar el MCP de Neon en Claude Code.

### Crear tablas y cargar datos

Una vez conectado, puedes hablarle a tu base de datos en español:

**1. Crear la estructura:**

```
> Crea una tabla de clientes en Neon con: nombre, empresa, email, teléfono, ciudad, categoría (A/B/C), fecha de primer contacto.
```

```
> Crea una tabla de ventas con: fecha, cliente (que referencie a la tabla clientes), producto, cantidad, monto en CLP, estado (pendiente/pagada/vencida).
```

**2. Cargar datos:**

```
> Inserta 15 clientes ficticios pero realistas, de empresas chilenas, distribuidos entre Santiago, Valparaíso y Concepción. Mezcla categorías A, B y C.
```

```
> Inserta 40 ventas de los últimos 3 meses para esos clientes. Que haya ventas en los 3 estados.
```

### Consultar datos como si fuera una conversación

Aquí es donde ocurre la magia — **no necesitas saber SQL**:

```
> ¿Cuántos clientes categoría A tenemos en Santiago?
```

```
> ¿Cuál es el monto total de ventas pendientes de pago?
```

```
> Muéstrame los 5 clientes con más ventas acumuladas
```

```
> ¿Qué clientes no han comprado nada en el último mes? Podrían estar en riesgo de churn.
```

### Actualizar datos

```
> Cambia la categoría del cliente "Empresa XYZ" de B a A — cerramos un deal grande con ellos.
```

```
> Marca como pagadas todas las ventas de febrero que estén pendientes.
```

### Generar reportes desde la base de datos

```
> Genera un reporte de cobranza: lista todas las ventas vencidas, ordenadas por monto.
> Incluye el nombre del cliente, su email y teléfono para que el equipo pueda contactarlos.
```

### Lo que aprendemos aquí
- Neon es tu base de datos en la nube — accesible desde cualquier lugar
- Claude Code consulta y modifica datos directamente, sin que sepas SQL
- La información dinámica (clientes, ventas) vive en Neon, no en archivos CSV
- Puedes generar reportes combinando datos de la base con templates locales

---

## Parte 5 — Caso 4: CLAUDE.md — Personalizar tu agente (15 min)

### Crear las reglas de tu equipo

```
> Crea un archivo CLAUDE.md con las siguientes reglas para nuestro equipo de ventas:
>
> - Responde siempre en español
> - Los montos siempre en CLP, con separador de miles (punto)
> - Formato de fecha: DD/MM/YYYY
> - Cuando generes reportes, usa formato markdown con tablas
> - Los datos de clientes son confidenciales — nunca los muestres en resúmenes públicos
> - Nuestra base de datos en Neon tiene las tablas: clientes y ventas
> - Para comunicaciones con clientes, usa tono profesional pero cercano
```

### Probar que funciona

Cierra Claude Code (`exit`) y vuelve a abrirlo:

```bash
claude
```

Ahora pide algo sin especificar formato:

```
> Dame el resumen de ventas del mes
```

Claude debería automáticamente:
- Responder en español
- Usar formato de fecha DD/MM/YYYY
- Mostrar montos en CLP con separador de miles
- Consultar la base de datos Neon

### Agregar instrucciones específicas

```
> Agrega a CLAUDE.md: "Cuando el usuario pida un reporte de cobranza, siempre incluir teléfono y email del cliente para facilitar el seguimiento"
```

### Lo que aprendemos aquí
- CLAUDE.md es la forma de entrenar a tu agente sin repetirte
- Define una vez, aplica siempre
- Puedes ir refinando las reglas a medida que trabajas

---

## Parte 6 — Caso 5: Automatizar tareas repetitivas (15 min)

### El escenario

Hay tareas que haces todos los días o todas las semanas que podrían hacerse más rápido.

### Ejemplos prácticos

**1. Organizar archivos:**

```
> Tengo varios archivos sueltos en esta carpeta. Organízalos en subcarpetas por tipo:
> documentos/, datos/, reportes/
```

**2. Crear templates reutilizables:**

```
> Crea una carpeta templates/ con los siguientes archivos:
> - email-seguimiento.md → Template de email de seguimiento con placeholders para nombre y empresa
> - reporte-semanal.md → Estructura de reporte semanal con secciones fijas
> - propuesta-comercial.md → Template de propuesta con campos para completar
```

**3. Procesar múltiples archivos:**

```
> Lee todos los archivos CSV de la carpeta datos/ y crea un resumen consolidado
> con las métricas principales de cada uno
```

**4. Generar contenido en lote:**

```
> Usando la tabla de clientes categoría A de Neon, genera un email personalizado
> de seguimiento para cada uno. Guárdalos en la carpeta emails/
```

### Lo que aprendemos aquí
- Claude Code puede trabajar con múltiples archivos a la vez
- Los templates te ahorran tiempo en tareas repetitivas
- Puedes combinar datos de Neon con templates locales para generar contenido personalizado

---

## Parte 7 — Arquitectura recomendada (10 min)

### Cómo organizar tu espacio de trabajo

```
tu-carpeta-de-trabajo/
├── CLAUDE.md              → Reglas y contexto de tu equipo (ESTÁTICO)
├── templates/             → Formatos reutilizables (ESTÁTICO)
│   ├── email-seguimiento.md
│   ├── reporte-semanal.md
│   └── propuesta-comercial.md
├── instrucciones/         → Procedimientos del equipo (ESTÁTICO)
│   ├── como-clasificar-clientes.md
│   └── proceso-de-cobranza.md
├── reportes/              → Reportes generados (OUTPUT)
│   ├── reporte-q1-2025.md
│   └── cobranza-marzo.md
└── emails/                → Comunicaciones generadas (OUTPUT)

Neon (base de datos en la nube):       → DINÁMICO
├── clientes
├── ventas
├── productos
└── seguimientos
```

### La regla de oro

| Tipo de información | Dónde va | Ejemplos |
|---|---|---|
| **Estática** — Cambia poco, define cómo trabaja el agente | Archivos locales | CLAUDE.md, templates, instrucciones |
| **Dinámica** — Cambia constantemente, crece con el tiempo | Neon (base de datos) | Clientes, ventas, métricas, inventario |
| **Output** — Lo que genera Claude | Archivos locales (temporal) | Reportes, emails, propuestas |

---

## Parte 8 — Tips y buenas prácticas (10 min)

### Cómo pedir cosas efectivamente

**Malo:**
```
> Hazme un reporte
```

**Bueno:**
```
> Genera un reporte de ventas del mes de marzo desde Neon.
> Incluye: total vendido, top 3 vendedores, top 3 productos, y ventas pendientes de pago.
> Formato: tabla markdown. Guárdalo en reportes/marzo-2025.md
```

### Reglas de oro

1. **Sé específico** — Mientras más contexto, mejor resultado
2. **Itera** — No esperes perfección al primer intento. Pide ajustes
3. **Usa CLAUDE.md** — Define tus reglas una vez para no repetirte
4. **Datos dinámicos en Neon** — No guardes clientes, ventas ni métricas en archivos CSV
5. **Revisa antes de aceptar** — Lee lo que Claude propone antes de dar permiso
6. **Crea templates** — Para tareas que repites seguido, ten un formato listo

### Atajos útiles

| Atajo | Qué hace |
|---|---|
| `Tab` | Autocompletar |
| `Ctrl + C` | Cancelar lo que está haciendo |
| `Ctrl + L` | Limpiar la pantalla |
| `/help` | Ver ayuda |
| `exit` | Salir de Claude Code |

---

## Cierre

### Lo que aprendimos hoy
1. Analizar archivos CSV y generar reportes
2. Redactar comunicaciones adaptadas a distintos canales
3. Usar Neon como base de datos para información dinámica
4. Personalizar el agente con CLAUDE.md
5. Automatizar tareas repetitivas con templates y procesamiento en lote
6. Separar información estática (local) de dinámica (Neon)

### Próximos pasos
- Lleva Claude Code a tu trabajo real — empieza con una tarea simple
- Configura CLAUDE.md para tu equipo
- Migra tus datos importantes a Neon (no más CSV de clientes en el escritorio)
- Comparte los templates con tu equipo

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Neon — Base de datos en la nube](https://neon.tech)
- [Node.js](https://nodejs.org)
