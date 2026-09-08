---
name: synthese
description: Produire une couche de synthèse réduite et sourcée à partir d'une sortie existante du vault (exigences, faits, matrice, contribution d'entité). Déclencher quand l'utilisateur tape /synthese, demande de re-synthétiser, de regrouper en sujets clés, ou dit qu'une sortie du vault est trop longue à relire.
---
Cible à synthétiser : $ARGUMENTS

## Règle de forme, avant tout le reste

Les deux questions ci-dessous sont des questions, pas des livrables. Lister tout ce qu'il y a
à lister, sans en couper. Tableau ou liste, peu importe.

**Ne jamais faire figurer** : la taille des fichiers, une colonne « nature » ou « type »,
le chemin complet. Le nom du fichier suffit, et c'est la seule chose utile pour choisir.

---

## Étape 1 — Quelle réglementation

Si $ARGUMENTS n'en nomme pas une, poser exactement ceci, puis **attendre** :

```
Quelle réglementation ?

  dsp3 (active)
  euro-numerique
  euro-numerique-wholesale
  amlr · nis2 · cyber-resilience-act  (dossiers encore vides)
```

Ne rien lire avant la réponse. Si la réponse est un dossier vide, le dire et s'arrêter :
ne pas synthétiser un gabarit, ne pas le combler avec une connaissance générale du texte.

## Étape 2 — Quelle cible

Lister les fichiers du dossier, les uns à la suite des autres, noms en clair. Exemple de forme
attendue sur dsp3 :

```
Qu'est-ce que je te synthétise ?

Exigences par chapitre
  01  champ d'application et définitions
  02  information et transparence précontractuelle
  03  frais, tarification et conversion de devises
  04  retrait d'espèces
  05  accès aux systèmes de paiement et de-risking
  06  open banking — accès aux données de compte
  07  open banking — consentement et tableau de bord
  08  open banking — obligations des prestataires tiers
  09  consentement et autorisation des opérations
  10  vérification du bénéficiaire (VoP)
  11  responsabilité et remboursement
  12  fraude — surveillance, partage et reporting
  13  authentification forte (SCA)
  14  exécution des opérations, délais et dates de valeur
  15  protection des données
  16  gestion du risque opérationnel et de sécurité
  17  réclamations, litiges et sanctions
  18  agrément et supervision des établissements de paiement
  19  fonds propres et cantonnement des fonds
  20  exemptions et régime transitoire
  21  monnaie électronique et jetons
  22  dispositions finales, actes délégués et calendrier
  99  annexes

Analyse
  faits · hypothèses · matrice d'impacts SI · journal

Contributions d'entités
  CAPS · BFB dashboard TPP Art.43 · BFB périmètre squad Open Banking
```

Accepter « tous les chapitres », « tout open banking », un numéro, un nom. **Attendre.**

---

## Étape 3 — Production

1. **Lecture.** Ouvrir uniquement la cible retenue. Déléguer selon la Règle n°7 de `CLAUDE.md` :
   la question est étroite (un domaine par fichier), donc délégation ; environ 50 Ko de source
   par agent, un agent peut porter plusieurs fichiers, extrait rendu fichier par fichier.
   La synthèse porte sur ce qui existe déjà dans le vault, **jamais sur les PDF** :
   re-synthétiser un maillon, pas re-décliner le texte. Pour décliner le texte, c'est `/exigence`.

2. **Regroupement.** Un sujet = un objet fonctionnel, pas un article. Nommer les sujets avec
   les mots du texte, pas avec des catégories inventées.

3. **Rédaction.** Par sujet, 5 à 10 lignes. Reformulation, `[SRC: …]` à chaque affirmation,
   sans exception. Aucune interprétation, aucune cotation, aucun impact SI : ce sont les maillons
   CARTOGRAPHIE et ARBRES qui les portent.

   En tête : **la liste des fichiers réellement ouverts**, nommés un par un. Ne jamais écrire
   « les 22 fichiers » si six ont été ouverts.

4. **Hypothèses.** En fin de chaque sujet, un encadré séparé, jamais dans le corps :

   > *Hypothèses entendues — à vérifier. Aucune conclusion ci-dessus ne s'y appuie.*
   > 🟢 TRANCHÉE citable · 🟡 OUVERTE citable avec la réserve écrite · ⚫ BLOQUANTE citable
   > et signalée comme blocage · 🔴 OBSOLÈTE jamais

   L'encadré renvoie à `hypotheses.md`, ce n'est pas une source. Une hypothèse ne produit
   jamais une affirmation dans le corps.

5. **En-tête « À lire d'abord ».** Avant les sujets, une sélection des sujets qui comptent le plus.
   C'est ce que l'utilisateur lit en trente secondes entre deux réunions ; le reste est de la
   documentation qu'il ouvrira seulement si cette ligne l'accroche.

   - **Deux à trois lignes par sujet, jamais plus**, et le numéro du sujet pour aller lire la suite.
   - **Pas de nombre fixe.** Autant de sujets qu'il en compte vraiment : trois ou douze.
   - Aucun fait qui ne soit déjà dans le corps. Cet en-tête ne source rien de neuf, il choisit.

   **Hiérarchiser est un jugement, donc il s'annonce et il se motive.** Titrer
   *« À lire d'abord — sélection proposée, à valider »*, et fonder le choix sur des signaux
   comptables du vault, jamais sur une impression : volume d'exigences du sujet · hypothèse
   ⚫ BLOQUANTE rattachée · brique cotée 2 dans `matrice-impacts-si.md` · contribution d'entité
   portant sur le sujet · obligation nouvelle plutôt que continuité de la DSP2.
   Nommer le signal retenu en fin de ligne, entre parenthèses.

   Forme attendue :

   ```
   À LIRE D'ABORD — sélection proposée, à valider

   § 13  Authentification forte
         Le PSP doit garantir à tout client un moyen de SCA gratuit sans dépendre d'un
         smartphone. C'est une obligation d'accessibilité nouvelle, pas un ajustement.
         (36 exigences · 2 briques cotées 2)

   § 07  Tableau de bord des consentements
         Interface à construire : retrait gratuit, rétablissement sous 48 h, historique
         deux ans. Une entité a déjà produit une étude dédiée.
         (10 exigences · contribution BFB · obligation nouvelle)
   ```

6. **Sortie.** Ne rien écrire. Présenter la synthèse et le diff, attendre validation (Règle n°2).
   Cible proposée : `synthese.md` dans le dossier de la réglementation, maillon dérivé,
   jamais en remplacement de la cible.
