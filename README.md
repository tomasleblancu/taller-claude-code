# Taller: Claude Code para equipos de trabajo

Bienvenido al taller práctico de **Claude Code** — la herramienta de Anthropic que te permite usar inteligencia artificial directamente desde tu computador, con acceso a tus archivos, datos y herramientas de trabajo.

Este taller está diseñado para personas que **no son programadoras**: equipos de ventas, operaciones, productividad y cualquier profesional que quiera multiplicar su capacidad de trabajo con IA.

---

## Qué vas a aprender

Al terminar este taller vas a poder:

- Usar Claude Code para analizar archivos, generar reportes y redactar comunicaciones
- Conectarte a una base de datos en la nube para consultar y actualizar información de clientes, ventas y más
- Configurar un agente personalizado con las reglas de tu equipo
- Automatizar tareas repetitivas de tu día a día

---

## Conceptos que necesitas conocer antes de empezar

### 1. La Terminal

La terminal es una ventana donde le das instrucciones escritas a tu computador. En vez de hacer clic en carpetas e íconos, le escribes qué hacer.

**Cómo abrirla:**
- **Mac:** `Cmd + Espacio`, escribe "Terminal", Enter
- **Windows:** Tecla Windows, escribe "PowerShell", Enter

**Los comandos básicos que usaremos:**

| Comando | Qué hace | Equivalente visual |
|---|---|---|
| `pwd` | Te dice en qué carpeta estás | Mirar la barra de dirección en Finder |
| `ls` | Muestra qué hay en la carpeta | Abrir una carpeta y ver su contenido |
| `cd Escritorio` | Entrar a una carpeta | Hacer doble clic en una carpeta |
| `cd ..` | Volver atrás | Presionar el botón "atrás" |
| `mkdir mi-carpeta` | Crear una carpeta nueva | Clic derecho > Nueva carpeta |
| `clear` | Limpiar la pantalla | — |

### 2. ¿Qué es una CLI?

CLI significa **Command Line Interface** — un programa que se usa escribiendo comandos en la terminal en vez de hacer clic en botones.

**Claude Code es una CLI.** En vez de ir a una página web, abres la terminal y escribes `claude`. La ventaja: la terminal permite automatizar, encadenar acciones y trabajar con muchos archivos a la vez.

### 3. ¿Qué es un paquete?

Un **paquete** es un programa empaquetado para instalarse fácil desde la terminal. Es como la App Store pero para programas de terminal.

El instalador que usaremos es **npm** (viene incluido con Node.js):

```bash
# Así se instala Claude Code — un solo comando
npm install -g @anthropic-ai/claude-code
```

### 4. Claude Code vs. el chat web

Ya conoces ChatGPT o Claude en el navegador. Claude Code es un paso más allá:

| Chat web (claude.ai) | Claude Code (terminal) |
|---|---|
| Le copias y pegas texto | Lee tus archivos directamente |
| No conoce tu contexto de trabajo | Conoce tu carpeta, tus archivos, tu proyecto |
| Solo conversa | Conversa **y ejecuta acciones** |
| Cada chat parte de cero | Recuerda las reglas de tu equipo |
| No se conecta con nada | Se conecta con bases de datos, Telegram, navegador, etc. |

**Ejemplo:**

En el chat web: *"Tengo esta tabla de ventas [pega 500 filas]. ¿Cuál fue el mejor mes?"*

Con Claude Code: *"Analiza el archivo ventas-2025.csv y dime cuál fue el mejor mes"*

Claude Code lee el archivo directo. Sin copiar, sin pegar, sin límite de tamaño.

### 5. Conceptos clave

#### CLAUDE.md — Las reglas de tu equipo

Un archivo que le dice a Claude cómo trabajar en tu proyecto. Se lee automáticamente cada vez que abres Claude Code en esa carpeta.

```markdown
# Ejemplo de CLAUDE.md para un equipo de ventas

- Responde siempre en español
- Los reportes deben incluir montos en CLP y USD
- Usa formato de fecha DD/MM/YYYY
- Los nombres de clientes son confidenciales
```

