# Manual de Mantenimiento — Perfil GitHub de GustavoTuesta

> Documento creado el 2026-07-27. Úsalo como referencia cada vez que necesites actualizar el perfil sin tener que analizar todo el proyecto desde cero.

---

## 1. Estructura del proyecto

```
GustavoTuesta/
├── README.md                  ← Perfil principal de GitHub (único archivo que GitHub muestra)
├── hacker.gif                 ← GIF animado de la sección "Sobre mí"
├── fondo.gif                  ← GIF animado original del fondo del hero (fuente, no se usa directamente)
├── assets/
│   ├── hero.gif               ← Hero generado: fondo oscurecido + texto superpuesto (REEMPLAZA el bloque hero original)
│   └── tecnologias.svg        ← SVG con las dos tarjetas de tecnologías
└── MANUAL.md                  ← Este archivo
```

### Convención de nombres
- **Minúsculas con guiones**: `hero.gif`, `tecnologias.svg`
- **Carpeta `assets/`**: todos los recursos generados automáticamente
- Los GIFs originales (`hacker.gif`, `fondo.gif`) permanecen en la raíz para referencia y regeneración futura

---

## 2. Componentes gráficos

### `assets/hero.gif`

| Campo | Detalle |
|-------|---------|
| **Qué representa** | La sección de bienvenida (hero) con fondo animado y texto superpuesto |
| **Por qué es imagen** | GitHub elimina `position: absolute`, `filter: brightness()`, `z-index`, `transform` y el bloque `<style>`. No es posible superponer texto sobre un GIF de fondo usando HTML en GitHub. |
| **Archivo que reemplaza** | El bloque HTML de las líneas 1–58 del README original (el `<style>` completo + el `<div>` con `fondo.gif` y `.hero-text`) |
| **Cómo editarlo** | Ver sección [Guía para futuras modificaciones → Modificar el hero](#hero) |

### `assets/tecnologias.svg` *(archivo de referencia, reemplazado en v2)*

| Campo | Detalle |
|-------|--------|
| **Qué representa** | Versión inicial de las tarjetas de tecnologías (v1) |
| **Por qué fue reemplazado** | GitHub bloquea por CSP todas las URLs externas dentro de un SVG renderizado como `<img>`. Los `<image href="https://skillicons.dev/...">` nunca se cargan. |
| **Reemplazado por** | URLs directas de `skillicons.dev` dentro de una `<table>` en el README |
| **Estado** | Archivo conservado como referencia. No se usa actualmente. |

### Sección Tecnologías (v2 actual)

| Campo | Detalle |
|-------|--------|
| **Qué representa** | Las dos columnas de tecnologías con sus íconos |
| **Por qué funciona** | `skillicons.dev` soporta múltiples íconos en una sola URL (`i=nodejs,nestjs,...`). GitHub renderiza `<img src="URL">` directamente sin restricciones de CSP. |
| **Ubicación** | README.md, sección `<!-- TECNOLOGÍAS -->` |
| **Cómo editarlo** | Ver sección [Agregar nuevas tecnologías](#agregar-nuevas-tecnologías) |

---

## 3. Guía para futuras modificaciones

### Cambiar textos

**Sección "Sobre mí"** — tabla de dos columnas en el README.md:
1. Abre `README.md`
2. Edita el texto dentro de `<td valign="middle" width="60%">`
3. Guarda y haz `git push`

**Sección hero (nombre y subtítulo)**:
1. Abre el script `generate_hero.py` (guardado en la misma carpeta o recréalo con el código original)
2. Modifica las variables `TITLE_TEXT` y `SUBTITLE_TEXT`
3. Ejecuta: `py generate_hero.py`
4. Reemplaza `assets/hero.gif` con el nuevo generado

### <a name="hero"></a>Modificar el hero

El hero se genera con el script Python. Si no lo tienes guardado, los parámetros clave son:

```python
BRIGHTNESS    = 0.22                              # Oscuridad del fondo (0=negro, 1=original)
BOX_ALPHA     = 0.72                              # Opacidad de la caja de texto
TITLE_TEXT    = "Hola, soy Gustavo Tuesta"        # Título del hero
SUBTITLE_TEXT = "Software Engineering Student · Backend Developer"
TITLE_COLOR   = (255, 255, 255)                   # Color del título (RGB)
TITLE_SIZE    = 26                                # Tamaño del título en px
SUBTITLE_SIZE = 14                                # Tamaño del subtítulo en px
```

Comando para regenerar:
```bash
py generate_hero.py
```

### Cambiar iconos de tecnologías

1. Abre `assets/tecnologias.svg` en cualquier editor de texto
2. Cada ícono es una línea como esta:
   ```xml
   <image href="https://skillicons.dev/icons?i=nodejs" x="32" y="72" width="55" height="55"/>
   ```
3. Cambia el parámetro `i=` con el nombre del ícono ([lista completa en skillicons.dev](https://skillicons.dev))
4. Guarda y haz `git push` — no necesitas regenerar nada

### Agregar nuevas tecnologías

Las tecnologías se muestran usando URLs directas de `skillicons.dev` en el README:

```html
<img src="https://skillicons.dev/icons?i=nodejs,nestjs,ts,postgres,docker,git,github&perline=4">
```

**Para agregar un ícono:**
1. Abre `README.md`, sección `<!-- TECNOLOGÍAS -->`
2. Agrega el nombre del ícono a la lista separada por comas en la URL correspondiente:
   - Tarjeta izquierda (principales): `i=nodejs,nestjs,...,**NUEVO**`
   - Tarjeta derecha (adicional): `i=java,python,...,**NUEVO**`
3. Consulta la [lista completa de íconos disponibles](https://skillicons.dev) para el nombre exacto
4. Ajusta `&perline=4` si quieres cambiar cuántos íconos aparecen por fila
5. Guarda y haz `git push` — no se necesita regenerar nada

### Agregar nuevos proyectos

Si en el futuro quieres una sección de proyectos, puedes agregarla directamente en el README.md usando Markdown estándar o `<table>` HTML:

```markdown
## Proyectos destacados

| Proyecto | Descripción | Tecnologías |
|----------|-------------|-------------|
| [Mi Proyecto](https://github.com/GustavoTuesta/mi-proyecto) | Descripción breve | Node.js, TypeScript |
```

### Cambiar colores

**Del hero:** Modifica `BOX_COLOR`, `TITLE_COLOR` y `SUBTITLE_COLOR` en el script Python, luego regenera.

**Del SVG de tecnologías:**
- Color de fondo de tarjeta: atributo `fill` del `<rect>` (ejemplo: `fill="rgba(255,255,255,0.04)"`)
- Color del título: atributo `fill` del `<text>` (ejemplo: `fill="#ffffff"`)
- Borde de la tarjeta: atributo `stroke` del `<rect>`

### Reemplazar una imagen existente

1. Genera o descarga la nueva imagen
2. Renómbrala igual a la existente (o actualiza la ruta en el README.md)
3. Haz `git add`, `git commit` y `git push`

### Crear un nuevo GIF siguiendo el mismo estilo

El `hero.gif` se genera componiendo frames de un GIF de fondo con texto usando Python + Pillow. Para crear otro GIF con el mismo estilo:

1. Elige un nuevo GIF de fondo (por ejemplo `nuevo_fondo.gif`)
2. Copia el script `generate_hero.py`
3. Cambia `INPUT_GIF = "nuevo_fondo.gif"` y `OUTPUT_GIF = "assets/nuevo_banner.gif"`
4. Ajusta los textos y colores según necesites
5. Ejecuta: `py generate_hero.py`

---

## 4. Limitaciones de GitHub

GitHub sanitiza (filtra) agresivamente el HTML de los archivos Markdown para prevenir inyección de código y estilos maliciosos.

### Propiedades CSS que NO funcionan

| Propiedad | Motivo |
|-----------|--------|
| `position: absolute/relative` | Eliminado por el sanitizador |
| `display: flex` | Eliminado |
| `gap` | Eliminado |
| `filter: brightness()` | Eliminado |
| `transform: translateX()` | Eliminado |
| `z-index` | Eliminado |
| `clamp()` | Eliminado |
| `border-radius` | Eliminado |
| `background: rgba(...)` | Eliminado |
| `border: 1px solid ...` | Eliminado |
| `@media` queries | Eliminado |
| Cualquier propiedad de `color:` en `style=` | Eliminado |

### Etiquetas/atributos HTML con limitaciones

| Elemento | Problema |
|----------|----------|
| `<style>` | Completamente eliminado |
| `<script>` | Completamente eliminado |
| Atributo `class=""` | Eliminado |
| Atributo `id=""` | Eliminado |
| Atributo `style=""` | Eliminado en casi todos los casos |

### Alternativas utilizadas en este proyecto

| Necesidad | Alternativa compatible |
|-----------|----------------------|
| Centrar contenido | `<div align="center">` |
| Flotar imagen a la derecha | `<img align="right">` |
| Texto a color con fondo visual | Imagen SVG con `fill="#color"` |
| Layout de dos columnas | `<img align="right">` + texto Markdown fluye alrededor |
| Fondo animado + texto superpuesto | GIF animado con texto ya compuesto (Python + Pillow) |
| Tarjetas con glassmorphism | SVG con `<rect>` con `fill="rgba(...)"` |

> **Nota:** GitHub SÍ renderiza SVGs referenciados como `<img src="archivo.svg">`, y los SVGs internamente pueden usar CSS y estilos que el sanitizador de Markdown no afecta.

---

## 5. Buenas prácticas

### Ligereza
- Mantén `hero.gif` por debajo de 500 KB. El actual pesa ~195 KB.
- Usa `optimize=True` al guardar GIFs con Pillow.
- Para el SVG, usa `<image href="URL">` en lugar de embeber imágenes en base64.
- Los íconos de skillicons.dev son SVGs ligeros cargados por URL — no los descargues localmente a menos que necesites soporte offline.

### Compatibilidad con GitHub
- Nunca uses `<style>` ni atributo `style=""` en el README.
- Para centrar: usa `<div align="center">`.
- Para flotar: usa `<img align="right">` o `<img align="left">`.
- Para layouts complejos: usa una imagen o SVG.
- Prueba siempre localmente con el [previsualizador de Markdown de VS Code](https://code.visualstudio.com/docs/languages/markdown) antes de hacer push. Ten en cuenta que VS Code es más permisivo que GitHub.

### Facilidad de mantenimiento
- Cada componente gráfico tiene su fuente editable (el script Python para el hero, el SVG de texto plano para tecnologías).
- Nunca uses rutas absolutas — siempre rutas relativas (`./assets/hero.gif`, no `/GustavoTuesta/assets/hero.gif`).
- Documenta en este manual cualquier nuevo componente que agregues.

### Consistencia visual
- **Paleta de colores:** fondo oscuro (`#0d1117` tono GitHub), texto blanco `#ffffff`, texto secundario `#b8b8b8`
- **Tarjetas:** `rgba(255,255,255,0.04)` para principal, `rgba(255,255,255,0.025)` para secundaria
- **Bordes:** `rgba(255,255,255,0.12)` para principal, `rgba(255,255,255,0.08)` para secundaria
- **Border-radius:** 16px consistente en todas las tarjetas
- **Íconos:** siempre 55×55px de skillicons.dev

---

## 6. Historial de componentes

| Componente | Tipo | Motivo de la decisión | Ubicación | Cómo modificarlo |
|------------|------|-----------------------|-----------|-----------------|
| **Hero banner** | GIF animado | `position:absolute`, `filter:brightness`, `z-index` y `<style>` son eliminados por GitHub. Imposible superponer texto sobre GIF usando CSS. | `assets/hero.gif` | Editar variables en `generate_hero.py` y regenerar |
| **Sobre mí** | HTML compatible | El layout de dos columnas se logra con `<img align="right">` que GitHub sí soporta. El texto usa Markdown puro. | `README.md` (sección `## Sobre mí`) | Editar directamente el párrafo en README.md |
| **Hacker GIF** | GIF existente (sin cambios) | GitHub renderiza `<img>` con atributos básicos. No requería CSS especial. | `hacker.gif` (raíz) | Reemplazar el archivo manteniendo el mismo nombre |
| **Tecnologías (tarjetas)** | SVG | `background:rgba`, `border-radius`, `border` y `display:flex` son eliminados. Las tarjetas visuales requieren SVG. | `assets/tecnologias.svg` | Editar el archivo SVG directamente (es texto plano) |
| **GitHub Streak** | HTML compatible | La URL externa de streak-stats funciona. Solo se necesitaba `<div align="center">` para centrar. | `README.md` (sección streak) | Cambiar el usuario en la URL si cambia el username |

---

*Manual generado automáticamente el 2026-07-27. Actualizar este documento cada vez que se agregue un nuevo componente gráfico al perfil.*
