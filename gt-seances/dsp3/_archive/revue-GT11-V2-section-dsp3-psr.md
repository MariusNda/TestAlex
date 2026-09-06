# Revue GT11 V2 — section DSP3/PSR (slides 10 à 36)

> Revue du 2026-08-21 sur « GT11 - Lancement DSP3-PSR - 16092026.pdf », 36 pages.
> Périmètre demandé : à partir de la section DSP3/PSR, soit **slides 10 à 36**. Les slides 1 à 9
> (objectifs du GT, euro numérique) sont hors revue.
> Objectif du livrable tel qu'énoncé : **être le point de départ de l'analyse IT de la réglementation.**
> Le critère de revue en découle : une omission ou une citation fausse ne se voit pas en séance,
> elle se voit six mois plus tard dans un chiffrage.
>
> **Méthode.** Contrôle article par article sur les PDF de compromis du 23/04/2026
> (PSR ST-8221, PSD3 ST-8222), croisement avec les 711 exigences de `exigences/` et avec
> `cartographie/matrice-impacts-si.md` (V2). La cotation de la slide 20 a été contrôlée par
> **analyse des couleurs du rendu**, pas à l'œil.
>
> **Réserve de méthode.** Articles relus directement pendant cette revue : PSR 32, 36, 38, 43, 44,
> 45, 50, 51, 54, 59, 85, 88, 88a, 97, 112. Les autres constats reposent sur des relevés verbatim
> effectués sur le même PDF par des passes de vérification dédiées : ils sont fiables mais méritent
> un dernier coup d'œil avant intégration lorsqu'ils sont structurants. Le règlement délégué
> 2018/389 (RTS SCA) et la DSP2 elle-même **ne sont pas dans le vault** : toute comparaison à cette
> ligne de base reste non tranchée et signalée comme telle.

---

## Verdict

Le support est bon là où on le regarde, et faux là où on s'en servira.

La partie pédagogique — les quatre slides de domaine (14 à 17), les neuf parcours (18), le focus API
(21) — est au-dessus de la pratique courante : format à trois colonnes avec la ligne « pour les
entités », exemples concrets, sources en pied de slide. C'est diffusable presque en l'état.

La partie qui porte l'analyse IT ne l'est pas. **Sept points bloquants**, dont trois créent un écart
entre le support et le vault, et un huitième déjà signalé le 19/08 et non traité. S'y ajoutent
**31 erreurs ou imprécisions de citation**, dont **5 régressions non propagées depuis la revue V1**,
et **10 trous de complétude** dont deux touchent des obligations qui deviendront des chantiers.

Le point le plus coûteux n'est pas une erreur, c'est un manque : **le support ne dit à aucun moment
ce que le GT attend des entités.** Pour une séance de lancement dont l'objet est de récolter, c'est
le seul défaut qui compromet l'objectif de la séance elle-même.

