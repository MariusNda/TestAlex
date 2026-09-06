# Revue du support GT11 (slides 7 à 15) — vérification réglementaire et recommandations

> Revue du 2026-08-18, sur le support « GT11 - Lancement DSP3-PSR - 16092026.pptx ».
> Vérification faite par lecture directe des PDF de compromis trilogue du 23/04/2026
> (PSD3 ST-8222, PSR ST-8221) déposés dans `reglementations/dsp3/`.
> Structure : (1) corrections bloquantes, (2) blocs de sources par slide, (3) améliorations
> de structure et d'illustration, (4) analyse de préparation au jour J.

---

## 1. CORRECTIONS BLOQUANTES (à traiter avant diffusion)

### 1.1 Erreurs de contenu réglementaire

| # | Slide | Ce qui est écrit | Ce que dit le texte | Correction |
|---|-------|------------------|---------------------|------------|
| C1 | 13 (Open Banking) | « l'Art. 45 interdit ce recours au scraping » | L'Art. 45 s'intitule **« Use of the customer interface by AISPs and PISPs »** : il **organise** cet usage. Le §1 pose l'accès exclusif par interface dédiée « **other than in the circumstances covered by Article 39 or exceptionally via another safe and efficient interface** ». Seul le scraping **sans identification** est proscrit, et par le **considérant 61** (non contraignant), pas par le dispositif. | Remplacer par : « le PSR interdit le scraping anonyme, sans identification du prestataire (considérant 61). L'accès par l'interface client reste possible dans les cas de dérogation de l'Art. 39, sous conditions d'identification, d'authentification et de journalisation (Art. 45(2)). Le mécanisme de fallback des RTS 2018/389 disparaît. » [SRC: PSR ST-8221 §Art. 45, §Art. 39, considérant 61] |
| C2 | 13 | Le disclaimer « ⚠️ Lecture à confirmer avant diffusion, pas encore vérifiée sur le texte source » est **imprimé sur la slide** | Note de travail interne | Supprimer. La vérification est faite (cf. C1). |
| C3 | 11 (VoP) | « partage de données de fraude entre PSP » présenté comme un levier, sans statut | Art. 83a : « Payment service providers **shall participate** in information sharing arrangements » | C'est une **obligation**, pas une faculté. À dire explicitement. |
| C4 | 11 | « remboursement intégral sauf négligence grave prouvée et notification faite dans les délais » | Art. 59(1) pose **quatre conditions cumulatives** : (1) l'utilisateur est un **consommateur**, (2) le tiers s'est fait passer pour **le PSP lui-même**, via ses canaux de communication, (3) notification au PSP sans délai indu, (4) **dépôt de plainte auprès de la police**. Art. 59(2) : le PSP dispose de **15 jours ouvrables** pour rembourser ou motiver son refus. | Ajouter la plainte, les 15 jours ouvrables, et la restriction aux consommateurs. Ce sont les trois points que la salle demandera. |
| C5 | 11 | « l'Art. 50 impose la vérification du bénéficiaire (VoP) avant tout virement » | L'Art. 50 est un **article de renvoi** au règlement (UE) 260/2012 modifié par l'IPR, appliqué *mutatis mutandis* à tous les virements, y compris hors périmètre SEPA. Exclusions : opérations « one-leg » (Art. 2(5)), jetons de monnaie électronique (Art. 67a(3)), opt-out possible pour les **non-consommateurs** (Art. 110c). | Formuler : « étend le dispositif VoP déjà né de l'IPR à tous les virements ». C'est aussi un message rassurant pour les entités : l'existant IPR est capitalisable. |
| C6 | 12 (SCA) | « des exemptions définies par les RTS de 2018 (faible montant, virements récurrents, bénéficiaires de confiance) » | Le PSR **ne reprend aucune de ces exemptions**. L'Art. 85(11) fixe seulement les **critères** des futures exemptions, que l'EBA définira par RTS. Nouveauté : « Exemptions **shall not be mandatory** ». | Reformuler au passé pour DSP2, et préciser que les exemptions actuelles seront **remplacées**, pas reconduites. Impact direct sur les parcours de paiement. |
| C7 | 12 | « l'Art. 88 impose qu'au moins une méthode d'authentification ne dépende pas d'un smartphone » | Art. 88 = **« Accessibility requirements regarding strong customer authentication »**. §1 : au moins un moyen **gratuit** adapté à chaque situation, y compris handicap, âge, faible littératie numérique. §2 : interdiction de dépendre d'un **moyen unique** ou du smartphone, **sauf accord explicite du client** pour un service 100 % mobile, et obligation de **développer plusieurs moyens**. | Élargir : c'est un article d'accessibilité et d'inclusion, plus large que le seul smartphone. |
| C8 | 12 | « l'Art. 85a crée un régime propre aux virements, dont récurrents » | Art. 85a = une **exemption** de SCA pour les virements récurrents initiés par le PSP du payeur, sous **quatre conditions cumulatives**. Applicable **dès l'entrée en vigueur** (Art. 112). | Corriger : c'est une exemption, pas un régime. Et c'est la seule disposition SCA applicable immédiatement. |
| C9 | 13 | « Avec l'Art. 38, la banque doit publier des statistiques trimestrielles » | L'obligation de publication est à l'**Art. 35(5)**. L'Art. 38 porte sur les **seuils d'indisponibilité** (présomption après 5 requêtes en échec ou sans réponse sous 30 secondes, préavis d'un mois pour l'indisponibilité planifiée). | Citer Art. 35(5) pour la publication, Art. 38 pour la disponibilité. |
| C10 | 14 (De-risking) | Art. 31a présenté sous l'axe de-risking | Art. 31a = **« Transparent practices of payment card schemes, processing entities and acquirers »** : transparence **tarifaire** des schemes cartes. | Soit le déplacer vers un axe monétique, soit assumer qu'il s'agit d'un sujet connexe et le dire. |

