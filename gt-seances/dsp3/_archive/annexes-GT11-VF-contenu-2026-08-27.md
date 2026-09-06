# GT11 — Annexes DSP3 / PSR, contenu VF

> ⚠️ **STATUT AU 2026-08-31 — contenu intégré au support V2, conservé comme trace de rédaction.**
> Les planches 1 à 8 sont reprises dans les annexes du support V2 (38 planches), avec les corrections
> de la passe du 27/08. Deux planches proposées ici ne sont **pas** dans le support :
> « Planche 9 — Les briques hors périmètre », qui reste un manque ouvert (§8 du registre consolidé),
> et « Planche 10 — Ce que le texte sanctionne », **écartée par arbitrage d'Alex du 31/08** (le volet
> sanctions ne relève pas des travaux d'architecture du GT). Ne pas la remettre au support.
> Même réserve de fiabilité que la note de propositions : revérifier sur le PDF avant réemploi.


> Format : 3 à 4 lignes par brique, autoportantes — l'existant, ce que le texte impose, ce que ça change.
> Corrections de la passe de vérification du 27/08/2026 intégrées. Les points encore ouverts sont en
> fin de note, hors texte de slide.

---

## Planche 0 — Comment lire cette matrice *(nouvelle, à garder si le temps le permet)*

**Titre.** « La matrice cote l'écart entre ce que le SI doit déjà porter et ce que le paquet ajoute »

La cotation mesure un **écart**, pas un état d'arrivée : une exigence du PSR qui reconduit le droit en
vigueur — DSP2, normes techniques de 2018, règlement virements instantanés, règlement SEPA, RGPD, DORA —
ne génère aucun impact. C'est ce qui explique que 45 briques sur 73 ressortent à zéro.

**(2) Impact fort** : la fonction n'existe dans aucune entité, ou elle passe d'une obligation de moyens à
une obligation de résultat opposable, mesurée, publiée ou sanctionnée. **(1) Impact modéré** : un
changement attribuable au paquet, absorbé par une brique existante. **(0) Impact faible** : reconduction,
ou effet générique de second ordre.

**La cotation dit la nature du changement, pas la charge.** Une brique cotée 1 peut porter un chantier
lourd si l'adaptation est large — l'interface d'accès aux comptes en est l'exemple. Le chiffrage ne se
déduit pas de la couleur.

**Et le PSR raisonne par rôle**, non par entité : teneur de compte, PSP du payeur, PSP du bénéficiaire,
prestataire tiers. Un article qui s'adresse aux tiers ne coûte rien à une banque teneuse de compte.

---

## Planche 1 — Gestion des identités et accès

**Titre.** « Le PSR ne touche pas l'IAM interne : il touche l'authentification du client, et les accès
qu'il donne à des tiers »

**Chapô.** Sept des onze briques du domaine sont hors périmètre — annuaire, habilitations, certificats,
clés, secrets — parce que l'article 80 du PSR reprend le standard RGPD sans exigence technique propre, et
que DORA porte le reste.

**SSO — (1) adaptation**
Aujourd'hui la banque impose une authentification forte à l'agrégateur tous les 180 jours et maîtrise le
parcours de redirection. Demain elle ne l'applique qu'au **premier accès d'un prestataire donné**,
l'obligation des 180 jours passant au tiers — qui peut appeler l'authentification de la banque (Art. 86).
Trois obstacles interdits visent le serveur d'autorisation : étapes ajoutées, redirection automatique,
double authentification en initiation seule (Art. 44). Le composant reste, ses parcours changent.

**Identités applicatives — (1) adaptation**
La banque vérifie l'agrément d'un tiers en consultant le registre européen, à la main. La DSP3 charge
l'Autorité bancaire européenne d'une **liste centrale lisible par machine** — nom, identifiant, statut
d'agrément — sans délai fixé (Art. 18(7) DSP3). Le contrôle d'accès de l'interface peut consommer ce flux
automatiquement, à condition de ne pas exiger du tiers la preuve du consentement client, ce que l'Art. 44
interdit.