| Axe de contrôle | Verdict |
|---|---|
| Complétude (couverture des domaines porteurs d'impact SI) | **Insuffisante** — 4 domaines sur 22 absents, dont les sanctions et l'exécution/délais |
| Exhaustivité (au sein des domaines traités) | **Correcte** sur fraude, SCA, open banking ; **faible** sur PSD3 et de-risking |
| Exactitude | **7 bloquants + 31 constats** — taux de citation exacte estimé à 80 % |
| Cohérence interne | **4 contradictions** entre slide 20, annexes et matrice du vault |
| Lisibilité | **Correcte en lecture, insuffisante en projection** — slides 18 et 20 illisibles au vidéoprojecteur |
| Traçabilité | **Excellente** — pieds de slide sourcés article par article, pratique à conserver |
| Dispositif de séance | **Manquant** — aucune demande, aucun attendu, aucune question posée aux participants |

---

## 0. Suivi de la revue V1 : cinq corrections non propagées

La revue du 19/08 (`revue-GT11-V1-slides-10-28.md`) a été largement appliquée : le titre de la
slide 20, la note de travail « y'a déjà plein de trucs qui existent », la coquille « CLIENS », le
« 3DSecure » de la slide 11, le « huit fonctions » devenu « neuf », le transfert des 180 jours à
l'AISP — tout cela est corrigé. Cinq points sont restés en arrière.

| Réf. V1 | Point | État au 21/08 |
|---|---|---|
| **C1** | Volet sanctions absent, classé **priorité 1** | Toujours absent. Voir A7. |
| **C3** | Ce que le GT attend des entités | Toujours absent. La slide 24 décrit ce que le GT va faire. Voir D1. |
| **B3** | Confusion notification à 10 s / recréditation immédiate (Art. 69(2d)-(2e)) | Non corrigée, désormais en annexe 6 (p. 34). |
| **B4** | Support humain gratuit présenté comme couvrant l'assistance SCA | Non corrigée, désormais en annexe 6 (p. 36). |
| **N4** | « 2 ans historique des consentements » au lieu de « consentements retirés ou expirés » | Non corrigée, désormais en annexe 2 (p. 30). |
| **D9** | Échéances par front disparues de la slide fraude (+27 mois prévenir, +21 détecter/réparer) | Toujours absentes de la p. 14. |

Les trois constats B3, B4 et N4 ont migré du corps du support vers les annexes sans être corrigés :
la V2 a déplacé le texte, pas relu la citation. C'est exactement le mode de défaillance que la
règle de propagation vise.

---

## A. Bloquants — à corriger avant diffusion

### A1 · slide 20 — la brique API est coloriée un niveau au-dessus de sa cotation

Contrôle par analyse des couleurs du rendu de la slide : **11 cellules** portent la couleur
« (2) Impact fort » (RGB 244,118,130) et **17** la couleur « (1) » (RGB 251,209,213). La matrice V2
du vault cote **10 briques en 2 et 18 en 1**. L'écart unique est **API**.

Or l'annexe 3 (p. 31), qui commente cette même brique, écrit : « **Ni capacité nouvelle ni
changement de régime** ». Et la matrice V2 documente explicitement la rétrogradation :
« API | **2 → 1** | la parité, la publication des statistiques […] existent déjà sous les
RTS 2018/389 ».

Le support affirme donc trois choses différentes sur la même brique dans le même document.

**Pourquoi c'est bloquant.** La slide 20 est la seule page du support qu'un lecteur pressé
photographiera. Elle deviendra la référence de priorisation. Un écart avec la source de vérité du
vault, sur la brique dont dépend toute la trajectoire open banking, se propagera dans le chiffrage.

**Correction.** Deux options, à trancher explicitement — pas à laisser au coloriage :
1. **Recolorier API en niveau 1**, cohérent avec la matrice et l'annexe. La slide 21 conserve sa
   force : elle explique justement qu'une adaptation peut coûter plus qu'une refonte.
2. **Assumer le 2 et le justifier**, en faisant remonter la charge dans la définition du niveau.
   Il faut alors recoter la matrice V2 en amont, pas la slide.

L'option 1 est la seule qui ne demande pas de retoucher le vault.

### A2 · slide 12 — le calendrier porte trois erreurs cumulées

| Ce que dit la slide | Ce que dit l'Art. 112 |
|---|---|
| « **deux échéances à tenir**, T3 2028 et T2 2029 » | Le PSR porte **trois** régimes d'application, pas deux : le corps du règlement à +21 mois, les Art. 50 et 57 (VoP) à +27 mois, et **les Art. 85a et 108a dès l'entrée en vigueur**. L'exemption des virements récurrents et le volet jetons de monnaie électronique s'appliquent immédiatement. |
| « ≈T4 2027 · Premiers RTS/ITS (**+12 mois**) » | Le **premier** mandat échoit à **+9 mois** : RTS statistiques d'interface et temps de rétablissement, Art. 38(5). Les RTS SCA sont bien à +12 mois (Art. 89(1)), l'acte délégué schemes à +15 mois (Art. 31a(4)), les lignes directrices double inhérence et négligence grave à +18 mois (Art. 85(12)). |
| « ≈T2 2029 · nouvelles exigences VoP (**+27 mois**) » | Arithmétique fausse. Si l'EEV est au T4 2026, +27 mois tombe au **T1 2029**, pas au T2. |

**Pourquoi c'est bloquant.** C'est la slide qui fonde le « il faut engager maintenant ». Le premier
jalon opposable n'est pas à +12 mois mais à +9, et il tombe précisément sur l'open banking, l'axe
que le GT porte. Un régime d'application dès l'EEV qui n'apparaît nulle part, sur une slide de
calendrier, est le genre d'oubli qui fait perdre neuf mois.

**Correction.** Trois régimes affichés, jalon EBA à +9 mois ajouté, arithmétique refaite. Et
puisque le JO n'est pas paru (veille du 17/08), **présenter l'axe en délais relatifs**, les dates
absolues en gris et explicitement conditionnelles — la slide 22 le dit déjà, la slide 12 le contredit.

### A3 · slide 14 — le remboursement pour usurpation présenté comme automatique

Le support écrit : « Si un fraudeur s'est fait passer pour la banque et que le client porte plainte,
la banque rembourse sous 15 jours ouvrables », et dans l'exemple : « La banque rembourse
**intégralement**, sous réserve des conditions prévues par le PSR ».

L'Art. 59 dit autre chose. Les quinze jours ouvrables sont un délai pour **rembourser *ou* motiver
un refus**, et ils ne courent qu'à compter de la notification **accompagnée du dépôt de plainte**.
Le droit est réservé aux **consommateurs**, il tombe en cas de **négligence grave** ou de fraude du
client, et l'exercice suppose une **procédure contradictoire** que le PSP doit outiller.

**Pourquoi c'est bloquant.** La slide décrit un remboursement de plein droit ; le texte décrit une
instruction de dossier avec charge de la preuve et motif de refus opposable. Ce ne sont pas les
mêmes composants SI : le premier appelle un flux de provision, le second appelle un **workflow de
qualification, de décision motivée et de traçabilité de la preuve**. C'est la brique Ticketing et la
brique Risque qui changent de nature selon la lecture retenue.

**Correction.** « Rembourser ou motiver un refus sous 15 jours ouvrables à compter du dépôt de
plainte, pour les consommateurs, hors négligence grave. » Et une ligne « pour les entités » qui dit
le vrai delta : un parcours de réclamation instrumenté, pas une provision.

### A4 · slide 14 — la VoP présentée en mécanisme binaire, et rattachée au mauvais article

Deux problèmes distincts sur le même schéma.

**Le mécanisme.** Le schéma en quatre étapes se termine sur « Concordance : virement validé / Écart :
alerte avant confirmation ». Le texte prévoit un **troisième état** : la concordance approchante,
avec **restitution du nom exact** du titulaire au payeur. Et un écart ne peut pas à lui seul fonder
un blocage — la décision reste au payeur.

**L'article.** Le pied de slide renvoie à l'« Art. 50 ». L'Art. 50 ne contient **aucun mécanisme** :
il applique l'art. 5c du règlement 260/2012 *mutatis mutandis*. Le mécanisme opérationnel est à
l'**Art. 110c**, qui modifie ce règlement. Citer l'Art. 50 devant quelqu'un qui ouvrira le texte,
c'est l'envoyer sur un article qui renvoie ailleurs.

**Manque associé.** Les jetons de monnaie électronique sont **exclus** du champ de la VoP
(Art. 67a(3)) ⚠️, et la VoP est le seul dispositif du paquet à **+27 mois** quand tout le reste est
à +21. Aucune des deux informations n'est sur la slide, et la seconde est un fait de séquencement.

**Correction.** Trois états au lieu de deux, renvoi « Art. 50 renvoyant à l'art. 5c du règlement
260/2012, mécanisme à l'Art. 110c », mention du décalage à +27 mois et de l'exclusion des jetons.

### A5 · slide 15 — « lève la dépendance au smartphone » est une lecture tronquée

Le titre de la slide annonce que le PSR « lève deux dépendances : au smartphone, et aux fabricants
d'OS ». La colonne 2 dit : « Un canal d'authentification alternatif à concevoir et à maintenir dans
la durée ».

L'Art. 88(2) porte deux réserves que la slide ne mentionne pas, et elles sont décisives pour le
chiffrage :

- l'interdiction de faire dépendre la SCA du smartphone tombe **« unless the payment service user
  has agreed to the provision of services exclusively through mobile applications on such
  device »** — l'accord du client rouvre la dépendance ;
- l'Art. 88(1) précise que l'obligation **« does not extend to providing devices to the payment
  service user »** — aucune obligation de distribuer du matériel.

**Pourquoi c'est bloquant.** Sans ces deux réserves, la slide fait conclure qu'il faut un second
canal universel et, potentiellement, un parc de dispositifs physiques. Avec elles, le chantier
devient un canal alternatif pour la population qui n'a pas consenti au tout-mobile, sans fourniture
de matériel. L'écart de chiffrage est d'un ordre de grandeur.

**Erreur associée, même slide.** L'exemple donné — « un code transmis par serveur vocal » — décrit
un dispositif **à un seul facteur**, qui ne satisfait pas la SCA. Et le schéma « au moins deux des
trois facteurs, de catégories différentes » omet la dérogation de l'Art. 85(12) : **deux éléments
d'inhérence** sont admis sur démonstration de leur indépendance à l'autorité nationale, avec
lignes directrices EBA à +18 mois. C'est une option d'architecture ouverte, pas un détail.

### A6 · slide 16 — le tableau de bord des consentements a un périmètre plus étroit et une nature différente

Le support écrit : « Tableau de bord unique dans l'application bancaire : voir, gérer et révoquer
**toutes** les autorisations », et le qualifie de « brique front nouvelle, à construire dans chaque
banque en ligne et application mobile ».

L'Art. 43(1) limite le périmètre : le tableau de bord couvre les consentements donnés pour des
services d'information sur les comptes ou d'initiation de paiement **« covering multiple or
recurrent payments »**. Une initiation ponctuelle n'y entre pas.

Et ce n'est pas une brique front. L'Art. 43 impose un **registre** alimenté par des **flux
bidirectionnels avec les prestataires tiers** : le tiers notifie l'ASPSP des consentements
obtenus, l'ASPSP notifie le tiers des retraits, et le tableau affiche les **dates d'accès
effectifs** (Art. 43(2)(a)(va)) — une donnée que la banque ne détient pas aujourd'hui.

**Pourquoi c'est bloquant.** C'est le chantier que la slide 23 classe en première candidature de
mutualisation Groupe, et DSP3-H03 est ouverte dessus. Le présenter comme une IHM conduira à
chiffrer un écran. Le coût est dans le registre et le protocole d'échange.

**Correction associée.** Les « 48 heures » de l'Art. 43(2)(c) sont mal lues dans tout le support
(p. 18, p. 29, p. 30) : ce n'est pas un délai de rétablissement, c'est une **fenêtre de
réversibilité de 48 h à compter du retrait**, adossée à une suppression différée côté tiers
(Art. 43(2b)). La spécification de l'IHM et le contrat de service en dépendent.

### A7 · le volet sanctions est absent — déjà priorité 1 le 19/08

Le support ne mentionne à aucun endroit les Art. 96 à 99. C'était la priorité 1 de la revue V1,
et le journal du 17/08 acte l'ajout des sanctions aux domaines fonctionnels du dossier.

Ce qui manque n'est pas un ordre de grandeur d'amende, c'est **une grille de priorisation fournie
par le texte lui-même**. L'Art. 97(1) désigne nommément cinq obligations dont le manquement est
sanctionné :

| Art. 97(1) | Obligation | Traitée dans le support ? |
|---|---|---|
| (a) | Accès aux comptes des établissements de paiement (Art. 32) | Oui, slide 17 |
| (b) | Services d'information et d'initiation (Titre III ch. 3) | Oui, slide 16 |
| (c) | Prévention de la fraude et SCA (Art. 85, 86, 87) | Oui, slides 14-15 |
| (d) | **Transparence des frais des opérateurs de DAB (Art. 20(c)(ii))** | **Non — nulle part** |
| (e) | **Délais de compensation (Art. 56(2), 57(2), 59(2), 63(2))** | Partiellement, sans le lien à la sanction |

Le texte dit donc que les quatre axes choisis par le support sont les bons — et il en désigne un
cinquième que le support ignore. Quant à l'assiette : 10 % du chiffre d'affaires annuel total,
calculé sur les **comptes consolidés de l'entreprise mère ultime** lorsque l'entité appartient à un
groupe consolidant (Art. 97(3)), plus astreintes à 3 % du CA journalier moyen (Art. 98).

**Correction.** Une slide, ou même un encadré sur la slide 22 : les cinq manquements sanctionnés,
l'assiette consolidée, la conséquence — l'exposition d'une filiale se calcule sur le Groupe. C'est
l'argument le plus court pour obtenir de la charge.

---

## B. Erreurs et imprécisions de citation

### B.1 — Slides 11 à 18 (corps du support)

| # | Slide | Le support dit | Le texte dit | Correction |
|---|---|---|---|---|
| B1 | 11 | « DSP2 : 2018 […] Introduction de l'authentification forte » | La DSP2 est de 2015, transposée en 2018 ; la SCA n'est opposable qu'au **14/09/2019** (RTS 2018/389) | Dissocier la directive de l'entrée en vigueur de la SCA |
| B2 | 11 | « les banques doivent partager les données […] **via des API ouvertes** » | La DSP2 n'a jamais imposé d'API : elle imposait un accès, l'interface dédiée n'étant qu'une des deux voies | « via un accès dédié, en pratique des API » |
| B3 | 11 | Adyen et Worldline en illustration du statut d'établissement de paiement | Ce sont des acquéreurs, dont l'activité relève largement du statut d'établissement de crédit ou d'agrément antérieur. Revolut ou Lydia illustreraient mieux | Changer les exemples |
| B4 | 12 | « Le régime applicable aux EP et aux **EME** est davantage harmonisé » | La catégorie EME **disparaît** : la PSD3 abroge 2009/110/CE et absorbe la monnaie électronique dans le statut d'établissement de paiement ⚠️ | « les deux statuts fusionnent » — c'est le fait marquant, pas une harmonisation |
| B5 | 14 | Ligne « Pour les entités » sur la VoP : « Le dispositif existe déjà pour les virements instantanés (IPR). Le delta porte sur le périmètre » | Exact, mais incomplet : l'Art. 50 étend le dispositif **à tous les virements, y compris hors euro et hors champ du règlement 260/2012**. Le delta porte donc aussi sur les devises et les identifiants | Ajouter le périmètre devises — c'est l'objet de DSP3-H08 |
| B6 | 14 | Échéances par front absentes | Prévenir à +27 mois, détecter et réparer à +21 mois | Réintroduire (constat V1 D9) |
| B7 | 15 | « DSP2 : exemptions figées par les RTS de 2018 et **obligatoires pour tous** » | L'Art. 85(11) explicite que les exemptions **« shall not be mandatory »** — il clarifie un principe, il ne renverse pas une obligation | « exemptions dont le caractère facultatif était discuté, désormais explicite » |
| B8 | 15 | « DSP2 : **aucune obligation** d'accessibilité » | L'Art. 88(1) s'ouvre par « **without prejudice to** Directive (EU) 2019/882 » : l'accessibilité est déjà due au titre de l'European Accessibility Act | « aucune obligation d'accessibilité *propre au droit des paiements* » |
| B9 | 15 | « DSP2 : **aucun droit d'accès** [aux fonctions du terminal] » | L'Art. 88a s'ouvre par « without prejudice to Article 6(7) of Regulation (EU) 2022/1925 » : le DMA porte déjà l'obligation pour les contrôleurs d'accès | « un droit d'accès élargi au-delà des seuls gatekeepers du DMA » |
| B10 | 15 | « Une contrainte qui se lève : ouverture pour les solutions de paiement propres au Groupe » | FRAND n'est pas gratuit, et l'Art. 88a(2) réserve les mesures nécessaires à l'intégrité du terminal ⚠️. C'est un **levier opposable à des tiers**, pas une capacité acquise | « un levier de négociation, à instruire » |
| B11 | 17 | « La DSP2 est **muette** sur l'accès des établissements de paiement aux comptes » | La DSP2 traitait déjà l'accès aux systèmes de paiement (art. 35) et aux comptes (art. 36) ⚠️. Le PSR durcit et outille, il ne comble pas un silence | « la DSP2 posait un principe sans procédure ni recours » |
| B12 | 17 | Case « (4) Recours […] **4 mois de préavis en cas de clôture** » | Les quatre mois sont un **préavis de clôture** (Art. 32(3) al. 2), pas un délai de recours. Le texte ne fixe **aucun** délai de recours | Sortir les 4 mois de la case Recours |
| B13 | 17 | Quatre motifs de refus limitatifs | Exact, mais l'Art. 32(3) al. 3 institue un **régime dérogatoire pour le motif AML** : notification sans motivation détaillée et préavis raccourci. C'est un branchement conditionnel dans le workflow, pas un cas particulier de rédaction | Ajouter le régime dérogatoire |
| B14 | 17 | Art. 31a présenté comme donnant la transparence « côté acquéreur **comme émetteur** » | L'Art. 31a ne couvre que les pratiques des schemes, processeurs et acquéreurs ⚠️ | Retirer « comme émetteur » |
| B15 | 18 (parcours 3) | « rétablissement sous 48 heures » | Fenêtre de réversibilité de 48 h (Art. 43(2)(c) + 43(2b)) | Voir A6 |
| B16 | 18 (parcours 2) | « délai de quatre heures si l'activation est à distance » | Exact, mais le client peut **ajuster ou désactiver** ce délai (Art. 51(4b)), tout changement étant lui-même soumis au délai en cours — verrou récursif à implémenter. Et l'Art. 51(4e) **exclut** l'entrée en relation et l'activation en agence | Ajouter l'opt-out, le verrou récursif et les deux exclusions |
| B17 | 18 (parcours 6) | « indisponibilité présumée après cinq requêtes en échec ou sans réponse sous 30 secondes » | À recontrôler : le seuil de l'Art. 38 est un compteur de requêtes en échec sur une fenêtre, la présomption ne se déclenche pas au premier franchissement ⚠️ | Vérifier avant diffusion |
| B18 | 18 (encadré) | « Les RTS de l'EBA préciseront la SCA, la communication et le monitoring, à +12 mois […] et les statistiques d'interface à +9 mois » | Correct, mais présenté à l'envers : le **premier** jalon est +9 mois. Et ce sont des dates de **soumission à la Commission**, l'adoption étant postérieure | Ordonner par échéance, préciser « soumission » |

### B.2 — Slide 21 (focus API) et slide 23

| # | Slide | Le support dit | Le texte dit | Correction |
|---|---|---|---|---|
| B19 | 21 | « le PSR n'impose aucun standard d'API » | L'Art. 35(3) impose une interface conforme aux **normes de communication émises par des organismes de normalisation européens ou internationaux** ⚠️, et les RTS de l'Art. 89(1) préciseront les exigences techniques | Nuancer : pas de standard nommé, mais une contrainte de normalisation et des RTS à venir. **Point sensible pour DSP3-H02 (STET / Berlin Group)** : l'affirmation en l'état ferme un arbitrage que le texte laisse ouvert |
| B20 | 21 | « La parité impose d'auditer chaque écran de la banque en ligne pour vérifier que l'API expose autant » | L'Art. 37 impose une parité de **disponibilité et de performance** (§1) et d'**information** (§2-3), pas une équivalence écran par écran | Attribuer l'affirmation au GT, ou la reformuler |
| B21 | 21 | Renvoi « Art. 44, 45 » pour la suppression immédiate d'un obstacle et la sanction | La suppression immédiate relève de l'**Art. 48** ⚠️ ; le préavis de changement de 2 mois de l'**Art. 35(4)** | Corriger les renvois |
| B22 | 21 | « Douze obstacles nommés » | Exact, mais l'Art. 44(1) dit « **shall include, but not be limited to** » : la liste est ouverte (constat V1 N1, non corrigé) | « au moins douze obstacles nommés » |
| B23 | 23 | Titre « **cinq** domaines » au-dessus d'un tableau de **six** lignes | — | Corriger le compte, ou fusionner la ligne surnuméraire |
| B24 | 23 | La 6ᵉ ligne (monétique et schemes) n'est portée par aucune brique cotée dans la matrice | — | Soit ajouter la brique manquante à la matrice, soit retirer la ligne |

### B.3 — Annexes (slides 29 à 36)

| # | Page | Le support dit | Le texte dit | Correction |
|---|---|---|---|---|
| B25 | 29 | « redirection automatique » comptée parmi les obstacles interdits | L'Art. 44(1)(k) n'interdit la redirection automatique **que si l'interface dédiée n'expose pas toutes les procédures d'authentification** de l'ASPSP | Rétablir la condition — sans elle, l'annexe fait conclure à l'abandon du modèle redirect |
| B26 | 29 | « trois obstacles nouvellement nommés touchent le serveur d'autorisation » | Au moins six des douze portent sur l'authentification ou l'autorisation : (a), (h), (i), (j), (k), (l) ⚠️ | Le compteur de trois sous-dimensionne la charge SSO |
| B27 | 29 | Transfert des 180 jours à l'AISP | Corrigé depuis la V1, mais l'Art. 86(3) maintient un déclencheur de ré-authentification **sur suspicion de fraude** côté ASPSP, et l'Art. 86(4) laisse l'AISP appliquer **la SCA de l'ASPSP** ⚠️ : la charge n'est pas intégralement transférée | Ajouter les deux réserves |
| B28 | 30 | « 2 ans historique des consentements » | Art. 43(2)(d) : deux ans pour les consentements **retirés ou expirés** (constat V1 N4, non corrigé) | Corriger |
| B29 | 30 | « Quatre durées maximales chiffrées et opposables, assorties d'une obligation de suppression active » | Deux plafonds de conservation (5 ans, Art. 83(2b) et 83a(3)) et deux **planchers de mise à disposition** (2 ans Art. 43(2)(d), 18 mois Art. 53(1)) — les seconds imposent l'inverse d'une suppression | Distinguer les deux régimes : ils appellent des dispositifs opposés |
| B30 | 30 | « preuve de notification pendant 18 mois […] **sans équivalent DSP2** » | La DSP2 (art. 70(1)(c)) porte déjà les 18 mois ⚠️ — à confirmer, le texte DSP2 n'est pas dans le vault | Si confirmé, la seule justification de la cotation de cette brique tombe |
| B31 | 31 | « les non-consommateurs peuvent convenir que la vérification intervienne après l'autorisation » | L'Art. 110c(3)(b) réserve cette faculté aux **canaux d'initiation automatisés dédiés** aux non-consommateurs, pas à tous les non-consommateurs | Restreindre — l'exigence DSP3-EX-253 porte la même approximation |
| B32 | 33 | « rapprochement des fonds cantonnés dont le calcul et la **périodicité** seront précisés par RTS » | Le mandat PSD3 Art. 9(7) couvre « segregation, designation, reconciliation and calculation » ⚠️ — aucune périodicité | Retirer la périodicité |
| B33 | 33 | « La PSD3 **ajoute** la méthode D » | La méthode existe en substance sous la directive monnaie électronique (2009/110/CE, art. 5) ⚠️, absente de la ligne de base de la matrice (constat V1 N3, non corrigé) | Ajouter 2009/110/CE à la ligne de base et ne compter comme delta que le cantonnement |
| B34 | 33 | « normes techniques attendues **douze mois après** l'entrée en vigueur » | Douze mois est la date de **soumission des projets** à la Commission ; le règlement s'applique à 21 mois | « projets soumis à 12 mois, adoption postérieure » |
| B35 | 34 | « notification de refus dans les 10 secondes **et recréditation instantanée** » | Les 10 secondes portent sur la notification au PSP du payeur, pour le **virement instantané uniquement** ; la recréditation est « immediately » (Art. 69(2d)(ii)) et la remise en état « immediately upon receiving the notification » (2e) — constat V1 B3, non corrigé | Dissocier les trois délais |
| B36 | 34 | Cantonnement présenté comme une « interdiction de fait » de concentrer les fonds | PSD3 Art. 9(2) : « **shall endeavour not to** » — obligation de moyens ⚠️. Relève de la PSD3 (transposition, marge nationale) et ne pèse que sur les EP/EME, pas sur les établissements de crédit du Groupe | Requalifier en obligation de moyens et poser le périmètre d'entités |
| B37 | 36 | « support humain gratuit incluant l'assistance à la réalisation de la SCA » | L'Art. 53(1)(c) couvre la notification et le déblocage d'instrument ; l'assistance SCA relève de l'Art. 88(1), sans condition d'horaire ni de langue ⚠️ — constat V1 B4, non corrigé | Dissocier : en l'état l'annexe crée une obligation qui n'existe pas |
| B38 | 36 | Usurpation du numéro appelant portée par le PSP | L'Art. 59a(5) fait peser l'obligation sur les **opérateurs de communications électroniques** ⚠️ ; côté PSP l'Art. 59(-1) impose des garanties techniques sur ses propres canaux | Distinguer les deux : l'un est un levier, l'autre une obligation |
| B39 | 31 | « 9 fonctions d'initiation minimales » | Le support a **raison** (Art. 36(4) énumère neuf points). Ce sont la matrice V2 et la note de DSP3-EX-149 qui portent encore « huit » | **Corriger le vault**, pas la slide |

---

## C. Incohérences internes

| # | Où | Contradiction |
|---|---|---|
| C1 | slide 20 vs annexe 3 vs matrice V2 | La brique API est cotée 2, 1 et 1. Voir A1. |
| C2 | slide 20, disclaimer | La ligne de base annoncée est « DSP2, RTS 2018/389, IPR, RGPD ». La matrice V2 y inclut aussi **DORA**, sur lequel reposent plusieurs cotations à 0 (PCA, SIEM, gestion du risque opérationnel). Un lecteur qui vérifie les briques d'infrastructure ne trouvera pas la justification. |
| C3 | p. 31, chapeau vs corps | Le chapeau dit « Adaptation, pas construction » ; le bullet API dit « ce ne sont pas des paramètres, ce sont des fonctions à construire ». |
| C4 | p. 30, chapeau vs corps | Le chapeau renvoie « les durées de conservation » au RGPD déjà en vigueur ; dix lignes plus bas, ce sont précisément les durées chiffrées qui justifient la cotation de la brique Archivage. |
| C5 | p. 32, chapeau | « Treize briques sur quinze hors périmètre […] **une** exception structurante » : 15 − 13 = 2, et l'annexe commente bien PRA **et** Traçabilité. |
| C6 | p. 34 | La brique Gestion des comptes est la seule commentée sans qualificatif (a) ou (b), alors que la légende de la slide 20 rend ce marqueur obligatoire pour lire le niveau 2. |
| C7 | slides 24 et 25 | **Ordre inversé** : la slide 24 porte le contenu « Next steps », la slide 25 est le bandeau de section « ÉTAPES SUIVANTES » qui devrait le précéder. |
| C8 | slide 22, point 05 | « Publication au JO annoncée pour le **troisième trimestre 2026**, un glissement à **septembre** est évoqué » : septembre est dans le T3. Écrire « glissement à l'automne » ou « au T4 ». |
| C9 | annexes, transverse | Aucune hypothèse ni facteur bloquant n'apparaît, alors que trois hypothèses du vault sont classées ⚫ bloquantes et portent directement sur des briques commentées : **H04** (clause « autre interface » sans critère ni RTS — dépendance : trajectoire API entière), **H10** (preuve de surveillance croisée, dispositif de place inexistant), **H26** (date d'EEV). |
| C10 | matrice V2 (vault) | ⚠️ **Constat corrigé le 2026-08-25.** Les briques CIAM et Usage et Consentement renvoient à « DSP3-H17 » : cet identifiant existait bien, défini dans `exigences/99-annexes.md` par la passe /exigence du 19/08, mais n'avait pas été transféré dans `hypotheses.md`. Il l'est désormais, énoncé resserré sur le registre des consentements et le protocole d'échange avec les tiers (le volet IHM restant porté par DSP3-H03). **Les renvois de la matrice sont valides : rien à corriger.** |
| C11 | nommage, transverse | Le support alterne « DSP3/PSR », « DSP3 » seul et « PSD3 ». La règle du vault est de toujours nommer le paquet « DSP3 / PSR », et le dossier retient « PSD3 » pour la directive. À harmoniser une fois pour toutes, y compris dans les titres de section. |

