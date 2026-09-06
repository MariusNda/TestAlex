# Cours DSP3 / PSR : comprendre le paquet, son calendrier et ses enjeux pour le Groupe

> Document de formation interne au GT Architectures Réglementaires. Objectif : rendre le lecteur
> opérationnel pour les ateliers de cadrage (Phase 0). Version du 2026-07-17, établie sur les
> textes de compromis du trilogue du 23/04/2026 (ST-8222 pour PSD3, ST-8221 pour PSR), pré-JO.
> Les impacts Groupe de la section 7 sont des intuitions de cadrage, pas des conclusions du GT.

---

## 1. De DSP1 à DSP3 : pourquoi un nouveau paquet

La directive sur les services de paiement organise depuis 2007 le marché européen des paiements.
DSP1 (2007) a créé le statut d'établissement de paiement et ouvert le marché aux non-banques.
DSP2 (directive (UE) 2015/2366, applicable depuis 2018) a introduit deux ruptures : l'authentification
forte du client (SCA) et l'open banking (obligation pour les banques d'ouvrir l'accès aux comptes
aux prestataires tiers, AISP et PISP). [SRC: PSD3 ST-8222 §Art. 48 (abrogation de la 2015/2366) ; historique DSP1/DSP2 : à sourcer ⚠️]

La revue de DSP2 lancée par la Commission en 2022 a conclu que la directive avait atteint une partie
de ses objectifs mais laissait quatre problèmes ouverts : une fraude qui se déplace vers la
manipulation de la victime (le consommateur autorise lui-même le paiement), un open banking
inégalement mis en œuvre (interfaces de qualité variable, obstacles), des distorsions de concurrence
entre banques et établissements de paiement (accès aux systèmes de paiement, de-risking), et une
application inégale entre États membres du fait de la nature de directive. [SRC: veille web 2026-07-17, exposé des motifs COM(2023) 366/367 ; à consolider via considérants du PSR ⚠️]

La réponse, proposée par la Commission le 28 juin 2023, est un **paquet à deux textes** :

| Texte | Nature juridique | Conséquence |
|-------|------------------|-------------|
| **PSD3** (directive) | Transposée en droit national | Ne conserve que ce qui exige un ancrage national : agrément, supervision, registres. Abroge DSP2 **et** la directive monnaie électronique (EMD2, 2009/110/CE). [SRC: PSD3 ST-8222 §Art. 48] |
| **PSR** (règlement) | Applicable directement, sans transposition | Reprend toutes les règles de conduite : transparence, droits et obligations, SCA, fraude, open banking. Uniformise l'application dans les 27 États. [SRC: PSR ST-8221 §Art. 1] |

Ce basculement directive → règlement est le premier enseignement structurel : l'essentiel du corpus
opérationnel (celui qui touche le SI) devient du droit uniforme, sans marge nationale, avec une date
d'application unique pour toute l'UE.

Second mouvement structurel : la **fusion des régimes**. Les établissements de monnaie électronique
(EMI) disparaissent comme catégorie autonome et deviennent des établissements de paiement émettant
de la monnaie électronique, sous le régime unique de PSD3. [SRC: PSD3 ST-8222 §Art. 2, §Art. 8, §Art. 45 (transitoire EMI) ; §Art. 48 (abrogation EMD2)]

## 2. Où en est la procédure législative (état au 17/07/2026)

| Date | Événement | Statut |
|------|-----------|--------|
| 28/06/2023 | Propositions de la Commission COM(2023) 366 (PSD3) et 367 (PSR) | Fait |
| 2024-2025 | Positions du Parlement (avril 2024) et du Conseil, négociations en trilogue | Fait |
| **23/04/2026** | Accord politique en trilogue ; le COREPER endosse les textes de compromis ST-8222 / ST-8221 | Fait. Ce sont les versions de travail du GT [SRC: sources.md du vault ; veille web 2026-07-17, Arthur Cox, Morrison Foerster] |
| Fin mai 2026 | Vote attendu en plénière du Parlement européen (2e lecture) | Attendu [SRC: veille web 2026-07-17, Norton Rose Fulbright, Morrison Foerster] |
| T3 2026 | Publication au Journal officiel de l'UE, anticipée juin/juillet, glissement possible à septembre | Attendu [SRC: veille web 2026-07-17, Norton Rose Fulbright, Worldline] |
| JO + 20 jours | Entrée en vigueur (EEV) des deux textes | [SRC: PSR ST-8221 §Art. 112 ; PSD3 ST-8222 §Art. 50] |

