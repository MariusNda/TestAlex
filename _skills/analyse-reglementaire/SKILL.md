---
name: analyse-reglementaire
description: Méthode du GT Architectures Réglementaires pour traiter une réglementation de bout en bout (rodée sur l'€N, GT8-GT10). Déclencher quand une nouvelle réglementation entre au GT ou pour vérifier la complétude d'une étude en cours.
---

# Skill : Analyse réglementaire (méthode GT)

Chaîne de production : TEXTE → EXIGENCES → CINÉMATIQUES → CARTOGRAPHIE → FAITS/HYPOTHÈSES → ARBRES → CONCLUSIONS.
Chaque livrable alimente le vault. Cadence type : 2 à 3 GT sur 2 à 3 mois, plusieurs dizaines d'ateliers.

> **Périmètre : ce skill décrit le traitement de NIVEAU 2 (Approfondi)** — le cœur du GT (40-60 j.h/texte),
> rodé sur l'€N. Voir CLAUDE.md § Niveaux de traitement pour les 3 niveaux.
> - **Niveau 1 (Cadrage, ~10 j.h)** : s'arrêter après la Phase 0 + une vue macro de la Phase 1 (domaines
>   impactés, impacts SI par couche), produire une reco d'arbitrage vers le niveau 2 ; ne PAS peupler les arbres.
> - **Niveau 3 (Suivi, ~5 j.h/mois)** : mode d'entretien post-niveau 2 (veille, ré-approfondissement ponctuel, visibilité).
> Vérifier le niveau courant de la réglementation dans son `_LISEZMOI.md` avant de dérouler.

## Phase 0 — Cadrage
- Identifier les entités impactées et les **entités contributrices** (celles qui ont déjà produit
  des études). Recenser leurs études dans sources.md ; les lire AVANT tout atelier : c'est la
  condition sine qua non pour traiter une réglementation.
- Indexer les textes officiels dans PageIndex ; inscrire la veille (actes d'exécution, standards
  harmonisés, guidances) dans sources.md section « Attendus ».
- Poser le rétroplanning dans journal.md : jalons réglementaires vs jalons GT.

## Phase 1 — Projection de la réglementation
1. **Déclinaison en exigences fonctionnelles** (via /exigence) : parcourir le texte domaine par
   domaine, créer les REG-EX-NNN dans exigences.md. Chaque zone floue du texte = hypothèse.
2. **Cinématiques / diagrammes de séquence** : modéliser les parcours et processus imposés
   (Mermaid dans cartographie/cinematiques/), chaque cinématique référencée à ses exigences.
3. **Cartographie applicative** : dériver les macro-briques ; qualifier chaque brique
   (New / Adaptation / périmètre externe / Entity specific) ; produire le glossaire.
4. **Audit de maturité des entités** : questionnaire, consolidation des niveaux d'avancement.

## Phase 2 — Évaluation des capacités (ateliers référents)
1. Impacts sur l'existant : briques partagées vs spécifiques, échelle d'impact
   (Très élevé / Élevé / Moyen / Faible / Très faible / N/A), map d'impacts colorée.
2. Étude des responsabilités : projection dans le modèle de rôles du texte, maps de
   responsabilités par rôle et par entité.
3. Consolidation FAITS (sourcés, dans faits.md) vs HYPOTHÈSES (trackées, dans hypotheses.md).

## Phase 3 — Production des réponses IT
1. **Peuplement des arbres** (arbres.md) : chaque groupe de briques passe dans l'arbre de
   mutualisation puis make vs buy ; tracer le chemin, la sortie, la justification, l'atelier source.
2. Scénarios de mise en commun : prérequis de chaque scénario, frontière des décisions prises.
3. Conclusions graduées (conclusions.md) + avis du GT + prochaines actions + rétroplanning.

## Arbre 1 — Mutualisation (niveaux 0→5)
0 Aucune synergie · 1 Socle commun d'exigences · 2 Build commun + run individuel ·
3 Mise à disposition par une entité · 4 Plateforme Groupe (France / Europe) · 5 Interbancaire
(niveau 5 absent des slides sources, à confirmer ⚠️).
**Blueprint complet (branchements, sorties, définitions des niveaux) : arbres-blueprint.md**
[SRC: support GT TEC/DTDI, captures du 2026-07-09]. Tout passage d'une brique dans un arbre
suit le blueprint, jamais la mémoire.

## Arbre 2 — Make vs Buy
Sorties : ADAPTER L'EXISTANT / BUILD INTERNE / BUILD EXTERNALISÉ / BUY.
**Blueprint complet : arbres-blueprint.md** (même source).

## Garde-fous permanents
- Les arbres sont des aides à la décision, pas des verdicts : chaque sortie se confirme en atelier.
- Le GT oriente sous l'angle architecture ; facteurs exogènes (gouvernance, capacité, juridique,
  calendrier, budget) = hypothèses BLOQUANTES.
- Justification propre à chaque niveau de mutualisation, jamais de logique tout-ou-rien.
- Le gain de mutualisation ne couvre qu'une partie de l'effort : l'adaptation locale demeure et
  se chiffre pour elle-même.
- Rédaction : appliquer systématiquement le skill redaction-gt.
