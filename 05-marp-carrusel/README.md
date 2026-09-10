# Carrusel de Instagram con Claude Code + Marp

**Videos:** "¿Y si crear un carrusel fuera simplemente escribir Markdown?" (9 de agosto, palabra `MARP`) y "Si estás harto de esperar 5 horas para usar Claude..." (10 de agosto, palabra `MODELO`) · Mismo contenido, dos videos.

## Qué es

En vez de diseñar cada slide a mano, le das a Claude Code un prompt que genera un archivo Markdown compatible con [Marp](https://marp.app/), y de ahí Marp exporta las imágenes del carrusel. La clave no es pedirle "hacé un carrusel": es darle un sistema (estructura, jerarquía, poco texto, reglas visuales).

## El prompt

Está en [`prompt.txt`](prompt.txt). Se pega en Claude Code reemplazando `[TEMA]` por el tema del carrusel.

## Cómo ejecutarlo

Después de que Claude Code genere `carousel.md`:

```bash
marp carousel.md --images png
```

Esto exporta cada slide como PNG, listo para subir como carrusel a Instagram.

## Cómo lo uso en el bot

Cuando alguien comenta `MARP` o `MODELO`, se le manda este prompt por privado (después de seguir la cuenta).
