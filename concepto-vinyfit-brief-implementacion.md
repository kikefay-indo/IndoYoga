# VinyFit — concepto + brief de implementación para indoyoga.org

## 1. El concepto

**Nombre:** VinyFit (así, junto, como marca) — se puede aclarar como subtítulo "Vinyasa Fit" la primera vez que aparece, para que quede claro el origen del nombre.

**Qué es:** una clase que fusiona Vinyasa Flow con entrenamiento funcional. No es "yoga con pesas" ni "gimnasia con posturas sueltas" — es una sola secuencia donde el flow construye movilidad y respiración, y los bloques de fuerza funcional construyen potencia real. El objetivo es que la persona salga habiendo entrenado fuerza Y habiendo practicado yoga, en 55-60 minutos.

**A quién le habla** (dos públicos que hoy no tienen un lugar claro en IndoYoga):

- **El deportista social** — juega al fútbol 5, pádel, corre, hace crossfit o entrena en el gym, y sabe que le falta movilidad, respiración y prevención de lesiones, pero un yoga tradicional le resulta lento o "espiritual" para lo que busca. VinyFit le da un entrenamiento real que además lo hace moverse mejor en su deporte.
- **El yogui/a que necesita fortalecerse** — practica yoga hace tiempo, valora el flow y la respiración, pero con la edad necesita más trabajo de fuerza (masa muscular, densidad ósea, fuerza funcional para el día a día) que una práctica centrada solo en flexibilidad no le da del todo.

El punto en común de ambos: fuerza + movilidad + respiración, sin curva de entrada — no hace falta experiencia previa en yoga ni ser "deportista de gimnasio".

**Posicionamiento en una frase:** "Para quien viene del deporte y quiere moverse mejor, y para quien viene del yoga y quiere estar más fuerte."

**Taglines posibles** (elegir uno o combinarlos):

- "VinyFit — fuerza que fluye."
- "Yoga y fitness, en una misma respiración."
- "Fuerza, movilidad y comunidad. Sin importar de dónde vengas."

**Estructura de clase sugerida (55-60 min):**

1. Activación y respiración (8-10 min)
2. Bloque Vinyasa Flow — calor, movilidad, equilibrio (18-20 min)
3. Bloque de fuerza funcional — peso corporal, bandas, patrones tipo animal flow (18-20 min)
4. Estiramiento guiado + respiración de cierre (8-10 min)

**Tono y diseño:** mantener la identidad visual actual de IndoYoga (tipografías Cormorant Garamond + Outfit, paleta ink/terracotta/cream/ivory/sage) para que se sienta parte de la misma escuela y no un producto aparte — el diferencial es el contenido, no un rebranding. Usar terracotta (color de acento actual) para el badge "Nuevo", y evitar un cuarto color que rompa la paleta.

## 2. Dónde y cómo agregarlo en el sitio (indoyoga.org)

El sitio es un único `index.html` con `css/styles.css` y `js/main.js`, sin dependencias externas. Estas son las clases CSS reales que ya existen y hay que reutilizar (confirmado leyendo el código fuente):

- Sección "Clases" → grilla `.class-types` (hoy `grid-template-columns:repeat(3,1fr)`, línea ~324 de styles.css) con tarjetas `.class-type-card` → `.class-type-icon` (SVG stroke terracotta) → `.class-type-name` (con `<em>` en terracotta) → `.class-type-desc` → `.class-type-meta`.
- `.section-eyebrow`, `.section-title` (con `<em>` en terracotta), `.section-desc` para encabezados de sección.
- `.btn-primary` con `<span>` + `<div class="btn-fill">` para botones.
- `.formacion-badge` como referencia de estilo para un badge pequeño en mayúsculas (se puede clonar para un badge "Nuevo").

### Cambios concretos a pedirle a Claude Code

1. Agregar una 4ª tarjeta en `.class-types` (sección `#clases`), después de "Ashtanga Mysore", siguiendo el mismo markup que las otras 3 tarjetas:
   - Ícono SVG en el mismo estilo lineal (stroke, sin relleno) — por ejemplo una mancuerna o un rayo/pulso.
   - `<h3 class="class-type-name">Vinyasa <em>Fit</em></h3>`
   - `<p class="class-type-desc">Fusión de Vinyasa Flow y entrenamiento funcional: fuerza, movilidad y respiración en una sola clase. Pensada tanto para quienes vienen del deporte como para practicantes de yoga que quieren sumar fuerza real.</p>`
   - `<div class="class-type-meta"><span>55 min</span><span>·</span><span>Todos los niveles</span></div>`
   - Agregar un badge "Nuevo" (clonar el estilo de `.formacion-badge` con `color:var(--terracotta)` en vez de `var(--sage)`, o crear `.badge-new` equivalente).
2. Ajustar el grid: cambiar `.class-types{grid-template-columns:repeat(3,1fr)}` a `repeat(auto-fit,minmax(240px,1fr))` (o `repeat(2,1fr)` en desktop grande) para que 4 tarjetas se acomoden bien en 2x2 sin romper el diseño responsive existente.
3. Actualizar la bajada de la sección Clases (`.section-desc` dentro de `#clases`) para que mencione la nueva propuesta sin perder el resto: algo como "Sesiones de 1 hora. Guiada/Flow, Ashtanga/Flow, Ashtanga Mysore y Vinyasa Fit — con instructores para cada nivel y objetivo."
4. Sumar VinyFit al dropdown "Horario preferido" del formulario de reserva de clase de prueba (`#trialForm`, el `<select name="horario">`) — agregar un `<optgroup label="Vinyasa Fit">` con 1-2 horarios de ejemplo. Importante: dejar un comentario HTML `<!-- TODO: confirmar días/horarios reales de VinyFit con Kike antes de publicar -->` porque los horarios todavía no están definidos.
5. Opcional pero recomendado — agregar un párrafo corto de "para quién es" justo debajo del título de la nueva tarjeta o como micro-sección, usando el mensaje de posicionamiento de la sección 1 (deportista social + yogui que quiere fortalecerse), para que la propuesta de valor quede clara de un vistazo y no solo el nombre.

**No tocar:** la sección Formación/instructorado, el formulario de contacto, ni los links de WhatsApp que ya ajustamos — este cambio es solo sobre la sección Clases.

## 3. Pendiente de tu lado antes de publicar

- Confirmar días/horarios reales de la clase VinyFit (y qué instructor la da).
- Decidir precio/si entra dentro de la membresía mensual actual o es un pase aparte.
- Una foto o video corto de una clase tipo VinyFit para la galería (opcional, mejora mucho la conversión).
