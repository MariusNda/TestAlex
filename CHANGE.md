# CHANGE.md — incohérences relevées dans le vault

> Relevé établi le **2026-09-06**, complété le **2026-09-08**, après lecture intégrale du vault :
> 179 fichiers, 1 039 Ko de markdown,
> les 38 planches du support GT11, et le transcript de la revue de harness du 04/09.
> Chaque point est vérifié et porte sa preuve. Rien n'a été corrigé : ce document est une liste à valider.
>
> Code : 🔴 bloquant · 🟠 à traiter · 🟡 confort

---

## A. Contradictions et fichiers périmés

### 🔴 A.1 — Contradiction sur la réglementation active

**Deux fichiers à la racine donnent une consigne opposée.**

- `CLAUDE.md` : « Réglementation active : **DSP3 / PSR** »
- `README.md` : titre « Vault CASA v3 · **Cyber Resilience Act** », plus une « Séquence de lancement CRA »
  et une base Notion « Actions **CRA** » qui n'existe plus (elle s'appelle « Actions GT »)

C'est la ligne qui pilote tout le routage du vault. Elle est fausse dans un fichier sur deux.

**Action proposée :** réécrire ou supprimer `README.md`.

---

### 🔴 A.2 — Trois fichiers périmés ne portent aucun avertissement

`gt-seances/dsp3/_archive/` contient **176 Ko**, soit 17 % du vault. Deux fichiers sur cinq signalent
leur obsolescence, trois ne la signalent pas.

| Fichier | Ko | Avertissement en tête |
|---|---:|---|
| `propositions-GT11-contenu-dsp3-2026-08-27.md` | 76 | ✅ « non fiable en l'état, ne rien reprendre sans revérifier » |
| `annexes-GT11-VF-contenu-2026-08-27.md` | 27 | ✅ « revérifier sur le PDF avant réemploi » |
| `revue-GT11-V2-section-dsp3-psr.md` | 39 | ❌ **aucun** |
| `revue-GT11-slides-7-15.md` | 22 | ❌ **aucun** |
| `revue-GT11-V1-slides-10-28.md` | 11 | ❌ **aucun** |

Les trois derniers s'ouvrent sur « Revue du support GT11, vérification faite par lecture directe des PDF ».
Rien ne les distingue d'une analyse à jour. Leurs constats ont pourtant été absorbés et corrigés par
`revue-GT11-registre-consolide.md` du 31/08.

**Action proposée :** renommer le dossier en `zz-obsolete-ne-pas-lire/`, et ajouter une première ligne
d'avertissement aux trois revues.

---

### 🟠 A.3 — Deux documents de doctrine divergent

`CLAUDE.md` (11,3 Ko) et `MODE-EMPLOI.md` (10,5 Ko) portent le même corpus de règles à 80 %.
`MODE-EMPLOI.md` affiche un « **État du vault au 2026-08-25** » qui ignore les douze derniers jours :
atelier CAPS du 01/09, atelier CATS du 03/09, versement de l'étude ET-04, report de LCL au 08/09.

Deux documents de référence finissent toujours par diverger. C'est fait.

**Action proposée :** désigner celui qui fait foi, et réduire l'autre à un renvoi.

---

### 🟠 A.4 — Le journal cite deux fichiers qui n'existent pas

`journal.md`, entrée du 2026-08-19 :

- `cartographie/_archive/vue-impacts-briques.OBSOLETE.md` : le dossier `cartographie/_archive/` n'existe pas
- `_archive/.trash-vue.md`, « à effacer manuellement » : le fichier n'existe pas

Sans gravité, mais un agent qui suit le journal part chercher deux fichiers fantômes.

**Action proposée :** corriger les deux entrées du journal.

---

### 🟠 A.5 — Un écart de statut signalé le 25/08, toujours ouvert

Sur la source **DSP3-DSP2-01**, les travaux DSP2 du Groupe de 2018 :

