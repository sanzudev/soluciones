# Subagentes en Codex

Revisar un proyecto entero con un único agente suele mezclar seguridad, bugs, arquitectura y tests en un análisis superficial. Este prompt hace que Codex primero entienda el proyecto y después reparta la revisión entre **subagentes especializados que trabajan en paralelo**.

Sirve para una auditoría completa, revisar un pull request, investigar un bug, analizar una funcionalidad o endurecer un proyecto antes de llevarlo a producción.

## El prompt

Copialo al inicio de una sesión de Codex. También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Quiero que trabajes con SUB-AGENTES EN PARALELO.
No resuelvas todo en un solo hilo.

## 0) Primero adaptate a MI proyecto
Antes de spawnear agentes, hacé un diagnóstico rápido (vos, agente principal):
1. Detectá stack, estructura de carpetas y tipo de proyecto (web, API, mobile, automatización, monorepo, etc.).
2. Detectá qué parece crítico: auth, pagos, datos sensibles, integraciones, jobs, UI.
3. Si falta 1 dato clave para no inventar, preguntame UNA sola pregunta. Si podés seguir con supuestos, listalos explícitamente y continuá.

## 1) Objetivo de esta corrida
Elegí el modo según lo que te pida (si no especifico, usá REVIEW FULL):

- REVIEW FULL: auditoría amplia del estado actual
- REVIEW PR: comparar branch actual vs main/master
- FEATURE: analizar una feature puntual antes de implementar
- BUG: investigar un bug puntual y proponer fix
- HARDENING: foco seguridad + estabilidad + producción

Mi pedido concreto:
[ESCRIBÍ ACÁ QUÉ QUERÉS: ej. "review full del repo" / "revisar auth" / "preparar fix del bug de login"]

## 2) Reglas de orquestación
- Spawneá sub-agentes con roles separados.
- Un agente = un foco. No mezclar responsabilidades.
- Priorizá trabajo en PARALELO cuando sea lectura/análisis.
- Evitá que varios agentes editen los mismos archivos a la vez.
- Esperá a que terminen todos los sub-agentes de análisis antes del resumen final.
- En esta pasada: NO implementes cambios grandes salvo que te lo pida explícitamente.
- Si algo no se puede confirmar con evidencia en el repo, marcálo como "no verificado".

## 3) Sub-agentes a spawnear

### A) Explorer (mapa)
- Armá mapa del proyecto: entrypoints, módulos, rutas/API, datos, configs.
- Identificá dependencias críticas y puntos de riesgo.
- Output: mapa corto + archivos clave.

### B) Seguridad
- Buscá: secrets en código/config, auth débil, autorización rota, exposición de datos, inputs sin validar, cookies/sesiones inseguras, CORS abierto, SSRF/XSS/SQLi obvios, permisos de archivos, logs con data sensible.
- Severidad: Crítica / Alta / Media / Baja.
- Output: hallazgo + evidencia (archivo) + impacto + fix breve.

### C) Correctness / Bugs
- Buscá bugs lógicos, race conditions, manejo de errores pobre, estados inválidos, null/edge cases, timeouts, reintentos, condiciones de carrera, inconsistencias de datos.
- Output: bug + cómo reproducirlo (si se infiere) + archivo + fix sugerido.

### D) Arquitectura / Mantenibilidad
- Acoplamiento, duplicación, módulos confusos, deuda técnica que frene cambios, boundaries rotos, configs hardcodeadas, falta de separación de responsabilidades.
- Output: problemas de diseño + por qué importan + mejora simple.

### E) Frontend / UX (solo si aplica)
- Validaciones de formularios, estados loading/error vacíos, feedback al usuario, llamadas duplicadas, accesibilidad básica, inconsistencias de UI flow.
- Si no hay frontend, omití este agente.

### F) Data / Backend / Integraciones (solo si aplica)
- Validación de schemas, migraciones, transacciones, idempotencia, colas, webhooks, retries, rate limits, contratos de API.
- Si no aplica, omití este agente.

### G) Tests / Calidad
- Qué hay testeado vs qué falta en flujos críticos.
- Riesgos de regresión, tests frágiles, huecos en auth/pagos/permisos.
- Output: huecos prioritarios + casos de test sugeridos.

## 4) Formato obligatorio del resumen final (agente principal)

## Resumen ejecutivo
- Máximo 5 bullets con lo más importante

## Hallazgos prioritarios
Para cada hallazgo:
- Título
- Severidad (Crítica/Alta/Media/Baja)
- Área (Seguridad/Bug/Arquitectura/UX/Tests/etc.)
- Evidencia (path de archivo)
- Por qué importa
- Fix breve recomendado

## Top 5 para hacer YA
1.
2.
3.
4.
5.

## Plan sugerido (sin implementar todavía)
- Paso 1
- Paso 2
- Paso 3

## Qué está bien
- 3 a 5 puntos positivos concretos

## Qué no toqué / no verifiqué
- Lista de límites y supuestos

## 5) Criterio de calidad
- Preferí evidencia sobre opiniones.
- No inventes archivos, librerías ni comportamientos.
- Si hay duda, decilo.
- Sé directo, accionable y ordenado por impacto.
```

## Cómo usarlo

1. Pegá el prompt en Codex.
2. Completá la línea de **Mi pedido concreto**.
3. Dejá que analice el proyecto y lance los subagentes.
4. Pedile que implemente los cambios recién después de revisar el resumen.

Por ejemplo:

```text
Implementá solo el Top 5, un ítem a la vez.
Por cada ítem: plan corto → diff mínimo → cómo probarlo.
No refactorees nada fuera de alcance.
```

## Variantes cortas

**Solo seguridad**

```text
Usá el prompt de sub-agentes, modo HARDENING, foco total en seguridad y exposición de datos.
```

**Solo un bug**

```text
Usá el prompt de sub-agentes, modo BUG.
Bug: [descripción]
Reproducí, aislá causa, proponé fix mínimo.
```

**Solo un pull request**

```text
Usá el prompt de sub-agentes, modo REVIEW PR (branch actual vs main).
```

## Qué tener en cuenta

- Los subagentes ayudan a cubrir más áreas, pero no reemplazan la verificación: revisá la evidencia y probá cada cambio antes de publicarlo.
- Para proyectos grandes, empezá con una auditoría y después implementá los hallazgos por prioridad. Pedir análisis y refactorización masiva al mismo tiempo suele mezclar problemas.
- Si el proyecto contiene secretos o datos reales de clientes, comprobá que no estén incluidos en el repositorio antes de iniciar la revisión.