**Authentification forte — (2) changement de régime**
L'authentification s'est bâtie autour du smartphone, sans obligation d'alternative. Le PSR impose **au
moins un moyen gratuit et adapté** aux clients handicapés, âgés ou sans accès numérique, exige d'en
développer plusieurs et interdit de dépendre du smartphone, sauf accord du client (Art. 88). Quatre
déclencheurs sortent du paiement : instrument tokenisé, hausse de plafond, mot de passe, coordonnées
(Art. 85). Les trajectoires de décommissionnement des moyens non mobiles sont à rouvrir.

**Consentement client — (2) capacité nouvelle**
La banque ignore quelles autorisations son client a données aux tiers, et le PSR lui **interdit même de
les vérifier** (Art. 49). Elle doit pourtant les afficher toutes dans un tableau de bord — prestataire,
compte, finalité, validité, catégories de données, dates d'accès — avec retrait gratuit, rétablissement
sous 48 heures et historique de deux ans (Art. 43). Fonction inexistante, et entièrement alimentée par
des tiers.

**Synthèse.** Une création, le tableau de bord des autorisations. Un changement de régime,
l'authentification, qui ne peut plus reposer sur le seul smartphone et se déclenche au-delà du paiement.

*Sources : PSR Art. 43, 44, 49, 80, 85, 86, 88 · DSP3 Art. 18(7) · ligne de base DSP2 art. 15, normes
techniques 2018/389 art. 10 et 30-32, RGPD, DORA.*

---

## Planche 2 — Données

**Titre.** « Le PSR n'invente pas de gouvernance de la donnée : il crée un objet qui n'existe pas, et il
chiffre des durées que le RGPD laissait à notre appréciation »

**Chapô.** Catalogue, qualité, lineage, entrepôt et décisionnel sortent du périmètre : cataloguer,
minimiser et taguer par finalité sont des obligations RGPD préexistantes.

**Applications opérationnelles — (1) adaptation**
La preuve servait la banque. Le PSR crée une preuve produite **au bénéfice du client** : pendant 18 mois,
il peut demander de quoi établir qu'il a bien notifié une perte, un vol ou un usage non autorisé
(Art. 53). Il faut un accusé horodaté, opposable et retrouvable, sur tous les canaux de notification —
téléphone compris.

**Référentiel des noms — (1) adaptation**
Le contrôle nom/IBAN tourne depuis octobre 2025 sur les virements SEPA en euro, au titre du règlement
virements instantanés. Le PSR l'étend à tous les virements de son champ, hors euro compris, et à tout
identifiant unique, **27 mois** après l'entrée en vigueur (Art. 50). Le mécanisme reste dans le règlement
SEPA, avec trois issues dont la concordance approchante. Extension de périmètre d'un service qui existe,
pas un service nouveau.

**Référentiels d'identifiants — (1) adaptation**
L'IBAN virtuel devient un identifiant de compte valide **partout où un IBAN est requis** (Art. 110c). Les
référentiels doivent savoir le qualifier, le relier au compte réel et le faire traverser tous les
contrôles adossés à l'IBAN. La question blanchiment qu'il ouvre est une hypothèse du GT, pas une exigence
du texte.

**Usage et consentement — (2) capacité nouvelle**
Rien n'existe : aucune interface DSP2 ne transporte d'objet consentement partagé. Les tiers devront
transmettre à la banque le contenu de chaque autorisation, tout changement étant **resynchronisé dans les
deux sens**, avec rétablissement sous 48 heures et historique de deux ans (Art. 43). C'est le pendant
back-office du tableau de bord : un référentiel à créer, et un protocole d'échange qui n'existe dans
aucun standard aujourd'hui.

**Archivage et suppression — (1) adaptation**
Le RGPD impose de limiter la conservation sans chiffrer aucune durée. Le PSR en chiffre quatre, **de deux
natures opposées** : supprimer au bout de 5 ans les données de surveillance et celles reçues d'autres PSP
(Art. 83, 83a), mais conserver 2 ans l'historique des autorisations et 18 mois la preuve de notification
(Art. 43, 53). La rétention descend à la maille de l'objet, avec une purge démontrable.

