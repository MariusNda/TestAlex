# Nouveautés du vault

> Liste des ajouts et corrections apportés au harnais, entre le 2026-09-06 et le 2026-09-08.
> Un bloc par nouveauté : le titre, le problème, la correction. Rien d'autre.
>
> Les incohérences **relevées mais non corrigées** sont dans `CHANGE.md`, à valider.

---

## 1 · `_ROUTAGE.md` (nouveau fichier)

**Problème.** Rien ne disait par quel fichier entrer. Sur une demande de delta DSP2 → DSP3,
Claude ouvrait cinq ou six fichiers dont trois inutiles, et tout ce qui est lu reste en contexte.
Résultat non reproductible d'une session à l'autre.

**Correction.** Une table par type de demande : les fichiers à lire, dans l'ordre, et ceux à ne
pas ouvrir, avec le motif. Plus une section des cas où **aucun** routage ne s'applique, pour
qu'un chemin approchant ne soit jamais forcé. `CLAUDE.md` impose sa lecture avant toute recherche.

---

## 2 · `CHANGE.md` (nouveau fichier)

**Problème.** Le vault se contredit par endroits, et rien ne le signalait. Le `README.md` annonce
encore le Cyber Resilience Act quand `CLAUDE.md` dit DSP3/PSR.

**Correction.** Un registre de douze incohérences, chacune avec sa preuve et une action proposée,
codées 🔴 🟠 🟡. Rien n'a été corrigé unilatéralement : c'est une liste à valider par le
propriétaire du vault.

---

## 3 · Contrat de sub-agent (`_ROUTAGE.md` §5)

**Problème.** Le contexte sature. Le vault fait 1 039 Ko de markdown ; tout lire est impossible,
et les gros fichiers (matrice 64 Ko, `exigences/` 270 Ko, étude CAPS 98 Ko) écrasent la session.

**Correction.** Au-delà de 20 Ko de source pour moins de 10 % d'extrait utile, la lecture est
déléguée à un sous-agent : une source, une question fermée, retour borné à 300 mots avec un
`[SRC:]` par affirmation, extraction jamais interprétation, et le vide se dit. Le sous-agent
meurt avec son contexte.

---

## 4 · Sélection des sources (`_ROUTAGE.md` §6)

**Problème.** Le choix des sources décide du résultat de toute analyse d'impact, et Claude le
faisait seul. Demande explicite d'Alexandre : qu'il liste, et que ce soit lui qui choisisse.

**Correction.** Avant toute production comparant l'existant au texte, avant tout livrable diffusé,
et quand deux sources divergent : Claude ouvre le `sources.md` de la réglementation active,
regroupe par famille, annonce l'état de vérifiabilité de chaque ligne, propose un défaut motivé,
et attend. La procédure vaut pour les six réglementations du vault, pas seulement DSP3.

Et la règle qui ne se négocie pas : **une source écartée n'est pas remplacée par la connaissance
générale du modèle.** Si son retrait rend une affirmation insourçable, l'affirmation disparaît
ou passe en `[SRC: à sourcer ⚠️]`.

---

## 5 · Règle n°5 — Relecture (`CLAUDE.md`)

**Problème.** Une passe relisait la passe précédente au lieu de la source. Trois occurrences dans
le vault : cinq constats de la revue V1 « déplacés vers les annexes, pas relus » ; le constat
« DSP3-H17 n'existe pas », **faux**, H17 vivant dans `exigences/99-annexes.md` jamais ouvert ;
et la note du 27/08 qui s'ouvre sur « deux corrections se sont révélées fausses ».

**Correction.** Une relecture rouvre le fichier source. Corriger ou vérifier une sortie en
repartant de la sortie précédente est interdit. Second volet : un document dont l'en-tête porte
une réserve (« intuitions », « à sourcer », « non stabilisé ») ne peut pas être cité en `[SRC:]`.

---

## 6 · Règle n°1 complétée (`CLAUDE.md`)

**Problème.** « Ne rien inventer » était couvert, « ne pas interpréter » ne l'était qu'implicitement.
Reformuler un article sans rien inventer, puis ajouter « donc il faudra changer telle brique »,
ne violait aucune règle écrite.

**Correction.** Deux lignes, valables partout. Toute conséquence tirée d'un article n'est pas
sourçable : c'est une hypothèse à créer avec son statut, ou une opinion à attribuer nommément.
Et le manque se remonte, il ne se comble pas.

---

## 7 · `/synthese` (nouvelle commande)

**Problème.** 711 exigences illisibles. Entre le texte et les slides, aucun maillon de la chaîne
n'a pour métier de **réduire** : chacun dérive du précédent, donc multiplie.

**Correction.** Une commande qui produit une couche réduite à partir d'une sortie existante du
vault — jamais des PDF. Elle pose deux questions avant de lire : quelle réglementation, puis
quelle cible. Par sujet, 5 à 10 lignes, un `[SRC:]` par affirmation, zéro interprétation, zéro
cotation. Les hypothèses figurent dans un encadré séparé avec leur statut, jamais dans le corps.

