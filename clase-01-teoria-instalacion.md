# Clase 1 — Teoría + Instalación de Claude Code

**Duración:** 2 horas
**Objetivo:** Entender qué es Claude Code, por qué es más potente que el chat web, e instalarlo en tu computador.

---

## Parte 1 — ¿Por qué estamos aquí? (10 min)

### El problema

Probablemente ya usas ChatGPT o Claude en el navegador. Le pides que te redacte un email, te resuma un documento, o te ayude con una tabla de datos. Funciona bien, pero tiene límites:

- Tienes que **copiar y pegar** archivos manualmente
- No puede **ver tus carpetas** ni trabajar directo con tus documentos
- No puede **ejecutar acciones** en tu computador
- Cada conversación parte de cero — **no recuerda** tu contexto de trabajo

### La solución

**Claude Code** es como tener a Claude sentado al lado tuyo, con acceso a tu computador. Puede:

- Leer y modificar tus archivos directamente
- Analizar tus planillas, CSVs y documentos sin copiar-pegar
- Ejecutar tareas en tu computador
- Recordar las reglas y preferencias de tu equipo
- Conectarse con herramientas externas (bases de datos, Telegram, navegador, etc.)

Para usarlo, necesitamos aprender algunos conceptos básicos primero.

---

## Parte 2 — Conceptos fundamentales (40 min)

### 2.1 — La Terminal

La terminal es una ventana donde le das instrucciones escritas a tu computador. En vez de hacer clic en carpetas e íconos, le escribes qué hacer.

**Analogía:** Imagina que tu computador es un restaurante. La interfaz gráfica (Finder, Explorador de archivos) es como el menú con fotos. La terminal es como hablarle directo al chef — más directo, más flexible, más poderoso.

**Cómo abrir la terminal:**

- **Mac:** Presiona `Cmd + Espacio`, escribe "Terminal" y presiona Enter
- **Windows:** Presiona la tecla Windows, escribe "PowerShell" y presiona Enter

**Los únicos comandos que necesitas saber:**

```bash
# Ver en qué carpeta estás (como preguntar "¿dónde estoy?")
pwd

# Ver qué hay en la carpeta actual (como abrir una carpeta en Finder)
ls

# Entrar a una carpeta
cd Escritorio

# Volver atrás
cd ..

# Crear una carpeta nueva
mkdir mi-carpeta

# Limpiar la pantalla
clear
```

> **Ejercicio en vivo:** Abre tu terminal, navega al escritorio y crea una carpeta llamada `taller-claude`.

---

### 2.2 — ¿Qué es una CLI?

CLI significa **Command Line Interface** — un programa que se usa escribiendo comandos en la terminal.

La mayoría de las herramientas que usas tienen botones e íconos (Excel, Word, Gmail). Una CLI se usa escribiendo texto. **Claude Code es una CLI** — en vez de ir a una página web, abres la terminal y escribes `claude`.

**¿Por qué no simplemente hacer una app con botones?** Porque la terminal permite hacer cosas que una interfaz gráfica no puede: automatizar, encadenar acciones, trabajar con muchos archivos a la vez, y conectar herramientas entre sí.

No te preocupes — no necesitas ser experto en terminal. Solo necesitas saber abrirla y escribir los comandos básicos que vimos arriba. Claude Code hace el resto.

---

### 2.3 — ¿Qué es un paquete?

Un **paquete** es un programa empaquetado para ser fácil de instalar desde la terminal.

**Analogía:** La App Store de tu celular te permite instalar apps con un toque. Un **package manager** es lo mismo pero para la terminal — le dices qué programa quieres y lo instala por ti.

El package manager que usaremos es **npm** (viene incluido con Node.js). Ejemplo:

```bash
# Así se instala Claude Code
npm install -g @anthropic-ai/claude-code
```

Eso es todo lo que necesitas saber sobre paquetes. Un comando y listo.

---

### 2.4 — ¿Qué es Claude Code?

Claude Code es la **herramienta oficial de Anthropic** para usar Claude desde tu terminal, con acceso directo a tus archivos.

| Chat web (claude.ai) | Claude Code (terminal) |
|---|---|
| Le copias y pegas texto | Lee tus archivos directamente |
| No conoce tu contexto de trabajo | Conoce tu carpeta, tus archivos, tu proyecto |
| Solo conversa | Conversa Y ejecuta acciones |
| Cada chat parte de cero | Recuerda las reglas de tu equipo (CLAUDE.md) |
| No se conecta con nada | Se conecta con bases de datos, Telegram, navegador, etc. |