### 1.2 Erreurs de cohérence interne

| # | Slide | Problème |
|---|-------|----------|
| I1 | 15 | Le titre porte « **PAS ENCORE REMPLI** » et les notes du présentateur décrivent le **DESP, la BCE et un nouveau rail de paiement** : contenu résiduel de l'euro numérique. À remplacer intégralement, sinon lecture publique d'une note hors sujet. |
| I2 | 13 | « **Deux** angles morts » suivi de **trois** puces. |
| I3 | 13 | Le second exemple est titré « **accès mobile** » (copie de la slide SCA) alors qu'il traite du tableau de bord de consentements. |
| I4 | 14 | Le bandeau intermédiaire reprend « Le parcours d'**Open Banking** est maintenant enrichi… » sur une slide de-risking. |
| I5 | 11 | Le chapo annonce **trois** leviers, le corps n'en développe que **deux** (le partage de données de fraude disparaît). |
| I6 | 9 | Titre de la frise « deux échéances à retenir, **mi-2028** et début 2029 », jalons affichés « ≈T3 2028 » et « ≈T2 2029 ». Harmoniser. |
| I7 | 8 | « Mise en place de l'authentification forte du client (SCA) **et du 3DSecure** » : 3-D Secure est un protocole de scheme antérieur à DSP2. DSP2 a imposé la SCA, ce qui a généralisé 3-D Secure v2. Formuler : « qui a généralisé 3-D Secure v2 sur le paiement en ligne par carte ». |
| I8 | 13 | Le schéma affiche « Interface API, Parité, **Art. 37** » : correct, mais le titre du bloc central parle de « fermeture du recours au scraping » sans que le schéma ne le montre. |

---

## 2. BLOCS DE SOURCES PAR SLIDE (à copier en pied de page)

> Convention : `[SRC: <doc> §Art. N]`, conforme à la Règle n°1 du vault.
> Doc = PSR ST-8221 ou PSD3 ST-8222, version compromis trilogue du 23/04/2026.

**Slide 8 (historique DSP1 → DSP2)**
```
Sources : directive 2007/64/CE (DSP1) ; directive (UE) 2015/2366 (DSP2) ; RTS (UE) 2018/389 (SCA) ;
abrogation de DSP2 et de la directive monnaie électronique : PSD3 ST-8222 §Art. 48.
```

