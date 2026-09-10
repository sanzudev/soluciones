# Carrusel de Instagram con Claude Code + Marp

En vez de diseñar cada slide a mano, le das a Claude Code un prompt que genera un archivo Markdown compatible con [Marp](https://marp.app/), y de ahí Marp exporta las imágenes del carrusel. La clave no es pedirle "hacé un carrusel": es darle un sistema — estructura, jerarquía, poco texto, reglas visuales.

## El prompt

Reemplazá `[TEMA]` por el tema del carrusel. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Quiero crear un carrusel de Instagram sobre [TEMA].

Generá un archivo carousel.md compatible con Marp.

El carrusel debe tener exactamente 7 slides.

Reglas:
- Una sola idea por slide.
- Poco texto.
- Títulos grandes.
- Jerarquía visual clara.
- Mucho espacio negativo.
- Fondo oscuro.
- Blanco como color principal.
- Violeta como color de acento.
- Estética técnica, minimalista y premium.
- No uses emojis.
- No hagas todos los slides iguales.

Estructura:
1. Hook fuerte.
2. Problema.
3. Consecuencia.
4. Solución.
5. Ejemplo práctico.
6. Resultado.
7. CTA.

Antes de terminar, revisá que ningún slide tenga demasiado texto y que todos sean legibles en formato vertical 1080x1920.

Para ejecutarlo: marp carousel.md --images png
```

## Cómo ejecutarlo

Después de que Claude Code genere `carousel.md`:

```bash
marp carousel.md --images png
```

Esto exporta cada slide como PNG, listo para subir como carrusel a Instagram.
