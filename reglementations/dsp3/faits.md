# Faits établis — DSP3 / PSR

> FAIT = affirmation sourcée et vérifiée. Numérotation : Fait n°X, puis FX.Y.
> Un fait sans source n'existe pas. Renvois croisés explicites (cf. DSP3-H01, cf. DSP3-EX-003).

## Fait n°1 : état des travaux DSP3 dans le Groupe au 2026-08-17
> F1.1 BforBank a **partiellement initié** un projet DSP3 répondant à l'obligation de tableau de bord de révocation des consentements. C'est le seul chantier DSP3 remonté par l'état des lieux réglementaire BFB. (cf. DSP3-H03) [SRC: synchro Hatim Benamar du 17/08/2026, restitution de la réponse d'Antoine Petit]
> F1.2 CAPS n'a pas de chantier DSP3 ouvert à date. Le sujet actif côté CAPS porte sur **DSP2** : une mise en conformité consécutive à un audit ayant remonté un taux de réussite faible, qui touche les distributeurs. (cf. DSP3-H01) [SRC: synchro Hatim Benamar du 17/08/2026]
> F1.3 CASA a produit un **catalogue des consentements** dont le volet DSP3 est resté incomplet, faute d'éléments sur les données pivots communes aux entités. (cf. DSP3-H03) [SRC: synchro Hatim Benamar du 17/08/2026]
> F1.4 Les travaux DSP2 du Groupe de 2018 sont archivés sur SharePoint et disponibles sur demande. (cf. DSP3-H01) [SRC: synchro Hatim Benamar du 17/08/2026]

