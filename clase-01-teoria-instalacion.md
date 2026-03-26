# Clase 1 — Teoría + Instalación de Claude Code

**Duración:** 2 horas
**Objetivo:** Reforzar los conceptos del README, resolver dudas, instalar Claude Code y lograr la primera interacción.

---

## Parte 1 — Bienvenida y contexto (10 min)

> Preguntar al grupo: "¿Quiénes ya han usado ChatGPT o Claude en el navegador? ¿Para qué lo usan?"

### Repasar brevemente

Los alumnos ya leyeron el README. Reforzar los puntos clave sin repetir todo:

- **El problema:** copiar-pegar, sin acceso a archivos, sin memoria, sin conexiones
- **La solución:** Claude Code — Claude con acceso a tu computador
- Preguntar: *"¿Quedó alguna duda del README?"*

---

## Parte 2 — Demo en vivo: La Terminal (15 min)

> Abrir la terminal en pantalla compartida y ejecutar cada comando mientras los alumnos siguen en su computador.

```bash
pwd              # "¿Dónde estoy?"
ls               # "¿Qué hay acá?"
cd Escritorio    # Entrar a una carpeta
ls               # Ver qué hay
cd ..            # Volver atrás
mkdir taller-claude   # Crear carpeta
cd taller-claude
pwd              # Confirmar que estamos adentro
```

### Ejercicio (3 min)

> "Abran su terminal, naveguen al escritorio y creen la carpeta `taller-claude`. Levanten la mano cuando estén adentro."

Verificar con el grupo. Resolver problemas comunes:
- Mac: "Terminal" no aparece → buscar en Aplicaciones > Utilidades
- Windows: usar PowerShell, no CMD

---

## Parte 3 — Conceptos clave en profundidad (25 min)

> Esta sección es conversacional. Usar las analogías del README pero ir más profundo con preguntas y ejemplos.

### CLI y paquetes (5 min)

Reforzar:
- CLI = programa que se usa escribiendo, no haciendo clic
- npm = App Store de la terminal
- Un solo comando instala Claude Code

> Preguntar: *"¿Alguien ha usado algún programa desde la terminal antes?"*

### Claude Code vs. chat web — demo en vivo (10 min)

> Abrir claude.ai en el navegador y hacer una tarea. Luego hacer la misma tarea en Claude Code para mostrar la diferencia.

**Demo sugerida:**
1. En claude.ai: pegar un texto y pedir que lo resuma
2. En Claude Code: *"Lee el archivo notas.txt y resúmelo"* (crear el archivo antes)

Destacar: "No copié nada. Claude leyó el archivo directo."

### Estático vs. dinámico (10 min)

> Este concepto es fundamental. Usar ejemplos concretos del trabajo de los alumnos.

Dibujar en pizarra/pantalla:

```
TU COMPUTADOR                    LA NUBE (Neon)
├── CLAUDE.md (reglas)           ├── clientes
├── templates/ (formatos)        ├── ventas
└── instrucciones/               └── métricas

    "CÓMO trabajar"              "CON QUÉ trabajar"
```

> Preguntar: *"En su trabajo, ¿qué información es estática y cuál es dinámica?"*

Ejemplos para guiar la conversación:
- Estático: el formato del reporte semanal, las reglas de descuento, el template de propuesta
- Dinámico: la lista de clientes, las ventas del mes, el inventario

---

## Parte 4 — Instalación guiada (30 min)

> Ir paso a paso. Esperar a que todos terminen cada paso antes de avanzar.

### Paso 1: Node.js

```bash
node --version
```

> "¿A quién le apareció un número? Perfecto, ya lo tienen. ¿A quién le dijo 'command not found'?"

Para los que necesitan instalar:
- **Mac:** `brew install node` (o descargar de nodejs.org)
- **Windows:** `winget install OpenJS.NodeJS.LTS` (o descargar de nodejs.org)

Verificar:
```bash
node --version
npm --version
```

> "Levanten la mano cuando ambos comandos muestren un número."

### Paso 2: Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

> Esperar. Puede tomar 1-2 minutos. Si alguien tiene error de permisos en Mac: `sudo npm install -g @anthropic-ai/claude-code`

Verificar:
```bash
claude --version
```

### Paso 3: Autenticación

```bash
cd ~/Desktop/taller-claude
claude
```

> "Se les va a abrir el navegador. Inicien sesión con su cuenta de Anthropic. Si no tienen cuenta, créenla ahora — es gratis con el trial."

> Esperar a que todos estén dentro de Claude Code.

---

## Parte 5 — Primera interacción (30 min)

> Todos deben tener Claude Code abierto. Ir haciendo cada ejercicio juntos.

### Ejercicio 1: Explorar (5 min)

```
> ¿Qué archivos hay en esta carpeta?
```

> Mostrar cómo Claude lee la carpeta y responde. Señalar que pidió permiso antes de ejecutar el comando.

### Ejercicio 2: Crear un archivo (5 min)

```
> Crea un archivo llamado notas.txt con las tareas pendientes de esta semana:
> 1. Enviar propuesta a cliente Acme
> 2. Preparar reporte mensual de ventas
> 3. Agendar reunión con equipo de operaciones
```

> Mostrar: Claude muestra qué va a hacer → pide permiso → crea el archivo → confirma.

> "Abran su Finder o Explorador de archivos y busquen la carpeta taller-claude. ¿Ven el archivo? Claude lo creó de verdad."

### Ejercicio 3: Trabajar con datos (10 min)

```
> Crea un archivo CSV llamado ventas-ejemplo.csv con datos ficticios de ventas:
> 10 filas, con columnas: fecha, cliente, producto, cantidad, monto en CLP
```

Ahora analizar:

```
> ¿Cuál fue el cliente con más ventas en total?
```

```
> Haz un resumen ejecutivo de las ventas por producto
```

> Destacar: "No copié ningún dato. Claude leyó el CSV directo."

### Ejercicio 4: Redactar contenido (5 min)

```
> Redacta un email profesional para un cliente que se llama María, agradeciéndole
> su compra y ofreciéndole un 10% de descuento en su próxima orden
```

```
> Ahora hazlo más corto y directo, estilo WhatsApp
```

> Mostrar cómo se puede iterar pidiendo cambios.

### Ejercicio 5: El sistema de permisos (5 min)

> Explicar mientras se trabaja:

- **y** (yes) — Permitir esta vez
- **n** (no) — Rechazar
- **a** (always) — Permitir siempre para este tipo de acción

> "Si no están seguros de lo que Claude va a hacer, respondan **n** y pídanle que explique primero. Siempre tienen el control."

---

## Cierre (10 min)

### Resumen rápido

> Preguntar: *"¿Qué fue lo que más les sorprendió?"*

Reforzar:
- Claude Code = Claude con acceso a tu computador
- Se instala una vez, se autentica una vez
- Siempre pide permiso — tú tienes el control

### Para la próxima clase

- Tener Claude Code funcionando
- Traer un **archivo real** de su trabajo (CSV, planilla, documento)
- Pensar en **tareas repetitivas** que hacen seguido

> "La próxima clase vamos a trabajar con sus datos reales y vamos a conectarnos a una base de datos en la nube."