**Slide 9 (paquet DSP3/PSR et calendrier)**
```
Sources : PSD3 ST-8222 §Art. 1, 2, 48, 49 (nature, champ, abrogation, transposition) ;
PSR ST-8221 §Art. 1, 112 (application directe ; EEV, +21 mois, +27 mois, Art. 85a et 108a immédiats) ;
§Art. 89(1) (RTS SCA à +12 mois) ; §Art. 38(5) (RTS statistiques à +9 mois) ; §Art. 85(12) (guidelines à +18 mois).
Chiffres de fraude : Banque de France, Observatoire de la sécurité des moyens de paiement, note S1 2025 (27/01/2026).
Statut procédural au 17/08/2026 : texte adopté en commission ECON le 05/05/2026, non publié au JO.
```

**Slide 11 (fraude et VoP)**
```
Sources : PSR ST-8221 §Art. 50 (vérification du bénéficiaire, renvoi au règlement (UE) 260/2012 modifié) ;
§Art. 57 (responsabilité en cas de vérification défaillante) ; §Art. 59 (fraude par usurpation d'identité,
conditions cumulatives et délai de 15 jours ouvrables) ; §Art. 59(-1) (obligation de garanties techniques
anti-usurpation) ; §Art. 83 et 83a (monitoring et partage obligatoire de données de fraude) ;
§Art. 2(5) et 67a(3) (exclusions one-leg et jetons de monnaie électronique) ; §Art. 112 (application à +27 mois).
```

**Slide 12 (SCA)**
```
Sources : PSR ST-8221 §Art. 3(35) (définition de la SCA, facteurs indépendants) ; §Art. 85 (champ élargi
de la SCA) ; §Art. 85(11) (critères des futures exemptions, non obligatoires) ; §Art. 85(12) (double inhérence
sous conditions, guidelines EBA à +18 mois) ; §Art. 85a (exemption pour virements récurrents, applicable
dès l'entrée en vigueur) ; §Art. 87 (externalisation) ; §Art. 88 (accessibilité) ; §Art. 88a (accès aux terminaux
mobiles, sans préjudice du DMA (UE) 2022/1925) ; §Art. 89(1) (nouveaux RTS à +12 mois).
```

**Slide 13 (open banking)**
```
Sources : PSR ST-8221 §Art. 35 (interface dédiée) et §Art. 35(5) (statistiques trimestrielles publiées) ;
§Art. 36 (données et fonctions exposées) ; §Art. 37 (parité de données) ; §Art. 38 (disponibilité et performance,
seuils d'indisponibilité) ; §Art. 39 (dérogation d'interface dédiée) ; §Art. 43 (tableau de bord de consentements) ;
§Art. 44 (obstacles interdits, liste non exhaustive de 12 points) ; §Art. 45 (usage encadré de l'interface client) ;
considérant 61 (interdiction du scraping sans identification).
```

**Slide 14 (accès aux systèmes et comptes)**
```
Sources : PSR ST-8221 §Art. 31 (accès aux systèmes de paiement, interdiction de discriminer sur le statut
institutionnel) ; §Art. 32 (fourniture de comptes aux établissements de paiement : motifs de refus limitatifs,
motivation sous un mois, préavis de clôture de quatre mois, droit de recours) ; §Art. 32(5) (format harmonisé,
RTS EBA à +12 mois) ; §Art. 31a (transparence tarifaire des schemes cartes, acte délégué à +15 mois).
```

**Slide 15 (matrice SI)**
```
Sources : matrice de capacités SI CASA ; cotations issues de PSR ST-8221 §Art. 35 à 48, 50, 57, 59, 82, 83, 83a,
85 à 89 et PSD3 ST-8222 §Art. 32. Intuitions de cadrage du GT, à confirmer en atelier avec les entités.
```

---

## 3. AMÉLIORATIONS DE STRUCTURE ET D'ILLUSTRATION

### 3.1 Problème transverse : la densité textuelle du bloc « angles morts »

