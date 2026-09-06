# Vault CASA — Mode d'emploi

> Brief de reprise. À lire au retour de congés pour tout avoir en tête.
> La source de vérité des règles reste `CLAUDE.md` ; ce document en est la synthèse opérationnelle.

## 1. À quoi sert ce vault

C'est la mémoire et l'outil de production du GT Architectures Réglementaires (Crédit Agricole S.A.).
Il centralise, pour chaque réglementation, toute la chaîne d'analyse : du texte de loi jusqu'aux
slides de restitution, avec traçabilité continue. On le lit en début de session, on le met à jour en fin.

## 2. La chaîne de traçabilité (colonne vertébrale)

Tout livrable dérive d'une chaîne continue où chaque maillon référence le précédent :

**TEXTE → EXIGENCES → CINÉMATIQUES → CARTOGRAPHIE → FAITS / HYPOTHÈSES → ARBRES → CONCLUSIONS → SLIDES**

Règle d'or : aucun élément n'existe sans citer son amont. Une brique de carto cite les exigences
qu'elle porte ; une conclusion cite ses faits et hypothèses ; un fait cite sa source. Quand un maillon
change (nouvelle version du texte, hypothèse invalidée), on remonte la chaîne et on signale les impacts en aval.

## 3. Les 4 règles non négociables

1. **Provenance obligatoire.** Aucune affirmation factuelle sans source : `[SRC: <doc> <version> §<article>]`,
   `[SRC: atelier <nom> du <date>]` ou `[SRC: REG-EX-NNN]`. Jamais inventer une référence d'article.
   Toujours distinguer FAIT (sourcé) / HYPOTHÈSE (trackée) / OPINION (attribuée : « le GT estime »).
2. **Cycle de vie des hypothèses.** Statuts 🟡 OUVERTE / 🟢 TRANCHÉE / 🔴 OBSOLÈTE / ⚫ BLOQUANTE.
   Chaque hypothèse a un ID stable, une source, des dépendances. Un changement de statut = mise à jour
   (jamais de suppression) + entrée journal + alerte sur les dépendances. On ne supprime jamais.
3. **Veille et diff de version.** À toute nouvelle version d'un texte / acte d'exécution / standard /
   guidance : l'indexer, la diffuser section par section vs la version précédente, croiser avec exigences
   et hypothèses, produire le rapport d'impacts et remonter la chaîne.
4. **Rédaction.** Tout livrable (slide, CR, note, email GT) applique le skill `_skills/redaction-gt/SKILL.md`.
   Le lire avant de rédiger, sans exception.

## 4. Règle de sourcing (contexte actuel : PageIndex épuisé)

Priorité décidée le 2026-07-17 :
1. **PageIndex d'abord** si le texte y est indexé → commande `/loi`, citation §exacte.
2. **Sinon lecture directe du PDF** déposé dans le dossier de la réglementation → citation `[SRC: <doc> §Art. X]`.

La Règle n°1 tient dans les deux cas. Quand les crédits PageIndex reviennent, on ré-indexe avec les noms
déjà prévus dans chaque `sources.md`, et `/loi` retrouve son plein régime.

## 5. Anatomie d'un dossier de réglementation

Chaque `reglementations/<reg>/` contient :

| Fichier | Rôle | Maillon |
|---------|------|---------|
| `_LISEZMOI.md` | Carte de navigation — **à ouvrir en premier** | — |
| `sources.md` | Registre des sources versionnées + règle de sourcing | Textes |
| `exigences.md` | Référentiel d'exigences (REG-EX-NNN). Au-delà de quelques dizaines d'exigences, le référentiel est éclaté en fichiers de domaine sous `exigences/` et `exigences.md` devient un renvoi vers `exigences/_index.md` (cas de DSP3 : 711 exigences, 22 domaines) | 2 |
| `cartographie/cinematiques/` | Diagrammes de séquence Mermaid | 3 |
| `cartographie/carto-applicative.md` + `glossaire.md` | Macro-briques + glossaire | 4 |
| `cartographie/matrice-impacts-si.md` | Cotation des impacts par brique (1/2/3) + briques mutualisables | 4 |
| `faits.md` | Faits établis (Fn.m) | 5 |
| `hypotheses.md` | Registre d'hypothèses (REG-Hnn) | 5 |
| `arbres.md` | Peuplement des 2 arbres de décision | 6 |
| `conclusions.md` | Conclusions graduées (Cn.m) | 7 |
| `journal.md` | Log chronologique + rétroplanning | — |

