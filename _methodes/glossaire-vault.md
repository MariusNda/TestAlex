# Glossaire du vault

> **Vocabulaire opérant du harnais : un terme, une définition, un nom canonique.**
> Ce fichier ne prescrit rien — les règles sont dans `CLAUDE.md`. Il fixe seulement le sens
> des mots que les règles et les commandes emploient, pour qu'un même mot ne désigne pas
> deux choses selon le fichier où on le lit.
>
> Ne décrit **pas** le vocabulaire réglementaire (PSP, TPP, SCA, VoP…) : celui-là appartient
> aux textes et aux exigences. Ici, seulement les mots du harnais lui-même.
>
> Structure et champs des objets manipulés : `_methodes/ontologie.md`.

## Termes de structure

| Terme canonique | Définition | À ne pas confondre avec |
|---|---|---|
| **vault** | L'ensemble du dépôt : règles, méthodes, commandes et contenu. | — |
| **fichier de règle** | Dit *comment travailler* : `CLAUDE.md`, `_methodes/`, `_skills/`, `.claude/skills/`. | fichier de contenu |
| **fichier de contenu** | Dit *ce qu'on sait* : exigences, faits, hypothèses, conclusions, cartographie, journal, CR. | fichier de règle |
| **commande** | Skill invocable de `.claude/skills/`, appelée par `/nom`. Les huit commandes sont listées dans `CLAUDE.md`. | document de méthode |
| **document de méthode** | Fichier de `_skills/` ou `_methodes/`. **Non invocable** : `Skill(redaction-gt)` échoue. Se lit avec l'outil de lecture. | commande |
| **réglementation active** | L'unique réglementation déclarée en tête de `CLAUDE.md`. Une commande sans argument s'y applique : elle en déduit le dossier, le préfixe et la page Notion. | réglementation *citée en argument*, qui ne change pas l'active |
| **niveau de traitement** | Profondeur de traitement d'une réglementation : 0 veille passive · 1 cadrage · 2 approfondi · 3 suivi. Déclaré dans le `_LISEZMOI.md` du dossier, récapitulé dans `_transverse/etat-mission.md`. | niveau de mutualisation (arbre 1, 0→5) |
| **registre** | Fichier qui tient la liste exhaustive d'un type d'objet : `sources.md`, `hypotheses.md`, `annuaire.md`, `exigences/_index.md`. | index de navigation (`_ROUTAGE.md`, `_LISEZMOI.md`) |

## Identifiants

| Terme canonique | Définition |
|---|---|
| **préfixe** | Les trois à quatre lettres qui ouvrent tout identifiant d'une réglementation : `DSP3-`, `AMLR-`, `NIS2-`, `CRA-`, `EN-`, `ENW-`. Table de référence : `CLAUDE.md`. |
| **`<PRÉFIXE>`** | **Notation de substitution, à remplacer par le préfixe réel au moment d'écrire.** `<PRÉFIXE>-EX-NNN` sur DSP3 s'écrit `DSP3-EX-042`. |
| **`REG`** | ⚠️ **N'est pas un préfixe et ne s'écrit jamais dans un fichier de contenu.** Un identifiant `REG-H01` est une erreur : c'est `DSP3-H01` qu'il fallait écrire. Là où un texte de règle dit « REG- », lire `<PRÉFIXE>-`. |
| **`<reg>`** | Nom de dossier d'une réglementation, en minuscules : `dsp3`, `amlr`, `nis2`, `cyber-resilience-act`, `euro-numerique`, `euro-numerique-wholesale`. Distinct du préfixe, qui est en majuscules. |

Motifs complets et emplacement de chaque type d'identifiant : `_methodes/ontologie.md`.

## Les trois natures d'affirmation

| Terme canonique | Définition | Marqueur |
|---|---|---|
| **fait** | Affirmation sourcée et vérifiée. Sans source, elle n'existe pas. | `[SRC: …]` obligatoire |
| **hypothèse** | Supposition, zone floue, arbitrage non rendu. Portée par un identifiant et un statut. | 🟡 🟢 🔴 ⚫ |
| **opinion** | Position tenue par quelqu'un. Toujours attribuée nommément (« le GT estime », « CAPS considère »). | attribution explicite |

Une conséquence tirée d'un article — « donc il faudra… », « l'impact est… » — n'est **pas** un fait :
c'est une hypothèse à créer ou une opinion à attribuer (Règle n°1).