## Fait n°2 : état des lieux BForBank sur l'open banking au 2026-08-24
> F2.1 BForBank gère **deux objets consentement distincts** : un objet consentement et un objet préférence côté marketing (bannière cookies, choix de partenaires, canal de communication préféré), et un objet consentement open banking lié au TPP. Seul le second entre dans le champ de l'Art. 43. (cf. DSP3-H03) [SRC: atelier BForBank du 24/08/2026]
> F2.2 Le consentement open banking de BFB est aujourd'hui porté par la brique **Access Management**, qui proxifie le fournisseur d'identité Keycloak et concentre le dialogue de génération de jetons. Cette brique n'appartient pas à l'équipe Open Banking. La cible portée par BFB consiste à en sortir le consentement vers un microservice dédié au périmètre Open Banking. [SRC: atelier BForBank du 24/08/2026]
> F2.3 L'étude BFB sur le tableau de bord est **opportuniste** : engagée à la demande du PM produit sans commande formelle, sans échéance, et sans retour du PM depuis. (cf. DSP3-ET-02) [SRC: atelier BForBank du 24/08/2026]
> F2.4 L'objet consentement de BFB **ne porte pas l'identifiant du refresh token**, condition technique de la révocation. Les autres attributs manquants relevés par BFB sont l'indicateur, la date et l'auteur de la révocation, la date du dernier accès et la date d'expiration du consentement. (cf. DSP3-H03, DSP3-H29) [SRC: atelier BForBank du 24/08/2026] ⚠️ **Annoté le 2026-08-25** : le tableau AS-IS de DSP3-ET-02 §2.2 liste `refreshTokenSessionId` comme attribut **existant** de l'objet consentement, et la liste d'attributs cibles du document ne le réclame pas : elle demande les autres manques énoncés ici (révocation, dernier accès, expiration), plus un compteur d'accès et les catégories de données autorisées. La formulation de séance est donc à confirmer auprès de BFB. Le fait est conservé en l'état, non réécrit, tant que l'écart n'est pas levé. (cf. F2.13) [SRC: DSP3-ET-02 §2.2 ; arbitrage Alex du 2026-08-25]
> F2.5 BForBank expose ses API open banking via **WSO2**, hébergé sur AWS et en cours de migration vers GCP. Ni Kong, solution Groupe, ni Apigee n'ont été retenus. Le reste des composants du périmètre sont des composants maison. (cf. DSP3-H02) [SRC: atelier BForBank du 24/08/2026]
> F2.6 Le **reporting trimestriel public de temps de réponse** de BFB était alimenté par des valeurs simulées via Datadog jusqu'au début 2026, et non par les données de production. Il est désormais branché sur les données réelles. Pertinent au regard des exigences de disponibilité et de performance de l'interface dédiée. [SRC: atelier BForBank du 24/08/2026 ; PSR ST-8221 §Art. 38]
> F2.7 BForBank n'a **aucune synchronisation** avec le Groupe ni avec les autres entités sur DSP3 à date. La trajectoire STET vers Berlin Group lui était inconnue. (cf. DSP3-H02) [SRC: atelier BForBank du 24/08/2026]
> F2.8 Durées de vie des jetons TPP chez BFB : **refresh token de 6 mois pour l'AISP et de 9 mois pour le PISP, access token de 30 minutes**. ⚠️ Corrige la valeur de 24 heures retenue le 24/08 depuis la séance et reportée dans DSP3-H29. ⚠️ Le document reste par ailleurs contradictoire sur ce point : il attribue un refresh token de 9 mois au PISP tout en déclarant le jeton PISP purement technique, machine to machine. (cf. DSP3-H29) [SRC: DSP3-ET-02 §2.1]
> F2.9 Le jeton d'accès du TPP est aujourd'hui généré par **Access Management via Keycloak**, sur l'endpoint `POST /v1/token`. La cible portée par BFB déplace cet endpoint vers le microservice `open-banking-consent-management`, qui valide l'authorization code dans sa propre base puis obtient les jetons réels auprès d'Access Management par **token exchange (RFC 8693)**. Les jetons restent générés par Keycloak. (cf. DSP3-H17) [SRC: DSP3-ET-02 §2.1, §3.2.2.1]
> F2.10 Access Management appelle directement Payment Core à l'acceptation d'un consentement PISP. BFB qualifie ce couplage de **dette technique** (violation du principe de responsabilité unique) et le résorbe en portant le lien depuis le nouveau microservice de consentement, à périmètre fonctionnel inchangé. [SRC: DSP3-ET-02 §2.3, §3.2.1]
> F2.11 Le périmètre de la squad Open Banking de BFB compte **huit composants** : Authorization (front et back d'authentification, on-prem, lié à WSO2), Enrolment, TPP Directory (droits et rôles des TPP, alimenté auprès de **SRC, service allemand**), TPP API (proxy BNA pour comptes, soldes, opérations et bénéficiaires), TPP Monitoring (rapport trimestriel publié sur bforbank.com/dsp2), TPP Communication, STET (exposition des API DSP2, **intégré à la gateway WSO2**) et Payment Core. (cf. DSP3-H02) [SRC: DSP3-ET-03]
> F2.12 Deux chantiers BFB en cours recoupent le PSR sans être portés comme chantiers DSP3 par l'entité : l'**intégration de la vérification du bénéficiaire (VoP) au parcours PISP**, et la mise en place de **pistes d'audit sur les virements initiés par un TPP**. Un troisième porte sur le scope `offline` du JWT pour l'AISP et le PISP, pour éviter une reconnexion du client après déconnexion. (cf. DSP3-H07, DSP3-H08, DSP3-H29 ; DSP3-EX-184 pour les dates de consultation) [SRC: DSP3-ET-03]
> F2.13 L'objet consentement actuel de BFB porte **quatorze attributs**, dont `refreshTokenSessionId`, décrit comme l'identifiant de la session globale Keycloak servant à révoquer l'accès global, AISP uniquement. ⚠️ En contradiction apparente avec F2.4, qui fait de cet identifiant le manque principal. Écart à lever avec BFB. [SRC: DSP3-ET-02 §2.2]

> F2.14 Au comité d'architecture BFB du 27/08/2026, **aucun autre chantier DSP3 n'était amorcé côté BFB** hors le tableau de bord de révocation des consentements (DSP3-ET-02/03) : le périmètre DSP3 de BFB se limite, à date, à l'open banking. ⚠️ La question du périmètre PISP de BFB (initiations ponctuelles seules vs mandats récurrents) reste ouverte. (cf. DSP3-H03, DSP3-H29) [SRC: retour Benjamin Henique, comité d'architecture BFB du 27/08/2026]

## Fait n°3 : dispositif Groupe DSP2 tel que décrit par CASA en août 2017

> ⚠️ **Portée limitée.** DSP3-DSP2-02 est daté du 25/08/2017, soit quatre mois avant l'application de
> la DSP2 et deux ans avant celle des RTS. Les faits ci-dessous établissent **ce que le Groupe
> annonçait mettre en place**, pas ce qui a été réalisé. Chacun appelle une vérification d'état 2026
> avant reprise en livrable. (cf. DSP3-H01)

