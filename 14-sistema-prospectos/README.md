# Sistema de prospección: leads + outreach automático

Un sistema para conseguir y contactar prospectos con IA, de punta a punta: perfil de cliente ideal, scraping con Appify, un workflow de n8n para el outreach automático, y un Excel con los prospectos rankeados.

## El prompt

Antes de armar nada, te pregunta a qué te dedicás, quién es tu cliente ideal, en qué zona buscás y por qué canal querés contactar. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Quiero que me armes un sistema completo para conseguir y contactar prospectos con IA.

IMPORTANTE:
- No asumas mi rubro.
- Primero preguntame:
  1. Qué vendo / a qué me dedico
  2. Quién es mi cliente ideal
  3. En qué ciudad/país busco
  4. Por qué canal quiero contactar (mail, etc.)

Cuando tenga eso, entregame:

1. Perfil de cliente ideal listo
2. Cómo usar Appify para scrapear (Google Maps / redes) según mi caso
3. Flujo de n8n
   - El JSON completo listo para importar (o la secuencia de nodos bien detallada)
   - Cómo importarlo
   - Qué credenciales necesito
   - Template de mail personalizado adaptado a lo que vendo
4. Cómo generar un Excel con prospectos (columnas: nombre, empresa, email, teléfono, ciudad, por qué sirve, score)
5. Cómo ordenarlos del mejor al peor

Todo adaptable a mi negocio. Empezá con las preguntas.
```