Sur les quatre slides d'axes, le bloc central est un pavé de six à huit lignes en petits caractères.
Un public novice ne le lira pas pendant que l'orateur parle. Deux options :

- **Option tableau** (recommandée) : deux colonnes « Avant, DSP2 » et « Après, DSP3/PSR », une ligne par
  angle mort, une phrase de dix mots maximum par cellule. Le détail passe en notes du présentateur.
- **Option pictogramme** : conserver les croix et coches, mais réduire chaque puce à une ligne unique.

### 3.2 Slide 11 (fraude), améliorations proposées

- Le schéma VoP en quatre étapes fonctionne. Ajouter une **branche visuelle** sur l'étape 4 : deux sorties,
  « concordance, virement exécuté » et « écart, alerte au payeur avant confirmation ». Le message
  « le client garde la main » est ce qui rassure la salle.
- Ajouter un **encart chiffré** en haut à droite : « +37 % de fraude par manipulation au S1 2025, 245 M€ »
  avec la source Banque de France. Le chiffre justifie l'axe à lui seul.
- Le troisième levier (partage obligatoire de données de fraude, Art. 83a) mérite une **troisième vignette**
  à côté des deux exemples, ou son retrait du chapo.

### 3.3 Slide 12 (SCA), améliorations proposées

- Le triptyque possession / connaissance / inhérence est bon. Ajouter la mention « **au moins deux,
  de catégories différentes** » en surtitre, et la nouveauté « **deux facteurs d'inhérence possibles
  sous conditions** » (Art. 85(12)) en note, car c'est une vraie inflexion par rapport à DSP2.
- Ajouter un **avant/après visuel** sur l'accessibilité : à gauche un parcours unique par application mobile,
  à droite deux parcours parallèles (application mobile, canal alternatif). C'est la façon la plus rapide
  de faire comprendre l'Art. 88.
- Le champ de la SCA s'est élargi au-delà du paiement (accès au compte, changement de coordonnées,
  hausse de plafond, création d'un instrument tokenisé). Un **bandeau de déclencheurs** serait utile.

### 3.4 Slide 13 (open banking), améliorations proposées

- Le schéma en quatre boîtes alignées ne montre pas la **parité**, qui est le cœur du sujet. Proposition :
  deux chemins parallèles partant de la banque, « interface client » et « interface dédiée », reliés par
  un symbole d'égalité annoté « même données, même performance (Art. 37) ».
- Le tableau de bord de consentements gagne à être montré comme une **maquette d'écran simplifiée**
  (trois lignes : nom du prestataire, données partagées, bouton révoquer). Le texte seul ne le rend pas.
- Le contenu obligatoire du dashboard est très précis dans le texte et parle immédiatement à un public
  novice : nom du prestataire, compte concerné, finalité, période de validité, catégories de données,
  dates de consultation, retrait gratuit à tout moment, rétablissement possible sous 48 heures,
  historique conservé deux ans, interdiction des dark patterns.

### 3.5 Slide 14 (de-risking), améliorations proposées

- Le parcours en quatre boîtes est correct. Ajouter les **délais**, qui sont l'apport concret du texte :
  motivation sous **un mois** après dossier complet, préavis de clôture de **quatre mois**.
- Ajouter les **quatre motifs de refus limitatifs** (infraction à la réglementation anti-blanchiment,
  manquement contractuel substantiel, documents non reçus, agrément refusé ou retiré) : c'est ce qui
  transforme un principe en contrainte opérationnelle pour les entités du Groupe qui tiennent ces comptes.
- Préciser que le Groupe est ici **du côté de la banque teneuse de comptes**, donc débiteur de l'obligation.
  C'est le seul axe où le Groupe subit une contrainte de process plutôt qu'une contrainte de parcours client.

### 3.6 Slide 15 (matrice SI)

- Remplacer le titre « pas encore rempli » et purger les notes du présentateur (contenu euro numérique).
- Appliquer les trois niveaux de couleur et faire figurer la légende.
- Prévoir une **slide d'annexe** avec la justification de chaque brique cotée, une ligne par brique,
  pour tenir la Règle n°1 sans alourdir la slide principale.

