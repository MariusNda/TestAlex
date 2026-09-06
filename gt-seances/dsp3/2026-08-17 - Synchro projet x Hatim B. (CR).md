# 17/08 - Synchro projet x Hatim B. (CR)

> Séance : synchro projet bilatérale de mission, 17/08/2026, 17h02, 45 min.
> Type : synchro de pilotage (ni GT plénier, ni atelier entité).
> Périmètre : transverse. La séance traite l'Euro numérique, DSP3/PSR, PCI-DSS, le wallet/eIDAS,
> la feuille de route réglementaire et le cadre contractuel.
> [SRC: enregistrement AI meeting notes Notion « Synchro projet avec Hatim le 17/08 », transcript intégral]
> Arbitrages de relecture validés par Alexandre Linck le 18/08/2026.

## Contexte et participants

| Personne | Entité | Rôle en séance |
|----------|--------|----------------|
| Hatim Benamar | CASA (TEC/ADA) | Architecte d'entreprise Groupe, référent de mission |
| Alexandre Linck | NDA Partners | Livraison GT Architectures Réglementaires |

Première synchro depuis le cadrage du 14/08. Elle balaie l'ensemble des chantiers du GT, pas la seule
réglementation active. Les points DSP3/PSR sont isolés en section 4 pour alimenter le dossier du vault.

## 1. Synthèse exécutive Euro numérique : préparation du passage en CAEG