**Synthèse.** Une seule création, le référentiel des autorisations données aux tiers. Le référentiel de
noms sert déjà la vérification du bénéficiaire depuis octobre 2025 : le périmètre s'élargit, la brique ne
change pas de nature.

*Sources : PSR Art. 43, 50, 53, 83, 83a, 110c · ligne de base règlement (UE) 2024/886 et art. 5b-5c du
règlement 260/2012, RGPD, DSP2 art. 72.*

---

## Planche 3 — Intégration et interopérabilité

**Titre.** « Aucune brique nouvelle : l'interface d'accès existe depuis 2019. Ce qui change, c'est le
niveau d'exigence — et il change beaucoup »

**Chapô.** Neuf briques sur treize sont hors périmètre : chiffrement, segmentation, pare-feu,
documentation et catalogue d'API sont déjà couverts par les normes techniques de 2018 et par DORA.

**Bus de messages — (1) adaptation**
Les banques n'échangent aujourd'hui que le message de paiement et ses rejets. Le PSR y ajoute cinq flux
porteurs de motifs et de délais opposables : refus notifié au payeur **et** au PSP du bénéficiaire, retour
de fonds et ses motifs **sous 10 secondes** en instantané, recréditation immédiate, rétablissement du
compte, échanges du dispositif désormais obligatoire de partage sur la fraude (Art. 65, 69, 83a). Un
sixième est exigé sans exister : la preuve que **les deux PSP** ont surveillé l'opération (Art. 83).

**Interface d'accès aux comptes — (1) par nature, chantier le plus lourd par la charge**
L'interface dédiée existe depuis 2019, déjà mesurée et publiée : le PSR ne crée pas la brique, il en
change le contenu et le régime de contrôle. Une liste minimale de fonctions d'initiation devient
obligatoire — ordre permanent, paiement à date future, multi-bénéficiaires, vérification du nom avant
initiation, choix de la méthode d'authentification (Art. 36) ; la performance est définie par le texte et
la parité porte sur les données et les statuts exposés, non sur l'iso-fonctionnalité écran (Art. 35, 37) ;
douze obstacles sont nommés et sanctionnés, le préavis de changement tombe à deux mois, et le mécanisme
de secours de 2018 disparaît sans remplaçant défini (Art. 44, 45).

**Traitements par lots — (1) adaptation**
Les remises en lot passent par des canaux automatisés, sans vérification du bénéficiaire. Les clients
**non-consommateurs** pourront convenir au contrat que la vérification intervienne après l'autorisation,
l'ordre s'exécutant sans intervention dans trois cas seulement, avec renoncement possible sur les canaux
automatisés dédiés (Art. 110c). Une convention contractuelle et un aiguillage à instrumenter dans les
chaînes batch.

**Mesure des interfaces — (1) adaptation**
La banque publie déjà ses statistiques chaque trimestre, avec ses propres définitions. Le texte impose les
indicateurs — requêtes d'information et d'initiation réussies — et ajoute un objectif de rétablissement
gradué selon la sévérité de l'incident, à fixer par norme technique (Art. 35, 38). La mesure existe, sa
définition ne nous appartient plus, et elle devient comparable d'une banque à l'autre.

**Synthèse.** Aucune brique nouvelle : l'interface, sa mesure et sa publication trimestrielle datent des
normes techniques de 2018, en application depuis septembre 2019. Adaptation par nature, refonte par la
charge.

*Sources : PSR Art. 35 à 38, 44, 45, 48, 65, 69, 83, 83a, 110c · ligne de base normes techniques
2018/389 art. 30-32 et 36, orientations EBA/GL/2018/07.*

---

## Planche 4 — Infrastructure et environnements d'exécution

**Titre.** « Domaine quasi hors périmètre, à une exception près : le socle de preuve »