---

## D. Complétude : ce qui manque

Croisement des 22 domaines fonctionnels du référentiel (711 exigences) avec la couverture du
support. Quatre domaines ne sont pas traités du tout, deux le sont trop peu.

| Domaine du référentiel | Exig. | Couverture | Enjeu |
|---|---:|---|---|
| 12. Fraude — surveillance, partage, reporting | 50 | Bonne | — |
| 13. Authentification forte (SCA) | 36 | Bonne, sous réserve A5 | — |
| 6-8. Open banking (interfaces, consentement, tiers) | 87 | Bonne, sous réserve A6 | — |
| 5. Accès aux systèmes et aux comptes | 18 | Correcte, sous réserve B11-B13 | — |
| 10-11. VoP, responsabilité et remboursement | 79 | Partielle (A3, A4) | Élevé |
| **14. Exécution, délais et dates de valeur** | **43** | **Absente du corps, une ligne en annexe** | **Élevé** |
| **17. Réclamations, litiges et sanctions** | **58** | **Absente** | **Élevé** — voir A7 |
| 18-20. Agrément, fonds propres, transitoire (PSD3) | 163 | Deux lignes slide 12 | Moyen à élevé selon les filiales |
| **3. Frais, tarification, conversion de devises** | **33** | **Un parcours (n°9), rien d'autre** | **Moyen** — sanctionné par l'Art. 97(1)(d) |
| 2. Information et transparence | 35 | Faible | Moyen |
| 21. Monnaie électronique et jetons | 18 | Absente | Moyen — s'applique **dès l'EEV** (Art. 108a) |
| 22. Dispositions finales et calendrier | 11 | Partielle, avec erreurs (A2) | — |