**Ejemplo concreto:**

En el chat web harías:
> "Tengo esta tabla de ventas [pega 500 filas]. ¿Cuál fue el mejor mes?"

Con Claude Code:
> "Analiza el archivo ventas-2025.csv y dime cuál fue el mejor mes"

Claude Code lee el archivo directo de tu carpeta. Sin copiar, sin pegar, sin límite de tamaño.

---

### 2.5 — Conceptos clave de Claude Code

#### CLAUDE.md — Las reglas de tu equipo

`CLAUDE.md` es un archivo que le dice a Claude cómo trabajar en tu proyecto. Se lee automáticamente cada vez que abres Claude Code en esa carpeta.

**Ejemplo para un equipo de ventas:**

```markdown
# CLAUDE.md

## Contexto
Somos el equipo de ventas de una empresa de software B2B en Chile.

## Reglas
- Responde siempre en español
- Los reportes deben incluir montos en CLP y USD
- Usa formato de fecha DD/MM/YYYY
- Los nombres de clientes son confidenciales — nunca los incluyas en resúmenes públicos
```

#### Skills — Atajos para tareas comunes

Las skills son comandos que empiezan con `/`. En vez de explicarle paso a paso qué hacer, invocas un atajo:

```
/help          → Ver qué puede hacer Claude Code
/commit        → Guardar cambios en el historial del proyecto
```

#### MCP — Conexiones con herramientas externas

MCP permite que Claude Code se conecte con otros servicios:

- **Bases de datos (Neon)** → Consultar y guardar datos sin saber SQL
- **Telegram** → Enviar mensajes y notificaciones
- **Navegador (Chrome)** → Interactuar con páginas web
- **Servicios de deploy** → Publicar proyectos

No necesitas entender los detalles técnicos ahora. Lo importante es saber que Claude Code puede ir más allá de solo leer archivos.

---

### 2.6 — Concepto clave: Información estática vs dinámica

Este es uno de los conceptos más importantes del taller. Hay dos tipos de información con los que trabajarás:

#### Información estática (va en archivos locales)

Es información que **no cambia frecuentemente** y que define cómo trabaja tu agente:

- `CLAUDE.md` — Las reglas y contexto de tu equipo
- Memorias — Lo que Claude aprende sobre ti y tu forma de trabajar
- Instrucciones — Templates, formatos, procedimientos
- Prompts — Cómo le pides las cosas a Claude

Esta información vive en carpetas dentro de tu computador. Es como el "manual de operaciones" de tu agente.

#### Información dinámica (va en una base de datos en la nube)

Es información que **cambia constantemente** y que crece con el tiempo:

- Clientes y sus datos de contacto
- Registros de ventas
- Hallazgos e insights
- Estado de proyectos
- Inventario, órdenes, métricas

Esta información **no debe guardarse en archivos locales**. ¿Por qué?

- Los archivos se pierden si tu computador falla
- No se comparten fácilmente entre equipos
- No escalan — un CSV de 100,000 filas se vuelve inmanejable
- No tienen control de acceso — cualquiera con el archivo ve todo

**La solución: una base de datos en la nube.** Nosotros usaremos **Neon** — una base de datos PostgreSQL en la nube que Claude Code puede consultar directamente vía MCP.

**Ejemplo del flujo:**

```
Tu carpeta local (estático):
├── CLAUDE.md          → "Somos equipo de ventas, montos en CLP..."
├── templates/         → Formatos de email, reportes, propuestas
└── instrucciones/     → Cómo clasificar clientes, cómo calcular comisiones

Neon - Base de datos en la nube (dinámico):
├── clientes           → 500 registros con datos de contacto
├── ventas             → 10,000 transacciones del último año
├── productos          → Catálogo actualizado con precios
└── seguimientos       → Estado de cada oportunidad comercial
```

Con esta separación, Claude Code usa tus instrucciones locales para saber **cómo** trabajar, y consulta Neon para acceder a los **datos** con los que trabaja.

---

## Parte 3 — Instalación paso a paso (40 min)

### 3.1 — Instalar Node.js

