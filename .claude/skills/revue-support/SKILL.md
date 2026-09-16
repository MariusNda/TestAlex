---
name: revue-support
description: Relire un support de séance (.pptx) contre le vault — chaque affirmation d'une planche est-elle rattachable à une exigence, un fait ou une hypothèse, et le registre de revue précédent a-t-il été traité ou seulement déplacé. Déclencher quand l'utilisateur tape /revue-support, demande de relire un support, de vérifier que ses slides sont bien sourcées, de contrôler un PPTX avant un GT, ou de savoir si les correctifs d'une revue précédente sont passés dans la nouvelle version. Lecture seule.
---
Support à relire : $ARGUMENTS (si vide : le `.pptx` le plus récent de `gt-seances/<réglementation active>/`, hors `_archive/`).

Tu **contrôles**, tu ne réécris pas. Une planche n'est pas fausse parce qu'elle te surprend :
elle est en défaut quand elle affirme sans rattachement, ou contre un maillon du vault.

Formats et motifs d'identifiants : `_methodes/ontologie.md`. Lis-le avant de commencer.

## 1. Extraire le support

```sh
python3 - <<'PY'
from pptx import Presentation
p = Presentation("<chemin du .pptx>")
for i, s in enumerate(p.slides, 1):
    print(f"\n=== PLANCHE {i} ===")
    for sh in s.shapes:
        if sh.has_text_frame and sh.text_frame.text.strip():
            print(sh.text_frame.text.strip())
        if sh.has_table:
            for r in sh.table.rows:
                print(" | ".join(c.text.strip() for c in r.cells))
PY
```

**La numérotation de cette extraction fait foi** pour tout le rapport. Annonce le nombre de
planches en tête : la pagination change d'une version à l'autre, et les numéros des revues
archivées ne valent plus rien.

## 2. Rattacher chaque affirmation

Une affirmation = une phrase qui énonce un fait, une obligation, un chiffre ou un délai.
Les titres, transitions et éléments de mise en page ne s'instruisent pas.

Pour chacune, cherche son rattachement dans le vault **par recherche textuelle d'abord** —
mot-clé, numéro d'article, montant, délai — sur `exigences/`, `faits.md`, `hypotheses.md`,
`conclusions.md`, `cartographie/matrice-impacts-si.md`. N'ouvre un fichier que si le grep l'a
désigné. Si le volume l'impose, délègue selon la Règle n°7.

Quatre issues, et quatre seulement :

| Issue | Ce que ça veut dire |
|---|---|
| **RATTACHÉE** | un identifiant du vault dit la même chose → citer l'identifiant |
| **NON RATTACHÉE** | rien dans le vault ne la porte → ni fausse ni vraie : insourçable en l'état |
| **CONTREDITE** | un maillon du vault dit autre chose → citer les deux, ne pas trancher |
| **ADOSSÉE À UNE HYPOTHÈSE** | ne tient que si une hypothèse 🟡 ou ⚫ se confirme → citer l'hypothèse et son statut |

⚠️ **Une hypothèse n'est pas une source.** Une planche qui affirme au présent ce qui repose sur
une 🟡 OUVERTE est en défaut, même si l'hypothèse est juste (Règle n°1).
⚠️ **Un document sous réserve n'est pas citable** : si le rattachement tombe sur un fichier dont
l'en-tête porte « intuitions », « à sourcer », « non stabilisé », le dire (Règle n°5).

## 3. Rejouer le registre précédent

**C'est le cœur de la commande, et ce qu'on ne sait pas faire à la main.**

Cherche dans `gt-seances/<reg>/` un registre de revue existant (`revue-*-registre-consolide.md`,
`revue-*-retours-*.md`) et les correctifs rédigés en réponse (`propositions-*-correctifs-*.md`).
Pour **chaque** constat qu'ils portent, dis lequel des quatre :

- **APPLIQUÉ** — le texte proposé se retrouve dans le support
- **NON APPLIQUÉ** — le texte d'origine est encore là, à l'identique
- **DÉPLACÉ** — le texte en défaut a changé de planche (souvent corps → annexes) sans être corrigé
- **DISPARU** — le passage n'existe plus, sans qu'un correctif l'explique

Repère-toi **par le titre et le texte**, jamais par le numéro de planche.
**DÉPLACÉ est le cas qui coûte cher** : il passe pour traité et ne l'est pas.

## 4. Rendu

En chat, dans le format déjà en usage dans `gt-seances/` :

```
REVUE — <support>, <N> planches, extraction du <date>

🔴 CONTREDIT PAR LE VAULT
| Réf | Planche | Ce qui est écrit | Ce que dit le vault | Identifiant |

🟠 NON RATTACHÉ
| Réf | Planche | Ce qui est écrit | Ce qui manquerait pour le sourcer |

🟡 ADOSSÉ À UNE HYPOTHÈSE OUVERTE
| Réf | Planche | Ce qui est écrit | Hypothèse | Statut |

📋 REGISTRE PRÉCÉDENT — <fichier>
| Constat | Verdict | Où il est maintenant |
```

Puis, en trois lignes :
- le **périmètre réellement contrôlé** — planches lues, fichiers ouverts, nommés ;
- ce qui est **rattaché sans réserve**, en compte, pas en liste ;
- ce que le contrôle **ne sait pas** juger : la justesse d'un `[SRC:]` contre le texte de loi
  (c'est `/loi`), l'opportunité d'un message, la forme et le design.

Une section vide s'écrit en une ligne. Ne gonfle pas le rapport : un support propre donne un
rapport court.

## Interdits

- **Aucune écriture.** Le rapport se présente, il ne se verse pas. Les correctifs rédigés sont un
  autre travail, et ils passent par validation.
- **Ne pas réécrire les planches.** Tu signales « non rattaché », tu ne proposes pas la phrase de
  remplacement, sauf si l'utilisateur la demande ensuite.
- **Ne pas trancher une contradiction.** Tu poses les deux versions et leurs identifiants.
  L'arbitrage est humain, et il peut donner tort au vault.
- **Ne pas combler.** Une affirmation que tu ne sais pas rattacher est NON RATTACHÉE, jamais
  complétée par ta connaissance générale du texte.