### Les cinq manques à traiter en priorité

**D1 · Ce que le GT attend des entités.** Le manque le plus coûteux, et le seul qui compromette
l'objet de la séance. La slide 24 énumère quatre étapes que **le GT** va conduire. Rien ne demande
quoi que ce soit aux participants : pas d'entité lead à confirmer, pas d'étude à remonter, pas de
référent à nommer, pas de date. Le format validé avec Hatim était « donner le lancement, après
récolte d'informations auprès des sachants » — sans demande explicite, la séance ne récolte rien et
il faudra un GT12 pour poser les questions. **Une slide : ce qu'on demande, à qui, pour quand.**

**D2 · Le volet sanctions.** Voir A7. Deuxième fois qu'il est signalé.

**D3 · Le volet PSD3 et les filiales.** Le support consacre deux lignes à un texte de 50 articles et
163 exigences. Les établissements de crédit du Groupe ne sont pas concernés par l'agrément — c'est
justement ce qui rend le sujet lisible : **seules les entités agréées PI ou EMI portent le
réexamen d'agrément**, avec une fenêtre de redocumentation, un capital initial recalibré et un
cantonnement renforcé. Une slide qui dit qui est concerné et qui ne l'est pas évite que chaque
entité se pose la question seule. Sujet de DSP3-H21.