> F3.1 La mise en œuvre de la DSP2 dans le Groupe était suivie dans le **comité de pilotage
> opérationnel « Nouvelle Banque au Quotidien »**, par un **suivi mensuel piloté par CASA** portant sur
> l'implémentation des RTS SCC & SCA, alimenté par un **référent désigné dans chaque entité**, et
> couvrant consolidation des rétro-plannings, surveillance des dépendances, suivi de l'avancement et
> remontée des alertes. Précédent direct de la question « faut-il un programme Groupe DSP3 ». ⚠️ À
> comparer au COPIL Groupe DSP3 animé par CAPS, l'Open Banking étant coordonné par CASA/TEC/ARC.
> (cf. DSP3-H01 ; DSP3-ET-01) [SRC: DSP3-DSP2-02 §Initiatives dans le Groupe]
> F3.2 Le Groupe mettait à disposition de ses entités un composant d'authentification mutualisé, le
> **SCAD — Service Centralisé d'Authentification Dynamique, porté par CAPS**, cité comme le composant
> technique fourni au Groupe par une entité pour la mise en œuvre DSP2. ⚠️ Statut, périmètre et
> utilisateurs en 2026 inconnus : à instruire auprès de CAPS. (cf. DSP3-H15) [SRC: DSP3-DSP2-02 §Technique]
> F3.3 La mise en œuvre technique s'appuyait sur quatre appuis normatifs de place ou de Groupe : les
> **spécifications interbancaires STET**, les **principes Groupe relatifs à l'API Management**, les
> **Normes d'Intégration techniques du Groupe CA** et le composant SCAD. L'ancrage STET du Groupe est
> donc contemporain de la DSP2 elle-même. (cf. DSP3-H02) [SRC: DSP3-DSP2-02 §Technique]
> F3.4 La sécurité applicative relevait de la cellule **SECAPI**, dont le **Standard SECAPI** est
> déclaré **obligatoire pour tous les projets**, développements spécifiques comme acquisitions de
> progiciels. SECAPI avait produit en 2016, **sous l'impulsion du GT normes d'intégration**, un cadre
> de sécurité des appels de services REST inter-entités, ainsi qu'une méthode d'analyse de risques
> proportionnée, **MESARI**. Cadre normatif préexistant à mobiliser pour les exigences de gestion du
> risque opérationnel et de sécurité du PSR. [SRC: DSP3-DSP2-02 §Sécurité]
> F3.5 CASA traitait la DSP2 comme **indissociable du RGPD** et avait produit un document
> **« Période transitoire DSP2 »** couvrant la fenêtre entre l'entrée en vigueur de la directive
> (13/01/2018) et l'application des RTS SCC & SCA : obligations d'agrément ou d'enregistrement comme
> PSP, modalités d'accès aux comptes en pratique, régime de responsabilité des PSP. Précédent de
> traitement du décalage directive/RTS, qui se reproduit sous DSP3 (+21 mois de transposition,
> RTS EBA à +12 mois après entrée en vigueur). (cf. DSP3-H01, DSP3-H26) [SRC: DSP3-DSP2-02 §Juridique]
> F3.6 Le dispositif d'accompagnement des entités prenait la forme d'un **« Booster AEG »** : un kit
> à six domaines — Technique, Sécurité, User eXperience, Achats, Initiatives dans le Groupe,
> Juridique — adossé à un parcours d'adoption en cinq temps, chaque domaine renvoyant à un contact et
> à des liens utiles. Le GT produit aujourd'hui le même type d'objet sur DSP3.
> [SRC: DSP3-DSP2-02 §Présentation générale]
> F3.7 À fin août 2017, CASA notait que les modalités de communication entre acteurs étaient **encore
> en discussion au niveau européen** et présentait ses éléments comme « volontairement macroscopiques
> et fournis à titre indicatifs ». Le GT est aujourd'hui dans une position homologue face au paquet
> pré-JO. [SRC: DSP3-DSP2-02 §User eXperience 1/3]

