# Ink House (escritorio del escritor)

Réplica autocontenida del escritorio Ink House en un solo `index.html`, con UI en **español e inglés** (conmutable) y seudónimos / nombres de pluma.

## Cómo abrir

1. Abre el archivo `index.html` en tu navegador (doble clic, o arrástralo a una ventana).
2. O, desde esta carpeta, sirve los archivos en local:

```bash
cd /workspace/ink-house
python3 -m http.server 8765
```

Luego visita `http://localhost:8765` en el navegador.

No hace falta instalar dependencias ni ejecutar un build: CSS y JavaScript van incluidos en el HTML. Las tipografías se cargan desde Google Fonts si hay red.

## Qué incluye

- **SPA de vistas** en la barra lateral (sin backend): Escritorio, Manuscritos, Tareas, Calendario, Estadísticas, Disparadores, Musa; **Ajustes** sigue siendo modal
- Selector de **nombres de pluma** debajo de Escritorio (solo elegir; no cambia de vista)
- Tema cute + elegante: blush / rosa caramelo / lila — **Claro / Oscuro / Sistema** en Ajustes
- Franja **Hoy escribo**, ciclo de escritura, temporizador, **Solo escribir**, **Cerrar sesión**
- Persistencia local de tareas, eventos, prompts, chispas y manuscritos (`folio-es-*` / `ink-house-view`)
- Confirmación in-app (Cancelar / Eliminar) antes de borrar pluma, tarea, evento, prompt, chispa o manuscrito
- **Exportar datos** (JSON y Markdown) y **Reporte por novela**
- **Idioma** Español | English desde Ajustes (un solo HTML)

## Nombres de pluma

- **Barra lateral (bajo Escritorio):** solo *chooser*. Lista los seudónimos; al hacer clic se activa uno. Sin formulario de creación en el nav.
- **Ajustes:** añadir, **Editar** (renombrar) y **Eliminar** (con confirmación). Al borrar el activo, se elige otro o queda vacío con aviso para añadir en Ajustes.
- **Por defecto:** `Jane Doe` y `John Doe` únicamente. Si `localStorage` solo tenía el set demo antiguo (Mileth P. / M. Rivera / Anónimo / Anonymous), al cargar se migra a Jane + John; nombres personalizados se conservan y no se reinyecta Mileth.
- Persistencia: `folio-es-pennames` (`{ names, active }`).

## Tema

En **Ajustes → Tema**: **Claro**, **Oscuro** o **Sistema** (`prefers-color-scheme`). Se guarda en `folio-es-theme` (`light` | `dark` | `system`). El botón de luna del header cicla los tres modos. Si existía `folio-theme`, se migra.

## Exportar y reportes

- **Exportar datos** (Ajustes): JSON o Markdown con nombres de pluma, sesiones, metadatos de borradores, notas de continuidad, proyectos y tareas.
- **Reporte por novela**: elige un manuscrito (en Ajustes o en Vista de proyectos) y **Generar reporte** descarga un Markdown con título, estado, progreso, sesiones, notas de continuidad y tareas relacionadas.

## Idioma (i18n)

En **Ajustes → Idioma / Language**: Español o English (`folio-es-lang`).

## Persistencia (localStorage)

| Clave | Uso |
|-------|-----|
| `folio-es-theme` | Tema: `light` \| `dark` \| `system` |
| `folio-es-lang` | Idioma (`es` \| `en`) |
| `folio-es-pennames` | Lista + nombre de pluma activo |
| `folio-mood` / `folio-mood-at` | Ánimo de sesión |
| `folio-quick` | Notas rápidas |
| `folio-es-sessions` | Historial de sesiones |
| `folio-es-drafts` | Borradores Solo escribir |
| `folio-es-words-today` / `folio-es-words-day` / `folio-es-words-week` | Impulso diario/semanal |
| `folio-es-manuscripts` / `folio-es-active-ms` | Lista de manuscritos + activo |
| `folio-es-tasks` | Tareas (añadir / completar / eliminar) |
| `folio-es-events` | Agenda / calendario |
| `folio-es-prompts` | Banco de disparadores |
| `folio-es-sparks` | Chispas guardadas (Musa) |
| `ink-house-view` | Última vista SPA abierta |

**Solo escribir** oculta el escritorio y deja un lienzo con manuscrito, pluma, borrador, temporizador y ánimo. **Cerrar sesión** registra palabras, ánimo, pluma, manuscrito y duración en `folio-es-sessions`.