**D4 · Cinq exigences structurantes du référentiel, absentes et porteuses d'impact SI.**

| Exigence | Article | Pourquoi ça compte pour l'IT |
|---|---|---|
| Clause « autre interface sûre et efficace » remplaçant le fallback | Art. 45(1) | La slide 16 annonce la disparition du mécanisme de secours des RTS 2018 comme un durcissement. Le texte lui substitue une clause **sans critère ni RTS**. C'est l'hypothèse H04, classée bloquante, et elle conditionne toute la trajectoire API. Le support présente une contrainte là où il y a une zone grise. |
| Preuve de surveillance croisée entre PSP | Art. 83(1a) | Le PSP du payeur rembourse s'il ne peut prouver que **les deux** PSP ont surveillé, sans qu'aucun véhicule d'échange de cette preuve existe. Seul cas du texte où un PSP répond du manquement d'un autre hors lien contractuel. Présent en annexe, absent du corps. H10, bloquante. |
| Double étage de blocage anti-fraude | Art. 69, 83 | Suspension côté payeur **et** retour de fonds côté bénéficiaire quand les motifs sont clairs et incontestables, charge de la preuve inversée. Deux dispositifs à construire, sur deux SI différents. |
| Délais d'exécution et dates de valeur | Art. 64 à 73 | 43 exigences, aucune slide. C'est le domaine qui touche le cœur des chaînes de paiement. |
| Régime applicable dès l'entrée en vigueur | Art. 85a, 108a | Exemption des virements récurrents et volet jetons de monnaie électronique : le seul délai qui ne laisse aucune marge. |