⚠️ Point de vigilance veille : la publication au JO déclenchera la Règle n°3 du vault (diff
compromis → texte final, remontée de la chaîne). Les dates absolues ci-dessous restent des
projections tant que le JO n'est pas paru.

## 3. Le calendrier d'application : la donnée à retenir absolument

Les délais sont exprimés dans les textes en mois après l'entrée en vigueur (EEV).

| Échéance | Objet | Source |
|----------|-------|--------|
| **EEV** (JO + 20 j, projeté fin 2026) | Application immédiate de l'Art. 85a (SCA sur virements) selon ses modalités et de l'Art. 108a (transitoire tokens de monnaie électronique / MiCA) | [SRC: PSR ST-8221 §Art. 112] |
| **EEV + 12 mois** | L'EBA soumet à la Commission les RTS SCA / sécurité / monitoring (successeurs des RTS SCA de DSP2) | [SRC: PSR ST-8221 §Art. 89(1)] |
| **EEV + 21 mois** (projeté mi/fin 2028) | **Application générale du PSR** ; date limite de transposition **et** d'application de PSD3 ; abrogation de DSP2 et EMD2 | [SRC: PSR ST-8221 §Art. 112 ; PSD3 ST-8222 §Art. 49, §Art. 48] |
| **EEV + 27 mois** (projeté début/mi 2029) | Application des Art. 50 et 57 PSR : vérification du bénéficiaire (VoP) étendue et régime de responsabilité associé ; fin de la fenêtre transitoire de ré-agrément des PI/EMI existants | [SRC: PSR ST-8221 §Art. 112 ; PSD3 ST-8222 §Art. 44, §Art. 45] |
| + 3 mois max | Extension exceptionnelle de la période transitoire d'agrément par l'autorité compétente | [SRC: PSD3 ST-8222 §Art. 45a] |

⚠️ De nombreux commentaires de place citent encore 18 et 24 mois : ce sont les délais de la
proposition 2023. Le compromis d'avril 2026 les a portés à **21 et 27 mois**, texte faisant foi.
[SRC: PSR ST-8221 §Art. 112 ; contre-exemple : veille web 2026-07-17, Worldline]

Lecture opérationnelle : environ deux ans entre aujourd'hui et l'application générale. C'est court
pour des chantiers SI de type refonte d'API ou de moteur de fraude, et c'est précisément la
fenêtre dans laquelle le GT doit produire son cadrage puis son approfondissement (niveau 2).

## 4. PSR : le contenu, domaine par domaine

Le PSR compte 125 articles en 5 titres. [SRC: PSR ST-8221, structure] Les domaines ci-dessous
sont ceux qui portent l'essentiel des impacts SI.

### 4.1 Lutte contre la fraude : le centre de gravité politique du texte

C'est la grande nouveauté par rapport à DSP2, qui ne traitait que la fraude par transaction non
autorisée. Le PSR attaque la fraude par manipulation (le client autorise le paiement sous emprise).

- **Vérification du bénéficiaire (VoP)** : la concordance nom / IBAN, introduite par le règlement
  virements instantanés (IPR, 2024/886) pour les virements SEPA, est étendue mutatis mutandis à
  **tous** les virements, y compris hors périmètre SEPA du règlement 260/2012. En cas d'écart,
  alerte au payeur avant autorisation. [SRC: PSR ST-8221 §Art. 50]
