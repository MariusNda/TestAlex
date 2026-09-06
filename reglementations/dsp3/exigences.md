# Référentiel d'exigences — DSP3 / PSR

> Maillon 2 de la chaîne : TEXTE → **EXIGENCES** → CINÉMATIQUES → CARTO → …
> Alimenté via /exigence. IDs séquentiels, jamais réutilisés. Statuts d'analyse :
> déclinée → cinématisée → cartographiée → évaluée (atelier) → conclue.

## ⚠️ Le référentiel est éclaté dans le dossier `exigences/`

Volume : **711 exigences** (DSP3-EX-001 à DSP3-EX-711). Le référentiel a été découpé par
domaine fonctionnel pour rester maniable. **Point d'entrée : [`exigences/_index.md`](exigences/_index.md)**,
qui porte la synthèse par domaine et la table des fichiers.

| Élément | Emplacement |
|---------|-------------|
| Index et synthèse par domaine | `exigences/_index.md` |
| 22 fichiers de domaine | `exigences/01-*.md` à `exigences/22-*.md` |
| Hypothèses dérivées, mandats EBA, options, alertes | `exigences/99-annexes.md` |

## Origine et périmètre

Passe complète `/exigence` du **2026-08-19** sur les deux textes de compromis du trilogue du
23/04/2026 (PSR ST-8221, PSD3 ST-8222), lus directement en PDF, PageIndex étant indisponible.
Granularité retenue : **une exigence par obligation distincte**, et non par article.
Statut initial de toutes les exigences : `déclinée`.

Couverture : PSR Art. 1 à 112 et PSD3 Art. 1 à 51, intégralement parcourus.

## Ce que la passe a produit

- **711 exigences** réparties en **22 domaines fonctionnels** (les 20 prévus, plus deux ajoutés :
  monnaie électronique et jetons de monnaie électronique, et dispositions finales du PSR).
- **25 hypothèses dérivées** proposées, numérotées **DSP3-H03 à DSP3-H27** pour ne pas entrer en
  collision avec DSP3-H01 et DSP3-H02 déjà ouvertes dans `hypotheses.md`.
- **34 mandats de niveau 2** recensés, dont 22 mandats EBA (12 RTS, 2 ITS, 4 jeux de lignes
  directrices, 3 rapports, 1 obligation opérationnelle), 5 habilitations à actes délégués et
  7 clauses de revoyure.
- **55 options** relevées : 23 nationales, 21 contractuelles, 11 facultés d'acteur.
- **23 alertes de qualité rédactionnelle** du compromis (renvois cassés, points supprimés,
  coquilles), à revérifier sur le texte publié au JO.

## Points saillants pour le Groupe

1. **Surveillance croisée** : le PSP du payeur doit rembourser s'il ne peut prouver que la
   surveillance a été effectuée par les deux PSP, alors qu'aucun véhicule d'échange de cette preuve
   n'existe dans le texte. Seul endroit où un PSP répond du manquement d'un autre hors lien
   contractuel. [SRC: PSR ST-8221 §Art. 83(1a)]
2. **Assiette des sanctions** : 10 % du chiffre d'affaires **consolidé de l'entreprise mère
   ultime**, et non de l'entité en faute, plus astreintes à 3 % du CA journalier moyen.
   [SRC: PSR ST-8221 §Art. 97(2)-(3), 98]
3. **Disparition du fallback** : le mécanisme de contingence des RTS 2018/389 disparaît, remplacé
   par une obligation de résultat sur la disponibilité de l'interface dédiée et, côté tiers, une
   clause « exceptionnellement via une autre interface sûre et efficace » sans critère ni RTS.
   [SRC: PSR ST-8221 §Art. 45(1), 38]
4. **VoP** : renvoi normatif intégral au règlement 260/2012 modifié, le mécanisme opérationnel
   n'est pas reproduit dans le PSR. Prévoit une **concordance approchante** avec restitution du nom
   exact, et une option de retrait pour les non-consommateurs. [SRC: PSR ST-8221 §Art. 50, 110c]
5. **Double étage de blocage anti-fraude** : suspension côté payeur, retour de fonds côté
   bénéficiaire lorsque les motifs sont clairs et incontestables, charge de la preuve inversée.
   [SRC: PSR ST-8221 §Art. 69, 83]

## Suite de la chaîne

Prochain maillon : cinématiques puis cartographie applicative. La priorisation des exigences à
cinématiser sera arbitrée en atelier, sur le croisement impact SI et potentiel de mutualisation.