**D5 · Un glossaire.** PSP, ASPSP, AISP, PISP, SCA, VoP, RTS, ITS, EBA, FRAND, EP, EME, IPR, DMA,
DSA sont employés sans définition. Signalé en V1, non traité. Une demi-slide en annexe.

---

## E. Lisibilité et forme

**Ce qui ne passera pas en projection.** Le support est calibré pour la lecture à l'écran, pas pour
une séance. Trois pages sont hors gabarit :

- **slide 18** — neuf vignettes de quatre lignes, soit la page la plus dense du support. Personne
  ne la lira en séance. Le format validé avec Hatim était « une dizaine de slides de
  vulgarisation ». **Garder trois ou quatre parcours en séance, les neuf en annexe.**
- **slide 20** — 73 cellules et une légende à trois niveaux dont le niveau 2 porte une
  sous-codification (a)/(b). Le décodage demandé est disproportionné pour une slide de cadrage.
  **Garder le coloriage, sortir la distinction (a)/(b) vers les annexes.**
- **slides 14 à 17** — 600 à 700 mots chacune. Le format à trois colonnes sauve la lecture, mais
  les pieds de slide en corps 6 sont illisibles au vidéoprojecteur. **Excellent réflexe de
  traçabilité, mauvais emplacement** : les basculer sur une page de sources en annexe, une par axe.