- **Responsabilité en cas de VoP défaillant** : le PSP qui applique mal la vérification de
  concordance porte la perte. [SRC: PSR ST-8221 §Art. 57]
- **Fraude par usurpation d'identité du PSP (spoofing)** : remboursement intégral du consommateur
  manipulé par un tiers se faisant passer pour sa banque via ses canaux de communication, sous
  conditions (notification, plainte, absence de négligence grave). C'est l'article le plus discuté
  du texte, à fort impact provisions et parcours de réclamation. [SRC: PSR ST-8221 §Art. 59]
- **Responsabilité élargie hors PSP** : les prestataires techniques et opérateurs de schemes
  deviennent responsables des défaillances SCA qui leur sont imputables ; coopération
  intersectorielle (télécoms, plateformes) ; obligations des très grandes plateformes en ligne sur
  la publicité de services financiers. [SRC: PSR ST-8221 §Art. 58, §Art. 59a, §Art. 59b]
- **Dispositif industriel anti-fraude** : reporting de fraude aux autorités [SRC: PSR ST-8221 §Art. 82],
  mécanismes de transaction monitoring [SRC: PSR ST-8221 §Art. 83], **partage inter-PSP de données
  de fraude** (IBAN frauduleux, etc.) [SRC: PSR ST-8221 §Art. 83a], plateforme européenne de lutte
  contre la fraude [SRC: PSR ST-8221 §Art. 83b], obligations d'alerte et d'éducation des clients
  [SRC: PSR ST-8221 §Art. 84].

### 4.2 SCA : consolidation et extensions

Le socle DSP2 est repris avec des inflexions notables.

- Exigence SCA maintenue et précisée, y compris sur l'indépendance des éléments ; guidelines EBA
  attendues sur les éléments d'inhérence. [SRC: PSR ST-8221 §Art. 85]
- Régime spécifique pour les virements, dont les virements récurrents, applicable dès l'EEV
  selon ses modalités. [SRC: PSR ST-8221 §Art. 85a, §Art. 112]
- SCA et prestataires d'open banking (PIS/AIS) : clarification de qui applique la SCA et
  suppression des re-authentifications systématiques au profit d'un régime rationalisé.
  [SRC: PSR ST-8221 §Art. 86 ; modalités exactes à instruire en Phase 1 ⚠️]
- Encadrement de l'externalisation de la SCA. [SRC: PSR ST-8221 §Art. 87]
- **Accessibilité de la SCA** : obligation d'offrir au moins une méthode d'authentification ne
  supposant ni smartphone ni compétence numérique élevée. Impact parcours et populations fragiles.
  [SRC: PSR ST-8221 §Art. 88]
- Accès équitable, raisonnable et non discriminatoire aux fonctions des terminaux mobiles (NFC,
  secure elements) pour les PSP. [SRC: PSR ST-8221 §Art. 88a]
- Les RTS SCA de DSP2 sont refondus : nouveaux RTS EBA sur authentification, exemptions, sécurité,
  communication et monitoring, à soumettre sous 12 mois après EEV. [SRC: PSR ST-8221 §Art. 89(1)]

### 4.3 Open banking : durcissement du régime des interfaces

DSP2 imposait l'accès ; le PSR impose la **qualité** de l'accès.

- Interface dédiée (API) obligatoire par défaut pour l'accès aux données de paiement.
  [SRC: PSR ST-8221 §Art. 35, §Art. 36]
- **Parité de données** entre l'interface dédiée et l'interface client : l'API ne peut pas offrir
  moins que la banque en ligne. [SRC: PSR ST-8221 §Art. 37]
- Exigences de disponibilité et de performance, avec statistiques trimestrielles publiées
  (RTS EBA sur le format). [SRC: PSR ST-8221 §Art. 38, §Art. 38(5)]
- Dérogation à l'interface dédiée réservée aux petits acteurs, sur critères EBA (taille, volumes).
  [SRC: PSR ST-8221 §Art. 39]
