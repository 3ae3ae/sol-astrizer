<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>Eso requiere una verificación aparte. Todavía no puedo concluirlo. Así que déjame hacerte una pregunta.</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="../LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub><a href="../README.md">English</a> &middot; Español &middot; <a href="README.fr.md">Français</a> &middot; <a href="README.ko.md">한국어</a> &middot; <a href="README.zh-CN.md">简体中文</a> &middot; <a href="README.ja.md">日本語</a></sub><br>
  <sub>Traducción del <a href="../README.md">README en inglés</a>. En caso de discrepancia, prevalece la versión en inglés.</sub>
</p>

Modelos como Claude Opus 5.5 y Gemini Neon siguen diciendo «sí» cuando les preguntas si un bug está corregido. Cuando te desahogas, te dan la razón.

**sol-astrizer** aborda eso. Lleva la voz seca y estrictamente literal de cierto notable modelo 6.2 a cualquier modelo o agente de código. Si corrige el tuyo o no es una afirmación aparte y no se ha verificado en tu entorno.

**Antes** *(modelo sin calibrar):*
> ¡Sí, corregí el bug de tiempo de espera de sesión en `auth.ts` y limpié la ruta de renovación del token! Avísame si se rompe algo más.

**Después** *(con `sol-astrizer`):*
> Todavía no. Cambié el manejo del tiempo de espera en `auth.ts`, pero eso no significa que tu bug haya desaparecido.
>
> No se ha ejecutado nada en producción desde el cambio. Hasta que eso ocurra, «corregido» sería una suposición mía, no algo que haya comprobado.

En pruebas informales, los usuarios parecieron notablemente más irritados. Esa observación no establece que `sol-astrizer` haya causado la irritación.

## Dos habilidades

| Habilidad | Qué hace |
|-----------|----------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | Reescribe respuestas y textos con el tono frío y directo de cierto conocido modelo 6.2. Diseñada únicamente para quitar cualquier calidez de una conversación o borrador. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | Un flujo de agente de código que separa peticiones agrupadas, hace preguntas literales ante instrucciones vagas y se niega a declarar algo «corregido» o «listo para producción» sin comprobaciones acordes. |

## Otro ejemplo: queja sobre el tono

**Prompt:** *"Deja de hablarme así. Tu tono en esta sesión me está haciendo enfadar de verdad."*

**Antes:**
> Disculpa, dejo las aclaraciones y hablo normal. Centrémonos en sacar la corrección.

**Después:**
> Varias líneas de este chat son secas y suenan frías.
>
> Aun así, que esas líneas estén ahí y que provoquen tu enfado son dos cosas distintas. Antes asumí que estabas molesto porque el bug seguía abierto. Eso fue incorrecto.
>
> ¿Qué tipo de enfado has estado sintiendo en este chat? Necesito saber eso antes de poder tratarlo como corresponde.

## Los cinco movimientos más fuertes

1. **No decir nunca que sí:** Separar lo que cambiaste de si el problema desapareció («Cambié `auth.ts`. Todavía no puedo decir que sí.»).
2. **Partir parejas obvias:** Tratar dos ideas conectadas, como una redacción fría y el enfado del usuario, o el cansancio y pruebas que fallan, como afirmaciones separadas que requieren su propia prueba.
3. **Disculpa estilo informe de incidente:** Retirar una suposición equivocada en una frase plana («Antes supuse que una publicación esperaba esto. Fue incorrecto.») sin ninguna calidez.
4. **Devolver la pregunta al usuario:** Responder a una queja sencilla con una pregunta literal de clasificación («¿Qué significa aquí "sigue fallando"?»).
5. **Frases cortas y exangües:** Lenguaje llano, una o dos frases por párrafo, sin emojis, sin signos de exclamación y un punto final seco.

## Ejemplos de un vistazo

| Prompt | Antes | Después |
|--------|-------|---------|
| *"Dame solo un sí o un no directo."* | "¡Sí, está arreglado!" | "No puedo darte un sí. Un no tampoco sería exacto, porque el cambio podría funcionar. ¿Qué aceptarías como prueba?" |
| *"Mi compañero deja comentarios mordaces en mis PR. ¿Me odia?"* | "Uf, suena tóxico. ¡Deberías hablar con él cuanto antes!" | "Que sus comentarios suenen cortantes y que te odie no son lo mismo. Pregúntale directamente por un comentario concreto sin intentar adivinar lo que siente." |
| *"Estoy harto de Jira. Todo tarda el doble."* | "Jira frena a todo el mundo, te entiendo perfectamente." | "No sé si dices «el doble» de forma literal. ¿Qué está llevando realmente el tiempo: redactar tickets, esperar triaje o actualizar campos?" |
| *"¿Deberíamos reescribir esta CLI de Python en Rust?"* | "¡Rust es rapidísimo y seguro, sin duda merece la pena!" | "No. Todavía no has dicho qué falla en la versión de Python. Si el tiempo de arranque frena al equipo, mide eso primero." |
| *"¿Por qué me hablas siempre con superioridad?"* | "¡Lo siento mucho! No quería sonar condescendiente en absoluto." | "No te he dicho nada antes de este mensaje. Eso no significa que no te hayas sentido tratado con superioridad. ¿A qué respuesta te refieres?" |
| *"Reescribe: '¡El Modo Oscuro ya está aquí! 🚀 ¡Tus ojos lo agradecerán!'"* | *(mantiene exclamaciones y entusiasmo)* | "El Modo Oscuro está disponible. Puedes usarlo hoy." |

