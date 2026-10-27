# REA: ingeniería inversa a cualquier app con Claude

Ves una función en una app que te encanta, pero no tenés el código para saber cómo la hicieron. REA (Reverse Engineer Anything) le da a Claude Code las herramientas para investigarla sin el código fuente: te explica cómo funciona, te muestra la evidencia y te arma tu propia versión.

Es open source (licencia MIT), tiene más de 390 mil estrellas en GitHub y el análisis corre en tu computadora.

👉 Repo oficial: https://github.com/morluto/rea · Web: https://rea.tools

> ⚠️ Bajalo solo de `morluto/rea`, de rea.tools o del paquete de npm `rea-agents`. Hay copias con nombres parecidos que no son oficiales.

## Antes de instalar: chequeá tu Node

REA necesita Node.js **22.23.4 o más nuevo dentro de la 22**, **24.22.1 o más nuevo dentro de la 24**, o **26.12.1 en adelante**. Fijate cuál tenés:

```bash
node -v
```

Si te da algo más viejo (por ejemplo `v24.18.0`), instalá la versión LTS desde [nodejs.org](https://nodejs.org) y volvé a correr `node -v`. Con una versión vieja la instalación falla.

## Instalación (2 minutos)

1. Abrí una terminal y corré:

   ```bash
   npx rea-agents setup
   ```

2. Si npm pregunta `Ok to proceed?`, respondé `y`.
3. Elegí **Claude Code** en la lista de agentes (también funciona con Codex, Cursor y Gemini CLI).
4. REA te muestra el plan: qué archivos va a tocar, y hace un respaldo de tu configuración. Revisalo y aprobalo.
5. Cerrá Claude Code y abrilo de nuevo para que cargue las herramientas.

## Cómo usarlo

Abrí Claude Code y pegale el prompt de abajo, con los corchetes completos. Sin instalar nada más funciona con apps de escritorio hechas en Electron (muchísimas apps de chat, notas y editores lo están), con apps .NET y con webs (para las webs necesitás Chrome o un navegador parecido).

Para programas nativos (.exe en C/C++) REA usa un descompilador: Ghidra (gratis), Hopper o IDA. El setup puede usar un Ghidra que ya tengas o instalarte Hopper si se lo aprobás.

## El prompt

También está en [`prompt.txt`](prompt.txt) para copiar limpio.

```text
Usá REA para investigar cómo funciona una función de una app y después armame mi propia versión.

LA APP Y LA FUNCIÓN
- App: [nombre y dónde está instalada (por ejemplo C:\Users\vos\AppData\Local\Programs\NombreApp), o la URL si es una web]
- Función que me interesa: [qué hace, cuándo aparece y qué ves en pantalla]
- Mi proyecto: [dónde la quiero meter: lenguaje, framework y carpeta]

REGLAS
- Antes de empezar, confirmá conmigo que es una app que puedo analizar: mía, open source o que tengo permiso para examinar. Si no queda claro, frená y preguntame.
- Todo lo que afirmes tiene que salir de lo que encontró REA. Para cada conclusión decime la evidencia: archivo, función, línea o llamada.
- Separá siempre lo confirmado de lo que es suposición. Si algo no se puede ver desde la app (por ejemplo, lo que pasa en el servidor de ellos), decilo.
- No copies el código de la app. Entendé la lógica y escribí una versión propia, limpia y adaptada a mi proyecto.
- No modifiques ni ejecutes la app original salvo que te lo pida.

PASOS
1. Reconocimiento: decime qué tipo de app es (Electron, nativa, .NET, web, Android...) y qué necesita REA para analizarla. Si falta una herramienta, decime cuál y cómo instalarla antes de seguir.
2. Ubicá la función: encontrá dónde arranca (el botón, el atajo o el evento) y seguí el camino hasta donde se resuelve.
3. Explicámela simple: qué hace, en qué orden, qué datos entran y qué sale. Máximo 10 líneas, como si yo no supiera programar.
4. Plan de mi versión: qué archivos vas a crear, qué dependencias necesito y qué partes no se pueden replicar (servicios pagos, APIs privadas, modelos propios), con una alternativa para cada una.
5. Esperá mi OK antes de escribir código.
6. Con mi OK: escribí mi versión con tests que comprueben que se comporta como la original en los casos que encontraste.
7. Corré los tests y mostrame el resultado real. Si algo falla, arreglalo antes de decir que terminaste.

FORMATO DE LA RESPUESTA FINAL
- Cómo funciona: resumen simple
- Evidencia: qué encontraste y dónde
- Sin confirmar: lo que es suposición
- Mi versión: archivos creados y cómo probarla
- Tests: el resultado real de correrlos
```

## Por qué el prompt está armado así

- **Evidencia obligatoria:** REA devuelve de dónde sale cada conclusión. Si se la pedís, Claude no puede inventarte cómo funciona algo.
- **Confirmado vs. suposición:** lo que pasa en los servidores de otra empresa no se ve desde la app. Mejor saberlo antes de prometer que lo podés replicar.
- **OK antes del código:** primero entendés y decidís; recién después se escribe. Así no tirás tokens en una versión que no querías.
- **Versión propia, no copia:** entender cómo funciona algo es una cosa; pegar el código de otro en tu proyecto es otra, y te puede traer problemas de licencia.

## Mantenerlo al día

REA saca versiones seguido. Para actualizar tu configuración:

```bash
npx rea-agents@latest setup
```

Si lo instalaste global (`npm install --global rea-agents`), con `rea update` alcanza. Para sacarlo: `rea uninstall`.

## Uso responsable

REA es para investigar, aprender, lograr compatibilidad entre programas y analizar software que es tuyo o que tenés permiso para examinar. Usalo con apps open source, con las tuyas o con autorización. Los términos de cada app y las leyes de tu país siguen valiendo.
