# Clase 2 — Práctica: Casos de uso reales con Claude Code

**Duración:** 2 horas
**Requisito:** Tener Claude Code instalado y funcionando (Clase 1).
**Objetivo:** Usar Claude Code en escenarios reales para resolver problemas concretos.

---

## Parte 1 — Repaso rápido y setup (15 min)

### Verificar que todo funciona

```bash
# Abrir la terminal
cd ~/Desktop/taller-claude
claude
```

Si alguien tiene problemas, resolverlos ahora.

### Repaso express

- Claude Code vive en la terminal
- Lee y modifica tus archivos directamente
- Siempre pide permiso antes de actuar
- Se invoca con `claude` dentro de una carpeta

---

## Parte 2 — Caso 1: Crear un proyecto desde cero (25 min)

### El escenario

Queremos crear una página web personal simple — un portafolio con tu nombre, una descripción, y links a tus redes sociales.

### Paso a paso

**1. Crear la estructura del proyecto:**

```
> Crea una página web personal con HTML y CSS. Quiero:
> - Mi nombre grande en el centro
> - Una descripción corta debajo
> - Links a GitHub, LinkedIn y Twitter como íconos
> - Diseño moderno y minimalista
> - Que sea responsive (se vea bien en celular)
```

**2. Observar cómo trabaja Claude:**
- Crea múltiples archivos (HTML, CSS)
- Estructura el código de forma organizada
- Aplica buenas prácticas automáticamente

**3. Ver el resultado:**

```
> Abre el archivo index.html en el navegador
```

O simplemente abre el archivo manualmente desde el explorador de archivos.

**4. Pedir cambios iterativos:**

```
> Cambia los colores a un esquema oscuro (dark mode)
```

```
> Agrega una sección de "Proyectos" con 3 cards
```

```
> Agrega una animación suave cuando haces scroll
```

### Lo que aprendemos aquí
- Claude Code puede crear proyectos completos desde una descripción
- Puedes iterar pidiendo cambios progresivos
- No necesitas saber HTML/CSS para tener un resultado funcional

---

## Parte 3 — Caso 2: Entender y explicar código (20 min)

### El escenario

Te pasaron un archivo de código que no entiendes y necesitas saber qué hace.

### Paso a paso

**1. Pedir una explicación general:**

```
> Explícame qué hace el archivo index.html como si tuviera 10 años
```

**2. Preguntar sobre partes específicas:**

```
> ¿Qué hace la sección de CSS que dice @media?
```

```
> ¿Por qué se usa display: flex?
```

**3. Pedir documentación:**

```
> Agrega comentarios en español explicando cada sección del HTML y del CSS
```

### Lo que aprendemos aquí
- Claude Code es excelente para aprender — puedes preguntar "por qué" sin límite
- Puede explicar a distintos niveles de profundidad
- Puede documentar código existente

---

## Parte 4 — Caso 3: Debuggear un problema (20 min)

### El escenario

Algo en nuestra página no funciona bien — vamos a romperla intencionalmente y pedirle a Claude que la arregle.

### Paso a paso

**1. Romper algo a propósito:**

Abre `index.html` con cualquier editor de texto y:
- Borra un `</div>` de cierre en algún lugar
- Cambia un nombre de clase CSS (ej: `container` → `contaienr`)
- Borra un `;` en el CSS

Guarda el archivo.

**2. Pedirle a Claude que lo arregle:**

```
> La página se ve rota. ¿Puedes revisar qué está mal y arreglarlo?
```

**3. Observar el proceso de debugging:**
- Claude lee los archivos
- Identifica los errores
- Explica qué encontró
- Aplica las correcciones

**4. Probar con errores más sutiles:**

```
> El botón no hace nada cuando le hago clic. ¿Puedes arreglarlo?
```

### Lo que aprendemos aquí
- Claude Code puede diagnosticar problemas sin que le digas exactamente qué está mal
- Lee el contexto completo del proyecto para entender el problema
- Explica el error antes de arreglarlo

---

## Parte 5 — Caso 4: Usar Skills (20 min)

### ¿Qué son las skills?

Las skills son comandos especializados que empiezan con `/`. Son atajos para tareas comunes.

### Skills esenciales

#### /help — Ver comandos disponibles

```
/help
```

Muestra todas las opciones y skills disponibles.

#### /commit — Hacer commits inteligentes

Primero necesitamos inicializar git en nuestro proyecto:

```
> Inicializa un repositorio git en esta carpeta y haz el primer commit
```

Ahora hagamos un cambio cualquiera:

```
> Agrega un footer a la página con el año actual
```

Y luego usamos la skill:

```
/commit
```

Claude Code va a:
1. Ver qué archivos cambiaron
2. Analizar los cambios
3. Escribir un mensaje de commit descriptivo
4. Crear el commit

#### /review-pr — Revisar código

Si tienes un pull request en GitHub:

```
/review-pr 123
```

Claude Code revisa el código y da feedback como lo haría un compañero de equipo.