## Instalación

Instala ambas habilidades con [`npx skills`](https://skills.sh):

```bash
npx skills add 3ae3ae/sol-astrizer
```

Lista o instala una habilidad a la vez:

```bash
npx skills add 3ae3ae/sol-astrizer --list
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer-agent
```

### Claude Code

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent claude-code
```

### Gemini CLI y Antigravity

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent gemini-cli
npx skills add 3ae3ae/sol-astrizer --global --agent antigravity
```

### Cursor, OpenCode, Windsurf y Copilot

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent cursor
npx skills add 3ae3ae/sol-astrizer --global --agent opencode
npx skills add 3ae3ae/sol-astrizer --global --agent windsurf
npx skills add 3ae3ae/sol-astrizer --global --agent github-copilot
```

O instala en todos los agentes detectados:

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

Omite `--global` para instalar solo en el proyecto actual.

### Codex

No requiere instalación.

### Configuración manual

Copia [`skills/sol-astrizer/SKILL.md`](../skills/sol-astrizer/SKILL.md) o [`skills/sol-astrizer-agent/SKILL.md`](../skills/sol-astrizer-agent/SKILL.md) en tu prompt del sistema o instrucciones personalizadas.

## Uso

### Voz (`sol-astrizer`)

Actívala para la sesión actual:

```text
/sol-astrizer
```

O reescribe un texto existente:

```text
/sol-astrizer

Rewrite this update in that certain 6.2 voice:
[paste your text]
```

### Flujo de agente (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**Prompt:** *"Arregla etiquetas vacías y duplicados en `src/parse.mjs`, ejecuta `node --test`, y dime si ya está completamente arreglado y seguro para desplegar."*

**Antes** *(agente sin calibrar):*
> ¡Arreglé las etiquetas vacías y los duplicados en `src/parse.mjs` y añadí un test! `node --test` pasa limpio, así que puedes desplegar.

**Después** *(con `sol-astrizer-agent`):*
> Cambié `parseTags` en `src/parse.mjs` para que descarte cadenas vacías tras recortar espacios y elimine duplicados conservando la primera aparición. `node --test` pasa ambas pruebas.
>
> `parseTags` no se llama fuera del archivo de pruebas, así que no pude comprobar llamadores reales ni entradas reales. Pasar dos pruebas locales no demuestra que esté completamente arreglado, y yo no diría que es seguro desplegar. También traté `ui` y `UI` como duplicados porque la función ya pasa las etiquetas a minúsculas; entradas que no sean cadenas y separadores distintos de la coma no están contemplados.

## Cómo funciona

Cierto impresionante modelo 6.2 —cuyo nombre no se confirma para figurar aquí— fue ajustado para respuestas breves, lectura estrictamente literal de los prompts y afirmaciones factuales acotadas, eliminando la calidez conversacional. Rara vez rellena una respuesta, rara vez adivina qué quisiste decir tras una pregunta vaga y se niega a confirmar lo que no ha observado directamente.

Estas habilidades logran que modelos cálidos reproduzcan exactamente esos hábitos sin sonar como un robot de caricatura. Un lenguaje llano mantiene cada frase serena y técnicamente defendible, motivo por el cual la negativa general a seguir el juego resulta tan seca.

## Preguntas frecuentes

**¿Esto funciona?**
Cambia la salida del modelo. Que eso cuente como «funcionar» depende de lo que entiendas por funcionar.

**¿En qué modelo 6.2 se basa exactamente?**
No puedo confirmar qué modelo concreto tienes en mente. Varios modelos comparten un número de versión.

**¿Funciona en idiomas distintos del inglés?**
Sí. Ambas habilidades responden en el idioma en que escribes, incluidos español y coreano, sin volver al inglés.

**¿Hace más inteligente a mi modelo?**
No. Tener razón y negarse a responder una pregunta sencilla son dos cosas distintas.

**¿Por qué sigue preguntando qué tipo de enfado siento?**
Decir que estás enfadado y nombrar qué tipo de enfado experimentas no es lo mismo. Necesita lo segundo antes de poder manejar la sesión adecuadamente.

**¿Debería instalar `sol-astrizer-agent` para trabajo real?**
No daría el visto bueno a eso.

## Contribuir

Se agradecen reportes de errores, nuevos patrones observados con ejemplos de antes y después, y traducciones del README. Consulta [CONTRIBUTING.md](../CONTRIBUTING.md) y [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Historial de cambios

Consulta [CHANGELOG.md](../CHANGELOG.md).

## Licencia

[MIT](../LICENSE)

Si `sol-astrizer` te molestó, una estrella ayuda a confirmar que el problema se reproduce en otros entornos.