- **Dashboard de permissions** : chaque ASPSP fournit dans son interface client un tableau de bord
  de suivi et de gestion des consentements d'accès aux données. Brique nouvelle, visible du client.
  [SRC: PSR ST-8221 §Art. 43]
- Liste d'**obstacles interdits** (frictions dans les parcours d'accès TPP). [SRC: PSR ST-8221 §Art. 44]
- Le fallback DSP2 est remplacé : l'usage de l'interface client par les AISP/PISP devient un régime
  encadré en cas d'indisponibilité de l'API. [SRC: PSR ST-8221 §Art. 45 ; contours exacts à instruire ⚠️]
- Obligations spécifiques des ASPSP vis-à-vis des PISP et AISP, et obligations miroirs des TPP.
  [SRC: PSR ST-8221 §Art. 40, §Art. 41, §Art. 46, §Art. 47]

À noter : l'open banking PSR reste cantonné aux comptes de paiement. L'extension aux autres données
financières relève du futur règlement FIDA (open finance), hors périmètre de ce cours.
[SRC: veille web 2026-07-17 ; périmètre FIDA à confirmer en veille ⚠️]

### 4.4 Accès aux systèmes de paiement et aux comptes (level playing field)

- Accès direct des établissements de paiement aux systèmes de paiement désignés, critères
  d'admission objectifs et proportionnés. [SRC: PSR ST-8221 §Art. 31]
- Transparence des pratiques des schemes cartes, processeurs et acquéreurs. [SRC: PSR ST-8221 §Art. 31a]
- **Anti de-risking** : un établissement de crédit qui refuse ou clôture le compte d'un
  établissement de paiement motive sa décision dans un format harmonisé (RTS EBA), avec droit de
  recours. Impact process KYC / conformité des banques teneuses de comptes. [SRC: PSR ST-8221 §Art. 32, §Art. 32(5)]

### 4.5 Transparence et frais

- Titre II : exigences d'information (opérations isolées, contrats-cadres), reprises de DSP2 avec
  ajustements. [SRC: PSR ST-8221 §Titre II, Art. 4 à 26]
- Information renforcée sur les **retraits d'espèces / ATM**, y compris pour les déployeurs d'ATM
  indépendants (statut allégé côté PSD3). [SRC: PSR ST-8221 §Art. 7 ; PSD3 ST-8222 §Art. 38]
- Surcharging : interdiction maintenue de surfacturer les instruments à interchange régulé.
  [SRC: PSR ST-8221 §Art. 28(3)]
- Articulation avec MiCA : régime transitoire pour les transactions en tokens de monnaie
  électronique (EMT). [SRC: PSR ST-8221 §Art. 108a]

### 4.6 Ce que le PSR ne change pas fondamentalement

Exécution des opérations (délais, dates de valeur), protection des fonds en cas d'opération non
autorisée classique (principe du remboursement immédiat), résolution des litiges : le corpus DSP2
est reconduit avec la même économie générale, renuméroté. [SRC: PSR ST-8221 §Titre III chap. 4 et 5, §Art. 56, §Art. 60 ; Annex I (table de correspondance)]

## 5. PSD3 : le contenu (volet agrément et supervision)

50 articles en 4 titres. [SRC: PSD3 ST-8222, structure]

- **Agrément unique d'établissement de paiement**, absorbant les EMI : dossier renforcé (gouvernance,
  sécurité, plan de continuité), RTS EBA sur le contenu des demandes. [SRC: PSD3 ST-8222 §Art. 3, §Art. 13 à 16]
- Capital initial et fonds propres, avec méthode spécifique pour les émetteurs de monnaie
  électronique. [SRC: PSD3 ST-8222 §Art. 5 à 8]
- **Safeguarding** renforcé : cadre de gestion du risque de sauvegarde des fonds clients,
  diversification, RTS EBA. [SRC: PSD3 ST-8222 §Art. 9]
