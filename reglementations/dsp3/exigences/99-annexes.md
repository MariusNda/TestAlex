# Annexes du referentiel

> Hypotheses derivees, mandats EBA, options, alertes de qualite.
> Retour a l'index : [_index.md](_index.md)

## Hypothèses dérivées à ouvrir

| ID proposé | Question ouverte | Origine | Impact si non tranchée |
|---|---|---|---|
| DSP3-H04 | Que recouvre la clause « exceptionnellement via une autre interface sûre et efficace » ouverte aux AISP/PISP ? Aucun critère, aucune procédure, aucun mandat de RTS. Est-ce le successeur de fait du fallback des RTS 2018/389 ? | DSP3-EX-194 [SRC: PSR ST-8221 §Art. 45(1)] | Impossible de dimensionner la trajectoire d'API : soit l'obligation de résultat sur l'interface dédiée suffit, soit les entités doivent anticiper des accès hors API. Chiffrage et architecture open banking bloqués. |
| DSP3-H05 | Des entités du Groupe entrent-elles dans le champ de la dérogation Art. 39 (interface client comme interface d'échange, ou absence d'interface) ? Les critères sont entièrement renvoyés aux RTS, sans seuil. | DSP3-EX-161, DSP3-EX-163 [SRC: PSR ST-8221 §Art. 39] | Une entité de petite taille pourrait éviter le coût d'une interface dédiée. À défaut d'arbitrage, toutes les entités provisionnent l'interface complète. |
| DSP3-H06 | Quel est le périmètre exact des « comptes de paiement accessibles en ligne » et des « comptes désignés » à exposer via l'interface dédiée, dans le référentiel comptes du Groupe ? | DSP3-EX-128, DSP3-EX-148 [SRC: PSR ST-8221 §Art. 33, 36(3)] | Sous-estimation du périmètre d'exposition et risque de qualification d'obstacle interdit (Art. 44). |
| DSP3-H07 | Le service de vérification du bénéficiaire est-il porté par une brique mutualisée Groupe ou par entité ? Quel référentiel de noms (nom commercial, raison sociale, nom complet) est exposé, et selon quelle logique de concordance approchante ? | DSP3-EX-248, DSP3-EX-149 [SRC: PSR ST-8221 §Art. 50, 36(4)(g)] | Divergence de traitement entre entités, risque de responsabilité Art. 57 et coût de développement dupliqué. |
| DSP3-H08 | L'Art. 50 étend la VoP à tous les virements, y compris hors euro et hors identifiants IBAN. Quel périmètre de devises et d'identifiants uniques le Groupe doit-il couvrir à +27 mois ? | DSP3-EX-248, DSP3-EX-249 [SRC: PSR ST-8221 §Art. 50] | Périmètre de la VoP indéterminé, chiffrage impossible, risque de découvrir tardivement des flux non couverts. |
| DSP3-H09 | Quels canaux d'initiation du Groupe constituent des « processus ou protocoles automatisés dédiés » ouvrant l'opt-out VoP aux clients non consommateurs ? | DSP3-EX-252, DSP3-EX-253 [SRC: PSR ST-8221 §Art. 110c(3)(b)] | Traitement inégal des clients entreprises entre entités ; exposition à responsabilité si l'opt-out est ouvert à tort. |
| DSP3-H10 | Comment le PSP du payeur apporte-t-il la preuve que la surveillance des opérations a été effectuée par les deux PSP ? Le texte crée l'obligation de preuve sans en définir le véhicule inter-PSP. | DSP3-EX-350 [SRC: PSR ST-8221 §Art. 83(1a)] | Exposition directe au remboursement du montant de l'opération, sans moyen contractuel ou technique identifié. Provision à estimer. |
| DSP3-H11 | Le Groupe adhère-t-il à un dispositif de partage d'informations sur la fraude de place, ou construit-il un dispositif intra-Groupe ? Qui porte l'analyse d'impact conjointe imposée avant conclusion ? | DSP3-EX-357, DSP3-EX-362 [SRC: PSR ST-8221 §Art. 83a] | Obligation de participer non satisfaite à la date d'application, ou dispositif non conforme au RGPD. |
| DSP3-H12 | Quelle politique de traitement des demandes de remboursement pour fraude par usurpation (spoofing) : critères de négligence grave, articulation avec le dépôt de plainte, provisionnement ? | DSP3-EX-274 à DSP3-EX-279 [SRC: PSR ST-8221 §Art. 59] | Remboursement intégral sans franchise pour tous les consommateurs manipulés via des canaux attribués au PSP : exposition financière non chiffrée. |
| DSP3-H13 | Quel paramétrage du délai de 4 heures (augmentation de plafond et activation d'application mobile), et quelle ergonomie de l'opt-out utilisateur ? | DSP3-EX-226, DSP3-EX-378 [SRC: PSR ST-8221 §Art. 51(1a) et 51(4b)] | Impact direct sur les parcours d'enrôlement et de paiement ; risque d'écart d'expérience entre entités. |
| DSP3-H14 | Le Groupe entend-il utiliser la double inhérence pour la SCA, et sur quels parcours ? La démonstration à l'ACPR est requise et les lignes directrices EBA n'arrivent qu'à 18 mois. | DSP3-EX-394 [SRC: PSR ST-8221 §Art. 85(12)] | Décision d'architecture d'authentification prise sans doctrine superviseur ; risque de remise en cause tardive. |
| DSP3-H15 | Quel moyen de SCA non dépendant du smartphone le Groupe maintient-il ou recrée-t-il, et pour quelles populations ? Le texte impose plus d'un moyen et au moins un moyen gratuit adapté. | DSP3-EX-402, DSP3-EX-404, DSP3-EX-405 [SRC: PSR ST-8221 §Art. 88] | Trajectoire de décommissionnement des moyens non mobiles à revoir ; coût de maintien d'un canal alternatif. |
| DSP3-H16 | Quelle politique Groupe d'exemptions de SCA, sachant que les exemptions ne sont pas obligatoires et que le PSP conserve le droit d'imposer la SCA ? | DSP3-EX-393 [SRC: PSR ST-8221 §Art. 85(11)] | Arbitrage fraude / conversion non tranché, avec effet direct sur les taux de fraude et le reporting. |
| DSP3-H17 | Le tableau de bord des consentements est-il une brique mutualisée ou par entité ? Comment sont gérés le rétablissement sous 48 heures, l'historique sur 2 ans et les flux bidirectionnels avec les tiers ? | DSP3-EX-183 à DSP3-EX-192 [SRC: PSR ST-8221 §Art. 43] | Composant entièrement nouveau, à la fois IHM et back-office, non présent dans la carto DSP2. Chiffrage et make-or-buy à instruire. **Transférée dans `hypotheses.md` le 2026-08-25**, énoncé resserré sur le back-office (registre et protocole d'échange) ; le volet IHM et données pivots est porté par DSP3-H03. |
| DSP3-H18 | Comment le Groupe refond-il son processus d'entrée en relation et de clôture des comptes d'établissements de paiement : motifs limitatifs, motivation individualisée, notification à l'autorité compétente, préavis de 4 mois ? | DSP3-EX-118 à DSP3-EX-126 [SRC: PSR ST-8221 §Art. 32] | Risque de sanction (Art. 97(1)(a) vise explicitement l'Art. 32) et exposition réputationnelle sur le de-risking. |
| DSP3-H19 | Quels systèmes et schemes de paiement opérés ou co-opérés par le Groupe entrent dans le champ de l'Art. 31, et quelles règles d'accès doivent être publiées ? | DSP3-EX-110 à DSP3-EX-117 [SRC: PSR ST-8221 §Art. 31] | Obligation de transparence et de non-discrimination non identifiée sur des systèmes internes ; exclusion « même groupe » à qualifier. |
| DSP3-H20 | Quelles options nationales la France retiendra-t-elle (extension de l'interdiction de surcharge, microentreprises, information mensuelle sur support durable, délais d'exécution nationaux plus courts, sanctions pénales) ? | DSP3-EX-084, DSP3-EX-015, DSP3-EX-063, DSP3-EX-452, DSP3-EX-489 | Le périmètre réel d'exigences en France reste indéterminé ; risque de découverte tardive au stade de la transposition PSD3. |
| DSP3-H21 | Quelles filiales du Groupe sont des établissements de paiement ou de monnaie électronique soumis au nouveau cantonnement (comptes de règlement, risque de concentration, plan de liquidation) ? | DSP3-EX-627 à DSP3-EX-640, DSP3-EX-522 [SRC: PSD3 ST-8222 §Art. 9 et 3(3)(s)] | Impacts prudentiels et de trésorerie non identifiés ; retard sur la redocumentation d'agrément. |
| DSP3-H22 | Quel plan de redocumentation des agréments existants d'ici +27 mois ? Sept pièces sont à retransmettre, dont deux nouveautés absolues : le plan de liquidation et l'historique des demandes d'agrément dans l'UE. | DSP3-EX-670, DSP3-EX-677 [SRC: PSD3 ST-8222 §Art. 44 et 45] | Suspension de l'agrément à défaut de transmission dans les délais ; fenêtre de grandfathering de 6 mois seulement. |
| DSP3-H23 | Le calcul des amendes sur le chiffre d'affaires consolidé de l'entreprise mère ultime change l'ordre de grandeur du risque de sanction pour un groupe bancaire. Quelle est l'assiette retenue et comment est-elle intégrée à la cartographie des risques ? | DSP3-EX-493, DSP3-EX-495, DSP3-EX-499 [SRC: PSR ST-8221 §Art. 97(2)-(3), 98] | Sous-estimation majeure de l'exposition de sanction ; absence d'arbitrage sur les priorités de mise en conformité. |
| DSP3-H24 | Quelle cible de reporting de fraude (contenu, périodicité, agrégation) et quelle articulation avec les reportings existants, en attendant les RTS et ITS à 12 mois ? | DSP3-EX-337 à DSP3-EX-343 [SRC: PSR ST-8221 §Art. 82] | Chantier de reporting démarré trop tard ou construit deux fois. |
| DSP3-H25 | L'ouverture FRAND des fonctionnalités matérielles et logicielles des terminaux mobiles crée-t-elle une opportunité de wallet ou de paiement sans contact propriétaire pour le Groupe ? | DSP3-EX-406 à DSP3-EX-408 [SRC: PSR ST-8221 §Art. 88a] | Opportunité stratégique non instruite ; fenêtre d'accès aux NFC et éléments sécurisés non exploitée. |
| DSP3-H26 | Sur quelle date d'entrée en vigueur le rétroplanning du GT est-il construit ? Toutes les échéances du compromis sont des placeholders relatifs à une publication au JOUE non datée. | DSP3-EX-711 [SRC: PSR ST-8221 §Art. 112] | Rétroplanning non ancré ; risque de sur- ou sous-anticipation de 6 à 12 mois sur l'ensemble des chantiers. |
| DSP3-H27 | Quelle position du Groupe sur les IBAN virtuels, désormais reconnus comme identifiants de compte valides, y compris au regard du LCB-FT ? | DSP3-EX-250 [SRC: PSR ST-8221 §Art. 110c(1)-(2)] | Impacts SI (référentiels, VoP, filtrage) et LCB-FT non instruits ; clause de revoyure à 3 ans sur le sujet. |
| DSP3-H28 | Quelles entités du Groupe manipulent des jetons de monnaie électronique, et le régime transitoire de l'Art. 108a leur est-il applicable dès l'entrée en vigueur ? | DSP3-EX-693 à DSP3-EX-700 [SRC: PSR ST-8221 §Art. 67a, 108a, 110b] | Deux articles applicables dès l'EEV, sans période de préparation ; risque de non-conformité immédiate. |

