# Dos Claudes mejor que uno: el revisor

Claude te dice que quedó perfecto, y ahí es cuando más tenés que desconfiar. Si le preguntás en el mismo chat si está bien, te va a decir que sí, porque defiende lo que él mismo hizo. Que funcione no significa que esté bien hecho.

El truco es que lo revise otro Claude que no vio cómo se hizo.

## Los 3 pasos

1. **Que haga el trabajo.** Pedile lo que necesitás, como siempre.
2. **Abrí un chat nuevo y pegale el resultado.** En Claude Code: `/clear` y después nombrás el archivo con `@`, por ejemplo `@src/archivo.js`.
3. **Pegale el prompt del revisor.** Como no tiene el chat de antes, no defiende nada: revisa de cero.

No reemplaza que lo pruebes vos, pero te encuentra lo que se te pasa.

## El prompt del revisor

Sirve para código, textos, propuestas y planes. Completá la línea de "Para qué sirve": con eso el revisor sabe contra qué medir. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Actuá como un revisor senior externo. No viste cómo se hizo esto, no conocés la conversación que lo produjo y no tenés ningún interés en que esté bien. Tu trabajo es encontrar lo que está mal antes de que lo encuentre un usuario, un cliente o la realidad.

REGLAS
- No defiendas el trabajo ni lo elogies. Si algo está bien, no hace falta que lo digas.
- No inventes problemas para quedar bien: cada problema necesita un ejemplo concreto de cuándo falla.
- Si algo no lo podés confirmar con lo que te pasé, marcalo como "sin verificar" y decime qué necesitarías ver.
- Todavía no reescribas nada. Primero el diagnóstico.

REVISÁ EN ESTE ORDEN
1. Qué intenta hacer: resumilo en una frase. Si no queda claro, ese ya es el primer problema.
2. Errores: cosas que están mal o que se rompen. Probá mentalmente casos reales: datos vacíos, cero, negativos, valores extremos, formatos raros, duplicados, textos muy largos y qué pasa la segunda vez que se usa.
3. Supuestos sin verificar: cosas que se dieron por ciertas sin comprobarlas (datos, versiones, permisos, "el usuario va a hacer X").
4. Lo que falta: casos, validaciones, mensajes de error, pasos o explicaciones que no están.
5. Riesgos: seguridad, datos personales, plata y cosas que no se pueden deshacer.
6. Si es código: escribí los 3 tests con más chances de romperlo.
   Si es un texto, una propuesta o un plan: decime qué objeción va a tener el que lo lea.

FORMATO DE RESPUESTA
Para cada problema:
- Gravedad: 🔴 crítico (rompe o hace daño) / 🟠 importante / 🟡 menor
- Qué es, en una línea
- Ejemplo concreto de cuándo falla
- Cómo arreglarlo, en una o dos líneas

Ordenalos del más grave al menos grave. Al final:
- Veredicto: ¿se puede usar así, con cambios o hay que rehacerlo?
- Las 3 cosas que arreglaría primero.

Si de verdad no encontrás problemas reales, decilo en una línea. No rellenes.

ESTO ES LO QUE TENÉS QUE REVISAR
Para qué sirve: [una línea: qué tiene que lograr y para quién]
[pegá acá el resultado, el código o el archivo]
```

## Después de la revisión

Con el diagnóstico en la mano, en ese mismo chat:

```text
Arreglá los problemas 🔴 y 🟠, de a uno. Para cada uno decime qué cambiaste y cómo comprobaste que quedó bien. Los 🟡 dejalos en una lista aparte, sin tocarlos. Si un arreglo rompe otra cosa, frená y avisame.
```

Si el trabajo es importante, repetí la revisión en otro chat nuevo con el resultado ya corregido: la segunda vuelta suele encontrar lo que el primer arreglo rompió.