- `hypotheses.md` la donne « **reçue de Hatim Benamar le 2026-08-24** »
- `sources.md` la laisse « **☐ à récupérer** »

Le journal du 25/08 relève l'écart lui-même et conclut « à trancher ». Douze jours plus tard,
les deux fichiers se contredisent toujours.

**Action proposée :** trancher, puis aligner les deux fichiers.

---

### 🟡 A.6 — Quatre templates vides ressemblent à des fichiers peuplés

`arbres.md`, `cartographie/glossaire.md`, `cartographie/carto-applicative.md`,
`cartographie/cinematiques/README.md`. Chacun porte un titre, un chapô et une structure de tableau,
sans aucune donnée. Un agent les ouvre, n'y trouve rien, et recommence ailleurs.

**Action proposée :** une première ligne `> ⚠️ VIDE — peuplé en Phase 1` ou `Phase 3` sur chacun.

---

### ✅ A.7 — `cours-dsp3-psr.md` daté du 17/07

Caduc : le fichier a été supprimé le 2026-09-07. Voir C.1.
---

### 🟠 A.8 — `_LISEZMOI.md` ne figure pas dans l'arborescence de `CLAUDE.md`

C'est le fichier d'entrée de chaque réglementation : il porte l'état exact du dossier, ce qui est
peuplé et ce qui ne l'est pas. `/brief` s'en sert, `_ROUTAGE.md` §2 et §3 y renvoient comme point
de départ de toute navigation libre.

Or l'arborescence de `CLAUDE.md` (lignes 35 à 62) liste `sources.md`, `exigences.md`, `faits.md`,
`hypotheses.md`, `conclusions.md`, `arbres.md`, `cartographie/`, `contributions-entites/` et
`journal.md` — **mais pas `_LISEZMOI.md`.**

Le fichier le plus utile du dossier est absent de la carte du dossier.

**Action proposée :** l'ajouter à l'arborescence, en tête de la liste, avec sa vocation
(« état du dossier, à lire en premier »). Une ligne. À traiter avec B.3, qui porte sur la même
absence dans la routine de début de session.

---

### 🟡 A.9 — Deux réglementations ne suivent pas la structure déclarée

`CLAUDE.md` déclare une structure uniforme pour `reglementations/<reg>/`. Elle est respectée par
DSP3, NIS2 et AMLR. Pas par les deux autres :

| Dossier | Écart constaté |
|---|---|
| `euro-numerique` | **ni `_LISEZMOI.md`, ni `exigences.md`, ni `faits.md`, ni `conclusions.md`, ni `arbres.md`.** À la place, deux fichiers que le harnais ne décrit nulle part : `decisions.md` et `restitution-finale.md` |
| `euro-numerique-wholesale` | ni `exigences.md`, ni `arbres.md` |

**Conséquence concrète.** `_ROUTAGE.md` §2 prescrit, pour une réglementation non active :
« ouvrir son `_LISEZMOI.md` d'abord, qui déclare son état et ce qui est peuplé ». Cette consigne
**échoue sur `euro-numerique`**, qui n'en a pas. Et `decisions.md` n'existant nulle part ailleurs,
rien ne dit ce qu'il contient ni quand l'ouvrir.

L'explication est probablement légitime : l'euro numérique est une mission **terminée**
(`restitution-finale.md`), présentée en séance comme la référence de maturité de la méthode.
Sa forme diffère parce que son cycle est clos. Mais alors le harnais doit le dire.

**Action proposée :** au choix — déclarer dans `CLAUDE.md` une variante « réglementation clôturée »
(`decisions.md` + `restitution-finale.md` remplacent les maillons de travail), ou ajouter un
`_LISEZMOI.md` d'une dizaine de lignes à `euro-numerique` qui l'annonce comme close et renvoie
vers sa restitution. La seconde est plus simple et suffit à réparer la consigne du §2.