**Chapô.** Treize briques sur quinze sortent du périmètre : datacenters, cloud, réseau, sauvegarde et
continuité relèvent de DORA, applicable depuis janvier 2025.

**Plan de reprise d'activité — (1) adaptation**
La banque fixe elle-même ses objectifs de rétablissement, sous DORA. Pour l'interface dédiée, un objectif
**gradué** selon le nombre de clients touchés et les fonctions affectées sera imposé par norme technique,
avec information des tiers sur les mesures prises et la durée estimée de résolution (Art. 38).
L'interface remonte de fait dans la hiérarchie de criticité.

**Traçabilité et auditabilité — (2) capacité nouvelle**
La charge de la preuve pesait déjà sur la banque, mais l'authentification forte suffisait à clore le
débat. Le PSR retire cet appui : ni l'authentification, ni l'enregistrement, ni la comptabilisation ne
suffisent, et le client doit être invité à documenter les faits, son silence ne valant pas conclusion
(Art. 55). Quatre objets de preuve nouveaux apparaissent — surveillance par les deux PSP, absence de
manquement à la suspension, au retour de fonds, et preuve de la négligence grave (Art. 59, 65, 69, 83). Il
faut journaliser des décisions, pas des transactions.

**Synthèse.** La charge de la preuve ne change pas de camp, elle change d'objet : la banque doit
démontrer après coup ce qu'elle a contrôlé, suspendu et retourné.

*Sources : PSR Art. 38, 55, 59, 65, 69, 83 · ligne de base DSP2 art. 72, DORA.*

---

## Planche 5 — Monitoring et reporting

**Titre.** « Aucune création : deux procédures s'ajoutent, dont une notification sortante que personne ne
porte aujourd'hui »

**Chapô.** Supervision, détection d'intrusion et SIEM relèvent de DORA ; le reporting de fraude existe
depuis la DSP2. Deux briques portent un delta.

**Centre opérationnel de sécurité — (1) adaptation**
La filière sécurité traite des incidents entrants ; elle n'émet rien vers l'extérieur du secteur
financier. Le PSR l'oblige à notifier sans retard aux **hébergeurs** les contenus frauduleux à l'origine
d'une fraude au paiement, selon la procédure du règlement sur les services numériques (Art. 59a). L'enjeu
est financier : la plateforme informée qui n'agit pas rembourse la banque — encore faut-il pouvoir
prouver qu'elle a été informée.

**Reporting prudentiel — (1) adaptation**
L'émission de monnaie électronique devient un service de paiement, et la méthode D de fonds propres — au
moins 2 % de l'encours moyen — est reprise à l'identique de la directive de 2009 (Art. 8 DSP3). La
nouveauté est le **cumul** : une entité qui fait émission **et** services de paiement additionne les deux
exigences. S'y ajoutera un rapprochement des fonds cantonnés dont la norme technique reste à écrire
(Art. 9 DSP3).

**Synthèse.** Deux procédures ajoutées à des dispositifs existants. Le format de la notification aux
hébergeurs est déjà fixé ; celui du reporting prudentiel attend une norme technique.

*Sources : PSR Art. 59a, 82 · DSP3 Art. 8, 9, annexe I point 8 · renvois règlement (UE) 2022/2065
art. 16 et 22 · ligne de base DSP2 art. 96(6), directive 2009/110/CE art. 5(3).*

---

## Planche 6 — Applications métiers (1/3) : cœur bancaire et canaux

**Titre.** « Le PSR entre dans le déroulement de l'opération, là où la DSP2 s'arrêtait à l'accès et à
l'authentification »

**Gestion des comptes — (2) changement de régime**
Le plafond est aujourd'hui une option contractuelle que la banque peut modifier. Il devient un
**paramètre du client**, à la granularité qu'il choisit, non modifiable unilatéralement, avec effet
différé de 4 heures sur toute hausse demandée à distance, notification à trois moments, blocage à
l'exécution en cas de dépassement et réévaluation d'un blocage sous 2 jours ouvrables (Art. 51). Même
fonction, mais outillée, chronométrée et opposable.

