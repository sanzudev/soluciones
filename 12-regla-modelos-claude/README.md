# Cuándo usar Haiku, Sonnet u Opus

**Video:** "Usar siempre el último modelo de Claude está bien… o no?" (18 de agosto) · Palabra clave: `AGENTE`

## La regla

Usar Opus para todo es tirar plata. La idea es elegir el modelo según la tarea:

- **Haiku** → tareas mecánicas: formatear, buscar, cambios chicos, resúmenes.
- **Sonnet** → el día a día: la mayoría de las tareas de programación normales.
- **Opus** → solo cuando hay que pensar en serio: arquitectura, debugging difícil, decisiones con trade-offs.

En Claude Code se cambia con `/model` según la tarea que estés por hacer.

## Nota

> ⚠️ Santiago: esto lo armé con lo que decís en el caption del video. Si tenías una versión más detallada o con más matices (ejemplos concretos, cuándo dudar entre Sonnet y Opus, etc.), pasámela y la reemplazo acá.

## Cómo lo uso en el bot

Cuando alguien comenta `AGENTE`, se le manda este texto por privado (después de seguir la cuenta).