---

## B. Manques structurels

### 🔴 B.1 — Aucune règle ne dit par quel fichier entrer

Le vault fait 863 Ko hors archive. `CLAUDE.md` porte les règles et la carte de l'arborescence,
mais jamais la correspondance « ce type de demande, donc ces fichiers-là ». Chaque prompt relance
une exploration, et la fenêtre de contexte est saturée avant la rédaction.

**Traité :** création de `_ROUTAGE.md`, appelé depuis `CLAUDE.md`.

---

### 🟠 B.2 — Aucune règle ne borne la longueur des sorties

`_skills/redaction-gt/SKILL.md` proscrit le tiret long, le « il faut » et le « nous ».
Il ne dit rien sur la longueur ni sur le niveau de détail attendu. C'est le seul endroit
où une telle règle aurait sa place, et c'est le grief principal remonté le 04/09.

**Action proposée :** ajouter un contrat de sortie en fin de ce skill.
Ordre de grandeur : 400 mots pour une réponse en chat, 12 lignes pour un bloc thématique,
une page pour un CR, dix constats pour une revue, deux pages pour une note d'analyse.

---

### 🟠 B.3 — La routine de début de session vise à côté

`CLAUDE.md` prescrit de lire, en début de session, `exigences.md`, `hypotheses.md` et `conclusions.md`
de la réglementation active. Sur DSP3, cela donne :

- `exigences.md` (3,8 Ko) : un simple renvoi vers `exigences/_index.md`, sans contenu propre
- `conclusions.md` (1,4 Ko) : quatre lignes de frontière de décisions, les conclusions arrivant en Phase 3
- `_LISEZMOI.md` (7,8 Ko), qui porte l'état exact du dossier, **ne figure pas dans la routine**

**Action proposée :** remplacer par `_LISEZMOI.md` + `hypotheses.md`, et laisser `_ROUTAGE.md` désigner
le reste selon la demande.

---

## C. Les trois points remontés par Alexandre au test du 04/09

> Ces trois-là ne sont **pas** des défauts de harnais, et c'est le résultat le plus important de l'audit.
> Aucune règle de lecture ne peut les corriger : dans les trois cas, **le vault demande ce qu'Alexandre
> reproche à la sortie**. Ce sont des arbitrages de documentation, et ils lui appartiennent.
> Ajouter un garde-fou par-dessus reviendrait à masquer la cause.

---

### ✅ C.1 — `cours-dsp3-psr.md` : supprimé

Le fichier a servi de base au test du 04/09 : **cité 9 fois**, contre 1 seule citation d'exigence,
et aucun des 22 fichiers de domaine ouvert. Il portait sa propre réserve en ligne 6 (« intuitions
de cadrage, pas des conclusions du GT »), citée trois fois en `[SRC:]` — une réserve ressortie
en source de vérité. `journal.md` du 17/08 notait déjà « ⚠️ construit à partir de
`cours-dsp3-psr.md` uniquement » : le même fichier avait contaminé un livrable trois semaines plus tôt.

