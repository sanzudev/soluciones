# Que Claude no se ponga tonto en chats largos

Si trabajás horas en el mismo chat, Claude rinde peor: pierde precisión y te gasta más tokens. Anthropic lo llama *context rot*. No hace falta aguantarlo: con tres pasos lo evitás.

## Los 3 pasos

1. **Un tema, un chat.** Cada tema nuevo va en un chat nuevo.
2. **Cerrá cada tema con un resumen.** Antes de dejar el chat, pedile un resumen en `.md` con el prompt de abajo, y usalo como primer mensaje del chat siguiente. Así arranca con el contexto de lo que ya hicieron.
3. **Lo fijo, en un Proyecto.** Las reglas o el contexto que siempre repetís los cargás una vez en un Proyecto de Claude, y los chats de adentro arrancan con eso.

## El prompt del resumen

Pegalo en el chat antes de cerrarlo. También está en [`guia.txt`](guia.txt) junto con los pasos, para copiar limpio.

```text
Antes de cerrar esta conversación, armame un resumen en formato .md para continuar en un chat nuevo. Incluí:

1. Objetivo: qué estamos intentando lograr, en una frase.
2. Hecho: qué quedó resuelto y funcionando.
3. Decisiones: qué elegimos y por qué, para no volver a discutirlo.
4. Pendiente: qué falta, en orden.
5. Contexto clave: archivos, datos o restricciones que el próximo chat tiene que saber.

Sé breve y concreto. Escribilo para que lo pegue tal cual como primer mensaje de un chat nuevo.
```