**Ce qui se corrige en dix minutes.**

| Page | Point |
|---|---|
| 24-25 | Ordre des slides inversé (C7) |
| 23 | « cinq domaines » au-dessus de six lignes (B23) |
| 22 | « T3 2026 » puis « glissement à septembre » (C8) |
| 29-36 | Ajouter une pastille de couleur devant chaque nom de brique, pour que le niveau se lise sans chercher le qualificatif dans le corps du texte (constat V1 D7, non corrigé) |
| transverse | Harmoniser DSP3/PSR — PSD3 (C11) |
| 5 | Hors périmètre de revue, mais le bandeau « A CONFIRMER » masque trois lignes de la roadmap, dont un texte entier |

**Un mot sur la légende.** « (0) Impact faible / modifications marginales » : la V1 avait demandé
« hors périmètre », parce que « faible » contredit la méthode du delta. La coquille est corrigée, le
libellé pas. Avec la méthode du delta, un 0 signifie « déjà couvert par la ligne de base » — ce qui
est une conclusion, pas une faiblesse d'analyse. Le libellé actuel invite le lecteur à lire une
approximation là où il y a un raisonnement.

---

## F. Ce qui est solide, et qu'il ne faut pas casser en corrigeant

La **structure des quatre slides de domaine** est la meilleure idée du support : trois fronts en
colonnes, trois lignes DSP2 / DSP3-PSR / « pour les entités », un schéma, deux exemples concrets.
La ligne « pour les entités » est exactement ce qu'un GT d'architecture doit produire — la
conséquence, pas la règle. À conserver comme gabarit pour les réglementations suivantes.