Transverses (racine) : `CLAUDE.md` (règles), `annuaire.md` (personnes & entités — à consulter avant
tout CR ou email), `_skills/` (méthode, rédaction, CR), `_transverse/` (registres communs à toutes les
réglementations, dont `stack-groupe.md`), `gt-seances/<reg>/` (CR de séance et revues de support).
Les 7 commandes vivent dans `.claude/skills/` (cf. §7).

## 6. La méthode en 4 phases (skill `analyse-reglementaire`)

- **Phase 0 — Cadrage.** Identifier entités impactées et **contributrices** ; recenser et lire leurs
  études AVANT tout atelier (condition sine qua non) ; indexer les textes ; poser le rétroplanning.
- **Phase 1 — Projection.** Décliner le texte en exigences (`/exigence`), modéliser les cinématiques,
  dériver la cartographie applicative, auditer la maturité des entités.
- **Phase 2 — Évaluation (ateliers référents).** Impacts sur l'existant, étude des responsabilités,
  consolidation FAITS vs HYPOTHÈSES.
- **Phase 3 — Réponses IT.** Peuplement des arbres (mutualisation, puis make vs buy), scénarios de mise
  en commun, conclusions graduées + avis du GT + prochaines actions.

Les deux arbres (Mutualisation niveaux 0→5, Make vs Buy) : blueprint dans
`_skills/analyse-reglementaire/arbres-blueprint.md`. Ce sont des aides à la décision, jamais des verdicts :
chaque sortie se confirme en atelier.

## 7. Commandes (skills)

- `/loi <question>` — question juridique sourcée sur le texte (PageIndex, citations §exactes).
- `/exigence <article ou domaine>` — décliner une portion du texte en exigences REG-EX (Phase 1).
- `/reunion [nom]` — AI meeting notes Notion → CR (page Notion) + vault + actions dans la base Notion « Actions GT » (attribut Réglementation = réglementation active).
- `/brief` — actions ouvertes de la réglementation active (base Notion « Actions GT », filtrée) + état du vault → ordre de bataille (lecture seule).
- `/mail [CR]` — transformer un CR en email prêt à envoyer (draft seul).
- `/veille [reg]` — veille réglementaire (calendrier, nouvelle version, actes délégués/RTS/ITS, guidances) ; delta vs baseline du vault, diff à valider. Tourne aussi en auto le lundi matin (tâche « veille-hebdo »).
- `/debrief [texte]` — vidage de contexte (dicté ou tapé) → routage classé et sourcé dans le vault, diff à valider.

## 8. Routines

- **Début de session :** lire `CLAUDE.md` + `exigences.md`, `hypotheses.md`, `conclusions.md` de la réglementation active.
- **Avant tout CR ou email :** consulter `annuaire.md` (noms, entités, registre tu/vous) ; proposer son enrichissement si un interlocuteur manque.
- **Post-réunion :** via `/reunion`. Toujours présenter le diff AVANT d'écrire ; tu valides.
- **Fin de session :** résumer ce qui a été appris/modifié + lister les `[SRC: à sourcer ⚠️]`.

## 9. Surfaces et écriture

- **Claude Code et Cowork** peuvent tous les deux écrire dans le vault. Choix libre selon le confort.
- **Sur les deux surfaces :** toute écriture passe par un diff présenté et validé par toi avant application. Aucune exception.

## 10. Conventions