## Chaîne et cartographie

| Terme canonique | Définition | À ne pas confondre avec |
|---|---|---|
| **maillon** | Un étage de la chaîne de traçabilité : TEXTE, EXIGENCES, CINÉMATIQUES, CARTOGRAPHIE, FAITS/HYPOTHÈSES, ARBRES, CONCLUSIONS, SLIDES. | fichier : un maillon peut être éclaté sur plusieurs fichiers |
| **brique** | Composant de la cartographie applicative. Porte un état et une cotation d'impact. | domaine fonctionnel, qui découpe les exigences et non le SI |
| **domaine fonctionnel** | Un des 22 chapitres qui découpent le référentiel d'exigences (`exigences/NN-*.md`). Indexé dans `exigences/_index.md`. | brique |
| **cotation** | Échelle d'impact d'une brique dans `cartographie/matrice-impacts-si.md`. | graduation d'une conclusion, sortie d'un arbre |
| **sortie d'arbre** | Résultat du passage d'une brique dans l'arbre 1 (niveau de mutualisation 0→5) ou l'arbre 2 (make vs buy). **Aide à la décision, jamais un verdict.** | décision du GT, qui se prend en séance |

## Sources et versions

| Terme canonique | Définition | À ne pas confondre avec |
|---|---|---|
| **source** | Document inscrit au registre `sources.md` de la réglementation, citable en `[SRC: …]`. | référence non inscrite, qui n'est pas citable |
| **baseline de veille** | Ce que le vault sait déjà d'un texte au moment où `/veille` démarre : version de référence de `sources.md` + dernière entrée `[REG]` de `journal.md`. C'est le point de comparaison du delta. | ligne de base |
| **ligne de base** | Le dossier `reglementations/<reg>/ligne-de-base/`, où sont **déposés les textes** antérieurs servant de référence de comparaison. Un dossier de fichiers, pas un état. | baseline de veille |
| **héritage** | Le dossier `heritage-<texte>/`, où sont versés les documents du texte précédent (ex. `heritage-dsp2/`). Sert le diff d'un régime à l'autre. | ligne de base |
| **diff** | Comparaison article par article entre deux versions d'un même texte, déclenchée par la Règle n°3. Produit une liste d'écarts et les identifiants du vault impactés. | delta de veille, qui compare des *nouveautés* à une baseline, pas deux rédactions |
| **contribution d'entité** | Étude ou note reçue d'une entité, reproduite à l'identique sous `contributions-entites/`, référencée `<PRÉFIXE>-ET-NN`. **Elle engage l'entité, pas le GT.** | production du GT |

## Glossaire des briques ≠ ce fichier

`reglementations/<reg>/cartographie/glossaire.md` s'appelle « glossaire » mais n'en est pas un au
sens de ce fichier : c'est le **catalogue des briques** de la cartographie, une ligne par composant,
avec son regroupement, son état et sa définition sourcée. Le vocabulaire du harnais, lui, est ici.

Quand un fichier dit « le glossaire », il désigne le catalogue des briques.
Ce fichier-ci s'appelle toujours « le glossaire du vault », jamais « le glossaire » seul.

## Séances

| Terme canonique | Définition |
|---|---|
| **GT** | Séance plénière du Groupe de Travail Architectures Réglementaires. Numérotée en continu (GT11, GT12…), transverse à toutes les réglementations. |
| **atelier** | Séance de travail restreinte, avec une entité ou un référent. Non numérotée. |
| **séance** | Terme générique couvrant GT et atelier. C'est le mot à employer quand la nature n'est pas déterminante. |
| **CR** | Compte rendu d'une séance, dans `gt-seances/<reg>/`. Méthode : `_skills/compte-rendu-gt/SKILL.md`. |

## Délégation (Règle n°7)

| Terme canonique | Définition |
|---|---|
| **balayage** | Passe large : une ligne par fichier en réponse à une question fermée (« lesquels portent X »). S'emploie quand c'est le *retour* qui sature. Précède l'extraction. |
| **extraction** | Passe étroite sur les seuls fichiers retenus : l'agent rend le passage, jamais son interprétation. |
| **contrat de retour** | Ce qu'un sous-agent doit rendre : une question fermée par fichier, un `[SRC:]` distinct par fichier, jamais de retour fusionné. Non négociable. |