Node.js es el motor que necesita Claude Code para funcionar. Solo hay que instalarlo una vez.

#### Verificar si ya lo tienes

Abre tu terminal y escribe:

```bash
node --version
```

Si ves algo como `v20.11.0`, ya lo tienes y puedes saltar al paso 3.2. Si dice "command not found", sigue las instrucciones:

#### En Mac

**Opción A — Con Homebrew (recomendado):**

```bash
# Instalar Homebrew (el package manager de Mac)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar Node.js
brew install node
```

**Opción B — Descarga directa:**

1. Ve a [nodejs.org](https://nodejs.org)
2. Descarga la versión LTS (el botón verde de la izquierda)
3. Abre el archivo descargado y sigue las instrucciones del instalador

#### En Windows

**Opción A — Con winget:**

```powershell
winget install OpenJS.NodeJS.LTS
```

**Opción B — Descarga directa:**

1. Ve a [nodejs.org](https://nodejs.org)
2. Descarga la versión LTS para Windows
3. Ejecuta el instalador (.msi)
4. **Importante:** Marca la casilla "Add to PATH" durante la instalación
5. Sigue las instrucciones hasta el final

#### Verificar

Cierra la terminal, vuelve a abrirla, y escribe:

```bash
node --version
npm --version
```

Si ambos muestran un número, estás listo.

---

### 3.2 — Instalar Claude Code

Un solo comando:

```bash
npm install -g @anthropic-ai/claude-code
```

Verifica:

```bash
claude --version
```

---

### 3.3 — Autenticación

```bash
# Entra a tu carpeta de trabajo
cd ~/Desktop/taller-claude

# Inicia Claude Code
claude
```

La primera vez se abre una ventana en el navegador para que inicies sesión con tu cuenta de Anthropic. Sigue las instrucciones en pantalla.

---

## Parte 4 — Primera interacción (30 min)

### 4.1 — Explorar lo básico

Ya dentro de Claude Code, prueba estos comandos:

**Preguntar algo simple:**
```
> ¿Qué archivos hay en esta carpeta?
```

**Crear un archivo:**
```
> Crea un archivo llamado notas.txt con las tareas pendientes de esta semana:
> 1. Enviar propuesta a cliente Acme
> 2. Preparar reporte mensual de ventas
> 3. Agendar reunión con equipo de operaciones
```

Observa cómo Claude:
1. Te muestra qué va a hacer
2. Te pide permiso antes de actuar
3. Crea el archivo y te confirma

### 4.2 — Trabajar con datos

Crea un archivo de ejemplo para practicar:

```
> Crea un archivo CSV llamado ventas-ejemplo.csv con datos ficticios de ventas:
> 10 filas, con columnas: fecha, cliente, producto, cantidad, monto en CLP
```

Ahora analízalo:

```
> ¿Cuál fue el cliente con más ventas en total?
```

```
> Haz un resumen ejecutivo de las ventas por producto
```

### 4.3 — Redactar contenido

```
> Redacta un email profesional para un cliente que se llama María, agradeciéndole
> su compra y ofreciéndole un 10% de descuento en su próxima orden
```

```
> Ahora hazlo más corto y directo, estilo WhatsApp
```

### 4.4 — El sistema de permisos

Claude Code siempre pide permiso antes de:
- Crear o modificar archivos
- Ejecutar comandos en la terminal
- Acceder a servicios externos

Puedes responder:
- **y** (yes) — Permitir esta vez
- **n** (no) — Rechazar
- **a** (always) — Permitir siempre para este tipo de acción

> **Tip:** Si no estás seguro de lo que Claude va a hacer, responde **n** y pídele que te explique primero.

---

## Cierre y próximos pasos

### Resumen de lo aprendido
- La terminal es tu herramienta para comunicarte con el computador vía texto
- Claude Code es Claude con superpoderes: acceso a tus archivos, ejecución de acciones, y conexión con herramientas
- Se instala con un solo comando y se autentica una sola vez
- Siempre pide permiso antes de actuar — tú tienes el control

### Para la próxima clase
- Tener Claude Code instalado y funcionando
- Traer un archivo real de tu trabajo (un CSV, una planilla, un documento) con el que te gustaría experimentar
- Pensar en tareas repetitivas de tu día a día que te gustaría automatizar

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Node.js](https://nodejs.org)
