# Blindaje legal para tu app (antes de que te demanden)

Hay 4 cosas que la mayoría de las apps hechas con IA se saltean, y que pueden terminar en una demanda:

1. Declarar que la app usa inteligencia artificial.
2. Cláusula de arbitraje en los Términos de Servicio.
3. Etiqueta / política de privacidad.
4. Agente DMCA designado (si los usuarios pueden subir contenido).

## El prompt

No es un PDF con la respuesta lista: es un prompt que te va guiando punto por punto y te dice cómo solucionar lo que falte. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Actuá como un abogado especializado en apps y SaaS (aunque no sos un abogado real). Voy a contarte cómo está armada mi aplicación. Revisá si tengo cubiertos estos 4 puntos y decime qué me falta:

1. Declaración clara de que uso inteligencia artificial (para evitar problemas de publicidad engañosa).
2. Cláusula de arbitraje en los Términos de Servicio (para reducir riesgo de demandas colectivas).
3. Etiqueta de privacidad / declaración de datos recolectados (Analytics, pixels, etc.) según lo que exigen Apple y Google.
4. Si los usuarios pueden subir contenido (imágenes, videos, PDFs, audio): ¿tengo registrado un agente DMCA y una cláusula de takedown que traslade la responsabilidad al usuario?

Por cada punto decime:
- Si lo tengo bien
- Si me falta algo
- Cómo lo soluciono de forma simple (texto listo para copiar si es posible)

Al final dame un resumen claro: qué está ok y qué tengo que arreglar antes de publicar o seguir escalando.
```

## Links oficiales

- Agente DMCA / registro de copyright: https://copyright.gov/
