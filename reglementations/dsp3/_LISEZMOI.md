# DSP3 / PSR — carte de navigation

> Point d'entrée du dossier. À lire en début de travail sur DSP3. Tenu à jour à chaque session.

## Où en est-on
- **Niveau de traitement : 2 (Approfondi)** — méthode complète, Phases 0→3. Voir CLAUDE.md § Niveaux de traitement.
- **Réglementation active** du vault (depuis 2026-07-17).
- **Phase 0 en cours** (au 2026-08-25). Les deux sources ouvertes le 17/08 sont reçues (24/08), le premier atelier entité est tenu (BForBank, 24/08) et la passe `/exigence` complète est faite (19/08). Reste à exécuter : la cohorte d'ateliers entités et le recensement de leurs études. GT11 le 16/09.
- **Cycle de GT arrêté** : 4 séances au 3e mercredi du mois, **GT11** 16/09, **GT12** 21/10, **GT13** 18/11, **GT14** 16/12/2026 (numérotation à la suite du GT10 de restitution €N du 08/07). Cycle transverse à toutes les réglementations.
- **Format du GT11 validé** (synchro Hatim du 17/08) : introduction DSP3 de vulgarisation, une dizaine de slides, sur le modèle de l'introduction €N. Le support existant (15 slides) est à recalibrer.
- **Statut du texte : toujours pré-JO** (veille du 2026-08-17). Le paquet est « close to adoption » : texte agréé approuvé en commission ECON le 05/05/2026, vote en plénière et adoption formelle par le Conseil **non encore intervenus**, donc pas de publication au JO. Règle n°3 non déclenchée, les compromis d'avril restent la version de travail. Les dates absolues dérivées de l'EEV glissent d'autant. [SRC: EP Legislative Train, consulté 2026-08-17]
- **Sourcing** : PageIndex indisponible (crédits épuisés depuis le 2026-07-17, sans date de retour connue) → lecture directe des PDF déposés dans ce dossier. ✅ **Les 2 PDF sont déposés et lisibles** (PSD3 167 p., PSR 431 p., texte extractible sans OCR). Le PDF du PSR, absent depuis le 27/08, a été **redéposé le 2026-08-31** : identité contrôlée et extraction validée à 125 articles. Les citations d'articles du PSR sont donc à nouveau re-vérifiables à la source. ⚠️ `data.consilium.europa.eu` est hors egress depuis le conteneur comme depuis le poste : un redépôt est toujours une action manuelle.
- **Préparation de l'atelier Hatim** : page Notion « JJ/MM - Atelier de cadrage DSP3 x Hatim B. (questions préparatoires) », 21 questions en 5 blocs, dans la page Notion 📋 DSP3.
- **Support du GT11 en préparation** par Alex, à partir du support 15 slides à recalibrer. Trois revues dans `gt-seances/dsp3/` (V1 slides 10-28, V2 section DSP3/PSR, slides 7-15) ; les bloquants de la revue V2 restent à traiter. ⚠️ Séquencement corrigé le 31/08 : le point Christel Body (CAPS métier) a lieu le **01/09**, avant le bouclage du support, et non après comme prévu initialement.
- **Registre transverse** : `_transverse/stack-groupe.md` (IDP et APIM du Groupe et des entités).

## Les deux textes de travail (version compromis trilogue 23/04/2026, pré-JO)
| Texte | Nature | Doc Conseil | Porte | PDF local |
|-------|--------|-------------|-------|-----------|
| **PSD3** | Directive (transposée) | ST-8222-2026-INIT | Agrément & supervision des PSP. Abroge DSP2 + directive monnaie électronique. | ✅ `PSD3 - compromis trilogue 2026-04 (ST-8222).pdf` (167 p.) |
| **PSR** | Règlement (applicable direct) | ST-8221-2026-INIT | Règles de conduite : SCA, anti-fraude, verification of payee, open banking. | ✅ `PSR - compromis trilogue 2026-04 (ST-8221).pdf` (431 p., 125 articles) |

Liens de téléchargement et détails : voir `sources.md`.
« I » Item Note (ST-8220) = contexte procédural, non indexé, non normatif.

## Règle de sourcing (priorité)
1. **PageIndex d'abord** si le texte y est indexé (/loi, citation §exacte).
2. **Sinon PDF local** : repérage par plage de pages, citation `[SRC: <doc> §Art. X]`.
Dans les deux cas, Règle n°1 respectée (aucune affirmation sans source localisée).