---

## 4. ANALYSE DE PRÉPARATION AU JOUR J

### 4.1 Ce qui manque au support pour tenir la promesse « présenter la réglementation »

Le support couvre quatre axes. Le PSR compte cinq titres et le Titre III neuf chapitres. Les manques
significatifs, par ordre de priorité pour un GT d'acculturation :

| Priorité | Domaine absent | Pourquoi il compte | Source |
|----------|----------------|--------------------|--------|
| **1** | **Sanctions** | Jusqu'à **10 % du chiffre d'affaires annuel total**, apprécié au niveau **consolidé de la maison mère ultime** ; 3 M€ pour une personne physique ; ou deux fois le profit tiré. Astreintes de 3 % du CA journalier, six mois maximum. Manquements visés : de-risking, open banking, SCA, transparence tarifaire des DAB, délais de remboursement. | PSR §Art. 96, 97, 98 |
| **2** | **Monitoring et blocage à la réception** | Le PSP du bénéficiaire peut, et doit si les motifs sont incontestables, ne pas mettre les fonds à disposition et les retourner. Monitoring obligatoire **des deux côtés** de l'opération. Impact SI lourd, absent du support. | PSR §Art. 69(2a), 83(1a) |
| **3** | **Fusion des statuts PI/EMI** | Abrogation de la directive monnaie électronique, capital initial recalibré, cantonnement des fonds renforcé, fenêtre de réexamen d'agrément jusqu'à +27 mois. Concerne directement les filiales agréées du Groupe. | PSD3 §Art. 5 à 9, 44, 45, 48 |
| **4** | **Transparence et information client** | Tout le Titre II du PSR, soit vingt-trois articles. Contrats-cadres, information précontractuelle, frais, conversion de devises. Impact certain sur les CGU et les écrans. | PSR §Art. 4 à 26, dont 20 |
| **5** | **Opérations non autorisées et délais de remboursement** | Remboursement au plus tard le jour ouvrable suivant, franchise de 50 €, exonération totale en l'absence de SCA, plafonds paramétrables par le client. Socle DSP2 remanié, structurant pour les réclamations. | PSR §Art. 51, 56, 60 |
| 6 | **Réclamations et litiges** | Réponse sous 15 jours ouvrables, 35 au maximum. Participation obligatoire aux procédures de médiation pour les consommateurs. | PSR §Art. 94, 95 |
| 7 | **Retraits d'espèces** | Cash en magasin sans achat plafonné à 150 €, déployeurs de DAB simplement enregistrés. Sujet d'accès au cash, très parlant. | PSD3 §Art. 37, 38 |
| 8 | **Surcharging et frais** | Interdiction de surfacturer les virements, y compris instantanés, et les prélèvements. | PSR §Art. 28 |
| 9 | **Plateformes en ligne** | Les très grandes plateformes doivent vérifier le numéro d'agrément de tout annonceur de service financier. Convergence PSR et DSA. | PSR §Art. 59a, 59b |
| 10 | **Pouvoir d'intervention produit de l'EBA** | L'EBA peut interdire ou restreindre temporairement un service ou une caractéristique de service, y compris avant commercialisation. | PSR §Art. 104 |

**Recommandation** : ajouter au minimum une slide « **ce que le support ne couvre pas encore** », listant
ces domaines avec leur article. Un GT d'acculturation qui annonce ses angles morts est plus crédible qu'un
GT qui laisse croire à l'exhaustivité. Les sanctions méritent en plus une slide dédiée : c'est l'argument
qui fait bouger les directions.

### 4.2 Ce qui manque au déroulé de séance

- **Une slide de synthèse « ce qu'il faut retenir »** en fin de partie réglementaire, trois à cinq messages.
  Sans elle, la salle sort avec quatre axes non hiérarchisés.
- **Un glossaire** : PSP, ASPSP, AISP, PISP, SCA, VoP, RTS, EBA. Le support les emploie sans les définir.
  Une slide d'annexe suffit.
