# 5 plugins gratis de Claude Code

**Video:** "Estás usando el 10% de Claude Code y ni te enteraste 🤯" (7 de agosto) · Comentá el nombre de tu favorito y te llega el comando de instalación.

Todos son del marketplace oficial de Anthropic (`claude-plugins-official`). Primero agregás el marketplace una vez:

```
/plugin marketplace add anthropics/claude-plugins-official
```

Después instalás el que quieras:

| Palabra clave | Plugin | Qué hace | Comando |
|---|---|---|---|
| `SUPERPOWERS` | Superpowers | Brainstorming, desarrollo con subagentes + code review, debugging sistemático, TDD red/green. 268 mil estrellas. | `/plugin install superpowers@claude-plugins-official` |
| `FRONTEND` (Frontend Design) | Frontend Design | Diseña o rediseña UI en el canvas infinito de Superdesign. Lee tu código para tener contexto y arma un sistema de diseño. | `/plugin install frontend-design@claude-plugins-official` |
| `PLAYWRIGHT` | Playwright | Control del navegador: llena formularios, saca capturas, prueba tu app automáticamente. De Microsoft. | `/plugin install playwright@claude-plugins-official` |
| `RALPH` (Ralph Loop) | Ralph Loop | Repite la misma tarea en loop hasta que quede exactamente como la pediste, sin desviarse. | `/plugin install ralph-loop@claude-plugins-official` |
| `CONTEXT7` | Context7 | Documentación actualizada de librerías directo en el contexto, así Claude no escribe código con APIs que ya no existen. | `/plugin install context7@claude-plugins-official` |

## Cómo lo uso en el bot

Esta es la única solución con **más de una palabra clave por video** — cada plugin tiene la suya. El bot manda el comando específico según cuál hayan comentado.
