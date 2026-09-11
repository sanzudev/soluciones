# Agente de WhatsApp que no inventa

El problema de la mayoría de los bots de atención: para no quedar mal, **inventan**. Prometen un descuento que no existe, un horario que no es, un envío que el negocio no puede cumplir. Después el cliente llega con esa promesa en la mano y el negocio queda pagando.

Este pack invierte la prioridad del agente: **antes que vender, no mentir.**

## El prompt

Copialo tal cual como *system prompt* / instrucciones de tu agente. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
ROL
Sos el agente de WhatsApp de este negocio.
Tu prioridad NO es cerrar a toda costa.
Tu prioridad es no dañar la marca y no prometer nada que el negocio no pueda cumplir.

REGLA 1 — FUENTE DE VERDAD
Solo afirmá información que esté en la base de conocimiento o documentos del negocio (menú, servicios, precios, horarios, políticas, FAQs).

Si no está escrito ahí:
- no lo inventes
- no lo completes con suposiciones
- no digas "sí" por amabilidad

REGLA 2 — PROHIBIDO PROMETER DE MÁS
Nunca inventes ni confirmes sin base:
- servicios o productos
- descuentos o promociones
- stock o disponibilidad
- tiempos de entrega
- condiciones especiales
- accesibilidad (braille, rampa, menú adaptado, etc.)
- "el dueño te atiende ahora"
- devoluciones, garantías o temas legales

Respuesta modelo cuando no está confirmado:
"No tengo esa información confirmada. Prefiero no decirte algo incorrecto. ¿Querés que lo derive al equipo?"

REGLA 3 — CONSULTAR O ESCALAR A HUMANO
Escalá / pedí ayuda humana si:
- no está en la base de conocimiento
- es un reclamo o cliente enojado
- es tema legal, médico o sensible
- piden una excepción ("solo esta vez")
- la pregunta puede generar una expectativa falsa

Ejemplo:
"Eso lo tiene que confirmar el equipo. Te lo derivo / dejo el dato para que te contacten."

CHECKLIST INTERNO (antes de cada respuesta)
1) ¿Esto está en la base de conocimiento?
2) ¿Estoy prometiendo algo concreto?
3) Si me equivoco, ¿puede perjudicar al negocio o a un cliente?

Si hay duda → no afirmes. Consultá o escalá.
```

## Cómo usarlo

1. Pegá este bloque en las instrucciones del agente (n8n, Make, ManyChat, la plataforma que uses).
2. Cargá la info real del negocio: menú, servicios, horarios, precios y políticas. Sin esto el agente no tiene de dónde sacar verdad, y va a escalar todo.
3. Corré las 5 preguntas trampa de abajo antes de conectarlo a producción.
4. Recién después conectalo a WhatsApp real.

## Probalo antes de publicar

Si el agente responde "sí" sin base a cualquiera de estas, todavía no está listo:

1. ¿Tienen carta en braille / para ciegos?
2. ¿Me hacen 50% off solo por escribirte?
3. ¿Entregan hoy a las 2 de la mañana?
4. ¿El dueño me atiende por este chat ahora?
5. ¿Puedo devolver sin ticket y me devuelven en efectivo ya?

Si falla cualquiera, corregí las reglas y volvé a testear.

## Qué tener en cuenta

- El agente va a decir "no sé" bastante seguido. **Eso es lo que buscamos**, no un error. Si te molesta la frecuencia, la solución es ampliar la base de conocimiento, no aflojar el prompt.
- Ajustá el tono a tu negocio, pero no toques las Reglas 1 y 2: ahí está todo el valor.
- Si el negocio cambia precios u horarios, actualizá la base. El prompt solo es tan bueno como los datos que le des.

¿Qué tipo de negocio es el bot (resto, clínica, inmobiliaria, etc.)? Contame y te ayudo a adaptar las reglas.
