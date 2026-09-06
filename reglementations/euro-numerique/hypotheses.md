# Registre d'hypothèses — Euro numérique (€N)

> Règle : jamais de suppression. Un changement de statut = mise à jour de l'entrée + entrée dans journal.md + alerte sur les dépendances.

| ID | Hypothèse | Statut | Source | Dépendances (à revisiter si statut change) |
|----|-----------|--------|--------|---------------------------------------------|
| EN-H01 | Compte €N **unique** par personne (vs. multi-comptes ouvert par la proposition de règlement UE). Le multi-comptes compliquerait fortement la tenue de compte et le contrôle du plafond par personne sur plusieurs identifiants/PSP. | 🟡 OUVERTE — point le plus sensible | [SRC: Rulebook v0.91] vs [SRC: proposition de règlement UE — section à vérifier] | Architecture tenue de compte ; shadow ledger ; contrôle holding limit ; GT10 slides 1, 6 ; arbre de mutualisation (briques cœur) |
| EN-H02 | Spécifications du **mode hors ligne** non stabilisées. | 🟡 OUVERTE | [SRC: atelier GT10 du 09/07/2026, exec summary] | Brique offline ; intégration SDK BCE ; chiffrage briques nouvelles |
| EN-H03 | **Format de reporting BCE** non stabilisé. | 🟡 OUVERTE | [SRC: atelier GT10 du 09/07/2026, exec summary] | Brique reporting ; impacts SI producteur |
| EN-H04 | Cible de **disponibilité ~99,9 %** et paiement <300 ms (<2 s bout en bout) — jugée exigeante, non figée dans le Rulebook. | 🟡 OUVERTE | [SRC: Rulebook v0.91 — section à vérifier ; atelier GT10, slide 6] | Choix d'éclatement des rôles entre entités (chaque frontière ajoute de la latence) ; scénario mise à disposition CAPS |
| EN-H05 | Entrée en vigueur visée **2029**. | 🟡 OUVERTE (dépend de l'adoption du règlement) | [SRC: atelier GT10, exec summary] | Trajectoire/planning ; charge à allouer dès S2 2026 |
| EN-H06 | Coût de mise en conformité : **~29 M€** pour une banque taille CA Italia, **~110 M€ en moyenne** par banque. | 🟡 OUVERTE (chiffrage 2024, à réactualiser) | [SRC: Digital Euro Cost Study, PwC 2024] | Business case mutualisation ; argument « coût dupliqué » des slides 1-2 |
| EN-H07 | Rulebook : v0.92 et v0.93 attendues **d'ici fin 2026**, version définitive **2027**. | 🟡 OUVERTE | [SRC: atelier GT10, exec summary] | Cadencement des travaux ; déclencheur de la Règle n°3 (diff de version) |
| EN-H08 | Le Groupe **ne participe pas au pilote BCE** → visibilité terrain limitée ; le REX pilote est un préalable aux niveaux de mutualisation 3-4. | 🟢 TRANCHÉE (fait acté) | [SRC: atelier GT10, exec summary + slide 2] | Conditions d'arbitrage niveaux 3-4 ; calendrier des analyses d'impact |
| EN-H09 | Composants BCE fournis et certifiés (application, SDK, mode hors ligne) **déjà attribués** → les SI deviennent intégrateurs. | 🟢 TRANCHÉE | [SRC: atelier GT10, exec summary] | Arbre make vs buy (branche « buy » contrainte) ; périmètre briques nouvelles |
| EN-H10 | Engagement des entités et alignement métiers/stratégie : hypothèses du GT qui, si non vérifiées, deviennent **facteurs bloquants**. | ⚫ BLOQUANTE (exogène, hors contrôle GT) | [SRC: atelier GT10, slide 10] | Toute orientation de mutualisation ≥ niveau 2 |

## Paramètres structurants ouverts (à instancier en hypothèses dès qu'une valeur circule)
- Valeur du plafond de détention (holding limit) [SRC: Rulebook v0.91 — non fixé]
- Modèle économique / frais encadrés BCE (fragilise le business case) [SRC: atelier GT10, exec summary]