## La chaîne de traçabilité (rappel) — état des maillons
TEXTE → EXIGENCES → CINÉMATIQUES → CARTO → FAITS/HYPOTHÈSES → ARBRES → CONCLUSIONS
| Maillon | Fichier | État |
|---------|---------|------|
| Exigences | `exigences/` (22 fichiers de domaine + `_index.md`) | **711 exigences** DSP3-EX-001 à DSP3-EX-711, statut « déclinée ». Passe `/exigence` du 2026-08-19 sur PSR Art. 1 à 112 et PSD3 Art. 1 à 51, lus en PDF. `exigences.md` n'est plus qu'un renvoi vers le dossier. Hypothèses dérivées, mandats EBA et options : `exigences/99-annexes.md` |
| Cinématiques | `cartographie/cinematiques/` | vide |
| Cartographie | `cartographie/carto-applicative.md` · `cartographie/matrice-impacts-si.md` · `glossaire.md` | carto applicative et **matrice d'impacts SI** peuplées (cotations 1/2/3, briques mutualisables, renvois exigences et hypothèses). Glossaire à compléter |
| Faits | `faits.md` | Fait n°1 : état des travaux DSP3 dans le Groupe au 17/08 (F1.1 à F1.4) · Fait n°2 : BForBank, atelier du 24/08 puis contributions versées le 25/08 (F2.1 à F2.13) |
| Hypothèses | `hypotheses.md` | **DSP3-H01 à DSP3-H29**. H01 amorcée (articulation DSP2→DSP3/PSR, instruisible depuis la réception du matériel DSP2) · H02 et H03 alimentées par l'atelier BForBank du 24/08 · H04 à H28 issues de la passe `/exigence` · H29 ouverte (portée technique de la révocation, refresh token vs access token ; **corrigée le 2026-08-25** : access token à 30 minutes, non 24 heures). **DSP3-H17 transférée depuis `exigences/99-annexes.md` le 2026-08-25**, énoncé resserré. Frontière arrêtée : **H03** porte le volet IHM et données pivots du tableau de bord, **H17** le registre des consentements et le protocole d'échange avec les tiers (back-office). Le constat C10 de la revue GT11 V2 est corrigé en conséquence : les renvois de la matrice d'impacts sont valides |
| Arbres | `arbres.md` | vide (peuplement en Phase 3) |
| Conclusions | `conclusions.md` | frontière des décisions : cycle GT et format GT11 **acquis**, mutualisation du dashboard **à étudier** (DSP3-H03), chiffrage jours-homme **écarté** sous forme frontale |
| Journal | `journal.md` | à jour au 2026-08-24 |
| Séances | `gt-seances/dsp3/` | 2 CR (17/08 synchro Hatim, 24/08 lancement x BForBank) · support GT11 `.pptx` · 3 revues de support |
| Contributions d'entités | `contributions-entites/` | **DSP3-ET-02** (étude BFB du tableau de bord TPP) et **DSP3-ET-03** (note de périmètre de la squad Open Banking BFB), versées le 2026-08-25, reproduites à l'identique sous en-tête de provenance. Dossier ouvert à cette occasion, à réemployer pour les prochaines entités |

## Prochaines étapes
0. ✅ Les deux sources ouvertes le 17/08 sont en main : matériel DSP2 du Groupe reçu de Hatim le 24/08 (DSP3-DSP2-01) et étude BForBank reçue le 24/08 (DSP3-ET-02, avec la note de périmètre de la squad Open Banking). L'étude BFB est **versée et exploitée le 25/08** (dossier `contributions-entites/`, F2.8 à F2.13, cinq hypothèses alimentées, trois écarts à lever avec BFB). Reste le diff DSP2 → DSP3 (DSP3-H01).
1. **GT11 du 16/09** : boucler le support d'introduction en traitant les bloquants de la revue V2, puis enchaîner le point Christel Body (CAPS métier).
2. Phase 0 (suite) : cohorte d'ateliers entités — CATS (tenu 03/09), CAPS (tenu 01/09), **LCL reprogrammé au mardi 08/09** (Raphaele Luton, Philippe Jeanbert), CAGIP — et recensement de leurs études → `sources.md`.
3. Veille : surveiller le vote en plénière du Parlement, puis la publication au JO (déclencheur Règle n°3). Aucun jalon absolu ne peut être figé avant.

## Domaines fonctionnels pressentis
SCA · anti-fraude (verification of payee, spoofing, refunds) · open banking (API, permission dashboard) ·
agrément/supervision PSP · protection consommateur & transparence des frais · accès aux systèmes de paiement.
