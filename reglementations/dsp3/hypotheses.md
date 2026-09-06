# Registre d'hypothèses — DSP3 / PSR

> Statuts : 🟡 OUVERTE / 🟢 TRANCHÉE / 🔴 OBSOLÈTE / ⚫ BLOQUANTE. Jamais de suppression.
> Changement de statut = mise à jour + journal.md + alerte sur les DÉPENDANCES.

| ID | Hypothèse | Statut | Source | Dépendances (exigences, briques, conclusions, slides) |
|----|-----------|--------|--------|--------------------------------------------------------|
| DSP3-H01 | *(première hypothèse structurante à instruire en Phase 0 — ex. articulation DSP2 → DSP3/PSR : ce qui est repris à l'identique vs ce qui change, et le périmètre exact des services de paiement du Groupe concernés)* | 🟡 OUVERTE | [SRC: cadrage GT, à dater] | Périmètre de exigences.md ; carto applicative entière |
| DSP3-H02 | Trajectoire de standard d'API open banking : le Groupe est sur **STET** (DSP2) ; la cible de place pour DSP3 serait le **Berlin Group**. Faut-il amorcer la bascule maintenant, ou la préparer pour la réaliser au moment de DSP3 ? Intuition Hatim Benamar : seconde option (bascule anticipée jugée compliquée), à confirmer. ⚠️ Prémisse à instruire : le PSR n'impose **aucun** standard d'API — l'écart STET → exigences PSR (parité de données Art. 37, disponibilité/performance Art. 38, obstacles interdits Art. 44, dashboard de consentements Art. 43) est à combler quel que soit le standard retenu. Argument calendaire en faveur de l'attente : les RTS EBA sur la communication sécurisée (Art. 89(1)) ne sortent qu'à EEV + 12 mois. | 🟡 OUVERTE | [SRC: CR Notion « 24/04 - Atelier DSP2/DSP3 - Codes de retour Open Banking » : pression CNMP sur dépassement de plafond et suspicion de fraude, versions STET de place 1.4.2 / 1.6.2, NOAS utilisé comme code fourre-tout, codes ISO 20022 Berlin Group AM02/AM04/AM18 et F00, ajout de codes sans montée de version jugé faisable] ; [SRC: PSR ST-8221 §Art. 37, §Art. 38, §Art. 43, §Art. 44, §Art. 89(1)] | Exigences open banking (Art. 35 à 48) ; briques carto « socle API » et « dashboard de consentements » ; arbre 1 (mutualisation) |

| DSP3-H03 | Le **tableau de bord de révocation des consentements** (PSR Art. 43) est mutualisable à l'échelle Groupe, plutôt que réimplémenté entité par entité. Trois éléments convergents : BforBank a partiellement initié le chantier de son côté, CASA détient un **catalogue des consentements** dont le volet DSP3 est resté vide faute d'éléments sur les **données pivots communes** aux entités, et le sujet consentement comporte plusieurs facettes (outil, donnée, exposition, dashboard) dont le dashboard n'est qu'une. À instruire : le jeu de données pivots minimal, et le degré de spécificité entité (distributeur vs producteur). | 🟡 OUVERTE | [SRC: synchro Hatim Benamar du 17/08/2026] ; [SRC: PSR ST-8221 §Art. 43] | Exigences open banking (Art. 43) ; brique carto « dashboard de consentements » ; catalogue des consentements CASA ; arbre 1 (mutualisation) ; DSP3-H02 (socle API) |

> ⚠️ DSP3-H01 alimentée le 2026-08-17 sans changement de statut : le diff DSP2 → DSP3 devient instruisible
> (matériel DSP2 du Groupe de 2018, **reçu de Hatim Benamar le 2026-08-24** (DSP3-DSP2-01), et chantier de mise
> en conformité DSP2 en cours côté CAPS et distributeurs, consécutif à un audit à taux de réussite faible).
> Le matériel étant désormais en main, le diff peut être lancé.

> ⚠️ DSP3-H03 enrichie le 2026-08-19 par la passe /exigence, sans changement de statut : le contenu
> obligatoire du tableau de bord est désormais sourcé (DSP3-EX-183 à DSP3-EX-192), dont le rétablissement
> d'un accès révoqué sous **48 heures**, la conservation de l'historique **2 ans**, et les flux
> bidirectionnels avec les prestataires tiers. Ces trois paramètres pèsent sur l'arbitrage make-or-buy.
>
> Répartition arrêtée le 2026-08-25 : **DSP3-H03 porte le volet IHM et données pivots** du tableau de bord,
> **DSP3-H17 porte le registre des consentements et le protocole d'échange avec les tiers** (back-office).
> Les deux se répondent, aucune n'absorbe l'autre. [SRC: arbitrage Alex du 2026-08-25]


> ⚠️ DSP3-H01 alimentée le 2026-08-25 par **DSP3-DSP2-02** (Booster DSP2 de CASA, 25/08/2017), sans
> changement de statut. Le document donne la structure du dispositif DSP2 côté Groupe — gouvernance
> (COPIL « Nouvelle Banque au Quotidien », suivi mensuel CASA, référents par entité), appuis normatifs
> (STET, Normes d'Intégration, principes API Management, Standard SECAPI, MESARI), une brique
> mutualisée (SCAD de CAPS) et un précédent de régime transitoire (« Période transitoire DSP2 »).
> ⚠️ Daté d'avant l'application de la DSP2 : il fixe l'**intention** de 2017, pas l'existant réalisé.
> Le diff DSP2 → DSP3 dispose désormais d'une trame de comparaison, mais l'état 2026 de chacun de ces
> éléments reste à vérifier entité par entité. (cf. Fait n°3)

> ⚠️ DSP3-H02 alimentée le 2026-08-25 : l'ancrage **STET** du Groupe est contemporain de la DSP2
> elle-même, les spécifications interbancaires STET figurant dès août 2017 parmi les quatre appuis
> techniques recommandés aux entités. L'ancienneté de l'ancrage pèse en faveur de l'option « préparer
> la bascule Berlin Group sans l'anticiper », sans la trancher. (cf. F3.3) [SRC: DSP3-DSP2-02 §Technique]

> ⚠️ DSP3-H15 alimentée le 2026-08-25 : le Groupe a déjà mutualisé un service d'authentification sous
> DSP2, le **SCAD porté par CAPS**. Précédent à instruire avant tout arbitrage sur les moyens de SCA
> imposés par l'Art. 88 (plus d'un moyen, au moins un moyen gratuit non dépendant du smartphone).
> ⚠️ Statut 2026 du SCAD inconnu. (cf. F3.2) [SRC: DSP3-DSP2-02 §Technique]

## Hypothèses issues de la passe /exigence du 2026-08-19

> Suivies activement : elles conditionnent une décision d'architecture, de mutualisation ou de chiffrage
> que le GT doit éclairer. Les autres sont en vivier plus bas, réactivables sur déclencheur.

| ID | Hypothèse | Statut | Source | Dépendances |
|----|-----------|--------|--------|-------------|
| DSP3-H04 | Que recouvre la clause « exceptionnellement via une autre interface sûre et efficace » ouverte aux AISP et PISP ? Aucun critère, aucune procédure, aucun mandat de RTS. Est-ce le successeur de fait du fallback des RTS 2018/389, qui disparaît ? | ⚫ BLOQUANTE (aucun critère dans le texte, aucun RTS mandaté) | DSP3-EX-194 [SRC: PSR ST-8221 §Art. 45(1)] | Trajectoire API entière ; chiffrage open banking ; DSP3-H02 |
| DSP3-H07 | Le service de vérification du bénéficiaire est-il porté par une brique mutualisée Groupe ou par entité ? Quel référentiel de noms est exposé (nom commercial, raison sociale, nom complet), et selon quelle logique de concordance approchante ? | 🟡 OUVERTE | DSP3-EX-248, DSP3-EX-149 [SRC: PSR ST-8221 §Art. 50, §Art. 36(4)(g)] | Brique carto « VoP » ; responsabilité Art. 57 ; arbre 1 (mutualisation) |
| DSP3-H08 | L'Art. 50 étend la VoP à tous les virements, y compris hors euro et hors identifiants IBAN. Quel périmètre de devises et d'identifiants uniques le Groupe doit-il couvrir à +27 mois ? | 🟡 OUVERTE | DSP3-EX-248, DSP3-EX-249 [SRC: PSR ST-8221 §Art. 50] | Chiffrage VoP ; capitalisation de l'existant IPR ; DSP3-H07 |
| DSP3-H10 | Comment le PSP du payeur apporte-t-il la preuve que la surveillance des opérations a été effectuée par les deux PSP ? Le texte crée l'obligation de preuve sans en définir le véhicule inter-PSP. | ⚫ BLOQUANTE (facteur exogène : dispositif de place inexistant) | DSP3-EX-350 [SRC: PSR ST-8221 §Art. 83(1a)] | Exposition financière à provisionner ; brique « transaction monitoring » ; DSP3-H11 |
| DSP3-H11 | Le Groupe adhère-t-il à un dispositif de partage d'informations sur la fraude de place, ou construit-il un dispositif intra-Groupe ? Qui porte l'analyse d'impact conjointe imposée avant conclusion ? | 🟡 OUVERTE | DSP3-EX-357, DSP3-EX-362 [SRC: PSR ST-8221 §Art. 83a] | Brique « partage de données de fraude » ; conformité RGPD ; arbre 1 (mutualisation) |
| DSP3-H15 | Quel moyen de SCA non dépendant du smartphone le Groupe maintient-il ou recrée-t-il, et pour quelles populations ? Le texte impose plus d'un moyen et au moins un moyen gratuit adapté. | 🟡 OUVERTE | DSP3-EX-402, DSP3-EX-404, DSP3-EX-405 [SRC: PSR ST-8221 §Art. 88] | Trajectoire de décommissionnement des moyens non mobiles ; briques SCA et parcours clients |
| DSP3-H17 | Le **registre des consentements** côté ASPSP et son protocole d'échange avec les prestataires tiers : brique mutualisée ou par entité ? Le texte impose l'alimentation par les tiers (finalité, période de validité, catégories de données), la resynchronisation dans les deux sens, le rétablissement d'un accès retiré sous 48 heures et la conservation de l'historique des consentements retirés ou expirés pendant 2 ans. Aucun équivalent DSP2 : sous DSP2 l'ASPSP ignore les consentements donnés aux tiers. | 🟡 OUVERTE | DSP3-EX-184, DSP3-EX-188, DSP3-EX-190, DSP3-EX-191 [SRC: PSR ST-8221 §Art. 43] ; transférée depuis `exigences/99-annexes.md` le 2026-08-25 [SRC: arbitrage Alex du 2026-08-25] | Briques carto « CIAM (Consentement) » et « Usage et Consentement » ; DSP3-H03 (volet IHM et données pivots) ; DSP3-H29 ; arbre 2 (make vs buy) |
| DSP3-H21 | Quelles filiales du Groupe sont des établissements de paiement ou de monnaie électronique soumises au nouveau cantonnement (comptes de règlement, risque de concentration, plan de liquidation) ? | 🟡 OUVERTE | DSP3-EX-627 à DSP3-EX-640, DSP3-EX-522 [SRC: PSD3 ST-8222 §Art. 9, §Art. 3(3)(s)] | Périmètre PSD3 ; recouvre partiellement DSP3-H01 |
| DSP3-H25 | L'ouverture FRAND des fonctionnalités matérielles et logicielles des terminaux mobiles crée-t-elle une opportunité de portefeuille ou de paiement sans contact propriétaire pour le Groupe ? | 🟡 OUVERTE | DSP3-EX-406 à DSP3-EX-408 [SRC: PSR ST-8221 §Art. 88a] | Opportunité stratégique ; à croiser avec le DMA (UE) 2022/1925 |
| DSP3-H26 | Sur quelle date d'entrée en vigueur le rétroplanning du GT est-il construit ? Toutes les échéances du compromis sont des placeholders relatifs à une publication au JOUE non datée. | ⚫ BLOQUANTE (facteur exogène : publication au JOUE) | DSP3-EX-711 [SRC: PSR ST-8221 §Art. 112] | Rétroplanning entier ; toutes les slides à échéance datée |

## Vivier, à réactiver sur déclencheur

> Hypothèses sourcées mais non suivies activement : elles dépendent d'un texte de niveau 2 à paraître,
> d'une option nationale, ou relèvent d'un recensement plutôt que d'un arbitrage d'architecture.
> Détail complet dans `exigences/99-annexes.md`.

| ID | Objet | Déclencheur de réactivation |
|----|-------|------------------------------|
| DSP3-H05 | Des entités entrent-elles dans la dérogation d'interface dédiée (Art. 39) ? | Publication des RTS de critères |
| DSP3-H06 | Périmètre des comptes à exposer via l'interface dédiée | Instruction de DSP3-H01 (périmètre) |
| DSP3-H09 | Canaux d'initiation ouvrant l'opt-out VoP aux non-consommateurs | Instruction de DSP3-H07 |
| DSP3-H12 | Politique de traitement des remboursements pour usurpation d'identité | Atelier fraude et risque |
| DSP3-H13 | Paramétrage du délai de 4 heures et ergonomie de l'opt-out | Cinématiques de parcours |
| DSP3-H14 | Recours à la double inhérence pour la SCA | Lignes directrices EBA à +18 mois |
| DSP3-H16 | Politique Groupe d'exemptions de SCA | RTS SCA à +12 mois |
| DSP3-H18 | Refonte du processus d'entrée en relation et de clôture des comptes d'établissements de paiement | Atelier conformité |
| DSP3-H19 | Systèmes et schemes opérés par le Groupe entrant dans le champ de l'Art. 31 | Recensement Phase 0 |
| DSP3-H20 | Options nationales retenues par la France | Transposition PSD3 |
| DSP3-H22 | Plan de redocumentation des agréments existants | Instruction de DSP3-H21 |
| DSP3-H23 | Assiette des sanctions et intégration à la cartographie des risques | Filière risques |
| DSP3-H24 | Cible de reporting de fraude et articulation avec l'existant | RTS et ITS à +12 mois |
| DSP3-H27 | Position sur les IBAN virtuels, y compris au regard du LCB-FT | Clause de revoyure à 3 ans |
| DSP3-H28 | Entités manipulant des jetons de monnaie électronique et régime transitoire Art. 108a | Recensement Phase 0 |

## Questions de démarrage (viviers d'hypothèses, à instancier en Phase 1)
- Quels services de paiement du Groupe entrent dans le périmètre DSP3/PSR ?
- Quels changements SCA / anti-fraude par rapport à DSP2 ? (IBAN/name check, partage de données de fraude)
- Impacts open banking : évolution des API, permission dashboard, suppression du fallback ?
- Jalons calendaires exacts (entrée en vigueur, période de transition) [SRC: à vérifier via /loi]
- RTS/ITS EBA et actes délégués : lesquels, quand, avec quel impact sur les exigences ?

## Hypothèse issue de l'atelier BForBank du 2026-08-24

| ID | Hypothèse | Statut | Source | Dépendances |
|----|-----------|--------|--------|-------------|
| DSP3-H29 | La révocation d'un consentement porte-t-elle sur le seul refresh token, ou également sur les access tokens en cours de validité ? Chez BFB l'access token vit **30 minutes**, le refresh token 6 mois en AISP et 9 mois en PISP : révoquer le seul refresh token laisserait un accès résiduel jusqu'à l'expiration de l'access token, alors que le retrait doit faire cesser l'accès (DSP3-EX-185). ⚠️ **Corrigé le 2026-08-25** : la valeur de 24 heures, retenue depuis la séance du 24/08, est fausse. L'hypothèse reste ouverte, son enjeu se réduit à une fenêtre résiduelle de 30 minutes. Question de conception commune à toutes les entités adossées à un fournisseur d'identité, donc candidate à un pattern Groupe. | 🟡 OUVERTE | [SRC: atelier BForBank du 24/08/2026] ; [SRC: DSP3-ET-02 §2.1, §3.2.3, §3.3] ; [SRC: PSR ST-8221 §Art. 43(2)(b), §Art. 43(2b)] | Brique carto « dashboard de consentements » ; DSP3-H03 ; briques IAM des entités |

> ⚠️ DSP3-H03 alimentée le 2026-08-24 par l'atelier BForBank, sans changement de statut : premier cas
> réel d'entité. Attributs manquants identifiés (identifiant du refresh token en tête), cible
> d'isolement du consentement open banking dans un microservice dédié, contenu du tableau de bord
> sous-estimé par l'entité (déduit d'écrans de concurrents, alors que l'Art. 43(2)(a) impose six
> informations dont les catégories de données partagées et les dates d'accès). Le jeu de données
> pivots minimal devient instruisible à partir d'un cas concret, à croiser avec le catalogue des
> consentements CASA transmis à BFB le 24/08.

> ⚠️ DSP3-H02 alimentée le 2026-08-24 sans changement de statut : BFB expose via WSO2 (AWS vers GCP)
> et n'a retenu ni Kong ni Apigee. La trajectoire de standard n'est pas connue de l'entité, ce qui
> confirme qu'aucune position de place n'est descendue aux entités à date.

> ⚠️ **Point de périmètre ouvert par l'atelier BForBank** (tracé ici, sans hypothèse dédiée) : BFB
> exclut le PISP du champ du tableau de bord au motif que le jeton est technique. Le critère du texte
> est la durée du consentement, non la propriété du jeton : l'Art. 43(1) vise les consentements AIS
> et les consentements PIS couvrant des paiements multiples ou récurrents, et le considérant 65 écarte
> l'initiation de paiement ponctuel. Ces mandats récurrents sont cités au considérant 56 comme service
> d'API premium, donc ouverts par choix commercial. À vérifier avec BFB : leur PISP couvre-t-il des
> mandats récurrents ? Rattaché à DSP3-H03 tant que la réponse n'impose pas d'hypothèse propre.
## Alimentations du 2026-08-25 (contributions BForBank versées : DSP3-ET-02, DSP3-ET-03)

> ⚠️ **DSP3-H29 corrigée et enrichie.** Correction des durées de vie de jetons (30 minutes, non 24 heures), reportée dans l'énoncé.
> L'étude BFB porte par ailleurs **deux conceptions concurrentes** du service de révocation, sans trancher : l'une dans Access Management
> (`DELETE /v1/refresh-token`, simple proxy vers l'endpoint Keycloak `openid-connect/revoke`), l'autre dans le nouveau microservice de consentement
> (`DELETE /v1/tokens/refresh-token` pour le retrait à l'initiative du tiers, `DELETE /v1/tokens/sessions/{refreshSessionId}` pour l'administration technique).
> Élément favorable relevé au passage : la révocation d'un refresh token par Keycloak révoque aussi le consentement de l'utilisateur pour le client OAuth
> correspondant, ce qui aligne la couche IAM sur l'objet métier. [SRC: DSP3-ET-02 §2.1, §3.2.3, §3.3]

> ⚠️ **DSP3-H17 alimentée**, sans changement de statut : premier design d'entité du registre des consentements. BFB sort le consentement open banking
> d'Access Management vers un microservice `open-banking-consent-management` dont les trois domaines d'API (gestion des consentements, échange de jetons,
> espace de partage de données côté client) constituent une première esquisse du protocole. **L'écart avec le texte est structurant** : la cible BFB ne couvre
> ni l'alimentation entrante par les tiers (DSP3-EX-188, DSP3-EX-191), ni le rétablissement d'un accès retiré sous 48 heures (DSP3-EX-184), ni la conservation
> deux ans, ni l'information du tiers en sortie (DSP3-EX-190). Ces obligations restent chez BFB au stade de questions ouvertes ou sont absentes. Le registre
> conçu est un registre des consentements **délivrés par BFB**, non un registre alimenté par les tiers, ce qui pèse sur l'arbitrage make vs buy. [SRC: DSP3-ET-02 §3.2.3]

> ⚠️ **DSP3-H03 alimentée**, sans changement de statut : trois attributs cibles de l'étude BFB sont des candidats directs aux données pivots, `lastAccessedAt`
> et `accessCount` pour les dates de consultation exigées à l'Art. 43(2)(a)(va), `authorizedDataCategories` pour les catégories de données partagées
> (DSP3-EX-184). L'étude ne liste en revanche aucun attribut portant la finalité du consentement ni le compte concerné, deux des six informations dues,
> l'objet ne rattachant le consentement qu'au `userUuid` du client. ⚠️ Maquettes : DSP3-ET-02 les déclare inexistantes et déduit le contenu du tableau de bord
> d'écrans de concurrents, alors que DSP3-ET-03 référence un board Figma « TPP in-app ». À clarifier avec BFB. [SRC: DSP3-ET-02 §3.1, §3.2 ; DSP3-ET-03]

> ⚠️ **DSP3-H02 alimentée**, sans changement de statut : chez BFB, **STET est un composant applicatif** intégré à la gateway WSO2, et non un simple format
> d'échange, ce qui donne une prise concrète à l'évaluation d'une bascule vers le Berlin Group (un composant à reprendre, pas seulement un contrat d'API à
> réécrire). Le référentiel des droits et rôles des TPP est par ailleurs alimenté auprès de **SRC, service allemand**, et non par un fichier européen comme
> retenu en séance. [SRC: DSP3-ET-03]

> ⚠️ **DSP3-H07 et DSP3-H08 alimentées**, sans changement de statut : BFB conduit un chantier d'**intégration de la VoP au parcours PISP**, non identifié
> comme chantier DSP3 par l'entité. C'est le premier existant VoP remonté par une entité, à instruire (périmètre couvert, référentiel de noms exposé, logique
> de concordance approchante). [SRC: DSP3-ET-03]

## Alimentations de l'atelier CATS du 2026-09-03

| ID | Hypothèse | Statut | Source | Dépendances |
|----|-----------|--------|--------|-------------|
| DSP3-H30 | La **restitution des statuts de virement aux prestataires tiers** relève-t-elle d'une interrogation par le tiers ou d'une poussée d'information par l'ASPSP ? CATS identifie l'impact mais n'a pas arrêté la mécanique. Toutes les entités françaises du Groupe étant basées sur les schemes STET, elles exposent les mêmes endpoints : la réponse est donc structurellement commune et candidate à un pattern Groupe plutôt qu'à un choix d'entité. | 🟡 OUVERTE | [SRC: atelier CATS du 03/09/2026] | Exigences open banking (Art. 36, Art. 46) ; brique carto « socle API » ; DSP3-H02 (scheme commun) ; arbre 1 (mutualisation) |

> ⚠️ **DSP3-H02 alimentée le 2026-09-03, statut OUVERTE inchangé, mais l'énoncé change de nature.**
> L'hypothèse est rédigée comme un arbitrage de séquencement (basculer maintenant ou au moment de
> DSP3), sur l'intuition Hatim Benamar. Trois éléments recueillis les 01/09 et 03/09 la déplacent :
> CAPS **milite pour STET** auprès de la place et a produit un papier resté sans retour du B-Comp
> (séance Christel Body du 01/09) ; CATS a rendu un **avis architecture d'impact majeur sans ROI**
> contre une bascule ; et **STET ne fournirait pas de version compatible DSP3 en cas de migration de
> place** (rapporté par Elisa Trolez, à confirmer). Aucun acteur du Groupe ne pousse donc la bascule :
> la question n'est plus « quand basculer » mais « le Groupe soutient-il activement le maintien de
> STET », et l'arbitrage est une décision de place en attente, non un choix d'architecture ouvert au
> GT. **Déclencheur nommé** : le retour de Christel Body et du B-Comp, attendu par CAPS comme par CATS.
> ⚠️ À ne pas confondre avec ce qui n'est **pas** conditionnel : la **montée de version STET est due quoi
> qu'il arrive** (F4.6), et constitue le seul impact open banking chiffrable à date indépendamment de
> l'arbitrage. [SRC: atelier CATS du 03/09/2026 ; séance Christel Body du 01/09/2026]