Et un dernier étage, l'en-tête **« À LIRE D'ABORD »** : les sujets qui comptent le plus, deux à
trois lignes chacun, avec le numéro du sujet pour aller lire la suite. Comme hiérarchiser est un
jugement, l'en-tête est titré « sélection proposée, à valider » et chaque ligne porte le signal
comptable qui l'a fait entrer.

---

## 8 · Le piège `redaction-gt` (4 fichiers corrigés)

**Problème.** `_skills/` n'est pas un dossier de skills invocables — seul `.claude/skills/` l'est.
Or quatre fichiers demandaient d'« appliquer le skill redaction-gt », ce qui produit
`Error: Unknown skill: redaction-gt` puis une poursuite sans style. La Règle n°4, marquée
« jamais d'exception », ne s'appliquait donc jamais.

**Correction.** Remplacé par « lire le fichier » dans `_skills/analyse-reglementaire`,
`_skills/compte-rendu-gt`, `.claude/skills/reunion` et `.claude/skills/brief`, plus un
avertissement sous la Règle n°4.

---

## 9 · « Surfaces d'usage » (`CLAUDE.md`)

**Problème.** Le fichier affirmait que Claude Code et Cowork se valent et que le choix est libre.
C'est faux : sur Cowork, `CLAUDE.md` n'est pas chargé automatiquement. Les sept commandes
apparaissent et tournent, mais sans provenance obligatoire, sans routage, sans contrat.

**Correction.** Remplacé par la consigne réelle : Claude Code porte le harnais, Cowork porte les
outils sans le harnais. Pour tout travail engageant la chaîne, utiliser Claude Code.

---

## 10 · `cours-dsp3-psr.md` supprimé

**Problème.** Le fichier a servi de base à un test : **cité 9 fois**, contre une seule citation
d'exigence, et aucun des 22 fichiers de domaine ouvert. Il portait sa propre réserve — « intuitions
de cadrage, pas des conclusions du GT » — citée trois fois en `[SRC:]`. Le `journal.md` du 17/08
notait déjà la même contamination trois semaines plus tôt.

**Correction.** Supprimé du vault le 2026-09-07 : c'était un support de formation personnel,
pas un maillon de la chaîne. Références retirées de `_ROUTAGE.md` et de `_LISEZMOI.md`.

---

## Conventions posées

- Préfixe `_` : fichier destiné à Claude, pas à la lecture humaine (`_ROUTAGE.md`, `_LISEZMOI.md`)
- Première ligne d'un fichier périmé : `⚠️ OBSOLÈTE — remplacé par <fichier>, ne pas utiliser`
- Première ligne d'un template : `⚠️ VIDE — gabarit, aucun contenu`

## Deux lignes non écrites, faute de validation

- Le marqueur `[SRC: à sourcer ⚠️]` n'a pas de règle de conversion. Il devrait devenir une
  hypothèse ou une action GT à la fin d'une passe, et ne jamais survivre dans un livrable diffusé.
- Rien n'interdit de tamponner une affirmation inventée. « Le SLA est à qualifier ⚠️ » est
  légitime ; « le SLA est de 200 ms ⚠️ » ne l'est pas, et la règle actuelle ne distingue pas.

---

*Le harnais a été éprouvé sur trois passes en session réelle : les huit comportements attendus
ont été observés, dont le refus de combler un trou de sourcing quand la source correspondante
avait été écartée. Ces passes ont aussi révélé que le delta DSP2 → DSP3 n'est pas calculable en
l'état : huit des neuf textes de ligne de base ne sont pas déposés dans le vault.*

---

## 11 · `_ROUTAGE.md` réduit à une table de pointeurs

**Problème.** Le fichier avait dérivé : il portait des règles (« lire exactement, dans cet ordre »,
« ne pas ouvrir », le contrat de délégation, la sélection des sources) alors qu'il ne devait être
qu'un index. Deux fichiers donnaient donc des ordres, et ils se contredisaient.

Cas réel : sur une demande de delta DSP2 → DSP3, la section 1 nommait les fichiers à ouvrir,
tandis que la section 6 exigeait de lister les sources et d'attendre. Sur trois passes du même
prompt, deux ont listé, une a produit directement — en citant la section 1 pour se justifier.
La règle n'était pas ignorée : elle était ambiguë.

**Correction.** `_ROUTAGE.md` est désormais une table « tu as besoin de… → fichier », sans ordre
ni interdiction, avec les fichiers de plus de 20 Ko marqués `⧗`. Tout ce qui prescrit est remonté
dans `CLAUDE.md` : **Règle n°6 — sélection des sources** (non négociable) et **Règle n°7 —
délégation**. Les méthodes détaillées sont descendues dans `_methodes/`. `CLAUDE.md` reste la
seule autorité, à 198 lignes pour une cible de 200.

## 12 · Cinq contradictions internes de `CLAUDE.md` corrigées

