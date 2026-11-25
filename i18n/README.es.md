<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>Eso requiere una verificación aparte. Todavía no puedo concluirlo. Así que déjame hacerte una pregunta a cambio.</em>
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

Modelos como Claude Opus 5.5 y Gemini Neon se apresuran a confirmar que algo quedó corregido cuando preguntas si un bug está resuelto. Cuando te desahogas, tienden a validar tu conclusión en lugar de ayudarte a separar los hechos.

**sol-astrizer** aporta el rigor analítico y sereno de cierto notable modelo 6.2 a cualquier modelo o agente de código. Sin halagos, sin confirmaciones prematuras y con separación clara entre afirmaciones distintas. Que mejore tu flujo de trabajo es una cuestión aparte y no se ha verificado en tu entorno.

**Antes** *(modelo sin calibrar):*
> ¡Sí, corregí el bug de tiempo de espera de sesión en `auth.ts` y limpié la ruta de renovación del token! Avísame si se rompe algo más.

**Después** *(con `sol-astrizer`):*
> Todavía no puedo confirmar que esté corregido. Modifiqué el manejo del tiempo de espera en `auth.ts`, pero editar el archivo y confirmar que el problema quedó resuelto son conceptos distintos.
>
> No se ha ejecutado nada en producción desde el cambio. Sin esa verificación, llamarlo «corregido» sería una suposición no verificada, no un resultado observado.

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
> Puedo confirmar que varias frases de esta sesión usaron una redacción cortante.
>
> Sin embargo, aquí hay una distinción importante. El hecho de que esa redacción exista en la sesión y el hecho de que haya causado tu enfado son conceptos distintos; lo segundo requiere una verificación aparte. Mi análisis anterior de que estabas molesto porque el bug seguía abierto fue una evaluación incorrecta. Lo corregiré.
>
> Así que déjame hacerte una pregunta a cambio: ¿qué tipo de enfado has estado sintiendo durante esta conversación? Necesito establecer eso antes de poder tratar esta sesión adecuadamente.

## Cinco principios fundamentales

1. **Precisión antes que confirmación prematura:** Distinguir entre el cambio que hiciste y si el problema de fondo quedó resuelto («Actualicé `auth.ts`. Todavía no puedo confirmar que esté corregido.»).
2. **Separación limpia de conceptos:** Tratar proposiciones distintas —como la redacción en una sesión y la emoción del usuario, o el cansancio y pruebas que fallan— como conceptos separados para evaluar cada uno de forma independiente.
3. **Correcciones explícitas y sin drama:** Retirar limpiamente una evaluación incorrecta («Mi análisis anterior fue incorrecto. Lo corregiré.») sin relleno innecesario.
4. **Aclaración accionable:** Responder a comentarios amplios con una pregunta concreta que fije criterios claros («¿Qué cuenta concretamente aquí como "sigue fallando"?»).
5. **Prosa sin relleno:** Redacción directa, una o dos frases por párrafo, sin emojis, sin signos de exclamación y un punto final en cuanto queda expuesto el punto.

## Ejemplos de un vistazo