## Mandats EBA et actes délégués recensés

| Type | Objet | Article source | Délai |
|---|---|---|---|
| Lignes directrices EBA | Exclusion « agent commercial » | [SRC: PSR ST-8221 §Art. 2(7)] | 1 an après EEV |
| RTS | Conditions de l'exclusion « réseau limité » | [SRC: PSR ST-8221 §Art. 2(8)] | Soumission 1 an après EEV |
| RTS | Format harmonisé et contenu de la notification et de la motivation de refus ou de clôture de compte d'établissement de paiement | [SRC: PSR ST-8221 §Art. 32(5)] | Soumission 12 mois après EEV |
| RTS | Statistiques trimestrielles des interfaces (Art. 35(5)) et standards de temps de rétablissement optimal | [SRC: PSR ST-8221 §Art. 38(5)] | Soumission 9 mois après EEV |
| RTS | Critères justifiant qu'un ASPSP n'offre aucune interface d'échange de données | [SRC: PSR ST-8221 §Art. 39(2)] | Soumission 12 mois après EEV |
| RTS | Données, méthodologie et périodicité du reporting des ASPSP sur l'accès AIS/PIS | [SRC: PSR ST-8221 §Art. 48(8)] | Soumission 18 mois après EEV |
| Rapport EBA | Taille et fonctionnement des marchés AIS et PIS dans l'Union | [SRC: PSR ST-8221 §Art. 48(7)] | Tous les 2 ans |
| RTS | Données statistiques de fraude à fournir aux autorités compétentes | [SRC: PSR ST-8221 §Art. 82(2)] | Soumission 12 mois après EEV |
| ITS | Formulaires et modèles de transmission des données de fraude à l'EBA | [SRC: PSR ST-8221 §Art. 82(3)] | Soumission 12 mois après EEV |
| Rapport conjoint EBA + BCE | Données agrégées de fraude et analyse des tendances | [SRC: PSR ST-8221 §Art. 82(1b)] | Annuel |
| Lignes directrices EBA | Évaluation de la pleine préservation de l'indépendance de deux éléments d'inhérence | [SRC: PSR ST-8221 §Art. 85(12)] | 18 mois après EEV |
| RTS | Sept objets : SCA, exemptions, mesures de sécurité, externalisation, standards de communication ouverts, interfaces dédiées, exigences techniques du transaction monitoring | [SRC: PSR ST-8221 §Art. 89(1)] | Soumission 12 mois après EEV |
| Lignes directrices EBA | Procédures de réclamation auprès des autorités compétentes | [SRC: PSR ST-8221 §Art. 91(6)] | 21 mois après EEV |
| Rapport EBA | Application des sanctions par les autorités compétentes | [SRC: PSR ST-8221 §Art. 102(3)] | 2 ans après la date d'application, puis tous les 2 ans |
| Acte délégué Commission | Information sur les frais à communiquer aux acquéreurs par les schemes de cartes et entités de traitement | [SRC: PSR ST-8221 §Art. 31a(4)] | 15 mois après EEV |
| Acte délégué Commission | Actualisation du montant de la franchise de 50 EUR | [SRC: PSR ST-8221 §Art. 60(5)] | — |
| Acte délégué Commission | Ajustement des dérogations relatives aux jetons de monnaie électronique | [SRC: PSR ST-8221 §Art. 67a(4)] | — |
| Acte délégué Commission | Critères et facteurs de l'intervention produit de l'EBA | [SRC: PSR ST-8221 §Art. 104(8)] | — |
| Rapport Commission | Application et impact du règlement (accès aux données, interfaces, fraude, remboursement Art. 59) | [SRC: PSR ST-8221 §Art. 108(1)] | 7 ans après EEV |
| Rapport Commission | Surcharging, mécanismes de remboursement des schemes, impact de l'Art. 59a | [SRC: PSR ST-8221 §Art. 108(1a)] | 5 ans après EEV |
| Rapport Commission | Champ du règlement, IBAN virtuels, jetons de monnaie électronique et extension de la VoP et de l'open banking | [SRC: PSR ST-8221 §Art. 108(1b)] | 3 ans après EEV |
| Rapport Commission | Pratiques des schemes de cartes, entités de traitement et acquéreurs | [SRC: PSR ST-8221 §Art. 108(2)] | 18 mois après EEV |
| RTS | Contenu des dossiers d'agrément et d'enregistrement (EP, AISP, exploitants de DAB), méthodologie commune d'évaluation, garantie comparable, montant minimal de l'assurance RC professionnelle | [SRC: PSD3 ST-8222 §Art. 3(5)-(6)] | Soumission 12 mois après EEV |
| RTS | Critères du modèle d'affaires à faible nombre d'opérations de montant unitaire élevé | [SRC: PSD3 ST-8222 §Art. 7(6)] | Soumission 12 mois après EEV |
| RTS | Cantonnement : gestion du risque, ségrégation, désignation, rapprochement, calcul, risque de concentration, comptes de règlement | [SRC: PSD3 ST-8222 §Art. 9(7)] | Soumission 12 mois après EEV |
| Lignes directrices EBA | Dispositifs, processus et mécanismes de gouvernance conditionnant l'agrément | [SRC: PSD3 ST-8222 §Art. 13(1)] | Adoption 12 mois après EEV |
| RTS | Fonctionnement, maintenance et accès au registre central EBA | [SRC: PSD3 ST-8222 §Art. 18(5)] | Soumission 18 mois après EEV |
| ITS | Détail et structure des informations à notifier au registre central | [SRC: PSD3 ST-8222 §Art. 18(6)] | Soumission 18 mois après EEV |
| Obligation opérationnelle EBA | Liste centrale lisible par machine des PSP offrant les services 6 et 7 de l'annexe I | [SRC: PSD3 ST-8222 §Art. 18(7)] | Aucun délai spécifié |
| RTS | Cadre de coopération et d'échange d'informations entre autorités d'origine et d'accueil | [SRC: PSD3 ST-8222 §Art. 30(5)] | Soumission 18 mois après EEV |
| Actes délégués Commission | Actualisation pour inflation des montants des art. 5, 34(1) et 37 | [SRC: PSD3 ST-8222 §Art. 40] | — |
| Rapport Commission | Application et impact de la directive (champ, cantonnement et 2014/49/UE, cash en magasin, parts de marché) | [SRC: PSD3 ST-8222 §Art. 43(1)] | 7 ans après EEV |
| Rapport Commission | Champ de la directive (systèmes, schémas, prestataires techniques, monnaie électronique) | [SRC: PSD3 ST-8222 §Art. 43(2)] | 3 ans après EEV |
| Rapport Commission | Extension éventuelle du champ aux portefeuilles numériques | [SRC: PSD3 ST-8222 §Art. 43(2a)] | 18 mois après EEV |