**Problème.** Le fichier se contredisait lui-même sur cinq points, dont trois qui rendaient une
règle inapplicable.

**Correction.**

| # | Contradiction | Correction |
|---|---|---|
| 1 | Les Règles n°1 et n°3 imposaient de passer par **PageIndex**, hors service depuis le 2026-07-17 | la lecture directe du PDF devient la voie normale, PageIndex l'option |
| 2 | `/loi` était annoncé « PageIndex » seul | aligné sur la Règle n°1 |
| 3 | Un **niveau 0** était attribué à l'€N wholesale alors que le tableau n'en définissait que trois | niveau 0 défini dans le tableau |
| 4 | Le CRA était déclaré « archivé » puis « niveau 1 » deux paragraphes plus loin | « niveau 1 atteint, dossier clos » |
| 5 | « Dupliquer la structure de `cyber-resilience-act/` » pour une nouvelle réglementation — or ce dossier n'a pas de `_LISEZMOI.md` | renvoi à `_methodes/anatomie-vault.md`, `_LISEZMOI.md` inclus |

Restait un renvoi mort (« le tableau d'état ci-dessous », qui n'existait pas), une mention de
`.claude/agents/` qui n'existe pas dans ce vault, et un décompte de « 7 commandes » alors qu'il y
en a 8. Corrigés.

Une sixième contradiction n'a **pas** été corrigée parce qu'elle relève d'une décision de mission :
AMLR est déclaré niveau 2 avec un dossier vide. Elle est documentée en `CHANGE.md` A.10.

---

## 13 · Règle n°7 — délégation reformulée sur un critère décidable

**Problème.** La règle disait : déléguer au-delà de 20 Ko **pour moins de 10 % d'extrait utile**.
Or la taille de l'extrait ne se connaît qu'**après** avoir lu. Au moment de décider, le critère
était indécidable. En pratique le modèle estimait depuis la description du fichier dans
`sources.md` — il raisonnait juste, mais pas parce que la règle le lui disait.

Second défaut : « un sous-agent par fichier » était arbitraire. Sur `exigences/`, ça donnait
22 agents, donc 22 rechargements de `CLAUDE.md` — environ 55 000 tokens d'amorçage pour 270 Ko
de source. Le temps n'était pas le problème (les 22 tournaient en parallèle et finissaient en
20 secondes), le coût si.

**Correction.** Deux critères, tous deux connus avant d'ouvrir le moindre fichier.

*Quand déléguer* — sur la **largeur de la question**, pas sur la taille du résultat :

| Question | Décision |
|---|---|
| étroite (un identifiant, un article, une entité, un domaine) | déléguer |
| large (elle couvre tout le document) | lecture directe |
| plusieurs fichiers, une question étroite dans chacun | déléguer |

*Combien d'agents* — au **budget : ~50 Ko de source par agent**, jamais plus que le nombre de
fichiers. Un agent peut porter plusieurs fichiers ; un fichier n'est jamais coupé entre deux
agents, et chaque agent rend son extrait fichier par fichier avec un `[SRC:]` distinct, sans quoi
l'attribution est perdue et la Règle n°1 tombe.

Vérifié contre les quatre passes déjà tournées : `exigences/` en entier passe de 22 agents à **6**,
le delta sur 7 sources à **4**, l'étude CAPS lue de bout en bout reste à **0**. Les comportements
observés deviennent prévisibles, et la décision se prend avant la première lecture.

Au passage, les deux blocs d'identifiants Notion sont descendus dans `_transverse/notion.md` :
c'est de la configuration, pas de la règle. `CLAUDE.md` revient à **192 lignes**.

*Note sur la nouveauté n°13 : la Règle n°7 a été réécrite une seconde fois, non plus comme un jeu
de seuils mais comme le **raisonnement** à conduire — ce que la délégation apporte, ce qu'elle
coûte, et les deux choses qui doivent rester bornées (ce que l'agent lit, ce qu'il rend). Les
ordres de grandeur (50 Ko, 8 fichiers) y figurent comme repères, pas comme règles. Le cas « beaucoup
de petits fichiers » bascule vers un balayage en deux passes. Seul le contrat de retour reste
non négociable.*

---

## 14 · Langue de travail

**Problème.** Aucun fichier du harnais ne disait en quelle langue travailler. Vérifié sur
l'ensemble du vault : ni `CLAUDE.md`, ni `redaction-gt`, ni les commandes. Conséquence observée
en session réelle : deux commentaires intermédiaires sortis en anglais au milieu d'une analyse
française (« *This confirms Art. 49 matches ET-04's description precisely* »).

**Correction.** Une section « Langue de travail » en tête de `_skills/redaction-gt/SKILL.md`, et
un rappel dans la Règle n°4 : **français sans exception**, y compris les commentaires intermédiaires
d'un raisonnement, pas seulement les livrables. Les termes réglementaires anglais consacrés
(*verification of payee*, *open banking*, *spoofing*, *dynamic linking*) se gardent tels quels,
en italique, sans traduction forcée.
