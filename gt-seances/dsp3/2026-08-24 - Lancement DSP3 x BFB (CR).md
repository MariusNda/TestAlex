# 24/08 - Lancement des travaux DSP3 x BFB (CR)

Réunion du 24/08/2026. Premier contact BForBank sur DSP3/PSR, présentation de l'étude BFB
sur le tableau de bord de révocation des consentements.

## Participants

- Benjamin Henique (BFB, architecte du périmètre Open Banking)
- Hatim Benamar (CASA, architecte d'entreprise Groupe)
- Alexandre Linck (NDA Partners)

## Points clés discutés

- Étude BFB sur le tableau de bord de révocation des consentements
    - Étude engagée à la demande du PM produit, sans commande formelle ni échéance, présentée comme non aboutie
    - Deux besoins fonctionnels retenus par BFB : afficher les accès accordés aux TPP, et permettre au client de révoquer les jetons associés
    - Cible d'architecture : sortir le consentement open banking de la brique Access Management, devenue un quasi-monolithe et détenue par aucune équipe en propre, vers un microservice dédié au périmètre Open Banking
    - Le chemin de révocation s'appuierait sur les services du fournisseur d'identité, aujourd'hui disponibles et non exploités
    - Attributs manquants dans l'objet consentement : identifiant du refresh token en tête, puis indicateur, date et auteur de la révocation, date du dernier accès, date d'expiration
    - Aucune maquette disponible, le contenu du tableau de bord a été déduit des écrans de concurrents

- Périmètre AISP et PISP, point d'écart avec le texte
    - Position BFB : le jeton AISP appartient au client et entre dans le périmètre, le jeton PISP est technique, machine to machine, et en sort
    - En creusant un peu, il semblerait que le critère ne soit pas la propriété du jeton mais la durée du consentement : ce qui dure entre dans le tableau de bord, ce qui est consommé par la transaction en sort. Le texte vise les consentements AIS et les consentements PIS couvrant des paiements multiples ou récurrents (Art. 43(1)), et écarte l'initiation de paiement ponctuel (considérant 65)
    - Et donc qu'un mandat donné à un tiers pour prélever un abonnement chaque mois relèverait du tableau de bord, même avec un jeton technique, là où un virement unique validé au moment d'un achat n'en relèverait pas
    - Ces mandats ne paraissent pas obligatoires : le considérant 56 les cite comme exemple de service d'API premium, ouvert par choix commercial. Leur exposition relèverait donc d'une décision produit, avec un effet direct sur le périmètre du tableau de bord
    - Reste à confirmer, et à vérifier avec BFB ce que couvre réellement leur PISP aujourd'hui, la séance n'ayant pas abordé la distinction. Point structurant pour le chiffrage

- Questions ouvertes de l'étude déjà tranchées par le texte
    - Historique des accès et des révocations : conservation obligatoire des consentements retirés ou expirés pendant deux ans (Art. 43(2)(d))
    - Annulation d'une révocation : le tableau de bord doit permettre de rétablir un accès retiré dans les 48 heures suivant le retrait (Art. 43(2)(c)), et le tiers ne supprime pas les données avant ce délai (Art. 43(2b)). La suppression logique puis physique pressentie par BFB est la bonne lecture
    - Information du TPP : la banque informe le tiers sans retard indu de tout changement apporté via le tableau de bord, retrait compris (Art. 43(4)). Le flux inverse existe aussi, le tiers alimentant la banque en informations d'affichage et l'informant de tout nouveau consentement (Art. 43(3b) et 43(4))
    - Canal de diffusion : le texte impose un tableau de bord intégré à l'interface client (Art. 43(1)) et facile à y trouver (Art. 43(3)), sans trancher entre web et mobile. La question reste organisationnelle chez BFB
    - Contenu obligatoire plus riche que la liste établie par BFB : six informations dues pour chaque consentement en cours (Art. 43(2)(a)(i) à (va)), dont les catégories de données partagées et les dates auxquelles les données du compte ont été consultées, ce qui suppose une journalisation restituable au client

- Périmètre et architecture de la squad Open Banking de BFB
    - Exposition et maintien des API réglementaires AISP et PISP, sandbox de test pour les TPP, référentiel des TPP autorisés alimenté par un fichier européen, application de communication vers les TPP
    - Reporting trimestriel de temps de réponse publié sur le site public. Ces rapports étaient construits sur des valeurs simulées jusqu'au début de l'année, désormais branchés sur les données de production. Le PSR resserrant les exigences de disponibilité et de performance de l'interface dédiée (Art. 38), la qualité de la mesure devient un sujet en soi
    - Aucune exigence réglementaire de performance ressentie à date, les objectifs de service sont internes
    - Migration des services on-prem vers GCP et décommissionnement de l'ancien socle en cours
    - La squad rejoint prochainement l'équipe paiement, le périmètre changera probablement d'architecte

- Dépendances Groupe, standards et gouvernance
    - BFB se considère autonome sur l'open banking, les composants du périmètre sont des composants maison
    - Seule dépendance identifiée : l'API manager WSO2, hébergé sur AWS, en cours de migration vers GCP. Ni Kong, solution Groupe, ni Apigee n'ont été retenus
    - La trajectoire de standard STET vers Berlin Group, portée en séance par Hatim Benamar, était inconnue de l'entité. Elle entre dans les questions à suivre de l'étude BFB
    - Deux objets consentement coexistent chez BFB, celui du marketing et celui de l'open banking. Le catalogue des modèles de consentement et données échangées de CASA, dont le volet DSP3 restait à ouvrir, a été transmis à Benjamin Henique à l'issue de la séance
    - Aucune synchronisation avec le Groupe ni avec les autres entités à date

## Décisions prises

- Benjamin Henique représente BFB au GT sur le périmètre open banking. Mickaël Ravez, PM produit, est associé sur le volet fonctionnel
- La représentation des entités se fait par périmètre et non par entité unique, un architecte cartes et paiements pouvant porter d'autres volets de DSP3 chez BFB
- Le GT communique à BFB le calendrier des séances arrêté jusqu'à décembre et les invitations associées

## Actions et prochaines étapes

- Alexandre Linck : transmettre à Benjamin Henique la lecture GT de l'Art. 43 avant son comité d'architecture, critère ponctuel contre récurrent, contenu obligatoire, rétablissement sous 48 heures, historique deux ans, information du tiers. Échéance : 26/08
- Alexandre Linck : partager le calendrier des GT et les invitations des séances de septembre à décembre. Échéance : 26/08
- Benjamin Henique : recenser les autres initiatives DSP3 chez BFB lors du comité d'architecture du 27/08 et transmettre les contacts au GT. Échéance : 04/09
- BFB : préciser si le PISP couvre uniquement des initiations ponctuelles ou également des mandats récurrents, et en tirer le périmètre du tableau de bord. Échéance : N/A