- Un relecteur juge l'argument de coût de la synthèse peu crédible : l'ordre de grandeur avancé, plusieurs
  milliers de jours-homme, est une projection sur une banque unique, or les impacts diffèrent d'un
  établissement à l'autre. La moyenne obtenue peut s'éloigner fortement de la réalité et desservir le
  dossier au lieu de le servir. ⚠️ [attribution à confirmer : le relecteur n'est pas nommé]
- Position de Hatim Benamar : conserver l'argument mais l'utiliser prudemment, en le présentant de façon
  isolée comme une projection européenne, non comme un chiffrage Groupe. Il porte cette reprise.
- Levier retenu à l'inverse : l'approche MVP. Elle installe une progressivité, montre que le sujet n'est
  pas « tout ou rien » et encourage un engagement rapide des entités.
- Traduction demandée, portée par Alexandre Linck : une slide qui rappelle le périmètre et les échéances
  du MVP de la BCE, puis déduit un rythme de mise en conformité Groupe en trajectoire parallèle au pilote.
- Cible de diffusion : première présentation en **CAEG** (Comité Architecture d'Entreprise Groupe) avec
  Marc ⚠️ [nom de famille à confirmer]. Socialisation interne ADA au préalable, notamment auprès de
  Jérôme et Bertrand ⚠️ [noms de famille à confirmer], puis arbitrage sur une remontée au Comex.
  La V2 de la synthèse et son passage en CAEG sont portés par Hatim Benamar.

## 2. Feuille de route réglementaire et capacité à faire

- Trois réglementations sont engagées et non arbitrables : « URN » ⚠️ [libellé à confirmer, l'euro
  numérique est l'hypothèse la plus probable], « Ordre Digital » ⚠️ [libellé à confirmer] et DSP3.
- Tout ajout au-delà de ces trois textes relève d'une négociation de charge, conduite directement avec
  Bertrand, sur la base de propositions chiffrées.
- Articulation des priorités, telle que décrite par Hatim Benamar : le GT Partage porte le corpus
  réglementaire et fixe le **premier niveau de priorité**, sept à dix textes jugés urgents. L'équipe
  architecture applique un **second niveau** selon les impacts pressentis, après une étude de premier
  niveau (chronophage ou non, impactant ou non, à approfondir ou non).
- Format de sortie attendu : une feuille de route glissante sur trois à quatre mois, tenue à jour en
  continu. Une première version existe et reste à affiner, sans échéance arrêtée en séance.
- Constat partagé : l'effectif actuel ne permet pas de traiter plus que les trois textes prioritaires.

## 3. Cadre contractuel et renforcement

- Le contrat NDA Partners court jusqu'à fin décembre 2026, conformément à l'appel d'offres initial.
- Une extension sans nouvel appel d'offres est envisageable si le dépassement d'enveloppe reste sous un
  certain seuil. Deux vérifications conditionnent la piste : l'appel d'offres d'origine prévoyait-il une
  extension, et quel seuil les achats acceptent-ils. ⚠️ [SRC: à sourcer, seuil non chiffré en séance]
- Un nouvel appel d'offres est à initier vers novembre 2026 pour la période postérieure à décembre.
- Hatim Benamar porte l'ensemble du sujet auprès de Bertrand, dès le 18/08 au matin, sous l'angle du
  besoin de renforcement et de la démarche architecture. La nature du renfort reste ouverte : appui sur
  l'architecture réglementaire, voire sur d'autres sujets qu'il traite directement. Aucune hypothèse
  n'est arrêtée à ce stade. Le suivi côté GT consiste à recueillir le retour de ce point.

## 4. DSP3 / PSR : préparation du GT11 et ouverture des contacts

- **Cycle de GT confirmé.** Le repositionnement des séances à intervalle d'un mois à partir du 16/09 est
  validé par Hatim Benamar. Le cycle arrêté le 14/08 est donc maintenu : **GT11 le 16/09**, GT12 le 21/10,
  GT13 le 18/11, GT14 le 16/12. La numérotation se poursuit après le GT10 de restitution finale €N (08/07).
- **Format du GT11 validé.** Une introduction DSP3 sur le modèle de l'introduction Euro numérique, une
  dizaine de slides de vulgarisation : pourquoi DSP3 arrive, ce qu'elle corrige par rapport à DSP1 et
  DSP2, premiers pressentiments d'impact, RTS attendus et calendrier de sortie. Objectif de la séance :
  donner le lancement, après avoir récolté un maximum d'informations auprès des sachants.
- **Matériel DSP2 du Groupe.** Des travaux DSP2 de 2018 sont archivés sur SharePoint. Hatim Benamar les
  partagera, sur demande. Ils constituent la base du diff DSP2 → DSP3 attendu par DSP3-H01.
- **CAPS, volet métier.** Christel Body est l'interlocutrice métier CAPS sur DSP3. Hatim Benamar a été
  désigné interlocuteur CASA architecture sur le sujet par son responsable. Il a de son côté un
  rendez-vous calé avec elle en septembre, « à la sortie des RTS » ⚠️ [jalon à requalifier : la veille du
  17/08 établit qu'aucun RTS n'est attendu avant EEV+12 mois].
  Alexandre Linck organise **son propre point** avec Christel Body, pour préparer DSP3 et présenter la
  démarche du GT. Ce point relève de l'initiative du GT et n'est conditionné par aucune sortie de RTS.
  - À date, le sujet ouvert avec elle porte sur **DSP2**, non sur DSP3 : une mise en conformité consécutive
    à un audit ayant remonté un taux de réussite faible, qui touche les distributeurs. Hatim Benamar a
    amorcé les travaux avec eux. ⚠️ [entités concernées à confirmer, transcript peu audible]
  - Modèle de collaboration attendu par CAPS : celui pratiqué avec l'AEG à l'époque de Marc et de
    Pierre Pujol, désormais à la retraite, à savoir un cadrage des travaux d'architecture entre entités.
  - Angle de la rencontre de septembre : présenter la démarche du GT, y intégrer les attendus de CAPS,
    et qualifier le delta DSP2 → DSP3 ainsi que les spécificités et complexités du texte, dont
    l'ouverture éventuelle vers l'Open Finance.
- **BforBank, point d'entrée identifié.** Antoine Petit a répondu à la demande d'état des lieux
  réglementaire. Un seul chantier DSP3 en ressort, issu d'une recherche sur leur Confluence : un projet
  partiellement initié pour répondre à l'obligation de tableau de bord de révocation des consentements.
  L'accès au Confluence est ouvert. Benjamin Hennig serait l'architecte porteur de l'étude, à confirmer
  auprès d'Antoine Petit avant d'organiser un atelier. ⚠️ [rôle de Benjamin Hennig à confirmer]
  Les deux objectifs, exploiter l'étude et ouvrir le contact, sont à calibrer ensemble.
- **Lien avec le catalogue des consentements.** Hatim Benamar a produit ce catalogue il y a quelques mois.
  Le volet DSP3 y a été laissé incomplet, faute d'éléments suffisants sur les données pivots communes aux
  entités qui doivent entrer dans un consentement. Le sujet consentement comporte plusieurs facettes,
  l'outil, la donnée, l'exposition, et le tableau de bord n'en couvre qu'une.

## 5. PCI-DSS : un livrable CAPS devenu livrable Groupe

- Le livrable PCI-DSS est en V2, la V1 datant de quelques mois. La V2 intègre des cas d'usage CTS et se
  transforme en livrable Groupe, sous forme de patterns d'exposition des données cartes, là où la V1
  restait interne à CAPS.
- Le GT est valideur : une séance de validation est à tenir avant la présentation en séance GT.
- Parties prenantes citées : Christophe Sali ⚠️ [orthographe à confirmer, l'annuaire porte
  « Christophe Salehi », CAPS], Alban Saunier (sécurité) et Philippe Ducourtieu (architecture CAPS).
  Zainab est également mentionnée comme ayant travaillé avec eux ⚠️ [nom complet et rôle à préciser].
- Demande parallèle de l'équipe CIR : étendre les standards de sécurité, les patterns PCI-DSS, à
  l'ensemble de l'entreprise pour tout ce qui touche aux données cartes. Conséquence : la cohérence entre
  le livrable PCI-DSS et le livrable CFP est à assurer, les deux documents devant renvoyer l'un à l'autre.
- **Réalisé au 18/08** : la demande de mise dans la boucle des ateliers de préparation et l'organisation
  de la séance de validation sont faites.

## 6. Wallet et eIDAS : la Direction Confiance Numérique

- Une Direction Confiance Numérique a été créée. Elle porte le programme eIDAS et wallet ainsi que les
  assets liés à la confiance numérique. ⚠️ [SRC: à sourcer, nom du responsable relevé comme « Osanto »,
  identité et périmètre à confirmer]
- Aucun point n'a encore eu lieu avec elle. Hatim Benamar entend échanger avec la direction de programme
  pour comprendre la démarche, la gouvernance et la place faite à l'architecture, en vue d'une restitution
  au GT suivant. Pas de suivi ouvert côté GT à ce stade.

## 7. Composants récurrents : la piste « constellation »

- Idée de fond, identifiée dès le début de la mission mais jamais instruite faute de recul : certains
  composants d'architecture se situent au carrefour de plusieurs réglementations. Exemples cités :
  API gateway, ID provider, brique de traçabilité et d'observabilité, socle de reporting client.
- Ces composants seraient candidats à devenir des assets ou des offres Groupe, instruits une fois puis
  réutilisés, plutôt que réinventés à chaque texte. Le terme « constellation de composants » circule
  côté Groupe ; Jérôme emploie celui de « building block », que Hatim Benamar ne reprend pas à son compte.
- Portée pour le GT : c'est la manifestation concrète de la mutualisation, qui est la finalité du GT.
  Travail de fond, coûteux en temps, à forte valeur. Aucun engagement de charge pris en séance.

## 8. Organisation des synchros récurrentes

- Les créneaux de 14h15 et 14h30 entrent systématiquement en concurrence avec d'autres points, et les
  points hebdomadaires reprennent en septembre. Ils sont supprimés.
- Les créneaux de 17h15 sont conservés et portés à **45 minutes**, la durée de 15 à 30 minutes s'étant
  révélée insuffisante. Recalage effectué au 18/08.

## Hypothèses évoquées

| ID | Mouvement | Contenu |
|----|-----------|---------|
| DSP3-H01 | alimentée | Le diff DSP2 → DSP3 devient instruisible : matériel DSP2 du Groupe sur SharePoint, et chantier de mise en conformité DSP2 en cours côté CAPS et distributeurs. |
| DSP3-H03 | 🟡 nouvelle | Le tableau de bord de révocation des consentements (PSR Art. 43) est mutualisable à l'échelle Groupe. Trois éléments convergents : BforBank a initié le chantier, CASA détient un catalogue des consentements dont le volet DSP3 est resté vide, et les données pivots communes aux entités ne sont pas définies. |

⚠️ La piste « constellation » de la section 7 n'est pas rattachée à DSP3 : elle est transverse et le vault
n'a pas de registre transverse. Elle est tracée dans le journal DSP3, à réorienter si un registre
transverse est ouvert.

## Actions

| # | Action | Réglementation | Porteur | Échéance |
|---|--------|----------------|---------|----------|
| 1 | Organiser un point avec Christel Body (CAPS, métier) pour préparer DSP3, présenter la démarche du GT et recueillir ses attendus et ceux de CAPS | DSP3/PSR | **Alexandre Linck** | 11/09 |
| 2 | Entrée BforBank : calibrer ensemble l'exploitation de l'étude Confluence (dashboard de révocation des consentements, DSP3-ET-02) et la confirmation de Benjamin Hennig auprès d'Antoine Petit, avant l'atelier | DSP3/PSR | **Alexandre Linck** | 04/09 |
| 3 | Demander à Hatim Benamar le matériel DSP2 du Groupe (2018, SharePoint), base du diff DSP2 → DSP3 | DSP3/PSR | **Alexandre Linck** | 28/08 |
| 4 | Préparer l'introduction DSP3 du GT11, sur le modèle de l'introduction Euro numérique | DSP3/PSR | **Alexandre Linck** | 11/09 |
| 5 | Préparer la slide MVP de la synthèse exécutive : périmètre et échéances du MVP de la BCE, rythme de mise en conformité Groupe en trajectoire parallèle | €N | **Alexandre Linck** | 28/08 |
| 6 | Retravailler l'argument de coût pour le présenter isolément comme projection européenne | €N | Hatim Benamar | 28/08 |
| 7 | Finaliser la V2 de la synthèse, la socialiser en interne (Jérôme, Bertrand) puis la présenter en CAEG avec Marc | €N | Hatim Benamar | 30/09 |
| 8 | Recueillir le retour du point de Hatim Benamar avec Bertrand : renforcement, cadre contractuel, démarche architecture et charges supplémentaires | Transverse | **Alexandre Linck** | 21/08 |
| 9 | Caler le point avec Leticia Tatemoto début septembre, avant le kick-off de la deuxième partie, et récupérer l'invitation du 18/09 | Transverse | **Alexandre Linck** | 04/09 |

Sujets évoqués sans suivi ouvert, par arbitrage du 18/08 : vérification du seuil d'extension auprès des
achats, initiation du nouvel appel d'offres de novembre, affinage de la feuille de route glissante, point
avec la Direction Confiance Numérique, instruction de la piste constellation. Le cycle de GT reste couvert
par l'action transverse du 14/08.

## Prochaine séance

Synchro suivante sur le créneau de 17h15, format 45 minutes. Attendu à cette échéance : la V2 de la
synthèse exécutive, et si la bande passante le permet, un premier retour sur le programme wallet.
Prochain GT : **GT11, mercredi 16/09/2026**.

## Points à sourcer ou à confirmer

- ⚠️ [SRC: à sourcer] Seuil d'enveloppe autorisant une extension de contrat sans appel d'offres.
- ⚠️ [SRC: à sourcer] Responsable de la Direction Confiance Numérique, relevé comme « Osanto ».
- ⚠️ [attribution à confirmer] Auteur de la critique de l'argument de coût.
- ⚠️ Libellés « URN » et « Ordre Digital » parmi les trois réglementations non arbitrables.
- ⚠️ Noms de famille : Bertrand, Jérôme, Marc, Zainab.
- ⚠️ Orthographe : Christophe Sali ou Christophe Salehi.
- ⚠️ Jalon « sortie des RTS » cité par Hatim Benamar pour son propre rendez-vous de septembre avec
  Christel Body, incompatible avec la veille du 17/08. Sans effet sur le point organisé par le GT.