**Tranché le 2026-09-07 : supprimé du vault.** C'était un support de formation personnel, pas un
maillon de la chaîne. Références retirées de `_ROUTAGE.md` et de `_LISEZMOI.md`.
Les mentions historiques du `journal.md` sont conservées (c'est un journal).

---

### 🟠 C.2 — La matrice d'impacts : le fichier se déclare source de vérité, Alexandre dit le contraire

**Ce qui s'est passé.** La matrice a été citée dans la sortie. Alexandre a signalé qu'elle
n'aurait pas dû l'être.

**Ce que le fichier dit de lui-même**, `cartographie/matrice-impacts-si.md` lignes 10-11 :

> « **Source de vérité unique** pour les impacts SI DSP3/PSR. La vue antérieure par parcours
> et la V1 sont archivées dans `_archive/` et ne doivent plus être utilisées. »

**Le problème exact.** Le vault désigne explicitement ce fichier comme *la* source autorisée pour
les impacts SI. La consigne écrite et la consigne orale disent l'inverse. Claude a suivi la consigne
écrite, et c'est ce qu'on lui demande de faire.

**Aucune règle ne peut trancher ça**, parce que la raison de la réserve n'est pas connue.
Deux lectures possibles, et elles n'appellent pas la même correction :

| Lecture | Ce que ça veut dire | Correction |
|---|---|---|
| **(a)** La V2 n'est pas assez stabilisée pour être citée | La matrice est un travail en cours | Retirer la mention « source de vérité unique » de l'en-tête et la remplacer par un statut de maturité |
| **(b)** Le problème est de mêler les natures | Les cotations 0/1/2 sont un **jugement du GT** ; un delta réglementaire **décrit le texte**. Les mélanger fait passer une opinion pour du droit | Garder l'en-tête, mais imposer que toute citation de cotation soit annoncée « position du GT au 19/08 », jamais « exigé par le texte » |

**Question à Alexandre :** (a) ou (b) ? Tant que ce n'est pas tranché, `_ROUTAGE.md` maintient
la matrice ouverte uniquement quand l'impact SI est explicitement demandé, et ses cotations
citées comme position du GT — ce qui est sûr sous les deux lectures, mais n'est pas une réponse.

---

### 🟠 C.3 — « Accès aux systèmes de paiement » : ce n'est pas une invention, le vault le demande

**Ce qui s'est passé.** La thématique « accès aux systèmes de paiement et de-risking » est
ressortie de la sortie. Alexandre l'a signalée hors cible.

**D'où elle vient, exactement.** `reglementations/dsp3/_LISEZMOI.md`, lignes 53-55,
section « Domaines fonctionnels pressentis », **dernière entrée de la liste** :

> « SCA · anti-fraude (verification of payee, spoofing, refunds) · open banking (API, permission
> dashboard) · agrément/supervision PSP · protection consommateur & transparence des frais ·
> **accès aux systèmes de paiement**. »

**Corroboré par** `journal.md`, entrée du 2026-08-17, qui décrit le support de cadrage comme :

> « 4 slides domaines (fraude, SCA, open banking, **accès aux systèmes de paiement**) »

**Le problème exact.** Le `_LISEZMOI.md` est la carte de navigation du dossier. La sortie l'a suivie
fidèlement. Une décision contraire existe pourtant, mais **ailleurs** :
`gt-seances/dsp3/revue-GT11-retours-Christel-2026-09-01.md` point B7 — Christel Body, sur la planche
de-risking : « ce n'est pas notre sujet, ça concerne CACI ». Cette décision n'a jamais été reportée
dans la carte de navigation.

**Ce qui manque réellement : le périmètre du GT n'est écrit nulle part.** Vérifié sur les 179 fichiers
du vault : aucun fichier de périmètre n'existe. Le seul document portant ce mot est
`contributions-entites/DSP3-ET-03`, qui décrit le périmètre de la squad Open Banking de BForBank,
sans rapport. Conséquence secondaire : la graduation « Hors périmètre » imposée par `redaction-gt`
n'a aucun référentiel pour être remplie.

**Deux corrections, à choisir :**

- [ ] **Retirer l'entrée** de la liste des domaines pressentis. Trente secondes. Ne vaut que pour
      DSP3, et se reperdra à la prochaine réécriture du fichier.
- [ ] **Écrire un `perimetre.md`** en tête de chaîne : entités concernées, statut de chacune
      (établissement de crédit ou de paiement), domaines dans le champ et hors champ **avec le motif**.
      Plus long, mais resservira pour AMLR et NIS2, et donne enfin un référentiel à « Hors périmètre ».

Tant que le périmètre n'est pas écrit, aucune règle de lecture ne peut le deviner, et la thématique
ressortira à chaque passe.
