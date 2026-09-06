# GT11 — Registre consolidé des revues de support

> Consolidation du 2026-08-31. Remplace les trois revues successives du support GT11, désormais
> archivées dans `_archive/` : `revue-GT11-slides-7-15.md` (18/08, V0), `revue-GT11-V1-slides-10-28.md`
> (19/08, 32 p.), `revue-GT11-V2-section-dsp3-psr.md` (21/08, 36 p.).
> Les propositions de contenu rédigées en réponse vivent dans
> `propositions-GT11-contenu-dsp3-2026-08-27.md` (P27), qui reste le document de travail actif.
>
> Ce fichier ne rejuge rien : il dit, pour chaque constat encore vivant, où se trouve la réponse
> rédigée et ce qui reste sans réponse.
>
> **Statut d'application vérifié le 31/08** contre `GT11 - Lancement DSP3-PSR - 16092026 V2.pptx`
> (38 planches, transmise par Alex). Voir §8. La pagination a changé : les numéros de planche des
> revues archivées (32 p. puis 36 p.) ne correspondent plus, se repérer par le titre.

## Pourquoi ce registre existe

Cinq constats de la revue V1 ont survécu à la V2 en migrant du corps du support vers les annexes :
le texte a été déplacé, pas relu. Trois revues qui se recouvrent rendent cette propagation
impossible à contrôler. D'où un registre unique, et une règle : **avant toute nouvelle version du
support, relire ce registre en même temps que le support.**

Un constat de revue n'est pas une vérité. Le constat C10 de la V2 (« DSP3-H17 n'existe pas ») était
faux, tranché le 25/08 : H17 existait dans `exigences/99-annexes.md` sans avoir été porté au
registre. Vérifier dans le vault avant d'appliquer.

## 1. Bloquants du corps du support