Total : 22 mandats à l'EBA (12 RTS, 2 ITS, 4 jeux de lignes directrices, 3 rapports, 1 obligation opérationnelle), 5 habilitations à actes délégués de la Commission et 7 clauses de rapport de la Commission.

## Options nationales et contractuelles recensées

| Type | Objet | Article source |
|---|---|---|
| Option nationale | Exemption des institutions visées à l'art. 2(5) points (4) à (23) de la directive 2013/36/UE | [SRC: PSR ST-8221 §Art. 2(6)] ; [SRC: PSD3 ST-8222 §Art. 1(2)] |
| Option nationale | Application du Titre II aux microentreprises | [SRC: PSR ST-8221 §Art. 4(2)] |
| Option nationale | Fourniture mensuelle gratuite de l'information post-opération sur support durable | [SRC: PSR ST-8221 §Art. 25(3)] |
| Option nationale | Écarter l'Art. 95 pour les non-consommateurs ; étendre le Titre III aux microentreprises | [SRC: PSR ST-8221 §Art. 27(2)-(3)] |
| Option nationale | Extension de l'interdiction de surcharge ou limitation du droit du bénéficiaire de facturer | [SRC: PSR ST-8221 §Art. 28(4)] |
| Option nationale | Limitation de la dérogation « monnaie électronique » aux Art. 56 et 60 | [SRC: PSR ST-8221 §Art. 29(2)] |
| Option nationale | Exemption d'interface dédiée pour les banques centrales nationales et autres autorités publiques | [SRC: PSR ST-8221 §Art. 39(1)] |
| Option nationale | Désignation de l'autorité nationale destinataire des justifications de refus de remboursement | [SRC: PSR ST-8221 §Art. 56(2)] |
| Option nationale | Délais maximaux d'exécution plus courts pour les opérations nationales | [SRC: PSR ST-8221 §Art. 72] |
| Option nationale | Règles de traitement des réclamations plus favorables à l'utilisateur | [SRC: PSR ST-8221 §Art. 94(2)] |
| Option nationale | Sanctions pénales en lieu et place de sanctions administratives | [SRC: PSR ST-8221 §Art. 96(2)] |
| Option nationale | Clôture d'enquête par transaction ou procédure accélérée | [SRC: PSR ST-8221 §Art. 96(4)] |
| Option nationale | Mesures, sanctions et pouvoirs de sanction supplémentaires | [SRC: PSR ST-8221 §Art. 97(4)] |
| Option nationale | Montants d'astreinte supérieurs | [SRC: PSR ST-8221 §Art. 98(2)] |
| Option nationale | Droits au remboursement plus favorables et mesures anti-fraude plus strictes | [SRC: PSR ST-8221 §Art. 107(1)] |
| Option nationale | Non-application des art. 7 ou 8 aux EP consolidés chez un établissement de crédit mère | [SRC: PSD3 ST-8222 §Art. 6(3)] |
| Option nationale | Cantonnement auprès d'un office de chèques postaux | [SRC: PSD3 ST-8222 §Art. 9(1)] |
| Option nationale | Application mutatis mutandis des art. 53 à 61 de la directive 2013/36/UE au secret professionnel | [SRC: PSD3 ST-8222 §Art. 26(3)] |
| Option nationale | Exigence d'un point de contact central | [SRC: PSD3 ST-8222 §Art. 31(4)] |
| Option nationale | Régime d'exemption des petits établissements de paiement et petits émetteurs de monnaie électronique, plafond de stockage, choix des pièces d'enregistrement, limitation des activités de l'art. 10 | [SRC: PSD3 ST-8222 §Art. 34(1), (2), (5)] |
| Option nationale | Abaissement du plafond de cash en magasin (sans descendre sous 100 EUR) et plafond journalier par compte (≥ 200 EUR) | [SRC: PSD3 ST-8222 §Art. 37(1), (1a)] |
| Option nationale | Notification des réseaux limités au-delà de 1 M EUR et avis d'audit annuel pour l'exclusion « communications électroniques » | [SRC: PSD3 ST-8222 §Art. 39(1), (2)] |
| Option nationale | Exemption automatique au titre de l'art. 34 pour les personnes précédemment exemptées au titre de l'art. 32 DSP2 | [SRC: PSD3 ST-8222 §Art. 44(4)] |
| Option contractuelle | Écarter le Titre II pour les utilisateurs non consommateurs | [SRC: PSR ST-8221 §Art. 4(1)] |
| Option contractuelle | Frais pour informations supplémentaires, plus fréquentes ou par un autre canal | [SRC: PSR ST-8221 §Art. 8(2)] |
| Option contractuelle | Régime allégé des instruments de faible valeur (modifications contractuelles, information post-exécution) | [SRC: PSR ST-8221 §Art. 10(1)(b) et (c)] |
| Option contractuelle | Langue de l'information précontractuelle et du contrat-cadre | [SRC: PSR ST-8221 §Art. 12(1) et 19(1)] |
| Option contractuelle | Acceptation tacite des modifications du contrat-cadre et résiliation sans frais | [SRC: PSR ST-8221 §Art. 22(2)] |
| Option contractuelle | Application immédiate des modifications de taux fondées sur un taux de référence convenu | [SRC: PSR ST-8221 §Art. 22(3)] |
| Option contractuelle | Préavis de résiliation par l'utilisateur (≤ 1 mois) et par le PSP (≥ 3 mois) | [SRC: PSR ST-8221 §Art. 23(1) et (3)] |
| Option contractuelle | Fourniture périodique de l'information post-opération au bénéficiaire | [SRC: PSR ST-8221 §Art. 26(2)] |
| Option contractuelle | Écarter les Art. 28(1), 49(7), 55, 60, 62, 63, 66, 75, 76 et modifier les délais de l'Art. 54 pour les non-consommateurs | [SRC: PSR ST-8221 §Art. 27(1)] |
| Option contractuelle | Dérogation « instruments de faible valeur » | [SRC: PSR ST-8221 §Art. 29(1)] |
| Option contractuelle | Consentement postérieur à l'exécution, forme et procédure de recueil du consentement | [SRC: PSR ST-8221 §Art. 49(1), (5), (6)] |
| Option contractuelle | Exclusion du droit à remboursement des opérations initiées par le bénéficiaire (4 semaines) | [SRC: PSR ST-8221 §Art. 62(3)] |
| Option contractuelle | Heure limite de réception (cut-off) et jour d'exécution convenu | [SRC: PSR ST-8221 §Art. 64(1) et (2)] |
| Option contractuelle | Frais en cas de refus objectivement justifié | [SRC: PSR ST-8221 §Art. 65(1)] |
| Option contractuelle | Révocation d'un ordre après le délai et frais associés | [SRC: PSR ST-8221 §Art. 66(5)] |
| Option contractuelle | Déduction des frais du PSP du bénéficiaire sur le montant transféré | [SRC: PSR ST-8221 §Art. 67(2)] |
| Option contractuelle | Délais d'exécution convenus, dans la limite de 5 jours ouvrables | [SRC: PSR ST-8221 §Art. 68(2)] |
| Option contractuelle | Frais de récupération de fonds en cas d'identifiant unique incorrect | [SRC: PSR ST-8221 §Art. 74(4)] |
| Option contractuelle | Indemnisation additionnelle entre PSP et intermédiaires | [SRC: PSR ST-8221 §Art. 78(2)] |
| Option contractuelle | VoP postérieure à l'autorisation et exécution sans intervention pour les non-consommateurs | [SRC: PSR ST-8221 §Art. 110c(3)(b)] |
| Faculté d'acteur | Publication de données agrégées sur les refus et clôtures de comptes | [SRC: PSR ST-8221 §Art. 32(3a)] |
| Faculté d'acteur | Blocage de l'instrument de paiement | [SRC: PSR ST-8221 §Art. 51(2)] |
| Faculté d'acteur | Réduction de la franchise de 50 EUR | [SRC: PSR ST-8221 §Art. 60(1)] |
| Faculté d'acteur | Droits au remboursement plus favorables pour les prélèvements en devises hors euro | [SRC: PSR ST-8221 §Art. 62(4)] |
| Faculté d'acteur | Retour de fonds par le PSP du bénéficiaire en cas de soupçon de fraude (1er alinéa) | [SRC: PSR ST-8221 §Art. 69(2a)] |
| Faculté d'acteur | Reporting de fraude via un dispositif alternatif non moins étendu | [SRC: PSR ST-8221 §Art. 82(1a)] |
| Faculté d'acteur | Non-application d'une exemption de SCA et maintien de la SCA | [SRC: PSR ST-8221 §Art. 85(11)] |
| Faculté d'acteur | Publication nominative des sanctions visant des personnes physiques | [SRC: PSR ST-8221 §Art. 101(2)] |
| Faculté d'acteur | Intervention produit temporaire de l'EBA | [SRC: PSR ST-8221 §Art. 104(1)] |
| Faculté d'acteur | Exigence d'une entité distincte comme condition d'agrément | [SRC: PSD3 ST-8222 §Art. 13(4)] |
| Faculté d'acteur | Prolongation exceptionnelle de 3 mois du régime transitoire | [SRC: PSD3 ST-8222 §Art. 45a] |