- **Le statut procédural exact** : le texte n'est pas publié au Journal officiel au 17/08/2026. Toutes les
  dates absolues sont des projections. Une ligne explicite évite un malentendu coûteux.
- **La question de la gouvernance** : l'étude CAPS du 07/07/2026 annonce un comité de pilotage Groupe animé
  par CAPS, avec l'open banking coordonné par CASA/TEC/ARC. L'articulation avec le GT n'est pas définie.
  Le sujet remontera en séance ; mieux vaut l'ouvrir que le subir.
- **L'attendu vis-à-vis des entités** : le support explique la réglementation mais ne dit pas ce que le GT
  demande concrètement aux participants, ni sous quel délai. Une slide « ce qu'on attend de vous »
  avec des échéances datées transforme une présentation en engagement.

### 4.3 Questions probables en séance, et éléments de réponse

| Question attendue | Élément de réponse sourcé |
|---|---|
| « La VoP, on l'a déjà fait pour les virements instantanés, qu'est-ce qui change ? » | L'Art. 50 étend le dispositif de l'IPR à **tous** les virements, y compris hors périmètre SEPA et hors euro. L'existant est capitalisable, le delta porte sur le périmètre, pas sur le mécanisme. |
| « Qui paie en cas de fraude au spoofing ? » | Le PSP rembourse intégralement, sous quatre conditions cumulatives, dans les 15 jours ouvrables. La charge de la preuve de la négligence grave pèse sur le PSP. Limité aux consommateurs. |
| « Le fallback disparaît vraiment ? » | Le mécanisme de fallback des RTS 2018/389 n'existe plus dans le PSR. Il est remplacé par les exigences de disponibilité de l'Art. 38 et le régime encadré de l'Art. 45. |
| « On doit basculer de STET vers Berlin Group ? » | Le PSR n'impose **aucun standard d'API**. Il fixe des propriétés fonctionnelles : parité, performance, dashboard, obstacles interdits. L'arbitrage STET/Berlin Group est une hypothèse ouverte du GT (DSP3-H02), pas une obligation du texte. |
| « Quand exactement ? » | Aucune date certaine : le Journal officiel n'est pas paru. Les délais relatifs sont sourcés, les dates absolues sont des projections. |
| « Combien ça coûte si on ne fait rien ? » | Jusqu'à 10 % du chiffre d'affaires annuel, potentiellement au niveau consolidé du Groupe. |
| « Et l'articulation avec DORA, l'IPR, FIDA, AMLR ? » | Une slide de positionnement serait utile ; à date le sujet est identifié mais non instruit. |

### 4.4 Risques d'animation

- **Densité** : quatre slides d'axes à ce niveau de détail représentent environ dix minutes chacune.
  Vérifier la cohérence avec le temps imparti.
- **Niveau hétérogène** : le support alterne pédagogie de base (les trois facteurs de la SCA) et technicité
  élevée (numéros d'articles dans le corps de texte). Déplacer les références en pied de page libère la
  lecture sans perdre la traçabilité.
- **Notes du présentateur** : celles de la slide 15 portent sur l'euro numérique. À purger avant tout
  partage du fichier, y compris interne.

### 4.5 Suggestion de plan cible

```
Partie 1  Rappel des objectifs du GT (existant, slides 3 à 6)
Partie 2  Comprendre le paquet
          - historique DSP1 → DSP2 (slide 8)
          - le paquet et le calendrier (slide 9)
          - NOUVEAU : glossaire, une slide d'annexe
Partie 3  Les grands axes fonctionnels
          - fraude et VoP (slide 11)
          - SCA (slide 12)
          - open banking (slide 13)
          - accès aux comptes et systèmes (slide 14)
          - NOUVEAU : sanctions, une slide
          - NOUVEAU : ce que le support ne couvre pas encore, une slide
Partie 4  Impacts pressentis sur le SI (slide 15, à compléter)
          - NOUVEAU : justification des cotations, une slide d'annexe
Partie 5  NOUVEAU : ce qu'on attend des entités, avec échéances
          - NOUVEAU : ce qu'il faut retenir, trois à cinq messages
```
