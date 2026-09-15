# Vault CASA — GT Architectures Réglementaires

Source de vérité du GT Architectures Réglementaires (Crédit Agricole S.A.). Deux natures de
fichiers qui ne se mélangent jamais : **les règles**, qui disent comment travailler, et **le
contenu**, qui dit ce qu'on sait.

**Réglementation active : DSP3 / PSR.** C'est l'interrupteur du vault : une commande sans argument
s'y applique et en déduit le dossier, le préfixe d'identifiants et la page Notion.

| Dossier `reglementations/…` | Préfixe | Niveau |
|---|---|---|
| `dsp3/` ⭐ **active** | `DSP3-` | 2 — approfondi |
| `amlr/` | `AMLR-` | 2 — approfondi |
| `nis2/` | `NIS2-` | à définir |
| `cyber-resilience-act/` | `CRA-` | 1 atteint, clos |
| `euro-numerique/` | `EN-` | mission terminée |
| `euro-numerique-wholesale/` | `ENW-` | 0 — veille passive |

Les deux euro numérique n'ont en commun que le nom : ne jamais fusionner leurs chaînes.
Niveaux, charges et critères d'activation : `_transverse/etat-mission.md`.

---

## Préséance des règles

Quand deux règles se contredisent sur une demande, **le dire avant de produire** : une
contradiction tranchée en silence donne deux comportements différents pour un même prompt.
À défaut d'arbitrage, l'ordre est **Règle n°1** (provenance), puis **Règle n°6** (sélection des
sources), puis les autres.

---

## La chaîne de traçabilité

Tout livrable dérive d'une chaîne continue, chaque maillon référençant le précédent :

```
TEXTE → EXIGENCES → CINÉMATIQUES → CARTOGRAPHIE → FAITS / HYPOTHÈSES
      → ARBRES → CONCLUSIONS → SLIDES
   (PDF)   (REG-EX-NNN)          (briques)    (Fn.m) / (REG-Hnn)
```

Aucun élément n'existe sans référencer son amont : une brique cite ses exigences, une conclusion
cite ses faits et hypothèses, un fait cite sa source.

**Quand un maillon change**, chercher son identifiant dans tout le dossier et signaler nommément
chaque élément qui le cite. Le champ `Dépendances` d'une hypothèse est un point de départ, pas la
réponse complète. `/lint` fait cette recherche systématiquement.

**Format de chaque maillon** — motif d'identifiant, emplacement, champs obligatoires, valeurs
autorisées : `_methodes/ontologie.md`. **À lire avant toute écriture dans un fichier de contenu**,
jamais de format écrit de mémoire. Le vocabulaire employé par les règles et les commandes est
fixé dans `_methodes/glossaire-vault.md` ; en particulier `REG-` n'est pas un préfixe mais une
notation de substitution, à remplacer par le préfixe réel de la réglementation.

---

## RÈGLE N°1 — PROVENANCE OBLIGATOIRE

*Non négociable. Ne cède devant aucune autre règle.*

Aucune affirmation factuelle sans source, sous l'une de ces trois formes :

```
[SRC: <document> <version> §<article ou section>]
[SRC: atelier <nom> du <date>]
[SRC: REG-EX-NNN]                              ← référence interne à la chaîne
```

- **Jamais d'invention de référence.** Localiser avant de citer, via `/loi` : PageIndex si indexé,
  sinon le PDF du dossier. Crédits PageIndex épuisés depuis le 2026-07-17, le PDF est la voie normale.
- **Trois natures à distinguer systématiquement.** FAIT, sourcé. HYPOTHÈSE, tracée avec son statut.
  OPINION, attribuée nommément (« le GT estime », « CAPS considère »).
- **Reformuler n'est pas interpréter.** Toute conséquence tirée d'un article — « donc il faudra… »,
  « l'impact est… » — n'est pas sourçable : c'est une hypothèse à créer, ou une opinion à attribuer.
  Jamais une phrase du corps d'un livrable.
- **Le manque se remonte, il ne se comble pas.** Marquer `[SRC: à sourcer ⚠️]` et lister ces marqueurs
  en fin de session. Jamais de reformulation de mémoire, jamais de connaissance générale du modèle.

## RÈGLE N°2 — CYCLE DE VIE DES HYPOTHÈSES

Statuts : **🟡 OUVERTE** · **🟢 TRANCHÉE** · **🔴 OBSOLÈTE** · **⚫ BLOQUANTE** (facteur exogène).

Format complet, avec exemple : `_methodes/format-hypothese.md`. Toute hypothèse porte un
identifiant stable, son statut daté, sa source, la question ouverte, et ses **dépendances** nommées.

**Jamais de suppression.** État courant en tête, historique daté dessous. Un changement de statut
entraîne une entrée au journal et une alerte `⚠️ à revisiter` sur chaque dépendance listée.

## RÈGLE N°3 — VEILLE ET DIFF DE VERSION

À la parution d'une nouvelle version d'un texte, d'un acte délégué ou d'exécution, d'un RTS/ITS
ou d'une guidance :

1. L'ajouter à `sources.md` de la réglementation concernée.
2. Diffuser le diff contre la version précédente, section par section.
3. Croiser avec `exigences/` et `hypotheses.md`, et remonter la chaîne.

Le rapport nomme, par écart : l'article, l'ancienne et la nouvelle rédaction, et les identifiants
du vault impactés. Un écart qui ne change aucune obligation tient en une ligne.

## RÈGLE N°4 — RÉDACTION

Tout livrable — slide, CR, note, email GT — applique `_skills/redaction-gt/SKILL.md`.
**Lire le fichier avant de rédiger, sans exception.**