| Réf. | Constat | Réponse rédigée | Reste à faire |
|---|---|---|---|
| V2·A1 | Planche 20 : brique API coloriée niveau 2 alors que la matrice la cote 1 | P27 §3.1 et §5 (planches 20-21) | Trancher, puis ajouter à la légende la distinction nature du changement / charge de travail |
| V2·A2 | Planche 12 : le calendrier annonce deux échéances, il y en a quatre (T+0, T+21, T+27 VoP, T+27 fin du transitoire d'agrément) ; premier mandat EBA à +9 mois ; T1 2029 et non T2 | P27 §5 (planche 12) | Appliquer |
| V2·A3 | Planche 14 : l'Art. 59 présenté en remboursement automatique, alors qu'il pose six conditions cumulatives et deux exclusions | P27 §5 (planche 14) et §2 (planche 35) | Appliquer |
| V2·A4 | Planche 14 : VoP binaire et rattachée au seul Art. 50 ; le mécanisme est à l'Art. 110c, la responsabilité à l'Art. 57 | P27 §5 (planche 14) | Appliquer |
| V2·A5 | Planche 15 : réserve de l'Art. 88(2) absente | P27 §5 (planche 15) et §1.6 | Appliquer |
| V2·A6 | Planche 16 : tableau de bord Art. 43 présenté comme brique front et en périmètre « toutes autorisations » | ⚠️ **aucune** — P27 §5 (planche 16) ne traite que la disparition du fallback | **Rédiger la correction** : périmètre AIS et PIS récurrents (Art. 43(1)), nature back-office autant que front |
| V2·A7 | Volet sanctions absent du support, signalé priorité 1 dès le 19/08 | P27 §4.6 (planche rédigée) | Intégrer |

## 2. Bloquants ajoutés le 27/08 sur les annexes

Tous ont leur correction rédigée dans P27 §1.1 à §1.11. Rappel des objets, pour ne pas les
redécouvrir : « la parité impose d'auditer chaque écran » est faux (la parité porte sur
disponibilité, performance et information) · « seuils de performance » n'existe pas dans le PSR
(le 5 requêtes / 30 s vient d'EBA/GL/2018/07) · les quatre durées de conservation mélangent deux
plafonds et deux planchers · brique « Conformité (KYC) » non cadrée (l'Art. 32 vise l'accès **des
EP** aux comptes chez un établissement de crédit) · Art. 59(-1) porte un mauvais numéro (c'est
l'Art. 59a(5), débiteur = opérateur télécom) · « la charge de la preuve bascule » est faux, elle y
était déjà (DSP2 art. 72) · trois phrases tronquées à la copie privent deux briques cotées 2 de
leur motif · « huit ou neuf fonctions d'initiation » : la chaîne se contredit, **non arbitrable
sans le PDF du PSR**.

## 3. Régressions V1 non propagées : état au 31/08

| Réf. V1 | Point | Réponse rédigée | Reste à faire |
|---|---|---|---|
| C1 | Volet sanctions | P27 §4.6 | Intégrer |
| C3 | Ce que le GT attend des entités | P27 §4.7 | Intégrer |
| B3 | Confusion notification à 10 s / recréditation (annexe 6) | P27 §2 (planche 31, lignes ESB 10 secondes et recréditation) | Appliquer |
| B4 | Support humain gratuit présenté comme couvrant l'assistance SCA (annexe 6) | ⚠️ **aucune** | **Rédiger la correction** |
| N4 | « 2 ans historique des consentements » au lieu de « consentements retirés ou expirés » (annexe 2) | ⚠️ **aucune** | **Rédiger la correction** |
| D9 | Échéances par front absentes de la planche fraude (+27 mois prévenir, +21 détecter/réparer) | ⚠️ **aucune** | **Rédiger la correction** |

## 4. Manques structurels

- **Les 45 briques cotées 0 ne sont justifiées nulle part** dans l'annexe, alors que c'est le message
  de la planche 20 et la première question qui viendra en séance. Planche proposée en P27 §3.2.
- **Aucune demande adressée aux entités.** Une séance de lancement dont l'objet est de récolter ne
  récolte rien sans demande explicite. Signalé trois fois (V1·C3, V2·D1). Rédigée en P27 §4.7.
- **Chaque planche métier sans conclusion propre** : les planches 34, 35 et 36 portent le même
  message de synthèse. P27 §3.3.
- Lisibilité en projection : planches 18 et 20 illisibles au vidéoprojecteur (V2·E). Planche 18 à
  réduire à quatre parcours.

## 5. Corrections dues dans le vault, en amont du support

Reprises de P27 §6. Ce sont les seules lignes de ce registre qui ne dépendent pas du support.

- [x] **PDF du PSR (ST-8221) redéposé le 31/08** par Alex. Identité contrôlée sur la page de garde
      (8221/26 du 17/04/2026, « payment services in the internal market »), extraction validée à
      **125 articles**. ⚠️ `data.consilium.europa.eu` est hors egress depuis le conteneur comme
      depuis le poste : tout redépôt reste une action manuelle.
- [x] `sources.md` et `_LISEZMOI.md` remis à jour (ils avaient déclaré le PDF présent alors qu'il
      manquait, puis absent alors qu'il est revenu).
- [x] **« Huit ou neuf fonctions d'initiation » tranché le 31/08 sur le texte : neuf.** L'Art. 36(4)
      énumère (a) à (g), puis (ha) et (hc) ; les points (h) et (hb) ont été supprimés au trilogue, ce
      qui explique le comptage à huit. DSP3-EX-149 et la matrice sont recalés. Le support disait déjà
      neuf : rien à corriger côté support.
- [x] Matrice, 31/08 : les 180 jours sont rattachés à l'**art. 10** des RTS 2018/389, tel que modifié
      par le règlement délégué (UE) **2022/2360** (90 → 180 jours, applicable depuis le 25/07/2023),
      et non aux art. 30 à 32. Vérifié sur EUR-Lex. Précision ajoutée par rapport à P27, qui ne citait
      que l'art. 10 sans son texte modificatif.
- [x] Matrice, 31/08 : l'« interdiction de fait » du cantonnement mono-domicilié est remplacée par
      l'obligation de moyens doublement conditionnée réellement portée par PSD3 Art. 9(2)
      (« éviter, lorsque c'est approprié » / « s'efforcer de ne pas »). Vérifié sur le PDF ST-8222.
- [x] Matrice, 31/08 : les **deux obligations à 10 secondes sont dédoublées**, vérifiées sur ST-8221.
      ⚠️ **P27 portait une erreur sur ce point** : l'Art. 65(1) al. 3 fait notifier le refus au payeur
      et met l'information à disposition du **PISP**, et non du PSP du bénéficiaire comme l'écrivait la
      note du 27/08. La seconde obligation, Art. 69(2d)(i), va bien du PSP du bénéficiaire vers le PSP
      du payeur. Point de départ commun : la réception de l'ordre par le PSP du payeur.
- [x] Matrice, 31/08 : le déclencheur de suppression d'un obstacle est corrigé — **l'identification de
      l'obstacle, d'où qu'elle vienne, y compris sur information d'un AISP ou d'un PISP** (Art. 48(1)),
      et non une demande de l'autorité. Reste à corriger côté support, où la formulation subsiste.
- [ ] Matrice : ajouter les trois exigences manquantes — remboursement des prélèvements de 10 à 15
      jours ouvrables (Art. 63(2)), cinématique d'activation d'application mobile rattachée à MFA
      (Art. 51(4a)-(4e)), cinq facteurs de risque minimaux (Art. 83(2b)). Désormais vérifiable sur
      le PDF, non fait.
- [x] `sources.md`, 31/08 : section **« Ligne de base réglementaire »** créée. Neuf textes
      enregistrés — RTS 2018/389 et son modificatif 2022/2360, IPR 2024/886, SEPA 260/2012,
      EBA/GL/2018/07, EBA/GL/2018/05, RGPD 2016/679, DORA 2022/2554, DSA 2022/2065 — chacun avec ce
      qu'il porte dans la chaîne et les cotations qu'il justifie. **PDF de l'IPR déposé** dans
      `reglementations/dsp3/ligne-de-base/`.
- [ ] Ligne de base annoncée sur la planche d'impacts du support : ajouter DORA. **Côté support.**

### Leçon du 31/08 : P27 n'est pas une source

Deux des corrections appliquées ce jour divergent de la note du 27/08 : les 180 jours (P27 citait
l'art. 10 sans son texte modificatif) et le destinataire de la notification de refus à 10 secondes
(P27 écrivait « PSP du bénéficiaire » là où le texte dit « payeur, et information mise à disposition
du PISP »). Appliquer P27 sans revérifier aurait introduit une erreur dans la matrice. **Toute
correction issue de P27 se vérifie sur le PDF avant d'entrer dans le vault.**

## 6. Ce qui est solide, à ne pas casser en corrigeant

- Les quatre planches de domaine (14 à 17) et les neuf parcours (18) : format à trois colonnes avec
  la ligne « pour les entités », exemples concrets. Au-dessus de la pratique courante.
- Les pieds de slide sourcés article par article. Traçabilité jugée excellente en V2, à conserver.
- Le tableau « ce que le texte dit / pourquoi la question se pose / pourquoi c'est difficile » de la
  planche 21, à garder tel quel en amorce.
- Le point C10 est soldé : DSP3-H03 porte le volet IHM et données pivots du tableau de bord, DSP3-H17
  le registre des consentements et le protocole d'échange avec les tiers. **Les renvois H17 de la
  matrice sont valides, rien à corriger.**

## 7. Méthode

- Contrôler le coloriage d'une matrice de briques par analyse des couleurs du rendu (`pdftoppm` puis
  comptage des pixels par teinte), pas à l'œil.
- Les annexes 29 à 36 sont la colonne « delta » de la matrice copiée telle quelle : d'où leur solidité
  factuelle et, en même temps, les trois troncatures relevées le 27/08. Toute correction de la matrice
  doit être répercutée dans l'annexe, et réciproquement.

## 8. État d'application dans le support V2 (38 planches, vérifié le 31/08)

Le support a intégré la grande majorité des corrections du 27/08. Les annexes en particulier sont
largement reprises. Ce qui suit est le reste.

### Traité, à ne pas rouvrir

Annexes : la parité porte sur les données et les statuts exposés et non sur l'iso-fonctionnalité
écran (§1.1) · les quatre durées de conservation sont dédoublées en deux plafonds et deux planchers
(§1.5) · la brique Conformité (KYC) est cadrée sur le compte qu'un EP ouvre chez nous (§1.7) · le
cantonnement est requalifié en obligation de moyens, « non interdiction » (§1.8) · l'usurpation du
numéro affiché est rattachée aux opérateurs télécoms (§1.9) · les six données pivots du tableau de
bord et le raccord H03 / H17 sont en place, avec l'argument de l'Art. 49 (§2) · le cinquième flux
inter-PSP et la preuve de surveillance par les deux PSP sont ajoutés (§2) · le remboursement des
prélèvements de 10 à 15 jours ouvrables est présent (§6.4).

Corps : la distinction nature du changement / charge de travail est explicite, planche 21 et légende
d'annexe (§3.1) · « neuf fonctions » est retenu · douze obstacles nommés, liste non limitative ·
préavis de changement à deux mois · la note « le PSR n'impose aucun standard d'API » est posée ·
la VoP a ses trois issues et son échéance à +27 mois · la réserve de l'Art. 88(2) figure dans les
notes de la planche SCA · les planches STET / Berlin Group et articulations avec les autres textes
sont créées (§4.2, §4.3, §4.4) · les quatre régimes d'application figurent sur la planche des enjeux.

### Bloquants restants

| # | Point | Où | Nature |
|---|---|---|---|
| 1 | **Volet sanctions toujours absent.** Aucune planche, seules deux mentions incidentes (« sanction à la clé », « sanctionnée »). Signalé priorité 1 le 19/08, réitéré le 21/08 et le 27/08. Planche rédigée en P27 §4.6, non intégrée. | — | Manque |
| 2 | **Rien n'est demandé aux entités.** La planche « Next steps » décrit ce que le GT va faire. Planche rédigée en P27 §4.7, non intégrée. Pour une séance de lancement dont l'objet est de récolter, c'est le défaut qui compromet l'objectif. | Next steps | Manque |
| 3 | **Calendrier : deux échéances annoncées au lieu de quatre**, et le titre porte « T3 2028 et T2 2029 » alors que le jalon en dessous dit « ≈T1 2029 ». La planche des enjeux, elle, énonce bien les quatre régimes. Contradiction interne entre les deux planches. | Planche calendrier vs planche enjeux | Erreur + incohérence |
| 4 | **« Publication au JO annoncée pour le T3 2026, un glissement à septembre est évoqué en place. »** P27 §5 demandait de remplacer par « aucune date de publication n'est acquise » : le paquet ne figure pas parmi les actes adoptés en plénière de juillet 2026, aucune date de plénière n'est connue. En l'état le support affirme un calendrier qui n'existe pas. | Planche enjeux, point 05 | Erreur |
| 5 | **Tableau de bord des consentements : périmètre « toutes les autorisations »**, alors que l'Art. 43(1) vise les consentements AIS et les consentements PIS couvrant des paiements multiples ou récurrents. Présent au corps comme en annexe. | Planche Open Banking + annexe Données | Erreur de périmètre |
| 6 | **Le même tableau de bord est dit « brique front nouvelle » au corps et « pendant back-office » en annexe.** L'annexe a raison. Le corps sous-estime le chantier d'un facteur important. | Planche Open Banking vs annexe | Incohérence |
| 7 | **« Attendre les RTS pour figer » sur la SCA** est vrai pour les exemptions, faux pour l'accessibilité (Art. 88) et l'activation d'application mobile (Art. 51(4a)-(4e)), qui sont dans le règlement et ne dépendent d'aucun RTS. | Planche de synthèse des domaines | Erreur |

### Imprécisions restantes

- **« Suppression immédiate sur demande de l'autorité »** : le déclencheur est l'identification d'un
  obstacle, d'où qu'elle vienne, y compris sur signalement d'un tiers (Art. 48(1)), pas une demande
  de l'autorité.
- **« Cinq requêtes en échec ou sans réponse sous 30 secondes »** : le seuil vient d'EBA/GL/2018/07,
  pas du PSR. Cité trois fois sans attribution. Idem « la performance est définie par le texte ».
- **« Plusieurs de ces fonctions n'existent dans aucune API du marché français aujourd'hui »** :
  affirmation resserrée depuis le 27/08 mais toujours non sourçable en l'état.
- **« Historique conservé deux ans »** : le texte porte sur les consentements **retirés ou expirés**,
  non sur l'historique de toutes les autorisations. Écart de volumétrie. (Constat V1·N4, non traité.)
- **Ticketing** : les 15 jours ouvrables sont le délai de la décision après investigation ; le
  remboursement lui-même est dû immédiatement et au plus tard fin du jour ouvrable suivant
  (Art. 56(1)). L'articulation manque, la planche laisse croire que le remboursement peut attendre.
- **Planche fraude** : les échéances par front (+27 mois prévenir, +21 détecter et réparer) sont
  toujours absentes, alors que la planche est construite sur les trois fronts. (Constat V1·D9.)
- **Justification des briques cotées 0** : aucune planche d'annexe ne la porte (P27 §3.2 non intégré).
  C'est le message de la planche d'impacts et la première question qui viendra en séance.

## 9. Arbitrages d'Alex du 2026-08-31 — points clos

Ces quatre points ne sont plus des constats de revue. **Ne pas les rouvrir.**

| Point | Arbitrage | Portée |
|---|---|---|
| **Volet sanctions absent** (§8 bloquant 1) | **Écarté du périmètre.** Le régime de sanctions ne relève pas des travaux d'architecture du GT. La planche rédigée en P27 §4.6 reste disponible si un autre porteur en a besoin, elle n'entre pas au support. | Clos |
| **Rien n'est demandé aux entités** (§8 bloquant 2) | **Écarté pour le GT11 : c'est trop tôt.** La séance est une introduction, la demande aux entités viendra à un GT ultérieur. Planche P27 §4.7 conservée pour cette échéance. | Clos pour GT11 |
| **Calendrier à deux échéances / T2 vs T1 2029** (§8 bloquant 3) | **Corrigé par Alex le 31/08** dans le support. | Clos |
| **Brique API coloriée en impact fort** (V2·A1, §8) | **Volontaire et assumé.** L'écart avec la cotation 1 de la matrice n'est pas une erreur : c'est la distinction nature du changement / charge de travail, désormais explicite dans la planche 21 et la légende d'annexe. La cotation de la matrice reste à 1, le coloriage du support à 2, et les deux sont justes. Contrôle du coloriage par analyse de teintes devenu inutile. | Clos |

### Point 4 du §8 — formulation retenue

Le point « publication au JO annoncée pour le T3 2026, un glissement à septembre est évoqué en place »
est à remplacer. Statut vérifié le **31/08/2026** : fiche EP Legislative Train à jour au 22/05/2026,
statut « close to adoption ». Restent le vote en plénière, l'adoption formelle par le Conseil, la
signature et la publication au JOUE. **Aucune date de plénière n'est annoncée.** Le « T3 2026 » est
une attente de place, le « glissement à septembre » n'est sourçable nulle part.

**Formulation retenue par Alex le 31/08, en place dans le support :**

> Publication au Journal officiel attendue au second semestre 2026, mais rien n'a bougé depuis mai
> et aucune date annoncée.

Pied de planche à ajouter : *EP Legislative Train, consulté le 31/08/2026 (fiche à jour au
22/05/2026)*.

Deux formulations écartées, pour mémoire : « publication **annoncée** pour le T3 2026 » (attribue une
annonce institutionnelle qui n'existe pas — le T3 est une anticipation de place) et « **stagne** »
(laisse entendre un blocage politique, alors que le dossier a avancé le 05/05 et qu'il ne reste que
des étapes formelles en file d'attente). Le T3 a par ailleurs été écarté comme maille : le GT11 se
tient le 16/09, en plein T3, et l'affirmation aurait été démentie avant le GT12 du 21/10.

⚠️ **Contrainte de cohérence** : si cette formulation est retenue, les jalons absolus de la planche
calendrier (≈T4 2026, ≈T3 2028, ≈T1 2029) doivent porter une mention d'hypothèse, sinon les deux
planches se contredisent.

### Reste ouvert après ces arbitrages

Bloquants : périmètre « toutes les autorisations » du tableau de bord (§8-5), et « brique front »
au corps contre « back-office » en annexe (§8-6). Plus le point 4 ci-dessus, en attente d'intégration.
Les imprécisions du §8 restent entières.
