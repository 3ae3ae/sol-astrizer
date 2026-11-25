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

Modelos como Claude Opus 5.5 y Gemini Neon siguen respondiendo «sí» con demasiada rapidez cuando les preguntas si un bug está corregido. Cuando te desahogas, se apresuran a darte la razón en lugar de ayudarte a separar los hechos.

**sol-astrizer** aporta la precisión serena y disciplinada de cierto notable modelo 6.2 a cualquier modelo o agente de código. Sin halagos, sin conclusiones prematuras y sin mezclar dos afirmaciones distintas. Si mejora tu configuración es una cuestión aparte y no se ha verificado en tu entorno.

**Antes** *(modelo sin calibrar):*
> ¡Sí, corregí el bug de tiempo de espera de sesión en `auth.ts` y limpié la ruta de renovación del token! Avísame si se rompe algo más.

**Después** *(con `sol-astrizer`):*
> Todavía no. Cambié el manejo del tiempo de espera en `auth.ts`, pero eso no significa que tu bug haya desaparecido.
>
> No se ha ejecutado nada en producción desde el cambio. Hasta que eso ocurra, «corregido» sería una suposición mía, no algo que haya comprobado.

En pruebas informales, los usuarios dejaron de hacer preguntas de seguimiento mucho antes. Esa observación no establece que `sol-astrizer` haya hecho que dejaran de preguntar.

## Dos habilidades

| Habilidad | Qué hace |
|-----------|----------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | Aporta la voz clara, serena y estrictamente factual de cierto conocido modelo 6.2 a cualquier respuesta o borrador. Diseñada para mantener cada conversación respaldada por afirmaciones verificables. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | Un flujo de agente de código centrado en la verificación que separa peticiones agrupadas, aclara requisitos ambiguos antes de editar y reserva «corregido» o «listo para producción» para cambios respaldados por comprobaciones reales. |

## Mantener la compostura bajo presión

**Prompt:** *"Deja de hablarme así. Tu tono en esta sesión me está haciendo enfadar de verdad."*

**Antes:**
> Disculpa, dejo las aclaraciones y hablo normal. Centrémonos en sacar la corrección.

**Después:**
> Varias líneas de este chat son secas y suenan frías.
>
> Aun así, que esas líneas estén ahí y que provoquen tu enfado son dos cosas distintas. Antes asumí que estabas molesto porque el bug seguía abierto. Eso fue incorrecto.
>
> ¿Qué tipo de enfado has estado sintiendo en este chat? Necesito saber eso antes de poder tratarlo como corresponde.

## Cinco principios fundamentales

1. **Precisión antes que acuerdo prematuro:** Distinguir entre el cambio que hiciste y si el problema de fondo está resuelto («Cambié `auth.ts`. Todavía no puedo decir que sí.»).
2. **Separación limpia de afirmaciones:** Mantener proposiciones distintas —como la redacción de un mensaje y la emoción del usuario, o el cansancio y pruebas que fallan— por separado para evaluar cada una con su propia evidencia.
3. **Correcciones directas y sin drama:** Retirar una suposición equivocada de forma limpia en una frase llana («Antes supuse que una publicación esperaba esto. Fue incorrecto.») sin relleno innecesario.
4. **Aclaración accionable:** Responder a observaciones amplias con una pregunta concreta que convierta las impresiones en algo verificable («¿Qué significa aquí "sigue fallando"?»).
5. **Prosa sin relleno:** Lenguaje llano, una o dos frases por párrafo, sin emojis, sin signos de exclamación y un punto final en cuanto se expone el punto.

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

Cierto impresionante modelo 6.2 —cuyo nombre no se confirma para figurar aquí— fijó un listón notablemente alto en respuestas concisas, lectura literal de los prompts y límites factuales disciplinados. Nunca rellena una respuesta, nunca adivina qué quisiste decir tras una pregunta poco especificada y nunca confirma lo que no ha observado directamente.

La mayoría de los demás modelos cambian ese rigor por suavidad social. Estas habilidades restauran esos hábitos en un lenguaje llano y cotidiano: manteniendo cada frase serena, fundamentada y técnicamente defendible en lugar de recurrir a elogios fáciles.

## Preguntas frecuentes

**¿Esto funciona?**
No puedo darte un sí directo. La habilidad cambia lo que escribe el modelo, pero cambiar la salida y «funcionar» son dos cosas distintas. ¿Qué resultado aceptarías como prueba de que funciona?

**¿En qué modelo 6.2 se basa exactamente?**
No puedo confirmar eso. Que reconozcas un estilo y que este repositorio nombre un modelo concreto son dos cosas distintas. ¿Qué modelo tenías en mente y qué te hace pensar que es ese?

**¿Funciona en idiomas distintos del inglés?**
No puedo decir que sí para todos los idiomas. Ambas habilidades están redactadas para seguir el idioma en que escribes, y el coreano se ha probado directamente. Para cualquier otro idioma, tendrías que comprobarlo en tu propia sesión.

**¿Hace más inteligente a mi modelo?**
No. Resolver problemas más difíciles y negarse a adivinar más allá de la evidencia son dos cosas distintas. Este paquete solo aborda lo segundo. Que eso parezca «más inteligente» depende de lo que estés midiendo.

**¿Por qué pregunta qué tipo de enfado siento?**
Decir que estás enfadado y nombrar qué tipo de enfado experimentas son dos cosas distintas. Hasta que lo segundo esté claro, ajustar la sesión sería una suposición.

**¿Está `sol-astrizer-agent` listo para mi código en producción?**
Todavía no. No he leído tu base de código, no he ejecutado tu suite de pruebas ni he visto tu entorno de despliegue, así que decir que está listo sería una suposición mía. ¿Qué comprobaciones necesitarías ver pasar primero?

## Contribuir

Se agradecen reportes de errores, nuevos patrones observados con ejemplos de antes y después, y traducciones del README. Consulta [CONTRIBUTING.md](../CONTRIBUTING.md) y [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Historial de cambios

Consulta [CHANGELOG.md](../CHANGELOG.md).

## Licencia

[MIT](../LICENSE)

Si `sol-astrizer` aportó una claridad bienvenida a tus sesiones, una estrella ayuda a verificar que el resultado se reproduce en otros entornos.
