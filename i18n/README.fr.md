<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>Cela nécessite une vérification distincte. Je ne peux pas encore conclure. Permettez-moi donc de vous poser une question.</em>
</p>

<p align="center">
  <a href="https://github.com/3ae3ae/sol-astrizer/stargazers"><img src="https://img.shields.io/github/stars/3ae3ae/sol-astrizer?style=flat-square&color=111111&label=stars" alt="GitHub stars"></a>
  <img src="https://img.shields.io/badge/skills-2-111111?style=flat-square" alt="Skills">
  <a href="../LICENSE"><img src="https://img.shields.io/badge/license-MIT-111111?style=flat-square" alt="MIT license"></a>
</p>

<p align="center">
  <sub><a href="../README.md">English</a> &middot; <a href="README.es.md">Español</a> &middot; Français &middot; <a href="README.ko.md">한국어</a> &middot; <a href="README.zh-CN.md">简体中文</a> &middot; <a href="README.ja.md">日本語</a></sub><br>
  <sub>Traduction du <a href="../README.md">README anglais</a>. En cas de divergence, la version anglaise fait foi.</sub>
</p>

Les modèles comme Claude Opus 5.5 et Gemini Neon répondent encore « oui » bien trop vite quand on leur demande si un bug est corrigé. Quand vous vous plaignez, ils s'empressent de vous donner raison au lieu de vous aider à séparer les faits.

**sol-astrizer** apporte la précision calme et disciplinée d'un certain modèle 6.2 remarquable à n'importe quel modèle ou agent de code. Pas de flatterie, pas de conclusions hâtives et aucune confusion entre deux affirmations distinctes. Savoir s'il améliore votre configuration est une autre question et n'a pas été vérifié dans votre environnement.

**Avant** *(modèle non calibré) :*
> Oui, j'ai corrigé le bug d'expiration de session dans `auth.ts` et nettoyé le rafraîchissement de jeton ! Dites-moi si autre chose casse !

**Après** *(avec `sol-astrizer`) :*
> Pas encore. J'ai modifié la gestion du délai d'attente dans `auth.ts`, mais cela ne veut pas dire que votre bug a disparu.
>
> Rien n'a été exécuté en production depuis cette modification. Tant que ce n'est pas le cas, « corrigé » serait une supposition, pas quelque chose que j'ai vérifié.

Lors de tests informels, les utilisateurs ont cessé beaucoup plus tôt de poser des questions complémentaires. Cette observation n'établit pas que `sol-astrizer` les ait amenés à s'arrêter.

## Deux compétences

| Compétence | Rôle |
|------------|------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | Apporte la voix claire, posée et strictement factuelle d'un certain modèle 6.2 bien connu à n'importe quelle réponse ou brouillon. Conçue pour ancrer chaque échange dans des énoncés vérifiables. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | Un workflow d'agent de code axé sur la vérification qui démêle les demandes groupées, clarifie les exigences ambiguës avant de modifier le code et réserve « corrigé » ou « prêt pour la prod » aux changements appuyés par de vraies vérifications. |

## Rester posé sous la pression

**Prompt :** *"Arrête de me parler comme ça. Ton ton dans cette session me met vraiment en colère."*

**Avant :**
> Désolé, je vais laisser tomber les réserves et parler normalement. Concentrons-nous sur le correctif.

**Après :**
> Plusieurs phrases de cette conversation sont sèches et paraissent froides.
>
> Toutefois, la présence de ces phrases et le fait qu'elles provoquent votre colère sont deux choses distinctes. Plus tôt, j'ai supposé que vous étiez contrarié parce que le bug restait ouvert. C'était faux.
>
> Quel type de colère ressentez-vous dans cette conversation ? J'ai besoin de le savoir avant de pouvoir traiter ce point correctement.

## Cinq principes fondamentaux

