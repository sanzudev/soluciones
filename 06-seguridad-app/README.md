# Auditá y arreglá la seguridad de tu app hecha con Claude

Publicar una app hecha con IA sin auditarla es dejarla vulnerable por defecto. Este prompt le pide a Claude que revise tu código como lo haría un auditor de seguridad, y que arregle lo que encuentre.

## El prompt

También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Actuá como un auditor de seguridad para apps hechas con IA.
Voy a contarte cómo está armada mi aplicación.
Revisá y buscá problemas típicos:

- Claves de API expuestas
- Endpoints sin autenticación
- Bases de datos con reglas de acceso inseguras
- Inyecciones / inputs sin validar
- Falta de rate limiting
- Información sensible expuesta

Por cada problema decime:
1. Qué está mal
2. Por qué es peligroso
3. Cómo lo corrijo de forma simple (código o pasos si es posible)

Al final dame un resumen: qué está crítico, qué es medio y qué está ok.
No inventes hallazgos: si no tenés evidencia, decí qué necesitarías ver para confirmarlo.
```
