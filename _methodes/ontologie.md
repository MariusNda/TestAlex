# Ontologie du vault

> **Déclaration unique des objets du vault.** Pour chaque type : son identifiant, où il vit,
> ce qu'il porte obligatoirement, ses valeurs autorisées, son amont et son aval.
>
> **C'est ici que les commandes lisent le format d'un objet avant d'écrire.** Une commande
> ne redéclare pas les champs d'une exigence ou d'une hypothèse : elle renvoie ici. Quand un
> format change, il change à un seul endroit.
>
> Vocabulaire employé : `_methodes/glossaire-vault.md`. Règles de travail : `CLAUDE.md`.
> Chemins d'accès : `_ROUTAGE.md`.

---

## Registre des réglementations

**Source unique : la table en tête de `CLAUDE.md`** (dossier, préfixe, niveau de traitement,
réglementation active). Aucune commande ne recopie cette liste : toutes la lisent là.

Détail des niveaux, charges et critères d'activation : `_transverse/etat-mission.md`.
État courant d'un dossier : son `_LISEZMOI.md`.

---

## La chaîne, et ce que chaque maillon produit

```
TEXTE ──► EXIGENCE ──► CINÉMATIQUE ──► BRIQUE ──► SORTIE D'ARBRE ──► CONCLUSION ──► SLIDE
   │                                      ▲              ▲                ▲
   └──► FAIT ────────────────────────────┘              │                │
        HYPOTHÈSE ───────────────────────────────────────┴────────────────┘
```

Aucun objet n'existe sans référencer son amont. **Quand un objet change, tout objet qui cite
son identifiant est à signaler nommément** (Règle n°2 et chaîne de traçabilité).

---

## Types d'objets

### Source