## Fait n°4 : état des lieux CATS sur l'open banking au 2026-09-03
> F4.1 CATS **n'a pas de point d'entrée DSP3 unique**. Le sujet est instruit tribu par tribu : des ateliers de relecture d'articles entre Product Owners ont démarré, organisés par **Julie Isenberg**, chaque PO retenant ce qui touche son périmètre. Elisa Trolez déclare qu'aucun référent DSP3 dédié n'existe ni sur ses deux tribus ni au niveau de l'entité. Contraste direct avec BFB, où un représentant unique porte le périmètre open banking. (cf. DSP3-H01) [SRC: atelier CATS du 03/09/2026]
> F4.2 Périmètre d'Elisa Trolez : **Product Owner de la tribu IIP** (instrument et initiation de paiements), sur les virements et les API Open Banking, qu'elle désigne comme « les API DSP2 ». Leader de la tribu : **Sophie Rigoletti**. La tribu **SAPE** (leader **Anne-Marie Faucon**) porte l'EDI et la fraude. L'archivage des notifications relève d'une **troisième tribu, communication client**. Au moins trois tribus de CATS sont donc dans le champ de DSP3. (cf. DSP3-H01) [SRC: atelier CATS du 03/09/2026]
> F4.3 **Christel Body (CAPS) transmet et traduit les articles du texte aux PO de CATS**, avec des échanges réguliers, dont un le jour même de la séance. CAPS joue donc de fait un rôle de diffusion réglementaire vers les distributeurs, sans que la gouvernance en soit formalisée : CAPS est encore, selon Elisa Trolez, en train de définir son organisation sur le sujet. (cf. DSP3-H01 ; DSP3-ET-04) [SRC: atelier CATS du 03/09/2026]
> F4.4 **Les clients de CATS voient déjà en self-care les accès accordés aux prestataires tiers, mais ne peuvent pas agir dessus** : le désenrôlement reste à implémenter. Le delta Art. 43 de CATS porte donc sur l'**action de retrait**, non sur l'affichage. Sens inverse du cas BFB, qui concevait l'objet et le registre avant l'IHM. (cf. DSP3-H03, DSP3-H17 ; DSP3-EX-183, DSP3-EX-185) [SRC: atelier CATS du 03/09/2026]
> F4.5 Deuxième impact open banking identifié par CATS : la **restitution des statuts de virement aux prestataires tiers**, dont la mécanique n'est pas arrêtée (interrogation par le tiers ou poussée d'information par l'ASPSP). Un business analyst est en cours de lecture du texte pour compléter la liste des impacts. (cf. DSP3-H30) [SRC: atelier CATS du 03/09/2026]
> F4.6 **CATS est sur une version STET ancienne, et une montée de version est due quoi qu'il arrive** : une mise à jour de scheme STET est attendue, et l'écart est décrit en séance comme « une marche assez importante ». L'alignement sur la dernière version de STET est acquis dans l'esprit de CATS, indépendamment de tout arbitrage de standard. Premier chiffrage d'impact open banking indépendant de DSP3-H02. (cf. DSP3-H02) [SRC: atelier CATS du 03/09/2026]
> F4.7 **CATS a rendu un avis architecture sur la bascule vers Berlin Group**, soulignant un impact majeur sans retour sur investissement identifié. Sans directive explicite de changer, CATS reste sur STET et attend le retour de Christel Body sur le caractère définitif du statut. ⚠️ Selon Elisa Trolez, **STET ne fournirait pas de version compatible DSP3 si la place partait sur Berlin Group** : dépendance de place structurante pour l'arbitrage, rapportée de seconde main, à confirmer. (cf. DSP3-H02) [SRC: atelier CATS du 03/09/2026]
> F4.8 **CATS est complètement indépendante des autres entités sur l'open banking**, sans brique mutualisée, mais **expose les mêmes API et les mêmes endpoints** que les autres entités françaises puisqu'elle est basée sur les schemes STET. Des échanges ont eu lieu avec LCL sur leur fonctionnement. Hatim Benamar indique que toutes les entités françaises du Groupe sont sur STET, les entités européennes probablement sur d'autres schemes. Le scheme commun est donc le vrai levier de mutualisation, plus que le partage de briques. (cf. DSP3-H02, DSP3-H30) [SRC: atelier CATS du 03/09/2026]
> F4.9 Calendrier CATS : **aucun rétroplanning formalisé**. Le **T4 2026 porte le jalon** : pas de développement, mais l'objectif d'une liste d'impacts claire par périmètre, pour attaquer début 2027. Un budget 2027 existe. ⚠️ Écart de lecture des délais relevé sans être tranché en séance : Elisa Trolez évoque une application à 12 ou 13 mois selon les articles après un vote pressenti en janvier, là où le vault retient 21 mois pour le PSR et 27 pour la vérification du bénéficiaire, les 12 mois correspondant au mandat de RTS de l'ABE. (cf. DSP3-H26) [SRC: atelier CATS du 03/09/2026 ; PSR ST-8221 §Art. 112]
