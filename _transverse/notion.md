# Notion — bases, pages et conventions

> Configuration appelée par `CLAUDE.md` et par les commandes `/reunion`, `/brief`, `/mail`.

## Base Notion « Actions GT » (cible des actions, toutes réglementations)
- Database : https://app.notion.com/p/2bcaca11fe2141418762ca8e35aab6bc
- Data source ID (pour création de pages) : ea98e4b8-cace-460e-a4f7-ef9014868332
- Propriétés : Action (titre) · Réglementation (CRA / DSP3/PSR / AMLR / NIS2 / €N) · Porteur (Alex / Autre entité) ·
  Échéance (date) · Statut (À faire / En cours / Fait / Abandonnée) · Séance source (texte) · Lien CR (URL)
- Base commune à toutes les réglementations : filtrer/grouper par l'attribut **Réglementation**.
- /reunion crée les actions avec Statut = À faire et Réglementation = réglementation active ;
  /brief lit les actions ouvertes filtrées sur la réglementation active.
- Option **Transverse** (ajoutée 2026-08-17) pour les actions qui portent sur toutes les réglementations
  (ex. le cycle de GT mensuels). ⚠️ /brief filtrant sur la réglementation active, une action Transverse
  n'y remonte pas : la vue « Mes actions » (Porteur = Alex, Statut ≠ Fait) reste le filet.

## Pages de séance Notion (CR, préparations d'atelier)

Page mission : https://app.notion.com/p/341852cc7e1580a889bbd1e2638d1972
Une page par réglementation sous la section « 🖊️ Comptes rendus » :
- **DSP3 : `3bf852cc7e1580158d26cb6170da092f`** ← page_id parent pour toute création (consigne Alex 2026-08-17)
- Euro Numérique : encore un toggle (historique) · CRA et NIS2 : toggles, à convertir en pages au besoin
Nommage : `JJ/MM - <type de séance> x <entité ou personne> (@Prénom N.)`. Si la date n'est pas fixée,
garder le préfixe littéral `JJ/MM` (cf. page « JJ/MM - Template (CR) »).
⚠️ Une section repliable Notion n'est pas une page : l'API ne peut pas y écrire, et une écriture ciblant
un bloc toggle peut répondre 200 **sans rien écrire**. Toujours relire la page après écriture.
