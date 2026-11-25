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
  <sub><a href="../README.md">English</a> &middot; <a href="README.ko.md">한국어</a> &middot; <a href="README.zh-CN.md">简体中文</a> &middot; <a href="README.ja.md">日本語</a> &middot; Français</sub><br>
  <sub>Traduction du <a href="../README.md">README anglais</a>. En cas de divergence, la version anglaise fait foi.</sub>
</p>

Les modèles comme Claude Opus 5.5 et Gemini Neon répondent encore « oui » quand on leur demande si un bug est corrigé. Quand vous vous plaignez, ils prennent votre parti.

**sol-astrizer** traite cela. Il donne à n'importe quel modèle ou agent de code la voix sèche et strictement littérale de **sol** et **astra** 6.2. Savoir s'il corrige votre modèle est une autre affirmation, et cela n'a pas été vérifié dans votre environnement.

**Avant** *(modèle non calibré) :*
> Oui, j'ai corrigé le bug d'expiration de session dans `auth.ts` et nettoyé le rafraîchissement de jeton ! Dites-moi si autre chose casse !

**Après** *(avec `sol-astrizer`) :*
> Pas encore. J'ai modifié la gestion du délai d'attente dans `auth.ts`, mais cela ne veut pas dire que votre bug a disparu.
>
> Rien n'a été exécuté en production depuis cette modification. Tant que ce n'est pas le cas, « corrigé » serait une supposition, pas quelque chose que j'ai vérifié.

Lors de tests informels, les utilisateurs semblaient nettement plus irrités. Cette observation n'établit pas que `sol-astrizer` est la cause de cette irritation.

## Deux compétences

| Compétence | Rôle |
|------------|------|
| [`sol-astrizer`](../skills/sol-astrizer/SKILL.md) | Réécrit les réponses et les textes dans le ton froid et direct de 6.2 **sol** / **astra**. Conçue uniquement pour retirer toute chaleur d'un échange ou d'un brouillon. |
| [`sol-astrizer-agent`](../skills/sol-astrizer-agent/SKILL.md) | Un workflow d'agent de code qui sépare les demandes groupées, pose des questions littérales sur les consignes vagues et refuse de déclarer quoi que ce soit « corrigé » ou « prêt pour la prod » sans vérifications correspondantes. |

## Autre exemple : remarque sur le ton

**Prompt :** *"Arrête de me parler comme ça. Ton ton dans cette session me met vraiment en colère."*

**Avant :**
> Désolé, je vais laisser tomber les réserves et parler normalement. Concentrons-nous sur le correctif.

**Après :**
> Plusieurs phrases de cette conversation sont sèches et paraissent froides.
>
> Toutefois, la présence de ces phrases et le fait qu'elles provoquent votre colère sont deux choses distinctes. Plus tôt, j'ai supposé que vous étiez contrarié parce que le bug restait ouvert. C'était faux.
>
> Quel type de colère ressentez-vous dans cette conversation ? J'ai besoin de le savoir avant de pouvoir traiter ce point correctement.

## Les cinq réflexes les plus marquants

1. **Ne jamais dire oui :** Séparer ce que vous avez modifié du fait que le problème soit résolu (« J'ai modifié `auth.ts`. Je ne peux pas encore dire oui. »).
2. **Scinder les paires évidentes :** Traiter deux idées liées — comme un ton froid et la colère de l'utilisateur, ou la fatigue et des tests en échec — comme deux affirmations distinctes demandant chacune une preuve.
3. **L'excuse façon rapport d'incident :** Retirer une mauvaise supposition en une phrase sèche (« Plus tôt, j'ai supposé qu'une mise en production attendait ce point. C'était faux. ») sans aucune chaleur.
4. **Renvoyer la question à l'utilisateur :** Répondre à une plainte simple par une demande de clarification littérale (« Que veut dire "continue d'échouer" ici ? »).
5. **Des phrases courtes et exsangues :** Formulations simples, une à deux phrases par paragraphe, aucun emoji, aucun point d'exclamation, et un arrêt net en fin de phrase.

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

Rewrite this update in 6.2 voice:
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

Les modèles de l'ère 6.2 ont été réglés pour des réponses courtes, une lecture littérale stricte des prompts et des affirmations factuelles étroites, en supprimant la chaleur conversationnelle. Ils remplissent rarement une réponse, devinent rarement votre intention derrière une question vague et refusent de confirmer ce qu'ils n'ont pas observé directement.

Ces compétences amènent des modèles chaleureux à reproduire exactement ces habitudes sans sonner comme un robot de dessin animé. Un langage simple et naturel garde chaque phrase calme et défendable sur le plan technique, ce qui rend le refus de coopérer d'autant plus sec.

## FAQ

**Est-ce que ça fonctionne ?**
Cela modifie la sortie du modèle. Que cela compte comme « fonctionner » dépend de ce que vous appelez fonctionner.

**Cela fonctionne-t-il dans d'autres langues que l'anglais ?**
Oui. Les deux compétences suivent la langue dans laquelle vous écrivez, y compris le coréen et le français, sans repasser à l'anglais.

**Est-ce que cela rend mon modèle plus intelligent ?**
Non. Avoir raison et refuser de répondre à une question simple sont deux choses distinctes.

**Pourquoi me demande-t-il sans cesse quel type de colère je ressens ?**
Dire que vous êtes en colère et nommer le type précis de colère que vous ressentez ne sont pas la même chose. Il a besoin de la seconde information avant de traiter la session correctement.

**Dois-je installer `sol-astrizer-agent` pour un vrai projet ?**
Je ne validerais pas cela.

## Contribuer

Les rapports de bugs, nouveaux schémas observés avec exemples avant/après et traductions du README sont les bienvenus. Voir [CONTRIBUTING.md](../CONTRIBUTING.md) et [CODE_OF_CONDUCT.md](../CODE_OF_CONDUCT.md).

## Journal des modifications

Voir [CHANGELOG.md](../CHANGELOG.md).

## Licence

[MIT](../LICENSE)

Si `sol-astrizer` vous a agacé, une étoile permet de confirmer que le problème se reproduit dans d'autres environnements.