**Langue de travail : français**, y compris les commentaires intermédiaires d'un raisonnement.
Les termes réglementaires anglais consacrés se gardent tels quels, en italique.

⚠️ `_skills/` porte des **documents de méthode**, pas des skills invocables : `Skill(redaction-gt)`
échoue. Seul `.claude/skills/` porte des commandes.

## RÈGLE N°5 — RELECTURE

**Une relecture rouvre le fichier source.** Corriger ou vérifier une sortie en repartant de la
sortie précédente est interdit. Relire deux fois, oui ; relire sa propre copie, non.

**Un document dont l'en-tête porte une réserve** — « intuitions », « à sourcer », « non stabilisé »
— ne peut pas être cité en `[SRC:]`. Lire l'en-tête avant de citer.

## RÈGLE N°6 — SÉLECTION DES SOURCES

*Non négociable. C'est l'utilisateur qui décide sur quoi le travail s'appuie, jamais toi.*

**Avant toute production qui s'appuie sur des exigences, des faits, une cartographie ou un texte**
— delta, grandes thématiques, impact SI, cotation, note, slide, CR, email — lister les sources
candidates et **attendre la réponse**.

- La liste se construit depuis le `sources.md` de la réglementation active, groupée par famille,
  chaque ligne portant son état de vérifiabilité et une proposition motivée. **Ne rien lire d'autre
  avant la réponse** : seuls `CLAUDE.md`, `_ROUTAGE.md` et `sources.md` servent à l'établir.
- **Sans objet** pour une question factuelle sur un article, un état des lieux, une recherche de
  contact ou une veille : la poser à chaque prompt la rendrait inutile.
- **Une source écartée n'est pas remplacée** par la connaissance générale du modèle. Si son retrait
  rend une affirmation insourçable, elle disparaît ou passe en `[SRC: à sourcer ⚠️]`.

Format de la liste : `_methodes/selection-sources.md`.

## RÈGLE N°7 — DÉLÉGATION

Déléguer isole la source du contexte : seul l'extrait revient. Mais l'agent recharge ce fichier au
démarrage et son retour doit être borné, sinon le pavé est seulement déplacé. **Le gain n'existe
que si l'extrait est bien plus petit que la source, et si le retour reste borné.** Le raisonnement :

1. **Un seul fichier** — rien à isoler : lecture directe, quelle que soit sa taille.
2. **Une question qui couvre tout le document** — l'agent devrait tout renvoyer : lecture directe.
3. **Sinon, répartir** en gardant bornés ce que chaque agent lit et ce qu'il rend. Repères, non
   seuils : **~50 Ko** et **~8 fichiers** par agent, le premier qui sature fixe le nombre. Jamais
   plus d'agents que de fichiers ; un fichier n'est jamais coupé en deux.
4. **Si c'est le retour qui sature d'abord** — beaucoup de fichiers, même petits — la question
   devient un **balayage** : « lesquels portent X », une ligne par fichier. Balayer, puis extraire
   sur les seuls retenus.

Annoncer le nombre d'agents et leur répartition avant de lancer.

**Contrat de retour, lui non négociable.** Une question fermée par fichier. Extraction, jamais
interprétation. Un `[SRC:]` distinct par fichier, jamais un retour fusionné — sans quoi
l'attribution est perdue et la Règle n°1 tombe. Le vide se dit. L'agent lit ce qu'on lui donne,
rien d'autre.

Dimensionnement détaillé et cas réels : `_methodes/delegation.md`.

---

## Commandes

| Commande | Ce qu'elle fait |
|---|---|
| `/loi <question>` | question juridique sourcée sur le texte, citations §exactes |
| `/exigence <article ou domaine>` | décliner une portion du texte en exigences `REG-EX` (Phase 1) |
| `/synthese [reg] [cible]` | couche de synthèse réduite à partir d'une sortie existante du vault |
| `/reunion [nom]` | enregistrement Notion → CR + vault + actions dans « Actions GT » |
| `/brief` | actions ouvertes + état du vault → ordre de bataille (lecture seule) |
| `/mail [CR]` | transformer un CR en email prêt à envoyer (draft seul) |
| `/veille [reg]` | veille réglementaire, delta contre la baseline du vault (Règle n°3) |
| `/debrief [texte]` | vidage de contexte → routage classé et sourcé dans le vault |
| `/lint [reg]` | contrôle de cohérence : identifiants, dépendances, énumérations, sources (lecture seule) |

## Routines

**Début de session** — lire `CLAUDE.md`, puis le `_LISEZMOI.md` et `hypotheses.md` de la
réglementation active.

**Avant tout CR ou email** — consulter `annuaire.md` (noms, entités, registre tu/vous) ; proposer
son enrichissement si un interlocuteur y manque.

**Fin de session** — résumer ce qui a été appris ou modifié, et lister les `[SRC: à sourcer ⚠️]`
encore ouverts. Après une passe d'écriture qui touche plusieurs maillons (`/exigence`, `/debrief`,
`/reunion`), proposer `/lint` : c'est lui qui voit ce que la session a cassé en amont ou en aval.

**Toute écriture** — diff présenté et validé par l'utilisateur avant application. Aucune exception.

## Où trouver quoi

Un fichier, par besoin : `_ROUTAGE.md`. Vocabulaire du harnais : `_methodes/glossaire-vault.md`.
Format des objets du vault : `_methodes/ontologie.md`. Pourquoi ces règles existent, avec les
incidents qui les ont motivées : `_methodes/pourquoi-ces-regles.md`.
Structure : `_methodes/anatomie-vault.md`.
Notion : `_transverse/notion.md`. État de la mission et niveaux : `_transverse/etat-mission.md`.
Incohérences à trancher : `CHANGE.md`. Changements du harnais : `NOUVEAUTES.md`.