| | |
|---|---|
| **Identifiant** | `<PRÉFIXE>-DIR` · `<PRÉFIXE>-REG` (textes) · `<PRÉFIXE>-ET-NN` (contribution d'entité) · `<PRÉFIXE>-<TEXTE>-NN` (héritage, ex. `DSP3-DSP2-02`) |
| **Emplacement** | `reglementations/<reg>/sources.md` — registre. Le document lui-même : PDF du dossier, `contributions-entites/`, `heritage-<texte>/`, `ligne-de-base/` |
| **Champs** | Réf. · Document (avec URL) · Version / date · Émetteur · PDF local · PageIndex |
| **Amont** | — (racine de la chaîne) |
| **Aval** | Exigence, Fait |
| **Règle** | Un document non inscrit ici n'est pas citable en `[SRC:]`. Une contribution d'entité engage l'entité, pas le GT. |

### Exigence

| | |
|---|---|
| **Identifiant** | `<PRÉFIXE>-EX-NNN`, séquentiel sur toute la réglementation (pas par domaine) |
| **Emplacement** | `reglementations/<reg>/exigences/NN-<domaine>.md`, une ligne de tableau. Index et prochain ID libre : `exigences/_index.md` |
| **Champs** | `ID` · `Exigence` (une phrase, verbe d'obligation) · `Source` (`[SRC:]`) · `Débiteur` (qui porte l'obligation) · `Délai / seuil` · `Paramètre ouvert` · `Statut` |
| **Statut** | `déclinée` → `cinématisée` → `cartographiée` → `évaluée` (atelier) → `conclue`. Cycle déclaré dans l'en-tête des référentiels. ⚠️ Les 711 exigences DSP3 sont toutes en `déclinée` : aucune commande ne fait avancer un statut à ce jour. |
| **Amont** | Source (article du texte) |
| **Aval** | Cinématique, Brique, Hypothèse (paramètre ouvert), Conclusion |
| **Règle** | Le référentiel est **éclaté** en `exigences/` sur DSP3. Un dossier sans éclatement porte un `exigences.md` unique. Vérifier lequel existe avant d'écrire. |
| **⚠️ Divergence** | Les gabarits encore vides (AMLR, NIS2, CRA) portent 8 colonnes — `Domaine fonctionnel · Rôles concernés · Briques · Hypothèses liées` — là où DSP3 en porte 7 : `Débiteur · Délai/seuil · Paramètre ouvert`. **Deux formats pour le même objet.** Le format DSP3 est retenu ici parce qu'il est le seul éprouvé sur un texte entier ; à arbitrer avant la première passe sur AMLR ou NIS2. |

### Cinématique

| | |
|---|---|
| **Identifiant** | ⚠️ **Aucun motif déclaré à ce jour.** Les cinématiques sont désignées par leur nom de fichier. À arbitrer si elles doivent être citables en `[SRC:]`. |
| **Emplacement** | `reglementations/<reg>/cartographie/cinematiques/` — Mermaid |
| **Amont** | Exigence (chaque cinématique référence les exigences qu'elle modélise) |
| **Aval** | Brique |

### Brique

| | |
|---|---|
| **Identifiant** | ⚠️ **Aucun motif déclaré.** Désignée par son nom de composant, qui doit être identique dans `glossaire.md`, `matrice-impacts-si.md` et `arbres.md`. |
| **Emplacement** | Catalogue : `cartographie/glossaire.md` · Cotation : `cartographie/matrice-impacts-si.md` · Vue : `cartographie/carto-applicative.md` |
| **Champs (catalogue)** | `Regroupement` · `Component` · `State` · `Définition` (avec réf. `<PRÉFIXE>-EX` et `[SRC:]`) |
| **State** | `New` · `Adapt.` (adaptation d'un existant) · `Ext.` (périmètre externe) · `Other`. ⚠️ **Divergence de libellés à trancher** : `_skills/analyse-reglementaire/SKILL.md` écrit la 4ᵉ valeur « Entity specific » et non « Other ». Les deux tables étant encore vides, l'arbitrage est sans coût aujourd'hui — il ne le sera plus après le premier peuplement. |
| **Cotation** | Très élevé · Élevé · Moyen · Faible · Très faible · N/A |
| **Amont** | Exigence, Cinématique |
| **Aval** | Sortie d'arbre |

### Fait

| | |
|---|---|
| **Identifiant** | `F<X>.<Y>` — regroupés sous un « Fait n°X » qui porte le sujet et sa date |
| **Emplacement** | `reglementations/<reg>/faits.md` |
| **Champs** | Énoncé · `[SRC:]` **obligatoire** · renvois croisés `(cf. <PRÉFIXE>-HNN, <PRÉFIXE>-EX-NNN)` |
| **Amont** | Source |
| **Aval** | Conclusion, Hypothèse |
| **Règle** | Un fait sans source n'existe pas. Un fait contredit par une source postérieure est **annoté, jamais réécrit** : l'écart se signale et se lève avec l'émetteur. |

### Hypothèse

| | |
|---|---|
| **Identifiant** | `<PRÉFIXE>-H<NN>` |
| **Emplacement** | `reglementations/<reg>/hypotheses.md`, une ligne de tableau + annotations datées dessous |
| **Champs** | `ID` · `Hypothèse` (avec la question ouverte) · `Statut` · `Source` · `Dépendances` (exigences, briques, conclusions, slides — **nommées par identifiant**) |
| **Statut** | 🟡 `OUVERTE` · 🟢 `TRANCHÉE` · 🔴 `OBSOLÈTE` · ⚫ `BLOQUANTE` (facteur exogène) |
| **Amont** | Exigence (paramètre ouvert), Fait, Source |
| **Aval** | Conclusion, Sortie d'arbre |
| **Règle** | **Jamais de suppression.** État courant en tête, historique daté dessous. Un changement de statut entraîne une entrée `journal.md` **et** une alerte `⚠️ à revisiter` sur chaque dépendance listée. Une hypothèse ne produit jamais une affirmation dans le corps d'un livrable. |

### Conclusion

| | |
|---|---|
| **Identifiant** | `C<X>.<Y>` — regroupées sous une « Conclusion n°X » |
| **Emplacement** | `reglementations/<reg>/conclusions.md` |
| **Champs** | Position · `Graduation` · `Source` · renvois `(cf. F<X>.<Y>, <PRÉFIXE>-HNN)` |
| **Graduation** | `Écarté` · `Acquis` · `À acter` · `À étudier` · `Hors périmètre GT` — **obligatoire sur toute position** |
| **Amont** | Fait, Hypothèse, Sortie d'arbre |
| **Aval** | Slide |

### Sortie d'arbre

| | |
|---|---|
| **Identifiant** | — (identifiée par la brique et l'arbre) |
| **Emplacement** | `reglementations/<reg>/arbres.md`. Blueprint des branchements : `_skills/analyse-reglementaire/arbres-blueprint.md` |
| **Champs** | `Brique(s)` · `Chemin` (réponses dans l'ordre) · `Sortie` · `Justification` · `Hypothèses conditionnantes` · `Séance` |
| **Sortie, arbre 1 — mutualisation** | `0` aucune synergie · `1` socle commun d'exigences · `2` build commun + run individuel · `3` mise à disposition par une entité · `4` plateforme Groupe · `5` interbancaire (⚠️ absent des slides sources, à confirmer) |
| **Sortie, arbre 2 — make vs buy** | `ADAPTER L'EXISTANT` · `BUILD INTERNE` · `BUILD EXTERNALISÉ` · `BUY` |
| **Amont** | Brique, Hypothèse |
| **Aval** | Conclusion |
| **Règle** | Tout passage suit le blueprint, jamais la mémoire. Une sortie est une aide à la décision : elle se confirme en atelier. |

### Entrée de journal

| | |
|---|---|
| **Emplacement** | `reglementations/<reg>/journal.md` |
| **Format** | `AAAA-MM-JJ — [TYPE] — description [SRC:]` |
| **Type** | `[GT]` · `[ATELIER]` · `[REG]` · `[HYP]` · `[SRC]` · `[EX]` · `[INIT]` |
| **Règle** | Append-only, ordre chronologique. Toute écriture dans un fichier de contenu s'accompagne d'une entrée. C'est le journal qui date la baseline de veille. |

### Compte rendu de séance

| | |
|---|---|
| **Emplacement** | `gt-seances/<reg>/<AAAA-MM-JJ> - <séance> (CR).md` + page Notion sous la page de la réglementation |
| **Méthode** | `_skills/compte-rendu-gt/SKILL.md` (fond) · `_skills/redaction-gt/SKILL.md` (style) |
| **Amont** | Séance |
| **Aval** | Fait, Hypothèse, Conclusion, Action |

### Action

| | |
|---|---|
| **Emplacement** | **Hors vault** : base Notion « Actions GT », data source `ea98e4b8-cace-460e-a4f7-ef9014868332` |
| **Champs** | `Action` (titre) · `Réglementation` · `Porteur` · `Échéance` · `Statut` · `Séance source` · `Lien CR` (URL — il n'existe pas de propriété de relation) |
| **Statut** | `À faire` → `Fait` |
| **Règle** | Sélectivité : seules les actions qui feront l'objet d'un suivi réel. Une liste courte vaut mieux qu'un inventaire. |

### Personne / entité

| | |
|---|---|
| **Emplacement** | `annuaire.md` |
| **Champs** | Nom · entité · rôle · registre tu/vous |
| **Règle** | À consulter **avant tout CR ou email**. Un interlocuteur manquant se propose à l'ajout, il ne s'invente pas. |

---

## Marqueurs transverses

| Marqueur | Sens | Où il se traite |
|---|---|---|
| `[SRC: <doc> <version> §<art.>]` | Provenance d'une affirmation (Règle n°1) | partout |
| `[SRC: atelier <nom> du <date>]` | Provenance orale | partout |
| `[SRC: <PRÉFIXE>-EX-NNN]` | Provenance interne à la chaîne | partout |
| `[SRC: à sourcer ⚠️]` | Manque assumé et remonté, jamais comblé | listé en fin de session et par `/lint` |
| `⚠️ à revisiter` | Dépendance d'un objet dont l'amont a changé | Règle n°2 |
| `⧗` | Fichier volumineux, candidat à la délégation (Règle n°7) | `_ROUTAGE.md` |

---

## Vérifier un identifiant

Remonter ou descendre la chaîne se fait par recherche textuelle sur l'identifiant, depuis la
racine du vault. Ces commandes remplacent une délégation quand la question est « qui cite quoi » :

```sh
# Tout ce qui cite un identifiant (usages ET déclaration)
grep -rn "DSP3-EX-183" reglementations/ gt-seances/

# Tous les identifiants d'un type réellement présents, dédoublonnés
grep -rhoE "DSP3-EX-[0-9]{3}" reglementations/dsp3/ | sort -u

# Les manques de source encore ouverts
grep -rn "à sourcer ⚠️" reglementations/ gt-seances/

# Les identifiants au mauvais préfixe (ne doit rien renvoyer)
grep -rnE "\bREG-(EX-[0-9]|H[0-9]|ET-[0-9])" reglementations/ gt-seances/
```

Le contrôle systématique de ces points est la commande `/lint`.