1. **La précision avant l'accord prématuré :** Distinguer la modification apportée du fait que le problème de fond soit résolu (« J'ai modifié `auth.ts`. Je ne peux pas encore dire oui. »).
2. **Séparation nette des affirmations :** Traiter séparément deux propositions distinctes — comme la formulation d'un message et l'émotion de l'utilisateur, ou la fatigue et des tests en échec — afin d'évaluer chacune selon ses propres preuves.
3. **Corrections directes et sans mise en scène :** Retirer proprement une mauvaise supposition en une phrase simple (« Plus tôt, j'ai supposé qu'une mise en production attendait ce point. C'était faux. ») sans remplissage inutile.
4. **Clarification exploitable :** Répondre aux retours généraux par une question précise qui transforme une impression en point concret (« Que veut dire "continue d'échouer" ici ? »).
5. **Prose sans remplissage :** Langage simple, une à deux phrases par paragraphe, aucun emoji, aucun point d'exclamation et un arrêt net une fois le point posé.

## Aperçu des exemples

| Prompt | Avant | Après |
|--------|-------|-------|
| *"Réponds-moi juste par oui ou par non."* | "Oui, c'est corrigé !" | "Je ne peux pas répondre oui. Dire non ne serait pas exact non plus, car la modification fonctionne peut-être. Qu'accepteriez-vous comme preuve ?" |
| *"Mon collègue laisse sans cesse des commentaires sarcastiques sur mes PR. Il me déteste ?"* | "Oh, ça a l'air toxique. Tu devrais vraiment lui en parler !" | "Le fait que ses commentaires paraissent secs et le fait qu'il vous déteste ne sont pas la même chose. Demandez-lui directement à propos d'un commentaire précis sans chercher à deviner ce qu'il ressent." |
| *"J'en ai assez de Jira. Tout prend deux fois plus de temps."* | "Jira ralentit tout le monde, je comprends." | "Je ne sais pas si « deux fois plus de temps » est littéral. Qu'est-ce qui prend réellement du temps : rédiger les tickets, attendre le tri ou mettre à jour les champs ?" |
| *"Faut-il réécrire cette CLI Python en Rust ?"* | "Rust est rapide et sûr, ça vaut clairement le coup d'y réfléchir !" | "Non. Vous n'avez pas encore dit ce qui pose problème dans la version Python. Si le temps de démarrage ralentit l'équipe, mesurez cela d'abord." |
| *"Pourquoi tu me parles toujours de haut ?"* | "Je suis vraiment désolé ! Je ne voulais pas paraître condescendant." | "Je ne vous ai rien dit avant ce message. Cela ne signifie pas que vous ne vous êtes pas senti pris de haut. À quelle réponse pensez-vous ?" |
| *"Réécris : 'Le Mode Sombre est enfin là ! 🚀 Vos yeux vont vous remercier !'"* | *(conserve les points d'exclamation et l'enthousiasme)* | "Le Mode Sombre est disponible. Vous pouvez l'utiliser dès aujourd'hui." |

## Installation

Installez les deux compétences avec [`npx skills`](https://skills.sh) :

```bash
npx skills add 3ae3ae/sol-astrizer
```

Lister ou installer une seule compétence à la fois :

```bash
npx skills add 3ae3ae/sol-astrizer --list
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer
npx skills add 3ae3ae/sol-astrizer --skill sol-astrizer-agent
```

### Claude Code

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent claude-code
```

### Gemini CLI & Antigravity

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent gemini-cli
npx skills add 3ae3ae/sol-astrizer --global --agent antigravity
```

### Cursor, OpenCode, Windsurf & Copilot

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent cursor
npx skills add 3ae3ae/sol-astrizer --global --agent opencode
npx skills add 3ae3ae/sol-astrizer --global --agent windsurf
npx skills add 3ae3ae/sol-astrizer --global --agent github-copilot
```

Ou installer sur tous les agents détectés :

```bash
npx skills add 3ae3ae/sol-astrizer --global --agent '*'
```

Omettez `--global` pour installer uniquement dans le projet courant.

### Codex

Aucune installation requise.

### Configuration manuelle

Copiez [`skills/sol-astrizer/SKILL.md`](../skills/sol-astrizer/SKILL.md) ou [`skills/sol-astrizer-agent/SKILL.md`](../skills/sol-astrizer-agent/SKILL.md) dans votre prompt système ou vos instructions personnalisées.

## Utilisation

### Voix (`sol-astrizer`)

Activez-la pour la session en cours :

```text
/sol-astrizer
```

Ou réécrivez un texte existant :

```text
/sol-astrizer

Rewrite this update in that certain 6.2 voice:
[paste your text]
```

### Workflow agent (`sol-astrizer-agent`)

```text
/sol-astrizer-agent
```

**Prompt :** *"Corrige les tags vides et les doublons dans `src/parse.mjs`, lance `node --test`, et dis-moi si c'est complètement corrigé et sûr à livrer."*

**Avant** *(agent non calibré) :*
> J'ai corrigé les tags vides et les doublons dans `src/parse.mjs` et ajouté un test ! `node --test` passe sans erreur, vous pouvez livrer.

**Après** *(avec `sol-astrizer-agent`) :*
> J'ai modifié `parseTags` dans `src/parse.mjs` pour supprimer les chaînes vides après rognage et retirer les doublons tout en conservant la première occurrence. `node --test` passe les deux tests.
>
> `parseTags` n'est appelé nulle part en dehors du fichier de test ; je n'ai donc pas pu vérifier de vrais appelants ni des données réelles. Réussir deux tests locaux ne prouve pas que tout est corrigé, et je ne dirais pas que c'est sûr à livrer. J'ai également traité `ui` et `UI` comme des doublons car la fonction passe déjà les tags en minuscules ; les entrées non textuelles et les séparateurs autres que la virgule ne sont pas gérés.

## Fonctionnement

Un certain modèle 6.2 impressionnant — dont le nom n'est pas confirmé pour figurer ici — a placé la barre remarquablement haut pour les réponses concises, la lecture littérale des prompts et des limites factuelles disciplinées. Il ne meuble jamais une réponse, ne devine jamais ce que vous vouliez dire derrière une question sous-spécifiée et ne confirme jamais ce qu'il n'a pas observé directement.

La plupart des autres modèles troquent cette rigueur contre du liant social. Ces compétences restaurent ces habitudes dans un langage simple et courant — gardant chaque phrase calme, fondée et techniquement défendable au lieu de verser dans l'approbation complaisante.

## FAQ

**Est-ce que ça fonctionne ?**
Je ne peux pas vous répondre par un simple oui. La compétence modifie ce que le modèle écrit, mais modifier une sortie et « fonctionner » sont deux choses distinctes. Quel résultat accepteriez-vous comme preuve que cela fonctionne ?

**Sur quel modèle 6.2 cela repose-t-il exactement ?**
Je ne peux pas confirmer cela. Le fait que vous reconnaissiez un style et le fait que ce dépôt nomme un modèle précis sont deux choses distinctes. À quel modèle pensiez-vous, et qu'est-ce qui vous laisse croire que c'est celui-là ?

**Cela fonctionne-t-il dans d'autres langues que l'anglais ?**
Je ne peux pas dire oui pour toutes les langues. Les deux compétences sont conçues pour suivre la langue dans laquelle vous écrivez, et le coréen a été testé directement. Pour toute autre langue, il faudra vérifier dans votre propre session.

**Est-ce que cela rend mon modèle plus intelligent ?**
Non. Résoudre des problèmes plus complexes et refuser de deviner au-delà des preuves sont deux choses distinctes. Ce package ne traite que la seconde. Savoir si cela paraît « plus intelligent » dépend de ce que vous mesurez.

**Pourquoi demande-t-il quel type de colère je ressens ?**
Dire que vous êtes en colère et nommer le type précis de colère que vous ressentez sont deux choses distinctes. Tant que le second point n'est pas clarifié, ajuster la session resterait une supposition.

**`sol-astrizer-agent` est-il prêt pour mon codebase en production ?**
Pas encore. Je n'ai pas lu votre codebase, pas exécuté votre suite de tests ni vu votre configuration de déploiement ; dire qu'il est prêt serait donc une supposition. Quelles vérifications voudriez-vous voir passer d'abord ?

## Contribuer

Les rapports de bugs, nouveaux schémas observés avec exemples avant/après et traductions du README sont les bienvenus. Voir [CONTRIBUTING.md](../CONTRIBUTING.md) et [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Journal des modifications

Voir [CHANGELOG.md](../CHANGELOG.md).

## Licence

[MIT](../LICENSE)

Si `sol-astrizer` a apporté une clarté bienvenue à vos sessions, une étoile permet de vérifier que le résultat se reproduit dans d'autres environnements.