> ⚠️ **DSP3-H03 alimentée le 2026-09-03**, sans changement de statut : **deuxième design d'entité, de
> sens inverse au premier.** CATS a déjà l'**affichage** des accès TPP en self-care mais pas l'action de
> retrait (F4.4), là où BFB construisait l'objet et le registre avant l'IHM. Le delta Art. 43 n'est
> donc pas le même selon l'entité, ce qui pèse sur la maille de mutualisation : un composant Groupe
> unique servirait mal deux entités dont les manques sont disjoints, alors qu'un **jeu de données
> pivots et un contrat de révocation** partagés serviraient les deux. Le cas CATS porte en outre le
> plus gros volume d'identité du Groupe (xConnect), ce qui lui donne le poids décisif sur ce jeu de
> données. [SRC: atelier CATS du 03/09/2026]

> ⚠️ **DSP3-H01 alimentée le 2026-09-03**, sans changement de statut : **la gouvernance des entités
> n'est pas homogène**, ce qui conditionne la méthode du GT. CATS instruit le sujet tribu par tribu
> sans point d'entrée unique, avec au moins trois tribus dans le champ (F4.1, F4.2), quand BFB a
> désigné un représentant par périmètre. La représentation par périmètre acceptée avec BFB reste donc
> le bon modèle, mais elle suppose côté CATS un arbitrage de leaders qui n'est pas rendu. À noter aussi :
> **CAPS diffuse et traduit déjà le texte aux PO des distributeurs** (F4.3), rôle de fait qui recoupe
> celui du GT et qu'aucune instance n'a attribué. [SRC: atelier CATS du 03/09/2026]