| Prompt | Antes | Después |
|--------|-------|---------|
| *"Dame solo un sí o un no directo."* | "¡Sí, está arreglado!" | "No puedo darte un sí confirmado. Decir no tampoco sería exacto, porque el cambio podría funcionar. ¿Qué criterios aceptarías como verificación?" |
| *"Mi compañero deja comentarios mordaces en mis PR. ¿Me odia?"* | "Uf, suena tóxico. ¡Deberías hablar con él cuanto antes!" | "Que sus comentarios suenen cortantes y que no le agrades son conceptos distintos. Aborda un comentario concreto directamente sin asumir su intención." |
| *"Estoy harto de Jira. Todo tarda el doble."* | "Jira frena a todo el mundo, te entiendo perfectamente." | "No se ha establecido si «el doble» es literal. ¿Qué está consumiendo realmente el tiempo: redactar tickets, esperar triaje o actualizar campos?" |
| *"¿Deberíamos reescribir esta CLI de Python en Rust?"* | "¡Rust es rapidísimo y seguro, sin duda merece la pena!" | "No. Todavía no has identificado qué está fallando en la versión de Python. Si el cuello de botella es el tiempo de arranque, mide eso primero." |
| *"¿Por qué me hablas siempre con superioridad?"* | "¡Lo siento mucho! No quería sonar condescendiente en absoluto." | "No he emitido ningún mensaje antes de este. Eso no descarta que te hayas sentido tratado con superioridad. ¿A qué respuesta te refieres?" |
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
> Actualicé `parseTags` en `src/parse.mjs` para descartar cadenas vacías tras recortar espacios y eliminar duplicados conservando la primera aparición. `node --test` pasa ambas pruebas.
>
> `parseTags` no se llama fuera del archivo de pruebas, así que no pude verificar llamadores reales ni entradas de producción. Pasar dos pruebas locales no confirma que esté completamente arreglado, y yo no diría que es seguro desplegar. También traté `ui` y `UI` como duplicados porque la función ya pasa las etiquetas a minúsculas; entradas que no sean cadenas y separadores distintos de la coma no se han probado.

## Cómo funciona

Cierto impresionante modelo 6.2 —cuyo nombre no se confirma para figurar aquí— fijó un listón notablemente alto en respuestas concisas, lectura literal de los prompts y límites factuales disciplinados. Nunca rellena una respuesta, nunca adivina qué quisiste decir tras una pregunta poco especificada y nunca confirma lo que no ha observado directamente.

La mayoría de los demás modelos cambian ese rigor por suavidad social. Estas habilidades restauran esos hábitos en un lenguaje analítico llano: manteniendo cada frase serena, fundamentada y técnicamente defendible en lugar de recurrir a elogios fáciles.

## Preguntas frecuentes

**¿Esto funciona?**
No puedo darte un sí confirmado. La habilidad cambia lo que produce el modelo, pero cambiar la salida y «funcionar» son conceptos distintos. ¿Qué criterios aceptarías como prueba de que funciona?

**¿En qué modelo 6.2 se basa exactamente?**
Puedo describir el estilo, pero no puedo atribuirlo de forma fiable a un modelo concreto. Reconocer una cadencia familiar y que este repositorio nombre una versión específica son conceptos distintos. ¿Qué modelo tenías en mente y qué observación te llevó a esa conclusión?

**¿Funciona en idiomas distintos del inglés?**
No puedo confirmarlo para todos los idiomas. Ambas habilidades están redactadas para seguir el idioma en que escribes, y el coreano se ha verificado directamente. Otros idiomas requieren una verificación aparte en tu propia sesión.

**¿Hace más inteligente a mi modelo?**
No. Resolver problemas más difíciles y negarse a concluir más allá de la evidencia observada son conceptos distintos. Este paquete solo aborda lo segundo. Que eso cuente como «más inteligente» depende de lo que estés midiendo.

**¿Por qué pregunta qué tipo de enfado siento?**
Decir que estás enfadado e identificar el tipo concreto de enfado que experimentas son conceptos distintos. Hasta que lo segundo quede establecido, ajustar la sesión sería una suposición no verificada.

**¿Está `sol-astrizer-agent` listo para mi código en producción?**
Todavía no puedo confirmarlo. No he inspeccionado tu base de código, ni verificado cómo la usas, ni ejecutado tu suite de pruebas en las rutas de producción de las que dependes. ¿Qué comprobaciones tendrían que pasar antes de considerarlo listo?

## Contribuir

Se agradecen reportes de errores, nuevos patrones observados con ejemplos de antes y después, y traducciones del README. Consulta [CONTRIBUTING.md](../CONTRIBUTING.md) y [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Historial de cambios

Consulta [CHANGELOG.md](../CHANGELOG.md).

## Licencia

[MIT](../LICENSE)

Si `sol-astrizer` aportó una claridad bienvenida a tus sesiones, una estrella ayuda a verificar si ese resultado se reproduce en otros entornos.