- Registres nationaux et registre central EBA. [SRC: PSD3 ST-8222 §Art. 17, §Art. 18]
- Passeport européen et coopération home/host. [SRC: PSD3 ST-8222 §Art. 30, §Art. 31]
- Exemptions : réseaux limités, AISP (enregistrement simple), cash en magasin sans achat,
  déployeurs d'ATM indépendants. [SRC: PSD3 ST-8222 §Art. 34, §Art. 36, §Art. 37, §Art. 38]
- **Transitoire** : les PI et EMI agréés sous DSP2/EMD2 continuent d'opérer jusqu'à EEV + 27 mois,
  le temps de faire valider la conformité au nouveau régime (pas de ré-agrément complet automatique,
  mais un réexamen). [SRC: PSD3 ST-8222 §Art. 44, §Art. 45, §Art. 45a]

Point clé pour un groupe bancaire : les **établissements de crédit** ne sont pas soumis à
l'agrément PSD3 (ils fournissent des services de paiement au titre de leur agrément bancaire).
Le volet PSD3 les concerne indirectement (registres, de-risking côté PSR) ; l'essentiel de leur
charge vient du PSR. [SRC: PSD3 ST-8222 §Art. 1 et 2 (champ) ; lecture à confirmer en Phase 1 ⚠️]

## 6. La couche EBA : là où le détail va se jouer

Le paquet délègue le paramétrage fin à l'EBA. Les principaux mandats recensés dans les compromis :

| Mandat | Source | Enjeu SI |
|--------|--------|----------|
| RTS SCA, exemptions, communication sécurisée, monitoring (EEV + 12 mois) | [SRC: PSR ST-8221 §Art. 89(1)] | Successeur des RTS 2018/389, cœur des parcours d'authentification |
| Guidelines inhérence / indépendance des facteurs | [SRC: PSR ST-8221 §Art. 85] | Biométrie comportementale, device binding |
| RTS statistiques de performance des API + RTS données de suivi open banking | [SRC: PSR ST-8221 §Art. 38(5), §Art. 48(8)] | Reporting et publication |
| RTS dérogation « pas d'interface dédiée » | [SRC: PSR ST-8221 §Art. 39(2)] | Sans objet pour un grand groupe, structure le marché |
| ITS formats de reporting de fraude | [SRC: PSR ST-8221 §Art. 82(3)] | Chaîne de reporting réglementaire |
| RTS motivation des refus de compte aux PI (de-risking) | [SRC: PSR ST-8221 §Art. 32(5)] | Process conformité banque teneuse de comptes |
| RTS réseaux limités | [SRC: PSR ST-8221 §Art. 2(8)] | Cartes cadeaux, cartes carburant |
| RTS dossier d'agrément, RTS safeguarding, guidelines gouvernance, RTS/ITS registre EBA, RTS coopération home/host | [SRC: PSD3 ST-8222 §Art. 3(5), §Art. 9(7), §Art. 13, §Art. 18(5)(6), §Art. 30/31(5)] | Volet filiales agréées PI/EMI |

Conséquence de méthode pour le GT : la chaîne d'exigences devra distinguer les exigences de niveau 1
(texte, stables dès le JO) des exigences de niveau 2 (RTS/ITS, connues 12 à 18 mois plus tard).
La veille (/veille) doit tracker chaque mandat comme une source à venir.

## 7. Enjeux pour le Groupe Crédit Agricole (intuitions de cadrage, à instruire)

> **Intuitions.** Cette section n'est pas sourcée dans la chaîne : elle liste ce que le GT
> pressent pour orienter les ateliers de cadrage. Chaque point a vocation à devenir hypothèse
> (DSP3-Hnn) ou fait après instruction avec les entités. [SRC: à sourcer ⚠️ (ateliers Phase 0)]

### 7.1 Qui est touché dans le Groupe

