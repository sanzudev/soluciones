# Auditá y arreglá la seguridad de tu app hecha con Claude

Publicar una app hecha con IA sin auditarla es dejarla vulnerable por defecto. Este prompt le pide a Claude que revise tu código como lo haría un auditor de seguridad, y que arregle lo que encuentre.

## El prompt

Está en [`prompt.txt`](prompt.txt) — se lo pasás a Claude Code para que audite tu proyecto.

## Qué revisa

- Claves de API expuestas
- Endpoints sin autenticación
- Bases de datos con reglas de acceso inseguras
- Inyecciones / inputs sin validar
- Falta de rate limiting
- Información sensible expuesta

Por cada hallazgo te explica qué está mal, por qué es peligroso y cómo corregirlo, y termina con un resumen de qué es crítico, qué es medio y qué está bien.