**Paiements et transactions — (2) capacité nouvelle**
La banque bloque un instrument ou rejette un ordre ; elle n'arrête pas un ordre en cours et n'intervient
pas sur des fonds déjà reçus. Elle devra **suspendre** un virement sur soupçon objectivement justifié,
rappeler le payeur et rétablir le compte (Art. 65), et côté réception ne pas créditer puis **retourner
les fonds** — avec notification au PSP du payeur sous 10 secondes en instantané (Art. 69). Deux
cinématiques que le SI ne sait pas exécuter, et le cœur de la charge du paquet.

**Dépôts et liquidité — (1) adaptation**
Le cantonnement existe et ne change pas de méthode. Deux contraintes s'y ajoutent : éviter le risque de
concentration lorsque c'est approprié et s'efforcer de ne pas tout cantonner chez un seul établissement —
obligation de moyens, non interdiction — et un rapprochement des fonds dont les modalités viendront par
norme technique (Art. 9 DSP3). Un pilotage à outiller, pas une refonte.

**Canal web — (1) adaptation**
Deux affichages nouveaux. Les frais de conversion doivent être donnés **à la fois** en montant et en
pourcentage de marge au-dessus du taux de référence, avant chaque initiation (Art. 13, 20). Et au moins
une entité de médiation doit être identifiée de façon claire et complète sur le site, l'application, en
agence et aux conditions générales (Art. 94). Un calcul en temps réel, et une information de recours à
gérer comme un contenu de référence.

**Canal mobile — (2) capacité nouvelle**
Installer l'application sur un nouveau téléphone est un parcours maison. Il devient réglementé :
authentification forte **et** second canal distinct, temporisation de 4 heures si l'activation est faite à
distance et ajustable par le client, notification immédiate par un autre canal, neutralisation de
l'application sur simple signalement (Art. 51). Aucune entité ne dispose aujourd'hui de cette
temporisation ni de cet interrupteur.

**Synthèse.** Suspension d'un virement suspect avec rappel du client, retour de fonds à l'arrivée,
plafonds fixés par le client, activation d'application temporisée.

*Sources : PSR Art. 13, 20, 51, 61, 65, 69, 94 · DSP3 Art. 9 · ligne de base DSP2 art. 68, 73, 87.*

---

## Planche 7 — Applications métiers (2/3) : parcours, conformité et risque

**Titre.** « Le middle et le back-office passent de l'obligation de moyens à l'obligation de résultat
opposable »

**Parcours clients — (2) capacité nouvelle**
Un client qui a validé son opération n'a aucun recours. Le PSR crée le **remboursement intégral, sans
franchise**, du consommateur manipulé par un faux conseiller usurpant les canaux de sa banque — sous
réserve d'une notification sans retard et d'un dépôt de plainte, décision sous 15 jours ouvrables, la
preuve d'une négligence grave incombant à la banque (Art. 59). S'y ajoute le parcours de rappel du client
après suspension d'un ordre (Art. 65). Un motif de remboursement à outiller, provisions comprises.

**Accès des établissements de paiement aux comptes — (2) changement de régime**
Il s'agit du compte qu'un établissement de paiement ouvre **chez nous**, pas du compte d'un particulier.
Aujourd'hui un refus ou une clôture ne demande aucune justification. Demain l'accès est dû sur des
critères objectifs, un refus n'est possible que pour **quatre motifs limitatifs**, motivé de façon non
générique, notifié au demandeur et à l'autorité sous un mois, avec préavis de clôture de quatre mois et
droit de recours (Art. 32). Une décision discrétionnaire devient une décision opposable — et sanctionnée.

**Risque et fraude — (2) capacité nouvelle *et* changement de régime, la seule brique qui cumule**
La surveillance existe côté payeur ; côté bénéficiaire, il n'y a rien. Le PSR impose au PSP du
bénéficiaire de **surveiller avant de mettre les fonds à disposition**, sur quatre catégories de données
limitativement autorisées, et fixe cinq facteurs de risque minimaux à tout dispositif de surveillance
(Art. 83). Le PSP qui ne surveille pas supporte le dommage, et celui du payeur rembourse s'il ne peut
prouver que **les deux** ont surveillé. Le partage d'informations entre PSP passe de faculté à obligation
(Art. 83a).

