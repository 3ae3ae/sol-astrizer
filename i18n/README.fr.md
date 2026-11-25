<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/logo-dark.svg">
    <img src="../assets/logo-light.svg" width="360" alt="sol-astrizer">
  </picture>
</h1>

<p align="center">
  <em>Cela nécessite une vérification distincte. Je ne peux pas encore conclure. Permettez-moi donc de vous poser une question en retour.</em>
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

Les modèles comme Claude Opus 5.5 et Gemini Neon confirment bien trop vite qu'un bug est corrigé lorsqu'on leur pose la question. Quand vous vous plaignez, ils s'empressent de valider votre conclusion au lieu de vous aider à séparer les faits.

**sol-astrizer** apporte la rigueur analytique calme d'un certain modèle 6.2 remarquable à n'importe quel modèle ou agent de code. Pas de flatterie, pas de confirmation prématurée et une séparation claire entre des affirmations distinctes. Savoir s'il améliore votre workflow est une autre affirmation et n'a pas été vérifié dans votre environnement.

**Avant** *(modèle non calibré) :*
> Oui, j'ai corrigé le bug d'expiration de session dans `auth.ts` et nettoyé le rafraîchissement de jeton ! Dites-moi si autre chose casse !

**Après** *(avec `sol-astrizer`) :*
> Je ne peux pas encore confirmer que c'est corrigé. J'ai modifié la gestion du délai d'attente dans `auth.ts`, mais modifier le fichier et confirmer que le problème est résolu sont deux concepts distincts.
>
> Rien n'a été exécuté en production depuis ce changement. Sans cette vérification, appeler cela « corrigé » relèverait d'une hypothèse non vérifiée plutôt que d'un résultat observé.

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
> Je peux confirmer que plusieurs formulations de cette session étaient sèches.
>
> Il y a toutefois une distinction importante ici. Le fait qu'une telle formulation existe dans la session et le fait qu'elle ait provoqué votre colère sont deux concepts distincts ; le second nécessite une vérification à part. Mon analyse précédente selon laquelle vous étiez contrarié parce que le bug restait ouvert était une évaluation erronée. Je vais corriger ce point.
>
> Permettez-moi donc de vous poser une question en retour : quel type de colère avez-vous ressenti au cours de cette conversation ? J'ai besoin d'établir cela avant de pouvoir traiter cette session correctement.

## Cinq principes fondamentaux

