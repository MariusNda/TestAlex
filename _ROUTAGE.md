# Routage — où trouver quoi

> **Table de pointeurs. Elle ne prescrit rien.**
> Elle ne dit pas dans quel ordre lire, ni ce qu'il est interdit d'ouvrir, ni quand demander
> quelque chose à l'utilisateur. Tout cela est dans `CLAUDE.md`, qui est la seule autorité.
> Ce fichier répond à une seule question : **de quel fichier vient telle information ?**
>
> `<reg>` = la réglementation active, déclarée dans `CLAUDE.md`.
> ⧗ = fichier volumineux (> 20 Ko), candidat à la délégation (Règle n°7).

## Méthode et style

| Tu as besoin de… | Fichier |
|---|---|
| le sens exact d'un terme du harnais (préfixe, maillon, brique, baseline…) | `_methodes/glossaire-vault.md` |
| le format d'un objet du vault (identifiant, champs, statuts autorisés) | `_methodes/ontologie.md` |
| la méthode du GT (3 phases, arbres de décision) | `_skills/analyse-reglementaire/SKILL.md` |
| le blueprint des arbres | `_skills/analyse-reglementaire/arbres-blueprint.md` |
| le style de rédaction d'un livrable | `_skills/redaction-gt/SKILL.md` |
| la méthode de rédaction d'un CR | `_skills/compte-rendu-gt/SKILL.md` |
| la méthode de sélection des sources | `_methodes/selection-sources.md` |
| la méthode de délégation à des sous-agents | `_methodes/delegation.md` |
| la structure du vault | `_methodes/anatomie-vault.md` |

## Contenu d'une réglementation

| Tu as besoin de… | Fichier |
|---|---|
| l'état du dossier, son niveau de traitement, ce qui est peuplé | `reglementations/<reg>/_LISEZMOI.md` |
| la liste des sources et leur vérifiabilité | `reglementations/<reg>/sources.md` |
| le texte de loi lui-même | les PDF de `reglementations/<reg>/` |
| une exigence par domaine fonctionnel | `reglementations/<reg>/exigences/<domaine>.md` ⧗ |
| l'index des exigences et le prochain ID libre | `reglementations/<reg>/exigences/_index.md` |
| les hypothèses dérivées et les options | `reglementations/<reg>/exigences/99-annexes.md` ⧗ |
| les faits établis, indexés par entité | `reglementations/<reg>/faits.md` |
| les hypothèses et leur statut | `reglementations/<reg>/hypotheses.md` ⧗ |
| les conclusions graduées | `reglementations/<reg>/conclusions.md` |
| le peuplement des arbres de décision | `reglementations/<reg>/arbres.md` |
| les impacts SI, brique par brique, et leur cotation | `reglementations/<reg>/cartographie/matrice-impacts-si.md` ⧗ |
| la carto applicative, le glossaire, les cinématiques | `reglementations/<reg>/cartographie/` |
| une étude ou note reçue d'une entité | `reglementations/<reg>/contributions-entites/<REG-ET-nn>` ⧗ |
| l'héritage d'un texte précédent | `reglementations/<reg>/heritage-dsp2/` |
| les textes de la ligne de base déposés | `reglementations/<reg>/ligne-de-base/` |
| l'historique daté et le rétroplanning | `reglementations/<reg>/journal.md` ⧗ |

## Séances et livrables

| Tu as besoin de… | Fichier |
|---|---|
| un compte rendu de GT ou d'atelier | `gt-seances/<reg>/<date> - <séance> (CR).md` |
| l'état consolidé des corrections d'un support | `gt-seances/<reg>/revue-*-registre-consolide.md` ⧗ |
| les correctifs les plus récents sur un support | `gt-seances/<reg>/propositions-*-correctifs-*.md` |
| le support de séance | le `.pptx` de `gt-seances/<reg>/` |
| le registre des constats de revue d'un support | `gt-seances/<reg>/revue-*-registre-consolide.md` ⧗ |
| le texte de l'oral | `gt-seances/<reg>/*-voiceover-*.md` ⧗ |

## Transverse

| Tu as besoin de… | Fichier |
|---|---|
| savoir qui est qui, quelle entité, quel registre | `annuaire.md` |
| les IDP et APIM du Groupe et des entités | `_transverse/stack-groupe.md` |
| les incohérences connues du vault | `CHANGE.md` |
| ce qui a changé dans le harnais | `NOUVEAUTES.md` |