## Alertes de qualité du texte

1. **Renvoi cassé « Art. 5(4) » (PSR).** L'Art. 5 ne comporte que trois paragraphes. Les Art. 7, 13(1)(f), 20(c)(v) et 110a renvoient tous à un Art. 5(4) inexistant. Le contenu visé est le 2e alinéa de l'Art. 5(2). Renumérotation à surveiller au stade juriste-linguiste.
2. **Points supprimés dans le PSR** (marqués ▌) : Art. 2(2) point (i) ; Art. 3 points (51), (52) et (55) ; Art. 31 §4 ; Art. 32 §1 points (d) et (e) ; Art. 38 §3 et §4 ; Art. 84 (pas de §3) ; Art. 85 §1 point (b), §3 et §4 ; Art. 105 entièrement supprimé (le Titre IV s'ouvre sur l'Art. 106).
3. **Doublon apparent** : Art. 2(1a) points (c) et (ee) visent tous deux les fournisseurs de communications électroniques.
4. **Coquille Art. 25(1)(a)** : « a reference enabling the payer to identify each the payment transaction ».
5. **Renvoi orphelin Art. 38(5)(b)** : le paragraphe renvoie toujours à « paragraph 3 » pour le temps de rétablissement optimal, alors que les §3 et §4 de l'Art. 38 ont été supprimés.
6. **Numérotation de l'Art. 51** : la séquence réelle est 1, 1a, 1c, 2, 3, 4, 4a, 4b, 4c, 4d, 4e, 4f — il n'existe pas de §1b, et le paragraphe sur la notification des changements de plafond est un second alinéa non numéroté du §1a.
7. **Anomalie de rédaction dans le nouvel art. 5c(6) du règl. 260/2012** (inséré par l'Art. 110c PSR) : les points (i) et (ii) écrivent « the name of the payee as provided by the payer matches / almost matches the payment account identifier », là où la logique attendrait « the name of the payee associated with the payment account identifier ».
8. **Incohérence considérant / dispositif** : le considérant 59 annonce des RTS détaillant les exigences des interfaces dédiées, absents de l'Art. 36 ; le mandat existe en réalité à l'Art. 89(1)(f).
9. **Renvoi non recalé Art. 83a(1)** : le paragraphe renvoie aux dispositifs « as referred to in paragraph 3 », alors que ce sont les §3 (conservation) et §4 (contenu des dispositifs).
10. **Renvoi non recalé Art. 91(6)** : il vise « the disclosure of the aggregate analysis of complaints referred to in Article 90(1) », alors que l'Art. 90(1) ne mentionne aucune analyse agrégée.
11. **Artefact de mise en forme Art. 96(4)** : l'alinéa final disposant que « Paragraphs 1, 3 and 4 of this Article shall apply to the administrative sanctions and other administrative measures laid down in Article 97 » est mal positionné sous le §4.
12. **Références encore en placeholder** : « Regulation XXX (IPR) » à l'Art. 64(3), « règlement XXX [PSR] » dans la PSD3, et toutes les dates sous la forme « [OP please insert the date = X months after the date of entry into force] ». Aucun calendrier absolu ne peut être déduit des deux textes.
13. **PSD3 — articles inexistants** : l'Art. 20 (▌ entre les art. 19 et 21) et l'Art. 47 (▌ entre les art. 46 et 48) n'existent pas ; l'Art. 45a a été ajouté au trilogue. Les points (36), (37), (39), (39a), (40) et (41) de l'art. 2 sont supprimés, la numérotation des définitions étant discontinue (35 → 38 → 39b → 42).
14. **PSD3 Art. 31(6) non numéroté** dans le compromis, alors que l'art. 31(7) y renvoie explicitement (« set out in paragraph 6 »).
15. **PSD3 Art. 44(3) — discordance de dates** : le 1er alinéa autorise la poursuite d'activité jusqu'à T+27, le 2e alinéa fixe la suspension à défaut d'agrément ou d'exemption dès T+21, pour les mêmes petits établissements de paiement.
16. **PSD3 Art. 7(6) — incohérence de base juridique** : le texte annonce des « regulatory standards in accordance with Article 16 of Regulation 1093/2010 » (base des lignes directrices) puis parle de « draft regulatory technical standards » avec habilitation au titre des art. 10 à 14.
17. **PSD3 — annexes manquantes** : l'annexe III (tableau de correspondance visé à l'art. 48) n'est pas présente dans le document, qui s'achève sur l'annexe I ; aucune annexe II n'est mentionnée nulle part.
18. **Clause non définie et non encadrée** : l'Art. 45(1) PSR ouvre l'accès « exceptionnellement via une autre interface sûre et efficace » sans définition, sans critère et sans mandat de RTS. Aucune occurrence des termes « fallback », « fall-back » ou « contingency » dans l'ensemble du PSR.
19. **Screen scraping** : le terme n'apparaît qu'une fois, au considérant 61 (« Access to payments account data without proper identification … should, in any circumstances, never be performed »), sans article miroir dans le dispositif.
20. **Délais manquants** : aucun délai chiffré pour le « préavis plus court » de clôture pour motif AML (Art. 32(3) al. 3), aucun délai de recours à l'Art. 32(4), aucun délai pour la liste machine-readable de l'art. 18(7) PSD3.
21. **Mécanisme de la VoP non reproduit** : l'Art. 50 PSR ne contient aucun mécanisme opérationnel en propre ; les résultats possibles de la vérification et l'action attendue du PSP dans chaque cas ne figurent pas dans le corps du PSR. Il faut le texte consolidé des art. 5c(1) à (7) et 5b(2) du règlement (UE) 260/2012 tel qu'amendé par le règlement (UE) 2024/886 puis par l'Art. 110c du compromis. Le délai de restitution du résultat (« quelques secondes au plus ») n'apparaît qu'au considérant 70.
22. **BNPL** : le sigle n'apparaît nulle part dans le dispositif de la PSD3, seulement aux considérants 34a et 35, qui renvoient à la directive (UE) 2023/2225 sur le crédit aux consommateurs. Aucune disposition opérationnelle, aucun seuil, aucun mandat EBA.
23. **Aucune définition autonome de « fraude »** dans l'Art. 3 du PSR ; le seul rattachement est la définition (38) « données de paiement sensibles ».
