# Clase 2 — Práctica: Casos de uso reales con Claude Code

**Duración:** 2 horas
**Requisito:** Tener Claude Code instalado y funcionando (Clase 1).
**Objetivo:** Resolver tareas reales del trabajo: analizar datos, redactar, consultar bases de datos, personalizar el agente y automatizar.

---

## Parte 1 — Repaso y setup (10 min)

```bash
cd ~/Desktop/taller-claude
claude
```

> "¿Alguien tiene problemas para abrir Claude Code?" — Resolver ahora.

### Repaso express

> Preguntar al grupo: *"¿Qué recuerdan de la clase pasada? ¿Qué es información estática y qué es dinámica?"*

Reforzar en una frase:
- Estático (archivos locales) = cómo trabaja el agente
- Dinámico (Neon) = con qué datos trabaja

---

## Parte 2 — Caso 1: Analizar datos de un archivo (25 min)

### El escenario

> "Imaginen que tienen un CSV con las ventas del trimestre y en 30 minutos tienen una reunión de equipo. Necesitan sacar conclusiones rápido."

### Hacer juntos

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

> Dar un momento para que todos vean el resultado. Preguntar: *"¿Cuánto se habrían demorado haciendo esto en Excel?"*

**3. Profundizar:**

```
> ¿Qué vendedor tiene el ticket promedio más alto?
```

```
> ¿Hay algún cliente que haya comprado solo una vez? Podrían ser oportunidades de seguimiento.
```

> Destacar que pueden hacer preguntas de negocio en español y Claude las responde.

**4. Generar un reporte:**

```
> Crea un archivo reporte-q1.md con un reporte ejecutivo completo.
> Incluye tablas, rankings y recomendaciones de acción para el equipo.
```

> Abrir el archivo generado y mostrarlo. "Esto lo pueden compartir directo por email o Slack."

### Punto clave

> "Claude Code lee archivos CSV directamente. No copian, no pegan. Y pueden pedir análisis complejos en español."

---

## Parte 3 — Caso 2: Redacción y comunicación (20 min)

### El escenario

> "Todos los días redactan emails, mensajes de WhatsApp, propuestas. Vamos a ver cómo Claude Code acelera esto."

### Hacer juntos

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

> Mostrar cómo Claude adapta el formato y tono según el canal.

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

### Punto clave

> "Pueden iterar rápido. Piden, ajustan, piden de nuevo. Todo queda guardado en archivos que pueden reusar."

---

## Parte 4 — Caso 3: Base de datos con Neon (30 min)

### Introducción

> "Hasta ahora trabajamos con archivos locales. Pero en la vida real, los datos de clientes y ventas no deberían vivir en un CSV en tu escritorio. Vamos a conectarnos a una base de datos en la nube."

### Configuración de Neon (10 min)

> Hacer esto en pantalla compartida. Los alumnos siguen paso a paso.

