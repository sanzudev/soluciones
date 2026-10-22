# Dos Claudes mejor que uno: el revisor

Claude te dice que quedó perfecto, y ahí es cuando más tenés que desconfiar. Si le preguntás en el mismo chat si está bien, te va a decir que sí, porque defiende lo que él mismo hizo. Que funcione no significa que esté bien hecho.

El truco es que lo revise otro Claude que no vio cómo se hizo.

## Los 3 pasos

1. **Que haga el trabajo.** Pedile lo que necesitás, como siempre.
2. **Abrí un chat nuevo y pegale el resultado.** En Claude Code: `/clear` y después nombrás el archivo con `@`, por ejemplo `@src/archivo.js`.
3. **Pegale el prompt del revisor.** Como no tiene el chat de antes, no defiende nada: revisa de cero.

No reemplaza que lo pruebes vos, pero te encuentra lo que se te pasa.

## El prompt del revisor

Pegalo en el chat nuevo. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Actuá como un revisor externo que no vio cómo se hizo esto. No defiendas el trabajo: tu tarea es encontrarle problemas.

Revisá lo que te paso abajo y buscá:

1. Errores: cosas que están mal o que se rompen con casos reales (datos vacíos, valores raros, límites).
2. Supuestos sin verificar: cosas que se dieron por ciertas sin comprobarlas.
3. Lo que falta: casos, validaciones o pasos que no están cubiertos.

Para cada problema decime qué es, por qué importa y un ejemplo concreto de cuándo falla. Ordenalos del más grave al menos grave.

Si algo no lo podés confirmar, decilo en vez de suponerlo. Si no encontrás problemas reales, decilo: no rellenes.

Esto es lo que tenés que revisar:
[pegá acá el resultado, el código o el archivo]
```