- **IDs :** un préfixe propre par réglementation (CRA-, DSP3-, AMLR-, NIS2-…), séquentiels, jamais réutilisés. Aucune référence ambiguë entre réglementations.
- **Une seule réglementation active à la fois** (ligne « Réglementation active » du `CLAUDE.md`) ; les autres en archive. Basculer cette ligne pour changer de focus.
- **Diagrammes :** source de vérité en Mermaid dans `cartographie/` ; conversion `.drawio` à la demande (skill NDA `drawio-diagram`).
- **Carto — code couleur :** New / Adaptation / Périmètre externe / Entity specific / Other. Maille « application / service » en macro-briques, jamais le composant unitaire.

## 11. Niveaux de traitement

Trois niveaux, activés selon le besoin ; **le niveau 2 est le cœur du GT** (méthode complète €N), les niveaux 1 et 3 sont des variantes ponctuelles. Détail dans `CLAUDE.md` § Niveaux de traitement.

- **(1) Cadrage** (~10 j.h) — impulsion, vue macro, reco d'arbitrage vers le niveau 2. S'arrête après un cadrage.
- **(2) Approfondi** ⭐ (40-60 j.h) — cartographie détaillée, mutualisation, make-or-buy, chiffrage, trajectoire d'archi. Déroule les Phases 0→3.
- **(3) Suivi** (~5 j.h/mois) — entretien post-niveau 2 : veille, ré-approfondissement, visibilité.

Chaque réglementation déclare son niveau courant dans son `_LISEZMOI.md`.

## 12. État du vault au 2026-08-25

| Réglementation | Statut | Niveau | Texte(s) | Préfixe |
|----------------|--------|--------|----------|---------|
| Euro numérique | restitué (GT10 du 08/07/2026) | 2 Approfondi | — | €N- |
| Cyber Resilience Act | archivé (réf. de méthode) | 1 Cadrage | dans PageIndex | CRA- |
| **DSP3 / PSR** | **ACTIVE** — Phase 0 en cours | 2 Approfondi | 2 PDF déposés (compromis trilogue 04/2026, pré-JO) — PSD3 ST-8222, PSR ST-8221 | DSP3- |
| AMLR | en attente (squelette prêt) | 2 Approfondi | PDF déposé — Règlement (UE) 2024/1624 | AMLR- |
| NIS2 | en attente (squelette prêt) | à définir | PDF déposé — Directive (UE) 2022/2555 | NIS2- |

**Avancement DSP3** (détail dans `reglementations/dsp3/_LISEZMOI.md`) :

- **711 exigences** déclinées le 19/08 (PSR Art. 1 à 112 + PSD3 Art. 1 à 51), éclatées en 22 fichiers de
  domaine sous `reglementations/dsp3/exigences/` — point d'entrée `exigences/_index.md`.
- **29 hypothèses** DSP3-H01 à H29, séquence complète depuis le transfert de H17 au registre le 25/08
  (H03 = volet IHM du tableau de bord, H17 = registre des consentements et protocole d'échange).
- 2 faits ouverts (état des travaux au 17/08, atelier BForBank du 24/08) ; carto applicative et matrice
  d'impacts SI peuplées ; cinématiques et arbres encore vides.
- 2 CR en séance dans `gt-seances/dsp3/`, support du GT11 (16/09) en préparation, 3 revues de support.
- Registre transverse ouvert : `_transverse/stack-groupe.md` (IDP et APIM du Groupe et des entités).

AMLR et NIS2 : fichiers de chaîne encore vides (templates), journaux et `sources.md` amorcés.
PageIndex : crédits épuisés depuis le 2026-07-17, sans date de retour connue → sourcing par lecture
directe des PDF.

## 13. Reprendre le fil — les 3 premiers pas

1. Ouvrir `reglementations/dsp3/_LISEZMOI.md` (réglementation active) pour l'état exact, puis `/brief`.
2. Boucler le support du **GT11 du 16/09** en traitant les bloquants de la revue V2
   (`gt-seances/dsp3/revue-GT11-V2-section-dsp3-psr.md`).
3. Poursuivre la **Phase 0** : cohorte d'ateliers entités et recensement de leurs études dans
   `sources.md`, puis instruire DSP3-H01 avec le matériel DSP2 reçu le 24/08.

Pour activer AMLR ou NIS2 à la place : basculer la ligne « Réglementation active » du `CLAUDE.md`, le reste du dossier est déjà prêt.