**Synthèse.** Le monitoring engage la responsabilité du PSP qui ne l'exécute pas, la surveillance côté
bénéficiaire n'existe nulle part, et le refus d'accès d'un établissement de paiement devient une décision
motivée, notifiée à l'autorité et attaquable.

*Sources : PSR Art. 32, 55, 59, 61, 65, 69, 83, 83a, 97 · ligne de base DSP2 art. 36 et 75, normes
techniques 2018/389 art. 2.*

---

## Planche 8 — Applications métiers (3/3) : réclamation et canaux de communication

**Titre.** « L'obligation sort du SI transactionnel et se porte sur les canaux »

**Réclamation — (1) adaptation**
Le workflow de réclamation et ses 15 jours ouvrables sont repris tels quels de la DSP2. Le delta est un
**type de décision** : après investigation, une décision motivée de remboursement ou de refus indiquant
les voies de recours, et transmission des motifs à une autorité si la banque conclut à une fraude du
client (Art. 56). Le remboursement d'un prélèvement passe de 10 à 15 jours ouvrables — seul délai que le
texte allonge (Art. 63).

**Téléphonie — (1) adaptation**
La voix était un canal de relation client, sans exigence propre. Elle entre dans le périmètre : garde-fous
techniques contre le détournement des canaux de la banque (Art. 59), support **humain et gratuit** dans
une langue officielle au moins aux heures ouvrées (Art. 53), et assistance au client qui n'arrive pas à
réaliser son authentification (Art. 88). L'usurpation du numéro affiché, elle, pèse sur les opérateurs
télécoms (Art. 59a).

**Messagerie — (1) adaptation**
SMS et courriels sortants n'ont aucune exigence d'intégrité opposable, alors qu'ils sont le principal
vecteur d'usurpation. La banque devra empêcher techniquement la réplication et le détournement de ses
canaux (Art. 59), décrire au contrat une procédure sécurisée de notification de fraude (Art. 20), et
alerter ses clients sur les nouvelles formes de fraude en visant les publics vulnérables (Art. 84). Le
sujet passe du contenu du message à la chaîne d'émission.

**Synthèse.** Les canaux de communication de la banque doivent devenir infalsifiables, la voix doit
offrir un humain gratuit, et la réclamation doit produire une décision motivée, tracée et transmissible à
l'autorité.

*Sources : PSR Art. 20, 53, 56, 59, 59a, 63, 84, 88, 94, 97 · ligne de base DSP2 art. 76(2) et 101.*

---

## Planche 9 — Les briques hors périmètre *(nouvelle)*

**Titre.** « Les deux tiers du SI sortent du périmètre, et c'est un résultat d'analyse, pas un défaut de
couverture »

**Identités internes, habilitations, certificats, clés, secrets.** L'article 80 du PSR reprend le standard
RGPD sur la limitation des accès sans exigence technique propre ; DORA porte la journalisation et la
détection ; le modèle de certificats est fixé depuis 2018.

**Gouvernance de la donnée : catalogue, qualité, lineage, entrepôt, décisionnel.** Inventorier, taguer par
finalité et minimiser sont des obligations RGPD préexistantes. Le reporting de fraude existe depuis la
DSP2 : y ajouter des champs ne crée pas d'impact attribuable au paquet.

**Infrastructure, cloud, réseau, continuité, supervision, SIEM.** DORA couvre le cadre de risque, les
incidents et les objectifs de rétablissement. La parité de temps de réponse est imposée depuis 2018, et le
seuil de présomption d'indisponibilité vient des orientations européennes, non du PSR.