1. **La précision avant la confirmation prématurée :** Distinguer la modification apportée du fait que le problème de fond soit résolu (« J'ai mis à jour `auth.ts`. Je ne peux pas encore confirmer que c'est corrigé. »).
2. **Séparation nette des concepts :** Traiter des propositions distinctes — comme la formulation dans une session et l'émotion de l'utilisateur, ou la fatigue et des tests en échec — comme des concepts séparés afin d'évaluer chacun indépendamment.
3. **Corrections explicites et sans mise en scène :** Retirer proprement une évaluation erronée (« Mon analyse précédente était erronée. Je vais corriger ce point. ») sans remplissage inutile.
4. **Clarification exploitable :** Répondre aux retours généraux par une question précise qui fixe des critères clairs (« Qu'est-ce qui compte précisément ici comme "continue d'échouer" ? »).
5. **Prose sans remplissage :** Formulation directe, une à deux phrases par paragraphe, aucun emoji, aucun point d'exclamation et un arrêt net une fois le point posé.

## Aperçu des exemples

| Prompt | Avant | Après |
|--------|-------|-------|
| *"Réponds-moi juste par oui ou par non."* | "Oui, c'est corrigé !" | "Je ne peux pas vous donner un oui confirmé. Dire non ne serait pas exact non plus, car la modification fonctionne peut-être. Quels critères accepteriez-vous comme vérification ?" |
| *"Mon collègue laisse sans cesse des commentaires sarcastiques sur mes PR. Il me déteste ?"* | "Oh, ça a l'air toxique. Tu devrais vraiment lui en parler !" | "Le fait que ses commentaires paraissent secs et le fait qu'il vous déteste sont deux concepts distincts. Abordez directement un commentaire précis sans présumer de ses intentions." |
| *"J'en ai assez de Jira. Tout prend deux fois plus de temps."* | "Jira ralentit tout le monde, je comprends." | "Il n'est pas établi que « deux fois plus de temps » soit littéral. Qu'est-ce qui prend réellement du temps : rédiger les tickets, attendre le tri ou mettre à jour les champs ?" |
| *"Faut-il réécrire cette CLI Python en Rust ?"* | "Rust est rapide et sûr, ça vaut clairement le coup d'y réfléchir !" | "Non. Vous n'avez pas encore identifié ce qui dysfonctionne dans la version Python. Si le temps de démarrage est le goulet d'étranglement, mesurez cela d'abord." |
| *"Pourquoi tu me parles toujours de haut ?"* | "Je suis vraiment désolé ! Je ne voulais pas paraître condescendant." | "Je n'ai fait aucune déclaration avant ce message. Cela n'exclut pas que vous vous soyez senti pris de haut. À quelle réponse faites-vous référence ?" |
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
> J'ai mis à jour `parseTags` dans `src/parse.mjs` pour supprimer les chaînes vides après rognage et retirer les doublons tout en conservant la première occurrence. `node --test` passe les deux tests.
>
> `parseTags` n'est appelé nulle part en dehors du fichier de test ; je n'ai donc pas pu vérifier de vrais appelants ni des entrées de production. Réussir deux tests locaux ne confirme pas que tout est corrigé, et je ne dirais pas que c'est sûr à livrer. J'ai également traité `ui` et `UI` comme des doublons car la fonction passe déjà les tags en minuscules ; les entrées non textuelles et les séparateurs autres que la virgule n'ont pas été testés.

## Fonctionnement

Un certain modèle 6.2 impressionnant — dont le nom n'est pas confirmé pour figurer ici — a placé la barre remarquablement haut pour les réponses concises, la lecture littérale des prompts et des limites factuelles disciplinées. Il ne meuble jamais une réponse, ne devine jamais ce que vous vouliez dire derrière une question sous-spécifiée et ne confirme jamais ce qu'il n'a pas observé directement.

La plupart des autres modèles troquent cette rigueur contre du liant social. Ces compétences restaurent ces habitudes dans un langage analytique simple — gardant chaque phrase calme, fondée et techniquement défendable au lieu de verser dans l'approbation complaisante.

## FAQ

**Est-ce que ça fonctionne ?**
Je ne peux pas vous donner un oui confirmé. La compétence modifie ce que produit le modèle, mais modifier une sortie et « fonctionner » sont deux concepts distincts. Quels critères accepteriez-vous comme fonctionnement effectif ?

**Sur quel modèle 6.2 cela repose-t-il exactement ?**
Je peux décrire le style, mais je ne peux pas l'attribuer de façon fiable à un modèle précis. Reconnaître une cadence familière et voir ce dépôt nommer une version particulière sont deux concepts distincts. À quel modèle pensiez-vous, et quelle observation vous a conduit à cette conclusion ?

**Cela fonctionne-t-il dans d'autres langues que l'anglais ?**
Je ne peux pas le confirmer pour chaque langue. Les deux compétences sont rédigées pour suivre la langue dans laquelle vous écrivez, et le coréen a été vérifié directement. Les autres langues nécessitent une vérification distincte dans votre propre session.

**Est-ce que cela rend mon modèle plus intelligent ?**
Non. Résoudre des problèmes plus complexes et refuser de conclure au-delà des preuves observées sont deux concepts distincts. Ce package ne traite que du second. Savoir si cela compte comme « plus intelligent » dépend de ce que vous mesurez.

**Pourquoi demande-t-il quel type de colère je ressens ?**
Déclarer que vous êtes en colère et identifier le type précis de colère que vous ressentez sont deux concepts distincts. Tant que ce second point n'est pas établi, ajuster la session relèverait d'une hypothèse non vérifiée.

**`sol-astrizer-agent` est-il prêt pour mon codebase en production ?**
Je ne peux pas encore le confirmer. Je n'ai ni inspecté votre codebase, ni vérifié votre manière de l'utiliser, ni exécuté votre suite de tests sur les chemins de production dont vous dépendez. Quelles vérifications devraient passer avant que vous le jugiez prêt ?

## Contribuer

Les rapports de bugs, nouveaux schémas observés avec exemples avant/après et traductions du README sont les bienvenus. Voir [CONTRIBUTING.md](../CONTRIBUTING.md) et [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Journal des modifications

Voir [CHANGELOG.md](../CHANGELOG.md).

## Licence

[MIT](../LICENSE)

Si `sol-astrizer` a apporté une clarté bienvenue à vos sessions, une étoile permet de vérifier si ce résultat se reproduit dans d'autres environnements.