Les **neuf parcours** sont une excellente idée pédagogique, mal dosée en séance. Le **focus API**
(slide 21) est la slide la plus utile du support : elle explique qu'une adaptation peut coûter plus
qu'une refonte, ce qui est précisément le message que la cotation en delta rend difficile à faire
passer. Elle est le meilleur argument pour A1, option 1.

La **traçabilité article par article** en pied de slide est très au-dessus de la pratique courante.
La **matrice cotée en delta**, avec une ligne de base explicite et une justification par brique, est
défendable en séance — c'est justement pour ça que l'écart de la slide 20 se remarquera.

Les 31 constats de la section B sont ponctuels. Aucun ne remet en cause la structure ni les
conclusions. Les sept bloquants, si.

---

## G. Plan de correction

| Ordre | Lot | Contenu | Charge |
|---|---|---|---|
| 1 | **Cohérence vault ↔ support** | A1 (recolorier API en 1), C2 (ajouter DORA à la ligne de base), ~~C10~~ (soldé le 25/08 : DSP3-H17 transféré dans `hypotheses.md`, les renvois de la matrice sont valides), B39 (corriger « huit » → « neuf » dans la matrice et DSP3-EX-149) | 45 min |
| 2 | **Les cinq citations bloquantes** | A2 calendrier, A3 Art. 59, A4 VoP, A5 Art. 88(2), A6 Art. 43(1) | 3 h |
| 3 | **Les deux slides manquantes** | D1 « ce que le GT attend des entités », A7/D2 sanctions | 2 h |
| 4 | **Les 31 constats de la section B** | Reprise en une passe, en commençant par les cinq régressions de la section 0 | 4 h |
| 5 | **Recalibrage séance** | Slide 18 réduite à 4 parcours, pieds de slide en annexe de sources, ordre 24/25, pastilles de niveau, libellé de légende | 2 h |
| 6 | **Compléments de fond** | D3 volet PSD3 et filiales, D4 les cinq exigences structurantes, D5 glossaire | 4 h |

Les lots 1 à 3 sont le minimum avant diffusion. Le lot 4 est le minimum avant que le support ne
serve de source à un autre livrable.

**Une remarque de méthode pour finir.** Cinq constats de la revue du 19/08 ont survécu à la V2 en
migrant du corps vers les annexes. La cause est mécanique : le texte a été déplacé, pas relu. Avant
la prochaine version, relire les deux revues existantes du support en même temps que le support —
c'est la règle de propagation, et elle vient de coûter cinq erreurs.