**1. Crear cuenta:**
1. Ir a [neon.tech](https://neon.tech) — cuenta gratuita
2. Crear proyecto nuevo: "taller-ventas"

**2. Conectar con Claude Code:**

> Mostrar en pantalla cómo configurar el MCP de Neon en Claude Code.

> "Levanten la mano cuando estén conectados."

### Crear tablas y cargar datos (5 min)

> Hacer juntos, esperando que todos completen cada paso.

```
> Crea una tabla de clientes en Neon con: nombre, empresa, email, teléfono, ciudad, categoría (A/B/C), fecha de primer contacto.
```

```
> Crea una tabla de ventas con: fecha, cliente (que referencie a la tabla clientes), producto, cantidad, monto en CLP, estado (pendiente/pagada/vencida).
```

```
> Inserta 15 clientes ficticios pero realistas, de empresas chilenas, distribuidos entre Santiago, Valparaíso y Concepción. Mezcla categorías A, B y C.
```

```
> Inserta 40 ventas de los últimos 3 meses para esos clientes. Que haya ventas en los 3 estados.
```

### Consultar datos — la parte mágica (10 min)

> "Ahora viene lo bueno. Le van a hacer preguntas a su base de datos en español. No necesitan saber SQL."

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

> Dar espacio para que prueben sus propias preguntas. *"Háganle una pregunta que les interese de verdad."*

### Actualizar datos (5 min)

```
> Cambia la categoría del cliente "Empresa XYZ" de B a A — cerramos un deal grande con ellos.
```

```
> Marca como pagadas todas las ventas de febrero que estén pendientes.
```

> "No solo pueden consultar. Pueden actualizar datos directamente."

### Punto clave

> "Neon es su base de datos en la nube. Claude Code la consulta y modifica sin que sepan SQL. Los datos dinámicos van acá, no en archivos CSV."

---

## Parte 5 — Caso 4: CLAUDE.md — Personalizar tu agente (15 min)

### Crear las reglas

> "Hasta ahora, cada vez que le pedimos algo a Claude tenemos que ser muy específicos. ¿Y si pudiéramos definir las reglas una vez y que se apliquen siempre?"

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

> "Salgan de Claude Code con `exit` y vuelvan a entrar."

```bash
claude
```

```
> Dame el resumen de ventas del mes
```

> "¿Notaron la diferencia? No le dije en qué formato, ni en qué idioma, ni de dónde sacar los datos. Ya lo sabe."

### Agregar reglas sobre la marcha

```
> Agrega a CLAUDE.md: "Cuando el usuario pida un reporte de cobranza, siempre incluir teléfono y email del cliente para facilitar el seguimiento"
```

### Punto clave

> "CLAUDE.md es el manual de operaciones de su agente. Lo definen una vez y se aplica siempre. Pueden ir refinándolo con el tiempo."

---

## Parte 6 — Caso 5: Automatizar tareas repetitivas (15 min)

### Ejercicios prácticos

> "Vamos a ver cómo Claude Code les ahorra tiempo en tareas que hacen seguido."

**1. Crear templates reutilizables:**

```
> Crea una carpeta templates/ con los siguientes archivos:
> - email-seguimiento.md → Template de email de seguimiento con placeholders para nombre y empresa
> - reporte-semanal.md → Estructura de reporte semanal con secciones fijas
> - propuesta-comercial.md → Template de propuesta con campos para completar
```

**2. Procesar múltiples archivos:**

```
> Lee todos los archivos CSV de la carpeta y crea un resumen consolidado
> con las métricas principales de cada uno
```

**3. Generar contenido en lote:**

```
> Usando la tabla de clientes categoría A de Neon, genera un email personalizado
> de seguimiento para cada uno. Guárdalos en la carpeta emails/
```

> Abrir la carpeta emails/ y mostrar los archivos generados. "Un email personalizado para cada cliente, en segundos."

### Punto clave

> "Templates + datos de Neon + Claude Code = contenido personalizado en lote, sin esfuerzo manual."

---

## Parte 7 — Arquitectura recomendada (5 min)

> Mostrar en pantalla:

```
tu-carpeta-de-trabajo/
├── CLAUDE.md              → Reglas y contexto (ESTÁTICO)
├── templates/             → Formatos reutilizables (ESTÁTICO)
│   ├── email-seguimiento.md
│   ├── reporte-semanal.md
│   └── propuesta-comercial.md
├── instrucciones/         → Procedimientos del equipo (ESTÁTICO)
├── reportes/              → Reportes generados (OUTPUT)
└── emails/                → Comunicaciones generadas (OUTPUT)

Neon (base de datos en la nube):       → DINÁMICO
├── clientes
├── ventas
├── productos
└── seguimientos
```

> "Estático en tu carpeta, dinámico en Neon, output donde quieran."

---

## Parte 8 — Tips y buenas prácticas (5 min)

### Cómo pedir cosas efectivamente

> Mostrar la diferencia:

**Malo:** `Hazme un reporte`

**Bueno:**
```
> Genera un reporte de ventas del mes de marzo desde Neon.
> Incluye: total vendido, top 3 vendedores, top 3 productos, y ventas pendientes de pago.
> Formato: tabla markdown. Guárdalo en reportes/marzo-2025.md
```

### Las 6 reglas de oro

1. **Sé específico** — Más contexto = mejor resultado
2. **Itera** — No esperes perfección al primer intento
3. **Usa CLAUDE.md** — Define reglas una vez, no te repitas
4. **Datos en Neon** — No guardes clientes ni ventas en CSV
5. **Revisa antes de aceptar** — Lee lo que Claude propone
6. **Crea templates** — Para tareas que repites seguido

### Atajos útiles

| Atajo | Qué hace |
|---|---|
| `Tab` | Autocompletar |
| `Ctrl + C` | Cancelar lo que está haciendo |
| `Ctrl + L` | Limpiar la pantalla |
| `/help` | Ver ayuda |
| `exit` | Salir de Claude Code |

---

## Cierre (5 min)

### Ronda rápida

> Preguntar a cada alumno: *"¿Cuál es la primera tarea de su trabajo que van a hacer con Claude Code?"*

### Próximos pasos

- Llevar Claude Code a su trabajo real — empezar con algo simple
- Configurar CLAUDE.md para su equipo
- Migrar datos importantes a Neon
- Compartir templates con el equipo

> "Ya tienen todas las herramientas. Ahora es cuestión de practicar."

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Neon — Base de datos en la nube](https://neon.tech)
- [Node.js](https://nodejs.org)