#### Skills — Atajos para tareas comunes

Comandos que empiezan con `/` para ejecutar acciones rápidas:

```
/help          → Ver qué puede hacer Claude Code
/commit        → Guardar cambios en el historial del proyecto
```

#### MCP — Conexiones con herramientas externas

MCP permite que Claude Code se conecte con otros servicios: bases de datos, Telegram, navegador, servicios de deploy, y más. No necesitas entender los detalles técnicos — lo importante es saber que Claude Code puede ir mucho más allá de solo leer archivos.

### 6. Información estática vs. dinámica

Esta es una de las ideas más importantes del taller:

| | Estática | Dinámica |
|---|---|---|
| **Qué es** | Información que cambia poco | Información que cambia constantemente |
| **Para qué sirve** | Define *cómo* trabaja tu agente | Son los *datos* con los que trabaja |
| **Dónde vive** | Archivos en tu computador | Base de datos en la nube (Neon) |
| **Ejemplos** | CLAUDE.md, templates, instrucciones | Clientes, ventas, métricas, inventario |

**¿Por qué no guardar todo en archivos?** Porque los archivos locales se pierden si tu computador falla, no se comparten fácil entre equipos, y no escalan (un CSV de 100,000 filas se vuelve inmanejable).

**La solución:** Usamos **Neon** — una base de datos PostgreSQL en la nube que Claude Code consulta directamente. Tus instrucciones van en archivos locales, tus datos van en Neon.

```
Tu carpeta local (estático):
├── CLAUDE.md          → "Somos equipo de ventas, montos en CLP..."
├── templates/         → Formatos de email, reportes, propuestas
└── instrucciones/     → Cómo clasificar clientes, calcular comisiones

Neon - Base de datos en la nube (dinámico):
├── clientes           → 500 registros con datos de contacto
├── ventas             → 10,000 transacciones del último año
├── productos          → Catálogo actualizado con precios
└── seguimientos       → Estado de cada oportunidad comercial
```

---

## Preparación antes de la primera clase

### 1. Instalar Node.js

Node.js es el motor que necesita Claude Code para funcionar.

**Verificar si ya lo tienes:**
```bash
node --version
```
Si ves algo como `v20.11.0`, ya lo tienes. Si dice "command not found", instálalo:

**Mac:**
```bash
# Opción A — Con Homebrew (recomendado)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install node

# Opción B — Descarga directa desde nodejs.org (botón verde LTS)
```

**Windows:**
```powershell
# Opción A — Con winget
winget install OpenJS.NodeJS.LTS

# Opción B — Descarga directa desde nodejs.org (versión LTS, marcar "Add to PATH")
```

**Verificar:**
```bash
node --version
npm --version
```
Si ambos muestran un número, estás listo.

### 2. Instalar Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verificar:
```bash
claude --version
```

### 3. Autenticación

```bash
# Crea una carpeta de trabajo
mkdir ~/Desktop/taller-claude
cd ~/Desktop/taller-claude

# Inicia Claude Code
claude
```

La primera vez se abre el navegador para iniciar sesión con tu cuenta de Anthropic. Sigue las instrucciones en pantalla.

### 4. Prueba rápida

Ya dentro de Claude Code, escribe:

```
> ¿Qué archivos hay en esta carpeta?
```

Si Claude responde, todo está funcionando.

---

## Estructura del taller

### Clase 1 — Teoría + Instalación
Entender qué es Claude Code, instalarlo, y hacer tu primera interacción.

### Clase 2 — Práctica con casos reales
Analizar datos, redactar comunicaciones, conectar con base de datos, y automatizar tareas.

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Neon — Base de datos en la nube](https://neon.tech)
- [Node.js](https://nodejs.org)

---

## Qué traer a clase

- Tu computador con Claude Code instalado y funcionando
- Un archivo real de tu trabajo (CSV, planilla, documento) para experimentar
- Ideas de tareas repetitivas que te gustaría automatizar
