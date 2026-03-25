# Clase 1 — Teoría + Instalación de Claude Code

**Duración:** 2 horas
**Objetivo:** Entender los conceptos fundamentales y terminar con Claude Code instalado y funcionando.

---

## Parte 1 — Conceptos fundamentales (45 min)

### 1.1 — La Terminal

La terminal es una ventana donde escribes comandos de texto para hablar con tu computador. En vez de hacer clic en botones e íconos, le das instrucciones escritas.

**¿Por qué importa?** Muchas herramientas de desarrollo (incluyendo Claude Code) viven en la terminal. No necesitas ser experto — solo saber abrirla y escribir comandos básicos.

**Cómo abrir la terminal:**

- **Mac:** Busca "Terminal" en Spotlight (Cmd + Espacio → escribe "Terminal")
- **Windows:** Busca "PowerShell" en el menú de inicio, o instala [Windows Terminal](https://apps.microsoft.com/detail/9n0dx20hk701) desde la Microsoft Store

**Comandos básicos para probar:**

```bash
# Ver en qué carpeta estás
pwd

# Listar archivos de la carpeta actual
ls

# Moverte a otra carpeta
cd Desktop

# Volver a la carpeta anterior
cd ..

# Crear una carpeta nueva
mkdir mi-proyecto

# Limpiar la pantalla
clear
```

> **Ejercicio en vivo:** Abre tu terminal, navega al escritorio y crea una carpeta llamada `taller-claude`.

---

### 1.2 — ¿Qué es una CLI?

CLI significa **Command Line Interface** (Interfaz de Línea de Comandos). Es un programa que usas escribiendo comandos en la terminal, en vez de hacer clic en una interfaz gráfica.

**Ejemplos cotidianos:**

| Tarea | Con interfaz gráfica | Con CLI |
|---|---|---|
| Crear una carpeta | Clic derecho → Nueva carpeta | `mkdir mi-carpeta` |
| Copiar un archivo | Arrastrar y soltar | `cp archivo.txt copia.txt` |
| Instalar un programa | Descargar .exe/.dmg | `npm install paquete` |

Claude Code es una CLI — lo usas escribiendo comandos, no haciendo clic en botones.

---

### 1.3 — ¿Qué es un paquete y un package manager?

Un **paquete** es un programa o librería empaquetada para que sea fácil de instalar. Piensa en ello como una app, pero para la terminal.

Un **package manager** es la "tienda de apps" de la terminal. Le dices qué quieres instalar y él se encarga de descargarlo y configurarlo.

**Package managers que usaremos:**

| Package Manager | Para qué sirve | Sistema |
|---|---|---|
| **npm** | Instalar paquetes de JavaScript/Node.js | Mac y Windows |
| **Homebrew (brew)** | Instalar programas del sistema | Solo Mac |
| **winget** | Instalar programas del sistema | Solo Windows |

**Ejemplo:**

```bash
# Instalar un paquete con npm (funciona en Mac y Windows)
npm install -g @anthropic-ai/claude-code

# Instalar algo con Homebrew (solo Mac)
brew install node
```

El `-g` significa "global" — que lo instala para todo tu computador, no solo para un proyecto.

---

### 1.4 — ¿Qué es Claude Code?

Claude Code es la **CLI oficial de Anthropic** para usar Claude directamente desde tu terminal. A diferencia de claude.ai (el chat en el navegador), Claude Code:

- **Vive en tu terminal** — trabaja directamente con tus archivos y carpetas
- **Lee y edita tu código** — puede ver tu proyecto, modificar archivos, y ejecutar comandos
- **Usa herramientas** — puede buscar en internet, leer documentación, crear archivos, correr tests
- **Es un agente** — no solo responde preguntas, sino que ejecuta tareas completas

**¿Cuándo usar Claude Code vs claude.ai?**

| claude.ai (chat web) | Claude Code (terminal) |
|---|---|
| Preguntas generales | Trabajar en un proyecto real |
| Conversaciones casuales | Crear, editar, debuggear código |
| No tiene acceso a tus archivos | Lee y modifica tus archivos directamente |
| Copias y pegas código manualmente | Aplica cambios automáticamente |

---

### 1.5 — Conceptos clave de Claude Code

#### Skills (Habilidades)

Las **skills** son comandos especializados que Claude Code puede ejecutar. Se invocan con `/` seguido del nombre.

```
/commit        → Crea un commit de git con un mensaje bien escrito
/review-pr     → Revisa un pull request
/help          → Muestra ayuda
```

Piensa en las skills como "atajos" — en vez de explicarle a Claude paso a paso qué hacer, invocas una skill que ya sabe cómo hacerlo.

#### CLAUDE.md (La memoria del proyecto)

`CLAUDE.md` es un archivo que pones en la raíz de tu proyecto. Claude lo lee automáticamente cada vez que abre ese proyecto. Es como dejarle una nota a Claude con instrucciones:

```markdown
# CLAUDE.md

## Sobre este proyecto
Este es un sitio web hecho con Next.js.

## Reglas
- Escribe todo el código en TypeScript
- Usa español para los comentarios
- Los tests van en la carpeta /tests
```

#### MCP (Model Context Protocol)

**MCP** permite conectar Claude Code con herramientas externas. Por ejemplo:

- Conectar con una **base de datos** (Neon, PostgreSQL)
- Conectar con **Chrome DevTools** para debuggear páginas web
- Conectar con **Telegram** para enviar mensajes
- Conectar con servicios como **Railway**, **GitHub**, etc.

No necesitas entender los detalles técnicos ahora — lo importante es saber que Claude Code es extensible y puede conectarse con casi cualquier servicio.

#### Hooks (Automatizaciones)

Los **hooks** son acciones automáticas que se ejecutan cuando algo ocurre. Por ejemplo:

- "Cada vez que Claude haga un commit, corre los tests"
- "Antes de editar un archivo, haz un backup"

Son opcionales y los veremos con más detalle en la Clase 2.

---

## Parte 2 — Instalación paso a paso (45 min)

### 2.1 — Requisitos previos

Necesitas tener instalado:

1. **Node.js** (versión 18 o superior)
2. **npm** (viene incluido con Node.js)
3. Una **cuenta de Anthropic** con acceso a Claude

#### Verificar si ya tienes Node.js

Abre tu terminal y escribe:

```bash
node --version
```

Si ves algo como `v20.11.0` o superior, ya lo tienes. Si dice "command not found", hay que instalarlo.

---

### 2.2 — Instalar Node.js

#### En Mac

**Opción A — Con Homebrew (recomendado):**

```bash
# Primero instalar Homebrew si no lo tienes
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Luego instalar Node.js
brew install node
```

**Opción B — Descarga directa:**

1. Ve a [nodejs.org](https://nodejs.org)
2. Descarga la versión LTS (Long Term Support)
3. Abre el instalador y sigue las instrucciones

#### En Windows

**Opción A — Con winget (recomendado):**

```powershell
winget install OpenJS.NodeJS.LTS
```

**Opción B — Descarga directa:**

1. Ve a [nodejs.org](https://nodejs.org)
2. Descarga la versión LTS para Windows
3. Ejecuta el instalador (.msi) y sigue las instrucciones
4. **Importante:** Marca la casilla "Add to PATH" durante la instalación

#### Verificar la instalación

Cierra y vuelve a abrir la terminal, luego:

```bash
node --version
npm --version
```

Ambos comandos deben mostrar un número de versión.

---

### 2.3 — Instalar Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Verifica que se instaló correctamente:

```bash
claude --version
```

---

### 2.4 — Autenticación

La primera vez que ejecutes `claude`, te pedirá autenticarte:

```bash
# Navega a tu carpeta de proyecto
cd ~/Desktop/taller-claude

# Inicia Claude Code
claude
```

Se abrirá una ventana en tu navegador para que inicies sesión con tu cuenta de Anthropic. Sigue las instrucciones en pantalla.

---

### 2.5 — Configuración inicial recomendada

Una vez dentro de Claude Code, algunos ajustes útiles:

```
# Cambiar el idioma de las respuestas
> Responde siempre en español

# Ver los comandos disponibles
/help
```

---

## Parte 3 — Primera interacción (30 min)

### 3.1 — Tu primer comando

Dentro de la carpeta `taller-claude`, inicia Claude Code y prueba:

```
> ¿Qué archivos hay en esta carpeta?
```

Claude va a usar sus herramientas para listar los archivos. Como la carpeta está vacía, te lo dirá.

### 3.2 — Crear tu primer archivo con Claude

```
> Crea un archivo llamado hola.txt que diga "¡Hola mundo! Este es mi primer archivo creado con Claude Code"
```

Observa cómo Claude:
1. Te muestra qué va a hacer
2. Te pide permiso antes de crear el archivo
3. Crea el archivo y te confirma

### 3.3 — Hacer preguntas sobre código

```
> Crea un archivo index.html con una página web simple que diga "Mi primera página" con un fondo azul
```

Después de que lo cree:

```
> Explícame qué hace cada línea del archivo index.html
```

### 3.4 — Modificar archivos existentes

```
> Cambia el color de fondo de index.html a verde y agrega un botón que diga "Haz clic aquí"
```

Observa cómo Claude lee el archivo, entiende su contenido, y aplica solo los cambios necesarios.

### 3.5 — Usar el sistema de permisos

Claude Code siempre pide permiso antes de:
- Crear o modificar archivos
- Ejecutar comandos en la terminal
- Acceder a servicios externos

Puedes responder:
- **y** (yes) — Permitir esta vez
- **n** (no) — Rechazar
- **a** (always) — Permitir siempre para este tipo de acción

---

## Cierre y próximos pasos

### Resumen de lo aprendido
- La terminal es tu interfaz para hablar con el computador vía texto
- Una CLI es un programa que vive en la terminal
- Los paquetes se instalan con package managers como npm
- Claude Code es la CLI de Anthropic para trabajar con Claude en tus proyectos
- Las skills, CLAUDE.md, MCP y hooks extienden lo que Claude Code puede hacer

### Para la próxima clase
- Tener Claude Code instalado y funcionando
- Tener una carpeta de proyecto lista para trabajar
- Pensar en un proyecto personal donde te gustaría usar Claude Code

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Node.js](https://nodejs.org)
- [Repositorio de Claude Code](https://github.com/anthropics/claude-code)