**Briques sollicitées sans exigence propre : relation client, ERP, comptabilité, crédits, RH.** Dates de
valeur, rétablissement du compte et remboursement au prorata sont repris à l'identique de la DSP2. Et un
programme de formation, même imposé, n'est pas un impact SI.

**La règle.** Est ramenée à zéro toute brique dont la seule justification serait vraie de n'importe quelle
réglementation : nouveaux champs, flux d'alimentation, catalogage, volumétrie de logs.

---

## Planche 10 — Ce que le texte sanctionne *(nouvelle)*

**Titre.** « Ce que nous présentons comme des délais de workflow est amendable jusqu'à 10 % du chiffre
d'affaires annuel total »

**Cinq catégories expressément sanctionnées (Art. 97(1))** : l'accès des établissements de paiement aux
comptes (Art. 32) ; les règles applicables aux prestataires d'information et d'initiation ; les mécanismes
de prévention de la fraude, **authentification forte incluse** (Art. 85-87) ; la transparence des frais de
retrait ; et le **non-respect des délais d'indemnisation** (Art. 56, 57, 59, 63).

**Les montants.** Au moins **10 % du chiffre d'affaires annuel total** pour une personne morale, 3 M€ pour
une personne physique, ou le double des profits retirés — ce dernier montant pouvant dépasser les deux
plafonds (Art. 97(2)). Des **astreintes journalières** de 3 % du chiffre d'affaires journalier moyen,
six mois au plus (Art. 98). Sanctions applicables aux dirigeants (Art. 96(3)), et **publication de chaque
décision** sur le site de l'autorité (Art. 101).

**Pourquoi c'est une planche d'architecture.** Trois des cinq catégories portent exactement sur les
briques cotées 2 de cette matrice. Un délai de workflow non instrumenté n'est plus un risque
opérationnel : c'est une assiette de sanction, avec publication de la décision.

---

## Récapitulatif

| Domaine | (2) Impact fort | (1) Impact modéré | (0) |
|---|---|---|---|
| Identités et accès | Authentification forte, Consentement client | SSO, Identités applicatives | 7 |
| Données | Usage et consentement | Applications opérationnelles, Référentiel des noms, Référentiels d'identifiants, Archivage | 5 |
| Intégration | — | Bus de messages, Interface d'accès, Traitements par lots, Mesure des interfaces | 9 |
| Infrastructure | Traçabilité et auditabilité | Plan de reprise d'activité | 13 |
| Monitoring et reporting | — | Centre opérationnel de sécurité, Reporting prudentiel | 5 |
| Applications métiers | Gestion des comptes, Paiements, Canal mobile, Parcours clients, Accès des EP aux comptes, Risque et fraude | Dépôts et liquidité, Canal web, Réclamation, Téléphonie, Messagerie | 6 |
| **Total** | **10** | **18** | **45** |

---

## Points à trancher avant diffusion *(hors slides)*

1. **Nombre de fonctions minimales de l'Art. 36(4)** — huit ou neuf. Le référentiel se contredit, le PDF
   du PSR n'est plus dans le vault. La planche 3 ne cite volontairement aucun chiffre.
2. **Conséquence d'une non-concordance à la vérification du bénéficiaire** — information du payeur, qui
   décide, ou refus de l'opération. C'est ce qui sépare un écran d'avertissement d'un rejet avec gestion
   d'exception et réclamation.
3. **Différé propre à l'open banking** — seul le différé de la vérification du bénéficiaire à 27 mois est
   documenté. Si les obligations d'interface mordent à 21 mois, le plan de charge change.
4. **Trois erreurs à corriger dans la matrice en amont** : rattachement des 180 jours à l'art. 10 des
   normes techniques de 2018, suppression de l'« interdiction de fait » sur le cantonnement, dédoublement
   des deux obligations à 10 secondes.
5. **Trois exigences à ajouter à la matrice** : remboursement des prélèvements de 10 à 15 jours ouvrables
   (Art. 63), activation d'application mobile rattachée à l'authentification forte (Art. 51(4a)-(4e)),
   cinq facteurs de risque minimaux (Art. 83(2b)).