### Lo que aprendemos aquí
- Las skills simplifican tareas repetitivas
- `/commit` escribe mejores mensajes de commit que la mayoría de los humanos
- Son extensibles — se pueden crear skills personalizadas

---

## Parte 6 — Caso 5: CLAUDE.md y personalización (15 min)

### Crear tu CLAUDE.md

```
> Crea un archivo CLAUDE.md para este proyecto con las siguientes reglas:
> - Responde siempre en español
> - Usa comentarios descriptivos en el código
> - El estilo de código debe ser limpio y simple
> - Cuando crees archivos HTML, usa la estructura semántica (header, main, footer)
```

### Probar que funciona

Cierra Claude Code (escribe `exit` o presiona Ctrl+C) y vuelve a abrirlo:

```bash
claude
```

Ahora pide algo nuevo:

```
> Crea una segunda página llamada contacto.html con un formulario de contacto
```

Verifica que Claude sigue las reglas del CLAUDE.md (español, semántica, comentarios).

### Modificar las reglas

```
> Actualiza CLAUDE.md para agregar: "Siempre usar colores del esquema oscuro que ya definimos"
```

### Lo que aprendemos aquí
- CLAUDE.md es la forma de darle contexto permanente a Claude sobre tu proyecto
- Se lee automáticamente cada vez que abres Claude Code en esa carpeta
- Puedes ir agregando reglas a medida que defines tu estilo de trabajo

---

## Parte 7 — Caso 6: Conectar con el mundo exterior — MCP (15 min)

### ¿Qué es MCP en la práctica?

MCP (Model Context Protocol) permite que Claude Code se conecte con servicios externos. Es como instalarle "plugins".

### Ejemplo conceptual: Base de datos con Neon

Con MCP configurado, podrías hacer cosas como:

```
> Muéstrame las tablas que tengo en mi base de datos
```

```
> Crea una tabla de usuarios con nombre, email y fecha de registro
```

```
> Inserta 5 usuarios de prueba
```

Claude Code habla directamente con la base de datos — no necesitas escribir SQL ni usar otra herramienta.

### Ejemplo conceptual: Chrome DevTools

```
> Abre mi página web en Chrome y toma un screenshot
```

```
> Haz una auditoría de rendimiento de mi página
```

### Ejemplo conceptual: Telegram

```
> Envía un mensaje a mi chat de Telegram diciendo "Deploy completado"
```

### Cómo se configura (demo visual)

Los MCP servers se configuran en el archivo de settings de Claude Code. No profundizaremos en la configuración hoy, pero es bueno saber que existe y lo que permite.

### Lo que aprendemos aquí
- MCP extiende Claude Code para conectar con servicios externos
- No necesitas cambiar de herramienta — todo desde la terminal
- Hay MCPs para bases de datos, navegadores, mensajería, deploys, y más

---

## Parte 8 — Tips y buenas prácticas (10 min)

### Cómo pedir cosas efectivamente

**Malo:**
```
> Haz una página
```

**Bueno:**
```
> Crea una página de landing para una cafetería. Debe tener un header con el nombre "Café Sol",
> una sección de menú con 5 productos con precio, y un formulario de reservas.
> Usa colores cálidos (tonos café y crema). Debe verse bien en celular.
```

### Reglas de oro

1. **Sé específico** — Mientras más contexto le des, mejor resultado obtienes
2. **Itera** — No intentes que quede perfecto al primer intento. Pide cambios progresivos
3. **Pregunta "por qué"** — Si no entiendes algo que Claude hizo, pregunta. Es la mejor forma de aprender
4. **Usa CLAUDE.md** — Define tus preferencias una vez y Claude las respeta siempre
5. **Revisa antes de aceptar** — Lee lo que Claude propone antes de dar permiso. Vas a aprender mucho solo leyendo
6. **No tengas miedo de experimentar** — Si algo sale mal, Claude puede deshacerlo

### Atajos útiles

| Atajo | Qué hace |
|---|---|
| `Tab` | Autocompletar |
| `Ctrl + C` | Cancelar lo que está haciendo |
| `Ctrl + L` | Limpiar la pantalla |
| `/help` | Ver ayuda |
| `/commit` | Crear un commit |
| `exit` | Salir de Claude Code |

---

## Cierre

### Lo que aprendimos hoy
1. Crear proyectos completos desde una descripción
2. Entender y documentar código existente
3. Debuggear problemas automáticamente
4. Usar skills para tareas comunes
5. Personalizar Claude Code con CLAUDE.md
6. Conectar con servicios externos vía MCP

### ¿Qué sigue?
- Practica con un proyecto personal
- Experimenta con diferentes tipos de proyectos (web, scripts, automatizaciones)
- Explora los MCP servers disponibles
- Crea tu propio CLAUDE.md personalizado

---

## Recursos

- [Documentación oficial de Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Skills disponibles](https://docs.anthropic.com/en/docs/claude-code/skills)
- [MCP Servers](https://github.com/modelcontextprotocol/servers)
- [Repositorio de Claude Code](https://github.com/anthropics/claude-code)
