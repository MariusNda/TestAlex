# Délégation à des sous-agents

> Méthode appelée par la **Règle n°7** de `CLAUDE.md`. La règle fait autorité ; ce fichier
> ne fait que la détailler.

Un sub-agent se justifie quand la source dépasse **20 Ko** et que l'extrait utile fait moins de **10 %** de la source. En dessous, la lecture directe coûte moins cher.

**Candidats à la délégation** (le nombre d'agents se calcule au budget, voir plus bas) :
`cartographie/matrice-impacts-si.md` (64 Ko), `exigences/` (270 Ko sur 22 fichiers),
`contributions-entites/DSP3-ET-04` (98 Ko), `journal.md` (43 Ko) en recherche historique,
`gt-seances/<reg>/` hors archive (115 Ko).

**Lecture directe :** `annuaire.md`, `_LISEZMOI.md`, `_transverse/stack-groupe.md`, `conclusions.md`, tout fichier de moins de 20 Ko.

Cinq règles, sans exception :

1. **Une source, une question.** Jamais « lis le dossier et remonte ce que tu trouves ». Toujours « dans tel fichier, quelles briques sont cotées 2 et pour quel motif ».
2. **Extraction, jamais interprétation.** Le sub-agent rapporte ce qui est écrit. Il ne conclut pas, ne priorise pas, ne reformule pas. La synthèse appartient à l'agent principal, seul à voir l'ensemble.
3. **Retour borné à 300 mots**, avec un `[SRC: …]` par affirmation. Un retour long annule le bénéfice.
4. **Le vide se dit.** Sans résultat, répondre « non trouvé dans ce fichier ». Ne jamais combler avec une connaissance générale, qui n'est pas sourçable et que rien ne distingue du reste.
5. **Périmètre fermé.** Le sub-agent lit la source qui lui est donnée, et rien d'autre. Pas de navigation libre, pas d'`_archive/`, pas de PDF non demandé.



## Dimensionnement — combien d'agents

Deux questions dans l'ordre : **est-ce qu'on délègue**, puis **en combien d'agents**.

| Cas réel | Volume | Décision |
|---|---|---|
| Un seul fichier, quelle que soit sa taille | 98 Ko (étude CAPS) | **0 agent** — lecture directe |
| Un seul fichier | 64 Ko (matrice d'impacts) | **0 agent** — lecture directe |
| `exigences/` en entier, un domaine par fichier | 270 Ko sur 22 fichiers | **6 agents** (270 ÷ 50) |
| Delta sur 7 sources distinctes | ~200 Ko sur 7 fichiers | **4 agents** |
| Trois CR d'entités à recouper | ~45 Ko sur 3 fichiers | **1 agent** portant les 3 |
| Plusieurs fichiers, mais moins de 20 Ko au total | 12 Ko sur 2 fichiers | **0 agent** |
| Beaucoup de petits fichiers | 600 fichiers de 1 Ko | **balayage d'abord** (retour en liste), extraction ensuite |

**Deux plafonds par agent, le premier atteint décide : ~50 Ko de source, ~8 fichiers.**

Le volume seul ne suffit pas. Avec 600 fichiers de 1 Ko, le budget de 50 Ko donnerait 50 fichiers
par agent — donc 50 × 300 mots de retour, soit 15 000 mots. Le pavé serait seulement déplacé.
C'est le plafond de fichiers qui mord dans ce cas.

Et au-delà de quelques dizaines de fichiers, la question change de nature : ce n'est plus une
extraction mais un **balayage**. « Lesquels de ces fichiers portent X » → retour en liste de noms
avec un repère par fichier, une ligne chacun. Balayer d'abord, puis extraire sur les seuls fichiers
que le balayage a retenus. Deux passes, deux contrats.

Chaque agent recharge `CLAUDE.md` à son démarrage, donc multiplier les agents sans raison coûte du
contexte pour rien — 22 agents sur `exigences/`, c'était 22 amorçages pour 270 Ko, soit environ
55 000 tokens de rechargement. Six suffisent.

Règles de répartition :

1. Un fichier n'est **jamais coupé** entre deux agents.
2. Un agent qui porte plusieurs fichiers rend son extrait **fichier par fichier**, jamais fusionné,
   avec un `[SRC:]` distinct par fichier.
3. Le nombre d'agents ne dépasse jamais le nombre de fichiers.
4. Annoncer la répartition avant de lancer : « 6 agents, 3 à 4 domaines chacun ».
5. Un fichier qui dépasse seul le budget part seul dans son agent.