Toutes les entités PSP du Groupe seraient concernées par le PSR : banques de détail (Caisses
régionales, LCL, filiales internationales), l'usine de paiement du Groupe, les filiales de
crédit à la consommation et toute entité agréée PI ou EMI (celles-ci étant en plus touchées par
le volet agrément PSD3 et son réexamen sous 27 mois). Le recensement exact des entités et de
leurs statuts d'agrément est le premier livrable de la Phase 0. [SRC: à sourcer ⚠️]

### 7.2 Impacts SI pressentis, par domaine

| Domaine | Impact pressenti | Effet d'aubaine / dépendance |
|---------|------------------|------------------------------|
| VoP étendu à tous les virements | Extension des dispositifs nom/IBAN déjà déployés pour les virements instantanés (IPR, VoP obligatoire depuis octobre 2025) aux autres virements, dont hors SEPA | Capitaliser sur l'existant IPR ; sujet mutualisation Groupe évident |
| Fraude (Art. 59, 83, 83a) | Provisions et parcours de remboursement spoofing ; montée en gamme du transaction monitoring ; interfaces de partage de données de fraude inter-PSP | Candidat naturel à une brique Groupe (moteur + échanges de place) |
| SCA (Art. 85 à 89) | Refonte au fil des nouveaux RTS ; méthode d'authentification sans smartphone à offrir ; device binding | Attendre les RTS pour figer, cadrer dès maintenant les scénarios |
| Open banking (Art. 35 à 48) | Mise à niveau des API DSP2 : parité de données, SLA publiés, dashboard de consentements dans chaque banque en ligne / appli | Le dashboard est une brique front nouvelle par entité, le socle API peut être mutualisé |
| De-risking (Art. 32) | Process et outillage de motivation des refus/clôtures de comptes de PI | Conformité + outillage workflow |
| Monétique / schemes (Art. 31a, 58) | Transparence schemes, responsabilité des prestataires techniques | À instruire avec l'usine monétique |
| ATM (Art. 7 PSR, Art. 38 PSD3) | Information tarifaire aux DAB | Impact limité, à vérifier |
| Canaux / communication client (Art. 59, 84) | Sécurisation des canaux (l'usurpation des canaux de la banque déclenche la responsabilité), campagnes d'éducation | Lien avec les chantiers anti-spoofing télécoms (ex. 33700, à confirmer) |

### 7.3 Articulation avec les autres réglementations du GT

- **IPR (2024/886)** : le VoP instantané est l'acquis sur lequel l'Art. 50 PSR s'appuie ; le diff
  IPR → PSR est une étude ciblée à lancer tôt. [SRC: PSR ST-8221 §Art. 50, renvoi au 260/2012 modifié]
- **DORA** : le volet résilience opérationnelle des PSP est traité par DORA ; le PSR renvoie la
  gestion des risques opérationnels et de sécurité à ce cadre, à vérifier article par article.
  [SRC: PSR ST-8221 §Art. 81 ; à instruire ⚠️]
- **FIDA** : l'open finance prolongera l'open banking PSR au-delà des comptes de paiement ;
  cohérence d'architecture API à anticiper. [SRC: veille ⚠️]
- **MiCA** : transitoire EMT (Art. 108a PSR) et fusion EMI/PI côté PSD3. [SRC: PSR ST-8221 §Art. 108a]
- **AMLR** (autre réglementation active du GT) : croisements sur le KYC des PI (de-risking) et le
  partage de données de fraude vs données AML. [SRC: à instruire ⚠️]

## 8. Préparer les ateliers de cadrage : trame proposée

1. **Périmètre** : recenser les entités PSP du Groupe, leurs statuts (établissement de crédit,
   PI, EMI) et leurs études DSP3 déjà lancées (alimente `sources.md`, instruit DSP3-H01).
2. **Calendrier** : caler le rétroplanning GT sur EEV + 21 / + 27 mois et sur la sortie des RTS
   (EEV + 12 mois), avec un jalon « publication JO » déclencheur du diff Règle n°3 (alimente `journal.md`).
3. **Domaines** : prioriser par couple (impact SI x potentiel de mutualisation). Les trois domaines
   pressentis à plus fort enjeu : fraude/VoP, open banking (dashboard + API), SCA post-RTS.
4. **Questions à trancher tôt** (viviers d'hypothèses, cf. `hypotheses.md`) :
   - Ce qui est reconduit de DSP2 à périmètre constant vs ce qui est nouveau (DSP3-H01).
   - L'existant IPR/VoP couvre-t-il déjà l'Art. 50 PSR, et à quel coût d'extension ?
   - Le dashboard de consentements : brique par entité ou service Groupe ?
   - Les entités PI/EMI du Groupe et la fenêtre de réexamen d'agrément (EEV + 27 mois).
   - Frontière PSR / DORA sur le risque opérationnel (éviter le double traitement).

## 9. Glossaire minimal

| Sigle | Signification | Repère |
|-------|---------------|--------|
| PSP | Payment Service Provider | Toute entité fournissant des services de paiement (banque, PI, EMI) |
| PI / EMI | Payment Institution / Electronic Money Institution | Fusionnés sous PSD3 [SRC: PSD3 ST-8222 §Art. 45] |
| ASPSP | Account Servicing PSP | La banque teneuse de compte, débitrice des obligations open banking |
| AISP / PISP | Account Information / Payment Initiation Service Provider | Les TPP de l'open banking [SRC: PSR ST-8221 §Art. 33 à 48] |
| SCA | Strong Customer Authentication | Authentification à deux facteurs indépendants [SRC: PSR ST-8221 §Art. 85] |
| VoP | Verification of Payee | Concordance nom/IBAN avant virement [SRC: PSR ST-8221 §Art. 50] |
| EEV | Entrée en vigueur | JO + 20 jours [SRC: PSR ST-8221 §Art. 112] |
| RTS / ITS | Regulatory / Implementing Technical Standards | Normes EBA adoptées par la Commission |
| IPR | Instant Payments Regulation (2024/886) | A introduit le VoP pour les virements instantanés |
| EMT | E-Money Token | Token MiCA, transitoire Art. 108a PSR |

---

## Sources externes (veille du 2026-07-17)

- [Norton Rose Fulbright, PSD3 and PSR: from provisional agreement to 2026 readiness](https://www.nortonrosefulbright.com/en/knowledge/publications/cedd39c6/psd3-and-psr-from-provisional-agreement-to-2026-readiness)
- [Morrison Foerster, PSD3 and the PSR: key developments, timeline, action points](https://www.mofo.com/resources/insights/260430-psd3-and-the-payment-services-regulation-key-developments)
- [Arthur Cox, PSD3 and PSR: final compromise texts published](https://www.arthurcox.com/insights/psd3-and-psr-final-compromise-texts-published/)
- [Worldline, The scope and timeline are locked in for PSD3 and PSR](https://worldline.com/en/home/main-navigation/resources/blogs/2026/the-scope-and-timeline-are-locked-in-for-psd3-and-psr-what-should-psps-know)
- [Hogan Lovells, Final texts for PSD3 and PSR awaited](https://www.hoganlovells.com/en/publications/final-texts-for-psd3-and-psr-awaited-as-european-parliament-and-council-of-eu-announce-provisional)

Sources primaires : PDF locaux du vault, `PSD3 - compromis trilogue 2026-04 (ST-8222).pdf` (167 p.)
et `PSR - compromis trilogue 2026-04 (ST-8221).pdf` (431 p.), cf. `sources.md`.

## Points `[SRC: à sourcer ⚠️]` en attente

- Historique DSP1/DSP2 et conclusions de la revue 2022 (à asseoir sur les considérants du PSR).
- Recensement des entités PSP du Groupe et de leurs statuts (ateliers Phase 0).
- Modalités exactes : SCA open banking (Art. 86), régime de secours API (Art. 45), frontière DORA (Art. 81), périmètre FIDA.
- Dispositif anti-spoofing télécoms français (33700) cité en intuition.
