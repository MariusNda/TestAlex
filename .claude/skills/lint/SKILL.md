---
name: lint
description: Contrôle de cohérence du vault — identifiants orphelins, dépendances non résolues, statuts hors énumération, manques de source ouverts, chaîne de traçabilité rompue. Déclencher quand l'utilisateur tape /lint, demande un contrôle de cohérence, une passe de santé du vault, de vérifier les identifiants ou les dépendances, ou après une grosse passe d'écriture (/exigence, /debrief, /reunion) pour vérifier ce qui a été cassé. Lecture seule, aucune écriture.
---
Réglementation à contrôler : $ARGUMENTS (si vide : la réglementation active de `CLAUDE.md`).

Objectif : faire par machine la tenue de livre que la Règle n°2 et la chaîne de traçabilité
imposent à la main. Tu **constates**, tu ne corriges pas, tu ne tranches pas le contenu.

**Référence de tous les motifs, énumérations et champs : `_methodes/ontologie.md`. Lis-le d'abord.**
Ne juge jamais un format sur ta mémoire ou sur ce qui te paraît logique.

## Méthode — grep d'abord, lecture ensuite

Le vault est volumineux (référentiel d'exigences ~300 Ko, matrice d'impacts ~66 Ko). **Les
contrôles 1 à 6 se font intégralement par recherche textuelle**, sans ouvrir les fichiers : c'est
ce qui rend la commande utilisable à chaque fin de session. N'ouvre un fichier que pour les
contrôles 7 et 8, et seulement les passages que le grep a désignés. Si un contrôle exige malgré
tout d'ouvrir beaucoup de fichiers, applique la Règle n°7 (balayage avant extraction).

Travaille depuis la racine du vault, sur `reglementations/<reg>/` et `gt-seances/<reg>/`.

## Les contrôles

**1. Préfixe.** Aucun identifiant ne doit porter le préfixe littéral `REG-` : c'est une notation
de substitution, jamais une valeur (`_methodes/glossaire-vault.md`). Signaler, avec fichier et
ligne, toute occurrence **en forme d'identifiant** dans un fichier de **contenu** : `REG-EX-` suivi
de chiffres, `REG-H` suivi de chiffres, `REG-ET-` suivi de chiffres. ⚠️ Ne pas signaler l'emploi
générique en prose (« avant qu'une REG-EX ne s'appuie sur… ») : c'est un raccourci de langage, pas
un identifiant écrit. Les fichiers de règle ont le droit d'employer la notation `<PRÉFIXE>`.

**2. Identifiants déclarés vs cités.** Pour chaque type portant un motif (`<PRÉFIXE>-EX-NNN`,
`<PRÉFIXE>-HNN`, `<PRÉFIXE>-ET-NN`, `F<X>.<Y>`, `C<X>.<Y>`), constituer deux ensembles :
les identifiants **déclarés** (dans leur fichier de rattachement, cf. ontologie) et les
identifiants **cités** (partout ailleurs). Puis signaler :
- **cité mais non déclaré** — renvoi dans le vide, le plus grave : la chaîne est rompue ;
- **déclaré mais jamais cité** — orphelin, souvent bénin (un objet récent), parfois le signe
  d'un maillon qui n'a pas été remonté.

**3. Séquence des exigences.** Comparer les identifiants réellement présents dans `exigences/`
au décompte et aux plages annoncés par `exigences/_index.md`. Signaler : doublons, trous dans
la séquence, écart entre le total annoncé par domaine et le total constaté, plage annoncée en
tête d'un fichier de domaine qui ne correspond pas à son contenu.

**4. Dépendances d'hypothèses.** Chaque identifiant listé dans la colonne `Dépendances` de
`hypotheses.md` doit résoudre vers un objet existant. Signaler ceux qui ne résolvent pas.
Signaler aussi les dépendances rédigées en prose sans identifiant (« la carto applicative
entière ») : elles ne sont pas vérifiables, donc pas propageables — c'est un constat, pas une faute.

**5. Énumérations.** Toute valeur de statut, de graduation, d'état de brique ou de type d'entrée
de journal doit appartenir à l'énumération déclarée dans l'ontologie. Signaler les valeurs hors
énumération, et les objets qui n'en portent aucune (une position sans graduation, une hypothèse
sans statut).

**6. Manques de source.** Inventaire complet des `[SRC: à sourcer ⚠️]` et des
`[attribution à confirmer]` du dossier, par fichier, avec le compte. C'est la liste que la
routine de fin de session ne produit que sur le périmètre de la session : ici elle est totale.
Signaler aussi toute ligne de `faits.md` sans aucun `[SRC:]` — un fait sans source n'existe pas.

**7. Règle n°2 — propagation.** Pour chaque hypothèse dont le statut n'est pas 🟡 OUVERTE, ou qui
porte une annotation datée postérieure à sa création : vérifier qu'une entrée `[HYP]` de
`journal.md` mentionne son identifiant, et que ses dépendances portent bien une alerte
`⚠️ à revisiter`. Signaler les propagations manquantes. C'est le contrôle le plus utile de la
commande : c'est celui qu'un humain oublie.

**8. Règle n°5 — citabilité.** Repérer les documents cités en `[SRC:]` dont l'en-tête porte une
réserve (« intuitions », « à sourcer », « non stabilisé », « non validé »). Ouvrir uniquement
l'en-tête des documents effectivement cités. Une citation d'un tel document est à signaler.

**9. Fraîcheur.** Hypothèses 🟡 OUVERTE dont la dernière annotation datée remonte à plus de
30 jours. Dernière entrée `[REG]` de `journal.md` remontant à plus de 30 jours (la veille est en
retard, cf. Règle n°3). Donner les dates, pas un jugement.

## Rendu

Un rapport court et scannable, **en chat uniquement**. Trois sections, dans cet ordre :

```
🔴 CHAÎNE ROMPUE          renvois dans le vide, propagations manquantes, faits sans source
🟠 À TRANCHER             valeurs hors énumération, écarts de séquence, citations réservées
🔵 CONSTATS               orphelins, dépendances en prose, manques de source ouverts, fraîcheur
```

Une ligne par anomalie : `fichier:ligne — ce qui est constaté — l'identifiant concerné`.
Grouper par nature, pas par fichier. **Si une section est vide, l'écrire en une ligne.**

Termine par :
- le **périmètre réellement contrôlé** (les fichiers parcourus, nommés — jamais « tout le vault »
  si six fichiers ont été lus) ;
- pour chaque anomalie 🔴, **la correction qu'elle appelle**, formulée mais **non appliquée** ;
- une ligne sur ce que le contrôle **ne sait pas** vérifier (la justesse d'un `[SRC:]` par rapport
  au texte, la pertinence d'une exigence : ça, c'est `/loi` et la relecture humaine).

## Interdits

- **Aucune écriture.** Ni vault, ni Notion, ni `CHANGE.md`. Une anomalie se rapporte, elle ne se
  corrige pas : la correction passe par la commande du maillon concerné, avec diff et validation.
- **Aucune interprétation de contenu.** Une contradiction entre deux faits n'est pas une anomalie
  de lint : c'est un écart à lever avec l'émetteur. Le lint contrôle la **forme** de la chaîne,
  pas la vérité de ce qu'elle transporte.
- **Ne rien inventer comme attendu.** Si l'ontologie ne déclare pas de motif pour un objet
  (cinématiques, briques), le dire et passer — ne pas contrôler contre une convention supposée.
