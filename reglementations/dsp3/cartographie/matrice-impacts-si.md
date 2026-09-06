# Matrice d'impacts SI — DSP3 / PSR

> **Version 2 du 2026-08-19, cotation en delta.** Remplace la V1 du 2026-08-19, qui cotait l'état
> d'arrivée réglementaire et surévaluait mécaniquement toute brique déjà touchée par la
> réglementation existante.
>
> Maillon 4 de la chaîne : EXIGENCES → **CARTOGRAPHIE**. Cotation dérivée du référentiel
> `exigences/` (711 exigences, passe du 2026-08-19). Chaque cotation cite ses exigences d'origine.
>
> **Source de vérité unique** pour les impacts SI DSP3/PSR. La vue antérieure par parcours et la V1
> sont archivées dans `_archive/` et ne doivent plus être utilisées.

## Principe de cotation

La V2 cote l'**écart** entre l'obligation DSP3/PSR et ce que le SI doit déjà porter au titre du droit
en vigueur. Une exigence du PSR qui reconduit une obligation déjà portée par la ligne de base ne
génère aucun impact et ne se cote pas.

**Ligne de base (réputée déjà en place, non comptée comme impact) :**

| Texte | Ce qu'il porte déjà |
|---|---|
| **DSP2** (directive (UE) 2015/2366) | Obligations d'information et de transparence, régime des opérations non autorisées et charge de la preuve (art. 72), accès des prestataires tiers aux comptes (art. 66 à 68), procédures de réclamation avec réponse sous 15 jours ouvrables et 35 en cas exceptionnel (art. 101), accès des établissements de paiement aux comptes de paiement (art. 36), cantonnement (art. 10), fonds propres méthodes A, B et C (art. 9), blocage d'instrument (art. 68), dates de valeur (art. 87) |
| **RTS 2018/389** | Authentification forte et dynamic linking, protection des données de sécurité personnalisées, mécanismes de surveillance des opérations (art. 2), interface dédiée et parité de disponibilité et de performance (art. 32(1)), publication trimestrielle des statistiques d'interface et des interfaces client (art. 32(4)), interdiction générale des obstacles (art. 32(3)), documentation technique gratuite et résumé publié avec préavis de 3 mois (art. 30(3)-(4)), facilité de test (art. 30(5)), messages d'erreur explicatifs aux tiers (art. 36(2)), communication sécurisée et certificats qualifiés (art. 34-35) |
| **IPR** (règlement (UE) 2024/886) | Vérification du bénéficiaire obligatoire sur les virements SEPA en euro depuis octobre 2025, avec le mécanisme opérationnel de l'art. 5c du règlement 260/2012 et le régime de responsabilité associé, plus l'alignement de gratuité |
| **RGPD** | Minimisation, limitation de finalité et de conservation, sécurité et pseudonymisation (art. 32), registre des traitements, analyse d'impact (art. 35) |
| **DORA** | Cadre de gestion du risque opérationnel, journalisation, détection, classification et déclaration des incidents, objectifs de rétablissement des fonctions critiques |

**Test anti-inflation appliqué à chaque brique.** Est rétrogradée à 0 toute brique dont la seule
justification est vraie de n'importe quelle réglementation : évolution du modèle de données, nouveaux
champs, catalogage, flux d'alimentation, qualité de la donnée, extension de la supervision,
croissance des volumes de logs. Ces effets sont des conséquences de second ordre, pas des impacts SI
attribuables au texte.

**Barème.**

| Niveau | Condition |
|:-:|---|
| **0** | Reconduction de la ligne de base, ou effet générique de second ordre |
| **1** | Changement nommable et attribuable au PSR ou à la PSD3, au-delà de la ligne de base, absorbé par une brique existante |
| **2** | (a) **capacité nouvelle** : la fonction n'existe aujourd'hui dans aucune entité, même partiellement ; ou (b) **changement de régime** : la fonction existe mais passe d'une obligation de moyens à une obligation de résultat opposable, mesurée, publiée ou sanctionnée, ce qui change son mode d'exploitation |

Le volume de sollicitation d'une brique ne justifie jamais à lui seul un 2.

## Ce que la V2 change par rapport à la V1

28 briques sur 73 changent de cotation, toutes à la baisse.

| Brique | V1 | V2 | Motif du changement |
|---|:-:|:-:|---|
| IAM | 1 | 0 | La limitation et l'enregistrement des accès aux données sensibles relèvent du RGPD art. 32 et de DORA ; l'Art. 80 du PSR les reconduit sans exigence technique propre |
| Gestion des habilitations | 1 | 0 | Même motif : limitation des accès déjà exigée, aucun profil ni règle d'habilitation nommé par le texte |
| PKI (Certificats) | 1 | 0 | Le modèle de certificats est fixé par les RTS 2018/389 art. 34 ; les RTS Art. 89(1)(e) ne sont pas publiés, aucun delta chiffrable à ce stade |
| HSM (Clés cryptographiques) | 1 | 0 | La protection des données de sécurité personnalisées est déjà exigée ; la hausse de volumétrie de signature est un effet générique |
| Data Lake / Data Warehouse | 1 | 0 | Justification réduite à l'évolution du modèle de données et de la rétention, effet de second ordre ; la contrainte réelle est portée par Risque et Archivage |
| BI | 1 | 0 | Le reporting de fraude existe sous DSP2 art. 96(6) et la publication trimestrielle des statistiques d'interface sous RTS 2018/389 art. 32(4) ; l'ajout de champs à deux reportings existants est un effet générique |
| Catalogue de données | 1 | 0 | Effet générique explicitement écarté par le commanditaire : cataloguer et taguer par finalité relève du RGPD, pas du PSR |
| Master Data Management | **2** | 1 | La vérification du bénéficiaire et le référentiel de noms opposable existent déjà au titre de l'IPR depuis octobre 2025 ; le delta est une extension de périmètre, pas un changement de nature |
| Qualité et lineage | 1 | 0 | « La qualité de la donnée conditionne le dispositif » est le type même de justification générique |
| Anonymisation / Pseudonymisation | 1 | 0 | Pseudonymisation exigée par le RGPD art. 32, facilité de test sans données personnelles déjà imposée par les RTS 2018/389 art. 30(5) |
| ETL | 1 | 0 | « Les flux d'alimentation sont impactés » est un effet générique |
| API | **2** | 1 | La parité, la publication des statistiques, la facilité de test et le préavis de changement existent déjà sous les RTS 2018/389 ; le delta réel porte sur l'extension fonctionnelle et sur la remontée des obstacles au niveau du règlement, sans changement de régime au sens (b) |
| Streaming | 1 | 0 | La contrainte de latence est portée par les briques Risque et Paiements ; « des topics en plus » est un effet de second ordre |
| Évènements | 1 | 0 | « De nouveaux évènements circulent » est un effet générique ; les notifications sont cotées sur les briques métier qui les produisent |
| Catalogue (gouvernance intégration) | 1 | 0 | Documentation gratuite, résumé publié et préavis de changement déjà imposés par les RTS 2018/389 art. 30(3)-(4) ; le préavis passe même de 3 à 2 mois |
| Sécurité (gouvernance intégration) | 1 | 0 | Refus d'accès motivé et signalement immédiat à l'autorité déjà prévus par DSP2 art. 68(5) |
| Monitoring (gouvernance intégration) | **2** | 1 | L'instrumentation comparative interface dédiée contre interfaces client existe déjà : les RTS 2018/389 art. 32(4) imposent la publication trimestrielle des deux séries ; le delta porte sur la définition des indicateurs de performance et sur le temps de rétablissement |
| Chiffrement TLS | 1 | 0 | La V1 constatait elle-même l'absence de changement de doctrine cryptographique |
| Load Balancer | 1 | 0 | La parité de temps de réponse est déjà imposée par les RTS 2018/389 art. 32(1) et le seuil de 30 secondes figure dans les orientations EBA/GL/2018/07 |
| PCA | 1 | 0 | Continuité d'activité couverte par DORA ; l'accès permanent à l'interface reconduit les RTS 2018/389 |
| Supervision infra | 1 | 0 | Indicateurs de disponibilité et seuil de présomption déjà en place au titre des RTS 2018/389 et des orientations EBA |
| Supervision applicative (Logs) | 1 | 0 | Les messages de notification explicatifs aux tiers sont déjà imposés par les RTS 2018/389 art. 36(2) |
| SIEM | 1 | 0 | Les facteurs de risque alimentent le moteur de fraude, pas le SIEM ; la journalisation de sécurité relève de DORA |
| Crédits | 1 | 0 | Le blocage pour risque de défaut sensiblement accru existe sous DSP2 art. 68(2) et le plafond de 12 mois du crédit accessoire sous DSP2 art. 18(4) ; la réévaluation sous 2 jours ouvrables est cotée sur Gestion des comptes |
| RH | 1 | 0 | Un programme de formation n'est pas un impact SI |
| Comptabilité | 1 | 0 | Dates de valeur, rétablissement du compte et remboursement au prorata sont repris à l'identique de DSP2 art. 87, 73(1) et 55(2) |
| CRM | 1 | 0 | « Enrichir le référentiel de préférences de contact » est un effet de second ordre ; les parcours de notification sont cotés sur Paiements et Parcours clients |
| Ticketing | **2** | 1 | La procédure de réclamation avec réponse sous 15 jours ouvrables, 35 au maximum, traitant tous les points soulevés, est reprise mot pour mot de DSP2 art. 101 ; le delta se limite à la décision motivée de remboursement et au signalement des motifs de fraude à l'autorité |

Cotations confirmées malgré le réexamen de vigilance : **Authentification simple / MFA** (2, au titre
du changement de régime de l'Art. 88), **Risque** (2, au titre du volet bénéficiaire inexistant),
**Conformité KYC** (2, au titre du passage à une décision opposable et sanctionnée),
**Gestion des comptes** (2, au titre du plafond devenu paramètre client opposable).

## Synthèse

| Domaine SI | Nb 2 | Nb 1 | Nb 0 | Message en une phrase, orienté nouveau contre adaptation |
|---|---:|---:|---:|---|
| Gestion des identités et accès | 2 | 2 | 7 | Deux capacités nouvelles ou en changement de régime, le tableau de bord de consentement et le socle de SCA accessible ; tout le reste de l'IAM interne est déjà couvert par le RGPD et les RTS 2018/389. |
| Données | 1 | 4 | 5 | Une seule vraie création, le registre des consentements ; la gouvernance de la donnée sort du périmètre, le référentiel de noms n'étant qu'une extension du service IPR existant. |
| Intégration / Interopérabilité | 0 | 4 | 9 | Aucune brique nouvelle : l'interface d'accès, sa mesure et sa documentation existent depuis les RTS 2018/389, le delta est fonctionnel et se traite en adaptation. |
| Infrastructure & Environnements d'exécution | 1 | 1 | 13 | Domaine quasi hors périmètre, à l'exception du socle de preuve, qui doit couvrir des objets sans équivalent DSP2. |
| Monitoring et Reporting | 0 | 2 | 5 | Aucune création : deux procédures ajoutées à des dispositifs existants, la notification DSA aux hébergeurs et le reporting prudentiel des filiales. |
| Applications Métiers | 6 | 5 | 6 | Le texte se concentre ici : six briques portent des cinématiques sans équivalent, du retour de fonds côté bénéficiaire au parcours de remboursement pour usurpation de canal. |
| **Total** | **10** | **18** | **45** | Près des deux tiers du SI hors périmètre une fois la ligne de base retirée, dix briques réellement en refonte, dix-huit en adaptation. |

Rappel V1 pour mémoire : 14 briques cotées 2, 38 cotées 1, 21 cotées 0.

## Vue d'ensemble

| Domaine SI | Sous-domaine | Brique | Niveau |
|---|---|---|:-:|
| Gestion des identités et accès | Identification | IAM | 0 |
| Gestion des identités et accès | Identification | Annuaire / Active Directory | 0 |
| Gestion des identités et accès | Identification | Provisioning / Déprovisioning | 0 |
| Gestion des identités et accès | Authentification | SSO (SAML / OAuth / OIDC) | 1 |
| Gestion des identités et accès | Authentification | Identité physique et applicative (NHI) | 1 |
| Gestion des identités et accès | Authentification | Authentification simple / MFA | **2** |
| Gestion des identités et accès | Autorisation et gestion des accès | CIAM (Consentement) | **2** |
| Gestion des identités et accès | Autorisation et gestion des accès | Gestion des habilitations | 0 |
| Gestion des identités et accès | Chiffrement et gestion des clés | PKI (Certificats) | 0 |
| Gestion des identités et accès | Chiffrement et gestion des clés | HSM (Clés cryptographiques) | 0 |
| Gestion des identités et accès | Chiffrement et gestion des clés | Vault de secrets | 0 |
| Données | Usages de la donnée | Opérationnelles (GED, CRM, ERP) | 1 |
| Données | Usages de la donnée | Data Lake / Data Warehouse | 0 |
| Données | Usages de la donnée | BI | 0 |
| Données | Gouvernance de la donnée | Catalogue de données | 0 |
| Données | Gouvernance de la donnée | Master Data Management | 1 |
| Données | Gouvernance de la donnée | Référentiels et nomenclature | 1 |
| Données | Gouvernance de la donnée | Qualité et lineage | 0 |
| Données | Cycle de vie et protection | Anonymisation / Pseudonymisation | 0 |
| Données | Cycle de vie et protection | Usage et Consentement | **2** |
| Données | Cycle de vie et protection | Archivage / Suppression | 1 |
| Intégration / Interopérabilité | Middleware d'intégration | ETL | 0 |
| Intégration / Interopérabilité | Middleware d'intégration | ESB / Messaging | 1 |
| Intégration / Interopérabilité | Middleware d'intégration | API | 1 |
| Intégration / Interopérabilité | Gestion des flux temps réel | Streaming | 0 |
| Intégration / Interopérabilité | Gestion des flux temps réel | Évènements | 0 |
| Intégration / Interopérabilité | Gestion des flux temps réel | Batch | 1 |
| Intégration / Interopérabilité | Gouvernance | Catalogue | 0 |
| Intégration / Interopérabilité | Gouvernance | Sécurité | 0 |
| Intégration / Interopérabilité | Gouvernance | Monitoring | 1 |
| Intégration / Interopérabilité | Sécurité des communications | Chiffrement TLS | 0 |
| Intégration / Interopérabilité | Sécurité des communications | VPN | 0 |
| Intégration / Interopérabilité | Sécurité des communications | Segmentation réseau | 0 |
| Intégration / Interopérabilité | Sécurité des communications | Firewalls | 0 |
| Infrastructure & Environnements d'exécution | Infrastructures physiques | Datacenters | 0 |
| Infrastructure & Environnements d'exécution | Infrastructures physiques | Serveurs | 0 |
| Infrastructure & Environnements d'exécution | Infrastructures physiques | Stockage | 0 |
| Infrastructure & Environnements d'exécution | Infrastructures physiques | Réseau | 0 |
| Infrastructure & Environnements d'exécution | Cloud et Virtualisation | IaaS / PaaS | 0 |
| Infrastructure & Environnements d'exécution | Cloud et Virtualisation | CaaS / Conteneurs | 0 |
| Infrastructure & Environnements d'exécution | Cloud et Virtualisation | Orchestrateurs | 0 |
| Infrastructure & Environnements d'exécution | Cloud et Virtualisation | FaaS | 0 |
| Infrastructure & Environnements d'exécution | Réseaux et Connectivité | WAN / LAN / SD-WAN | 0 |
| Infrastructure & Environnements d'exécution | Réseaux et Connectivité | Load Balancer | 0 |
| Infrastructure & Environnements d'exécution | Réseaux et Connectivité | Interconnexions Cloud | 0 |
| Infrastructure & Environnements d'exécution | Résilience | PCA | 0 |
| Infrastructure & Environnements d'exécution | Résilience | PRA | 1 |
| Infrastructure & Environnements d'exécution | Résilience | Sauvegarde / Réplication | 0 |
| Infrastructure & Environnements d'exécution | Résilience | Traçabilité et auditabilité | **2** |
| Monitoring et Reporting | Monitoring et Observabilité | Supervision infra | 0 |
| Monitoring et Reporting | Monitoring et Observabilité | Supervision applicative (Logs) | 0 |
| Monitoring et Reporting | Surveillance et Détection | SIEM | 0 |
| Monitoring et Reporting | Surveillance et Détection | SOC | 1 |
| Monitoring et Reporting | Surveillance et Détection | Détection d'intrusion | 0 |
| Monitoring et Reporting | Reporting et Auditabilité | Reporting extra financier (RSE) | 0 |
| Monitoring et Reporting | Reporting et Auditabilité | Reporting financier | 1 |
| Applications Métiers | Core Banking | Gestion des comptes | **2** |
| Applications Métiers | Core Banking | Paiements / Transactions | **2** |
| Applications Métiers | Core Banking | Crédits | 0 |
| Applications Métiers | Core Banking | Dépôts / Liquidité | 1 |
| Applications Métiers | Front office | Web | 1 |
| Applications Métiers | Front office | Mobile | **2** |
| Applications Métiers | Front office | Parcours clients | **2** |
| Applications Métiers | Middle & back-office | Conformité (KYC) | **2** |
| Applications Métiers | Middle & back-office | Risque | **2** |
| Applications Métiers | Middle & back-office | RH | 0 |
| Applications Métiers | Middle & back-office | Comptabilité | 0 |
| Applications Métiers | Gestion de la relation client | CRM | 0 |
| Applications Métiers | Gestion de la relation client | ERP | 0 |
| Applications Métiers | Gestion de la relation client | Ticketing | 1 |
| Applications Métiers | Outils de collaboration | Messagerie | 1 |
| Applications Métiers | Outils de collaboration | Partage & Gestion doc | 0 |
| Applications Métiers | Outils de collaboration | Téléphonie | 1 |

## Cotation détaillée

### Gestion des identités et accès

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| IAM | 0 | RGPD art. 32 et DORA : limitation et enregistrement des accès aux données sensibles | Aucun. L'Art. 80 du PSR reprend le standard RGPD sans exigence technique propre ; le processus documenté du dossier d'agrément est un livrable de conformité, pas un développement | DSP3-EX-456, DSP3-EX-457, DSP3-EX-458, DSP3-EX-522 | aucune | haute |
| Annuaire / Active Directory | 0 | Sans objet | Aucune exigence ne porte sur l'annuaire des identités internes | aucune | aucune | haute |
| Provisioning / Déprovisioning | 0 | Sans objet | Aucune exigence sur le cycle de vie des comptes collaborateurs | aucune | aucune | haute |
| SSO (SAML / OAuth / OIDC) | 1 | RTS 2018/389 art. 30 à 32 : session d'authentification, appui sur les procédures de l'ASPSP ; RTS 2018/389 **art. 10**, tel que modifié par le règlement délégué (UE) 2022/2360 (90 → 180 jours, applicable depuis le 25/07/2023) : renouvellement de la SCA pour l'accès aux informations de compte | La SCA n'est plus applicable qu'au premier accès d'un AISP donné, et non plus tous les 180 jours côté ASPSP ; trois obstacles nouvellement nommés touchent directement le serveur d'autorisation : parcours de redirection ajoutant des étapes, redirection automatique, double SCA dans un parcours d'initiation seule | DSP3-EX-171, DSP3-EX-398, DSP3-EX-399, DSP3-EX-400 | DSP3-H04 | à confirmer par cinématique |
| Identité physique et applicative (NHI) | 1 | DSP2 art. 15 : registre EBA des prestataires agréés, consultable | La PSD3 crée une liste centrale **lisible par machine** des prestataires offrant les services 6 et 7 de l'annexe I, avec identifiant et statut d'agrément ; la vérification du statut du tiers devient une consommation automatisée à intégrer au contrôle d'accès de l'interface | DSP3-EX-147, DSP3-EX-551, DSP3-EX-556 | aucune | haute |
| Authentification simple / MFA | **2** | RTS 2018/389 : SCA, dynamic linking, protection des données de sécurité personnalisées, exemptions | Changement de régime au sens (b). L'Art. 88 n'a aucun équivalent DSP2 : il impose une obligation de résultat opposable et sanctionnée de fournir plus d'un moyen de SCA, dont au moins un gratuit et adapté aux clients sans accès numérique, et interdit de faire dépendre la SCA de la possession d'un smartphone. Cela remet en cause les trajectoires de décommissionnement des moyens non mobiles. S'y ajoutent quatre déclencheurs de SCA nommés qui n'étaient pas explicités : création ou remplacement d'un instrument tokenisé, augmentation de plafond, changement de mot de passe en ligne, changement de coordonnées en ligne | DSP3-EX-384, DSP3-EX-394, DSP3-EX-402, DSP3-EX-403, DSP3-EX-404, DSP3-EX-405 | DSP3-H14, DSP3-H15, DSP3-H16 | haute |
| CIAM (Consentement) | **2** | Rien d'équivalent. Sous DSP2, l'ASPSP ne connaît pas les consentements donnés aux tiers, et l'Art. 49(4) du PSR lui interdit même de les vérifier | Capacité nouvelle au sens (a). Le tableau de bord de l'Art. 43, intégré aux canaux client, affiche chaque consentement en cours avec sa finalité, sa période de validité, les catégories de données partagées et les dates de consultation, permet le retrait gratuit et le rétablissement sous 48 heures, et proscrit toute conception orientant le client | DSP3-EX-183, DSP3-EX-184, DSP3-EX-186, DSP3-EX-187 | DSP3-H17 | haute |
| Gestion des habilitations | 0 | RGPD art. 32, DORA, et politique d'accès du dossier d'agrément | Aucun. Le texte exige la limitation des accès sans nommer de profil, de règle ni de granularité qui n'existerait pas déjà | DSP3-EX-458, DSP3-EX-522 | aucune | haute |
| PKI (Certificats) | 0 | RTS 2018/389 art. 34 et 35 : certificats qualifiés eIDAS, standards de communication reconnus, intégrité et confidentialité des données de sécurité personnalisées | Aucun delta chiffrable à ce stade. Le PSR renvoie le détail aux RTS de l'Art. 89(1)(e), non publiés. ⚠️ À revisiter à la publication de ces RTS, la cotation pouvant remonter | DSP3-EX-136, DSP3-EX-145, DSP3-EX-409 | aucune | à confirmer par cinématique |
| HSM (Clés cryptographiques) | 0 | RTS 2018/389 art. 22 à 27 : protection des données de sécurité personnalisées ; DSP2 pour le cycle de vie des clés | Aucun. La hausse de volumétrie de signature liée à l'élargissement des déclencheurs de SCA est un effet générique de second ordre | DSP3-EX-237, DSP3-EX-391 | aucune | haute |
| Vault de secrets | 0 | Sans objet | Aucune exigence sur la gestion des secrets applicatifs internes | aucune | aucune | haute |

### Données

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| Opérationnelles (GED, CRM, ERP) | 1 | DSP2 art. 41 à 47 : information sur support durable, mise à disposition du contrat-cadre sur demande ; DSP2 art. 72 : charge de la preuve du PSP | Le PSP doit fournir à l'utilisateur, sur demande et pendant 18 mois, les moyens de prouver **que celui-ci a effectué sa notification** de perte, vol ou usage non autorisé. C'est un objet de preuve produit au bénéfice du client, sans équivalent DSP2, qui suppose un accusé opposable et conservé | DSP3-EX-242, DSP3-EX-053, DSP3-EX-535 | aucune | haute |
| Data Lake / Data Warehouse | 0 | RGPD : minimisation, limitation de finalité et de conservation | Aucun impact propre. Le changement de modèle de données et de rétention est un effet de second ordre ; les contraintes réelles portent sur les briques Risque, qui exécute le monitoring, et Archivage, qui porte les durées | DSP3-EX-353, DSP3-EX-354, DSP3-EX-355 | aucune | haute |
| BI | 0 | DSP2 art. 96(6) et orientations EBA/GL/2018/05 : reporting statistique de fraude ; RTS 2018/389 art. 32(4) : publication trimestrielle des statistiques d'interface | Aucun impact propre. L'ajout du nombre et de la valeur des remboursements refusés avec leur motif est un champ de plus dans un reporting déjà produit ; la mesure comparative d'interface est cotée sur la brique Monitoring de l'intégration | DSP3-EX-337, DSP3-EX-338 | DSP3-H24 | haute |
| Catalogue de données | 0 | RGPD : registre des traitements, limitation des finalités, minimisation | Aucun. Inventorier et taguer par finalité est une obligation RGPD préexistante. Effet générique explicitement écarté | DSP3-EX-456, DSP3-EX-457 | aucune | haute |
| Master Data Management | 1 | IPR : la vérification du bénéficiaire est en production depuis octobre 2025 sur les virements SEPA en euro, avec le référentiel de noms, la logique de concordance approchante et le régime de responsabilité de l'art. 5c du règlement 260/2012 | Extension de périmètre du service existant, sans changement de nature : l'Art. 50 applique l'art. 5c mutatis mutandis à tous les virements, y compris hors champ du règlement 260/2012, donc hors euro, et lit les renvois à l'IBAN comme visant tout identifiant unique. S'y ajoute l'obligation d'identifier le bénéficiaire par son nom commercial dans l'information post-ordre. Le mécanisme opérationnel n'est pas reproduit dans le PSR | DSP3-EX-248, DSP3-EX-249, DSP3-EX-044, DSP3-EX-061 | DSP3-H07, DSP3-H08 | à confirmer par cinématique |
| Référentiels et nomenclature | 1 | IPR et règlement 260/2012 : nomenclature IBAN | L'IBAN virtuel entre au règlement 260/2012 comme identifiant de compte de paiement valide partout où un IBAN est requis, ce qui ouvre une question de qualification et de contrôle sur les référentiels d'identifiants, y compris au regard du LCB-FT | DSP3-EX-250, DSP3-EX-249 | DSP3-H06, DSP3-H27 | à confirmer par cinématique |
| Qualité et lineage | 0 | RGPD art. 5(1)(d) : exactitude des données ; IPR : la qualité du référentiel de noms conditionne déjà la réponse de vérification | Aucun. « La qualité de la donnée conditionne le dispositif » est une justification générique ; l'exposition à responsabilité est cotée sur Master Data Management et Traçabilité | DSP3-EX-259, DSP3-EX-350 | DSP3-H10 | haute |
| Anonymisation / Pseudonymisation | 0 | RGPD art. 32 : pseudonymisation ; RTS 2018/389 art. 30(5) : facilité de test, sans données de production | Aucun. Le dispositif de partage impose des mesures « permettant la pseudonymisation », ce qui reprend le standard RGPD ; l'interdiction de données personnelles dans la facilité de test reconduit la pratique imposée depuis 2019 | DSP3-EX-142, DSP3-EX-359 | DSP3-H11 | haute |
| Usage et Consentement | **2** | Rien d'équivalent | Capacité nouvelle au sens (a). Un registre des consentements est à créer côté ASPSP, alimenté par les prestataires tiers qui transmettent finalité, période de validité et catégories de données, resynchronisé à chaque changement dans les deux sens, avec rétablissement d'un accès retiré sous 48 heures et conservation de l'historique des consentements retirés ou expirés pendant deux ans. Le protocole d'échange n'existe dans aucune interface DSP2 | DSP3-EX-184, DSP3-EX-188, DSP3-EX-190, DSP3-EX-191 | DSP3-H17 | haute |
| Archivage / Suppression | 1 | RGPD : limitation de conservation, sans durée chiffrée ; DSP2 : aucune durée de rétention pour les données de surveillance | Quatre durées maximales chiffrées et opposables apparaissent, assorties d'une obligation de suppression active : 5 ans après la fin de la relation pour les données de monitoring, 5 ans après l'opération suspectée pour les données reçues via le partage inter-PSP, 2 ans pour l'historique des consentements, 18 mois pour la preuve de notification | DSP3-EX-355, DSP3-EX-360, DSP3-EX-184, DSP3-EX-242 | aucune | haute |

### Intégration / Interopérabilité

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| ETL | 0 | Sans objet | Aucun. « Les flux d'alimentation du monitoring et du reporting sont impactés » est un effet générique de second ordre | aucune | aucune | haute |
| ESB / Messaging | 1 | Rien d'équivalent pour les messages concernés : DSP2 ne connaît ni le retour de fonds côté bénéficiaire ni la notification de refus sous contrainte de latence | Messages inter-PSP nouveaux à router. **Deux obligations distinctes à 10 secondes, de sens inverse, à ne pas fusionner** (vérifiées sur ST-8221 le 2026-08-31) : (1) le PSP du **payeur** notifie le refus au payeur et met l'information à disposition du **PISP** (Art. 65(1) al. 3 — ⚠️ et non au PSP du bénéficiaire, contrairement à ce qu'indiquait la note de propositions du 27/08) ; (2) le PSP du **bénéficiaire** notifie au PSP du **payeur** le retour de fonds et les motifs du refus (Art. 69(2d)(i)), et crédite immédiatement les fonds déjà reçus (Art. 69(2d)(ii)). Dans les deux cas le point de départ des 10 secondes est la **réception de l'ordre par le PSP du payeur**, non la décision, et les deux ne valent que pour le virement instantané. S'y ajoutent le rétablissement du compte du payeur dans son état antérieur et les échanges du dispositif de partage sur la fraude. La contrainte tipping-off (Art. 73(5) du règlement (UE) 2024/1624) encadre le contenu | DSP3-EX-426, DSP3-EX-442, DSP3-EX-445, DSP3-EX-446, DSP3-EX-357 | DSP3-H11 | à confirmer par cinématique |
| API | 1 | RTS 2018/389 : interface dédiée obligatoire (art. 30), parité permanente de disponibilité et de performance (art. 32(1)), interdiction des obstacles (art. 32(3)), publication trimestrielle des statistiques (art. 32(4)), documentation gratuite avec résumé publié et préavis de 3 mois (art. 30(3)-(4)), facilité de test (art. 30(5)), messages d'erreur explicatifs (art. 36(2)) | Ni capacité nouvelle ni changement de régime : la parité était déjà une obligation de résultat mesurée et publiée. Le delta est fonctionnel et normatif. **Neuf** fonctions d'initiation minimales sont désormais imposées — Art. 36(4) points (a) à (g), (ha) et (hc), les points (h) et (hb) ayant été supprimés au trilogue, ce qui explique le comptage erroné à huit (vérifié sur ST-8221 le 2026-08-31) — dont l'ordre permanent, le paiement à date future, les paiements vers plusieurs bénéficiaires, la vérification du nom du titulaire avant initiation et le choix de la procédure d'authentification. Douze obstacles nommés remontent au niveau du règlement, liste explicitement non limitative (Art. 44(1)). Le déclencheur de la suppression immédiate n'est pas une demande de l'autorité mais **l'identification de l'obstacle, d'où qu'elle vienne, y compris sur information transmise par un AISP ou un PISP** (Art. 48(1), vérifié sur ST-8221 le 2026-08-31) ; l'autorité prend alors les mesures d'exécution et les sanctions appropriées. Le préavis de changement passe de 3 à 2 mois | DSP3-EX-149, DSP3-EX-171, DSP3-EX-172, DSP3-EX-138, DSP3-EX-173 | DSP3-H04, DSP3-H05, DSP3-H06 | haute |
| Streaming | 0 | Sans objet | Aucun impact propre. La contrainte de latence du monitoring avant exécution et avant mise à disposition des fonds est cotée sur les briques Risque et Paiements, qui la portent | DSP3-EX-347, DSP3-EX-348 | aucune | haute |
| Évènements | 0 | Sans objet | Aucun. « De nouveaux types d'évènements circulent » est un effet générique ; chaque notification est cotée sur la brique métier qui la déclenche | DSP3-EX-227, DSP3-EX-379, DSP3-EX-447 | aucune | haute |
| Batch | 1 | DSP2 art. 78 et 87 : heure limite de réception, délai d'exécution, dates de valeur, tous repris à l'identique ; IPR : vérification du bénéficiaire, sans régime propre aux lots | Un régime batch spécifique apparaît pour la vérification du bénéficiaire : les non-consommateurs peuvent convenir que la vérification intervienne **après** l'autorisation, y compris pour les ordres en lot, avec exécution sans intervention supplémentaire dans trois cas seulement, et un opt-out réservé aux canaux d'initiation automatisés dédiés | DSP3-EX-252, DSP3-EX-253 | DSP3-H09 | haute |
| Catalogue (gouvernance) | 0 | RTS 2018/389 art. 30(3)-(4) : documentation technique gratuite et sans retard, résumé publié sur le site, préavis de 3 mois sur tout changement, documentation des changements d'urgence | Aucun. Le PSR reconduit le dispositif et raccourcit même le préavis à 2 mois | DSP3-EX-137, DSP3-EX-138, DSP3-EX-139 | aucune | haute |
| Sécurité (gouvernance) | 0 | DSP2 art. 68(5) : refus d'accès au tiers pour raisons objectivement justifiées, information de l'utilisateur et notification immédiate à l'autorité ; RTS 2018/389 : intégrité et confidentialité des données transmises via les tiers | Aucun. La clause de sauvegarde antifraude de l'Art. 44(1a) encadre une faculté déjà exercée, sans créer de contrôle technique nouveau | DSP3-EX-169, DSP3-EX-170, DSP3-EX-172 | aucune | haute |
| Monitoring (gouvernance) | 1 | RTS 2018/389 art. 32(4) : publication trimestrielle de la disponibilité et de la performance de l'interface dédiée **et** des interfaces client ; orientations EBA/GL/2018/07 : présomption d'indisponibilité après 5 requêtes consécutives sans réponse sous 30 secondes | L'instrumentation comparative existe déjà. Le delta porte sur la définition imposée de la performance, désormais mesurée par le ratio de requêtes d'information réussies et par le nombre et le volume de requêtes d'initiation réussies, et sur l'ajout d'un temps de rétablissement optimal gradué par sévérité d'incident, à fixer par RTS | DSP3-EX-140, DSP3-EX-158, DSP3-EX-160 | aucune | haute |
| Chiffrement TLS | 0 | RTS 2018/389 art. 35 : sécurité des canaux de communication | Aucun changement de doctrine cryptographique | DSP3-EX-145, DSP3-EX-241 | aucune | haute |
| VPN | 0 | Sans objet | Aucune exigence sur les accès distants | aucune | aucune | haute |
| Segmentation réseau | 0 | DORA chapitre II | Aucune exigence de segmentation propre au PSR | aucune | aucune | haute |
| Firewalls | 0 | Sans objet | Aucune exigence de filtrage réseau ; les pouvoirs de blocage d'interface s'exercent côté autorité | aucune | aucune | haute |

### Infrastructure & Environnements d'exécution

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| Datacenters | 0 | DORA | Aucune exigence d'hébergement physique | aucune | aucune | haute |
| Serveurs | 0 | DORA | Aucune exigence sur le socle serveur | aucune | aucune | haute |
| Stockage | 0 | DORA | Aucune exigence sur le stockage ; les contraintes de rétention portent sur les briques de données | aucune | aucune | haute |
| Réseau | 0 | DORA | Aucune exigence sur l'infrastructure réseau physique | aucune | aucune | haute |
| IaaS / PaaS | 0 | DORA chapitre V : externalisation et prestataires tiers critiques | L'externalisation est traitée sous l'angle contractuel et prudentiel, sans exigence technique sur le socle cloud | aucune | aucune | haute |
| CaaS / Conteneurs | 0 | DORA | Aucune exigence sur les plateformes de conteneurs | aucune | aucune | haute |
| Orchestrateurs | 0 | DORA | Aucune exigence sur l'orchestration | aucune | aucune | haute |
| FaaS | 0 | DORA | Aucune exigence sur les fonctions managées | aucune | aucune | haute |
| WAN / LAN / SD-WAN | 0 | DORA | Aucune exigence sur les réseaux d'entreprise | aucune | aucune | haute |
| Load Balancer | 0 | RTS 2018/389 art. 32(1) : parité de temps de réponse ; orientations EBA/GL/2018/07 : seuil de 30 secondes | Aucun. La politique de répartition et de capacité sur le chemin API est déjà dimensionnée sur ces deux contraintes | DSP3-EX-146, DSP3-EX-153, DSP3-EX-156 | aucune | haute |
| Interconnexions Cloud | 0 | DORA | Aucune exigence sur les interconnexions | aucune | aucune | haute |
| PCA | 0 | DORA chapitre II : politique de continuité et tests ; RTS 2018/389 art. 33 : mécanisme de contingence garantissant la continuité pour les tiers | Aucun. L'obligation de permettre l'accès à l'interface en permanence reconduit l'objectif de continuité déjà porté. ⚠️ La disparition du mécanisme de secours obligatoire est traitée par DSP3-H04, côté trajectoire API | DSP3-EX-135, DSP3-EX-459 | DSP3-H04 | haute |
| PRA | 1 | DORA art. 11 et 12 : objectifs de rétablissement définis par l'établissement pour ses fonctions critiques | Le temps de rétablissement de l'interface dédiée cesse d'être auto-défini : un temps de rétablissement optimal, gradué selon le nombre de clients impactés et les fonctionnalités affectées, sera fixé par RTS, avec obligation d'informer les tiers des mesures prises et de la durée estimée de résolution | DSP3-EX-158, DSP3-EX-160 | aucune | à confirmer par cinématique |
| Sauvegarde / Réplication | 0 | DORA | Aucune exigence de sauvegarde ou de réplication | aucune | aucune | haute |
| Traçabilité et auditabilité | **2** | DSP2 art. 72 : le PSP prouve que l'opération a été authentifiée, correctement enregistrée et comptabilisée, et que l'usage de l'instrument enregistré ne suffit pas nécessairement | Capacité nouvelle au sens (a) sur les objets de preuve. Le PSR interdit de se fonder sur la seule authentification, impose d'inviter l'utilisateur à documenter les évènements ayant précédé l'opération et d'intégrer sa réponse à l'analyse, et crée trois objets de preuve sans équivalent : la preuve que le monitoring a été effectué par **les deux** PSP, la preuve de l'absence de manquement à l'obligation de suspension, la preuve de l'absence de manquement au retour de fonds. Le véhicule inter-PSP de la première n'existe pas | DSP3-EX-259, DSP3-EX-260, DSP3-EX-350, DSP3-EX-420, DSP3-EX-441 | DSP3-H10 | haute |

### Monitoring et Reporting

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| Supervision infra | 0 | RTS 2018/389 art. 32(4) : sondes produisant les indicateurs de disponibilité et de performance ; orientations EBA/GL/2018/07 : seuil de présomption d'indisponibilité | Aucun. Le paramétrage et le périmètre de mesure sont en place depuis 2019 | DSP3-EX-153, DSP3-EX-156 | aucune | haute |
| Supervision applicative (Logs) | 0 | RTS 2018/389 art. 36(2) : messages de notification explicatifs au tiers en cas d'évènement inattendu ou d'erreur ; art. 30(4) : documentation des changements d'urgence ; DORA : journalisation | Aucun. « Les logs augmentent » est un effet générique | DSP3-EX-143, DSP3-EX-139 | aucune | haute |
| SIEM | 0 | DORA : détection, classification et corrélation des évènements de sécurité ; RTS 2018/389 art. 2 : mécanismes de surveillance des opérations | Aucun impact propre. Les cinq facteurs de risque imposés alimentent le moteur de fraude, coté sur la brique Risque, et non la corrélation de sécurité | DSP3-EX-356 | aucune | haute |
| SOC | 1 | DSP2 art. 68(5) : signalement immédiat à l'autorité du refus d'accès à un tiers ; DORA : déclaration des incidents majeurs | Une procédure opérationnelle nouvelle apparaît : le PSP doit, sans retard indu, notifier aux fournisseurs de services d'hébergement les contenus frauduleux à l'origine d'une fraude de paiement, en suivant la procédure des articles 16 ou 22 du DSA. Aucun canal ni format n'existe aujourd'hui pour cette notification sortante | DSP3-EX-327 | aucune | haute |
| Détection d'intrusion | 0 | DORA | Aucune exigence de détection d'intrusion réseau ; les signaux de compromission des terminaux sont portés par le moteur de fraude | aucune | aucune | haute |
| Reporting extra financier (RSE) | 0 | Sans objet | Aucune exigence de reporting extra financier dans le PSR ni dans la PSD3 | aucune | aucune | haute |
| Reporting financier | 1 | DSP2 art. 5 et 9 : information comptable séparée auditée, fonds propres méthodes A, B et C ; DSP2 art. 10 : cantonnement | La PSD3 ajoute la méthode D, soit au moins 2 % de la monnaie électronique en circulation moyenne pour les établissements n'offrant que l'émission de monnaie électronique, et impose un rapprochement des fonds cantonnés dont le calcul et la périodicité seront précisés par RTS. Le périmètre s'élargit aux filiales de monnaie électronique, l'annexe I en faisant un service de paiement | DSP3-EX-624, DSP3-EX-640, DSP3-EX-533, DSP3-EX-030 | DSP3-H21 | haute |

### Applications Métiers

| Brique | Niveau | Déjà exigé sous DSP2, RTS 2018/389, IPR, RGPD ou DORA | Delta apporté par DSP3/PSR | Exigences | Hypothèses | Confiance |
|---|:-:|---|---|---|---|---|
| Gestion des comptes | **2** | DSP2 art. 68(1) : le PSP **peut** convenir de limites de dépense avec le payeur ; DSP2 art. 68(2) à (4) : blocage d'instrument et déblocage | Changement de régime au sens (b). Le plafond cesse d'être une option contractuelle à la main du PSP pour devenir un paramètre appartenant au client : il le fixe au seul choix de sa granularité, par moyen de paiement y compris les virements, par instrument, par opération ou par période, et le PSP ne peut plus le modifier unilatéralement. Toute augmentation demandée à distance ne prend effet qu'après 4 heures, délai que le client peut lui-même ajuster ou désactiver, avec notification immédiate à trois moments. S'y ajoute la réévaluation du maintien d'un blocage sous 2 jours ouvrables | DSP3-EX-223, DSP3-EX-224, DSP3-EX-225, DSP3-EX-226, DSP3-EX-227, DSP3-EX-228, DSP3-EX-231 | DSP3-H06, DSP3-H13 | haute |
| Paiements / Transactions | **2** | IPR : vérification du bénéficiaire intégrée au flux de virement SEPA en euro ; DSP2 art. 79 : refus d'exécution et notification du motif | Capacité nouvelle au sens (a) sur deux cinématiques sans équivalent. Côté payeur, la suspension d'un ordre en cas de soupçon objectivement justifié, avec reprise de contact du payeur, décision documentée et rétablissement du compte dans son état antérieur ; l'exception d'un caractère simplement inhabituel est écartée. Côté bénéficiaire, la non-mise à disposition des fonds et leur retour au PSP du payeur lorsque les motifs de fraude sont clairs et incontestables, avec notification des motifs et recréditation en 10 secondes sur virement instantané | DSP3-EX-418, DSP3-EX-421, DSP3-EX-422, DSP3-EX-436, DSP3-EX-437, DSP3-EX-442, DSP3-EX-445, DSP3-EX-447 | DSP3-H10, DSP3-H12 | haute |
| Crédits | 0 | DSP2 art. 68(2) : blocage d'un instrument à ligne de crédit pour risque de défaut sensiblement accru ; DSP2 art. 18(4) : crédit accessoire plafonné à 12 mois et non finançable par les fonds cantonnés | Aucun. Les deux régimes sont repris à l'identique ; la réévaluation du blocage sous 2 jours ouvrables est cotée sur Gestion des comptes, qui porte le workflow | DSP3-EX-229, DSP3-EX-641 | aucune | haute |
| Dépôts / Liquidité | 1 | DSP2 art. 10 : cantonnement, non-mélange, dépôt ou investissement au plus tard le jour ouvrable suivant, actifs sûrs liquides à faible risque | Deux obligations nouvelles pèsent sur le dispositif de cantonnement : l'évitement du risque de concentration, formulé en obligation de moyens doublement conditionnée — « éviter, **lorsque c'est approprié**, le risque de concentration » et « **s'efforcer** de ne pas cantonner l'ensemble des fonds auprès d'un seul établissement de crédit » (PSD3 Art. 9(2), vérifié sur ST-8222 le 2026-08-31) — et non en interdiction, et un rapprochement des fonds cantonnés dont le cadre de gestion, la désignation et le calcul seront fixés par RTS | DSP3-EX-631, DSP3-EX-635, DSP3-EX-640 | DSP3-H21 | à confirmer par cinématique |
| Web | 1 | DSP2 art. 45 et 52 : information précontractuelle et contrat-cadre ; DSP2 art. 101 : information sur les voies de recours | Deux affichages nouveaux : les frais estimés de conversion de devise exprimés à la fois en montant dans la devise du compte et en pourcentage de marge au-dessus du taux médian agrégé, communiqués avant chaque initiation de virement ; et l'identification d'au moins une entité de règlement extrajudiciaire, présentée de façon claire et accessible sur le site, dans l'application mobile, en agence et dans les conditions générales | DSP3-EX-076, DSP3-EX-077, DSP3-EX-482 | aucune | haute |
| Mobile | **2** | RTS 2018/389 art. 24 : association des données de sécurité personnalisées à l'utilisateur, sans cinématique imposée | Capacité nouvelle au sens (a). L'activation d'une application mobile devient une cinématique réglementée : authentification forte, second canal de communication distinct, temporisation de 4 heures si l'activation est à distance, ajustable ou désactivable par le client, notification immédiate par un canal différent incluant les instructions à suivre, et neutralisation sans retard indu de l'application sur simple signalement du client. Aucune entité ne dispose aujourd'hui de la temporisation paramétrable par le client | DSP3-EX-377, DSP3-EX-378, DSP3-EX-379, DSP3-EX-380, DSP3-EX-381 | DSP3-H13, DSP3-H15 | haute |
| Parcours clients | **2** | IPR : présentation du résultat de vérification du bénéficiaire sans empêcher l'autorisation ; DSP2 art. 75 : blocage de fonds de montant inconnu subordonné au consentement au montant exact, pour les opérations par carte | Capacité nouvelle au sens (a). Deux parcours n'ont aucun équivalent : le remboursement intégral du consommateur manipulé lorsque la fraude a emprunté un canal attribué au PSP, avec notification accompagnée d'un rapport de police et décision sous 15 jours ouvrables ; et le parcours de reprise de contact après suspension d'un ordre pour soupçon, avec motifs précis, procédure de correction et garantie d'un moyen d'être joint en retour. Le blocage de montant inconnu, lui, s'étend simplement de la carte au virement | DSP3-EX-274, DSP3-EX-275, DSP3-EX-421, DSP3-EX-425, DSP3-EX-244, DSP3-EX-252 | DSP3-H09, DSP3-H12 | haute |
| Conformité (KYC) | **2** | DSP2 art. 36 : les établissements de crédit accordent aux établissements de paiement un accès aux comptes sur une base objective, non discriminatoire et proportionnée, et notifient à l'autorité compétente tout refus dûment motivé | Changement de régime au sens (b). Le refus et la clôture cessent d'être une décision discrétionnaire encadrée par un principe pour devenir une décision opposable : quatre motifs limitatifs, motivation spécifique aux risques posés et explicitement non générique, notification au demandeur **et** à l'autorité sous un mois à compter d'une demande complète, préavis de clôture de quatre mois, prise en compte de la capacité de l'établissement de paiement à respecter son cantonnement, droit de recours et format harmonisé à venir par RTS. Le régime AML fait exception avec une notification aveugle et un préavis raccourci | DSP3-EX-118, DSP3-EX-119, DSP3-EX-121, DSP3-EX-122, DSP3-EX-123, DSP3-EX-125, DSP3-EX-126 | DSP3-H18 | haute |
| Risque | **2** | RTS 2018/389 art. 2 : mécanismes de surveillance des opérations côté PSP du payeur, en obligation de moyens, adossés à la politique d'exemption | Cumul de (a) et (b). Capacité nouvelle : le PSP du bénéficiaire doit exécuter une surveillance avant mise à disposition des fonds, sur un jeu de quatre catégories de données, et décider d'un retour de fonds ; ce volet n'existe nulle part. Changement de régime : le monitoring devient une obligation de résultat, le PSP qui ne l'exécute pas supportant le dommage, et le PSP du payeur devant rembourser à défaut de preuve que la surveillance a été effectuée par les deux PSP. La participation à un dispositif de partage d'informations entre PSP passe de faculté à obligation | DSP3-EX-346, DSP3-EX-347, DSP3-EX-348, DSP3-EX-349, DSP3-EX-350, DSP3-EX-354, DSP3-EX-356, DSP3-EX-357 | DSP3-H10, DSP3-H11, DSP3-H16 | haute |
| RH | 0 | RGPD art. 39 : sensibilisation au traitement des données ; DORA art. 13(6) : formation à la sécurité | Aucun impact SI. Un programme de formation annuel sur les tendances de fraude est un dispositif de conformité, pas une modification du SI | DSP3-EX-374, DSP3-EX-458 | aucune | haute |
| Comptabilité | 0 | DSP2 art. 87 : dates de valeur au débit et au crédit ; DSP2 art. 73(1) : rétablissement du compte avec date de valeur au crédit non postérieure au débit ; DSP2 art. 55(2) : remboursement au prorata des frais périodiques ; DSP2 art. 5 : comptabilité séparée | Aucun. Les quatre règles sont reprises à l'identique | DSP3-EX-453, DSP3-EX-455, DSP3-EX-265, DSP3-EX-059 | aucune | haute |
| CRM | 0 | DSP2 art. 70 : moyens de notification disponibles à tout moment et gratuits ; RGPD : gestion des préférences de contact | Aucun impact propre. L'enrichissement de la stratégie de contact est un effet de second ordre ; l'obligation de garantir un moyen d'être joint en retour après suspension est cotée sur Parcours clients, et l'alerte sur les nouvelles formes de fraude sur Messagerie | DSP3-EX-368, DSP3-EX-421 | aucune | haute |
| ERP | 0 | Sans objet | Aucune exigence sur la gestion interne des ressources | aucune | aucune | haute |
| Ticketing | 1 | DSP2 art. 101 : procédures de réclamation adéquates et efficaces, réponse traitant tous les points soulevés sous 15 jours ouvrables, 35 au maximum en cas exceptionnel, dans une langue officielle ; DSP2 art. 103 : sanctions | Le workflow de réclamation et ses délais sont repris mot pour mot. Le delta est un type de décision nouveau à instrumenter : après investigation d'une opération contestée, une décision motivée de remboursement ou de refus sous 15 jours ouvrables, indiquant les organes de recours, et, en cas de conclusion à la fraude du payeur, la transmission des motifs de cette conclusion à une autorité nationale désignée | DSP3-EX-262, DSP3-EX-263, DSP3-EX-276, DSP3-EX-479, DSP3-EX-481 | DSP3-H12 | haute |
| Messagerie | 1 | Rien d'équivalent : DSP2 n'impose aucune protection des canaux de communication du PSP contre leur usurpation | Le PSP doit mettre en place des mesures de prévention et des garde-fous techniques robustes empêchant la réplication et le détournement de ses canaux de communication par des fraudeurs. L'obligation vise l'authentification des expéditeurs et l'intégrité des gabarits, et se combine avec la description contractuelle d'une procédure sécurisée de notification en cas de fraude suspectée | DSP3-EX-273, DSP3-EX-050, DSP3-EX-368 | DSP3-H12 | haute |
| Partage & Gestion doc | 0 | Sans objet | Aucune exigence sur les outils de partage internes ; les obligations de support durable sont portées par la GED | aucune | aucune | haute |
| Téléphonie | 1 | DSP2 art. 70(1)(c) : moyens de notification et de déblocage disponibles à tout moment et gratuits | Deux obligations nouvelles pèsent sur les canaux voix : les garde-fous techniques contre l'usurpation du numéro affiché, au titre du même Art. 59(-1) que la messagerie, et un support **humain** gratuit dans une langue officielle de l'État membre, au moins pendant les heures ouvrées, incluant l'assistance à la réalisation de la SCA | DSP3-EX-273, DSP3-EX-239, DSP3-EX-403 | DSP3-H12 | haute |

## Capacités réellement nouvelles

Neuf capacités n'existent aujourd'hui dans aucune entité, même partiellement. Elles sont classées par
candidature à la mutualisation Groupe. Toutes les autres cotations 2 relèvent d'un changement de
régime sur une fonction existante.

| Capacité nouvelle | Brique | Mutualisation | Pourquoi |
|---|---|---|---|
| Tableau de bord des consentements (IHM) | CIAM (Consentement) | **forte** | Composant sans équivalent DSP2, spécifié à l'identique par l'Art. 43 pour toutes les entités, sans différenciation concurrentielle possible puisque le texte interdit toute conception orientant le client. Un seul développement, une intégration par canal. Exigences : DSP3-EX-183, DSP3-EX-184, DSP3-EX-186, DSP3-EX-187. Hypothèse : DSP3-H17 |
| Registre des consentements et flux bidirectionnels avec les tiers | Usage et Consentement | **forte** | Sous DSP2, l'ASPSP ignore les consentements donnés aux tiers. Le protocole d'échange, la resynchronisation dans les deux sens et l'historique de deux ans gagnent à être uniques au niveau Groupe. Exigences : DSP3-EX-184, DSP3-EX-188, DSP3-EX-190, DSP3-EX-191. Hypothèse : DSP3-H17 |
| Surveillance des opérations côté bénéficiaire, avant mise à disposition des fonds | Risque | **forte** | Obligation entièrement nouvelle, adossée à quatre catégories de données limitativement énumérées et à une décision de retour de fonds. L'usine de paiement est le point naturel de mutualisation, les entités conservant leur politique de décision. Exigences : DSP3-EX-348, DSP3-EX-354, DSP3-EX-436, DSP3-EX-437. Hypothèse : DSP3-H10 |
| Retour de fonds et suspension d'ordre avec reprise de contact du payeur | Paiements / Transactions | **forte** | Deux cinématiques d'exécution absentes de DSP2 et de l'IPR, sous contrainte de 10 secondes pour le virement instantané et sous contrainte de non-divulgation LCB-FT. Le séquencement et les formats de message gagnent à être uniques. Exigences : DSP3-EX-418, DSP3-EX-421, DSP3-EX-436, DSP3-EX-442, DSP3-EX-445, DSP3-EX-447. Hypothèse : DSP3-H12 |
| Dispositif de partage d'informations sur la fraude entre PSP | Risque | **forte** | Participation obligatoire, avec analyse d'impact conjointe préalable et pseudonymisation. Le choix entre dispositif de place et dispositif intra-Groupe est un arbitrage Groupe par nature. Exigences : DSP3-EX-357, DSP3-EX-358, DSP3-EX-359, DSP3-EX-362. Hypothèse : DSP3-H11 |
| Preuve que la surveillance a été effectuée par les deux PSP | Traçabilité et auditabilité | **moyenne** | Objet de preuve créé par le texte sans que le texte en définisse le véhicule inter-PSP. Le format de preuve et sa conservation se normalisent au niveau Groupe, la collecte restant attachée aux moteurs de chaque entité. Exigences : DSP3-EX-350, DSP3-EX-420, DSP3-EX-441. Hypothèse : DSP3-H10, bloquante |
| Temporisation de 4 heures ajustable par le client | Gestion des comptes ; Mobile | **forte** | Même mécanisme sur deux évènements distincts, l'augmentation de plafond à distance et l'activation d'application mobile : prise d'effet différée, ajustement ou désactivation à la main du client, notification à chaque étape. Aucun équivalent existant. La doctrine de paramétrage et l'ergonomie de l'opt-out se décident au niveau Groupe, le déploiement restant par entité. Exigences : DSP3-EX-226, DSP3-EX-227, DSP3-EX-378, DSP3-EX-379. Hypothèse : DSP3-H13 |
| Remboursement du consommateur manipulé via un canal attribué au PSP | Parcours clients | **forte** | Régime de remboursement intégral sans franchise, déclenché par une notification accompagnée d'un rapport de police, avec décision sous 15 jours ouvrables. Ni DSP2 ni la jurisprudence actuelle n'outillent ce parcours. La doctrine de traitement et le provisionnement sont des arbitrages Groupe. Exigences : DSP3-EX-274, DSP3-EX-275, DSP3-EX-276. Hypothèse : DSP3-H12 |
| Garde-fous techniques contre l'usurpation des canaux du PSP | Messagerie ; Téléphonie | **forte** | Obligation de résultat nouvelle portant sur l'authentification des expéditeurs et l'intégrité des gabarits, sur tous les canaux sortants. La doctrine technique et les référentiels d'expéditeurs légitimes se mutualisent naturellement. Exigences : DSP3-EX-273, DSP3-EX-050 |

Deux capacités retenues en V1 sortent de cette liste : la **mesure et la publication trimestrielle de
la parité d'interface**, déjà imposée par les RTS 2018/389 art. 32(4), et le **service de vérification
du bénéficiaire**, en production depuis octobre 2025 au titre de l'IPR. Le **moyen d'authentification
forte indépendant du smartphone** en sort également, des moyens non mobiles subsistant partiellement
dans les entités ; il reste le fondement de la cotation 2 de la brique MFA, au titre du changement de
régime.

## Écarté du périmètre d'impact

Trente briques passent de 1 à 0. Les quinze briques déjà à 0 en V1 le restent, sans reprise ici.

**Effet générique de second ordre (10 briques)**

| Brique | Raison |
|---|---|
| Catalogue de données | Cataloguer et taguer par finalité est une obligation RGPD, vraie de toute réglementation |
| Data Lake / Data Warehouse | « Le modèle de données et la rétention évoluent » ; la contrainte réelle est portée par Risque et Archivage |
| Qualité et lineage | « La qualité de la donnée conditionne le dispositif » |
| ETL | « Les flux d'alimentation sont impactés » |
| Streaming | « Des topics et un budget de latence en plus » ; la contrainte est portée par Risque et Paiements |
| Évènements | « De nouveaux types d'évènements circulent » ; chaque notification est cotée sur sa brique métier |
| SIEM | « La supervision doit couvrir les nouveaux traitements » ; les facteurs de risque alimentent le moteur de fraude |
| HSM (Clés cryptographiques) | Hausse de volumétrie de signature, sans changement de doctrine ni de cycle de vie |
| CRM | « Enrichir le référentiel de préférences de contact » |
| RH | Un programme de formation n'est pas une modification du SI |

**Déjà couvert par DSP2 ou les RTS 2018/389 (17 briques)**

| Brique | Raison |
|---|---|
| IAM | Limitation et enregistrement des accès : RGPD art. 32 et DORA, reconduits par l'Art. 80 |
| Gestion des habilitations | Même motif, sans profil ni règle nommés par le texte |
| PKI (Certificats) | Certificats qualifiés et standards de communication : RTS 2018/389 art. 34 et 35 ; RTS Art. 89(1)(e) non publiés |
| Anonymisation / Pseudonymisation | Pseudonymisation : RGPD art. 32 ; facilité de test sans données de production : RTS 2018/389 art. 30(5) |
| Catalogue (gouvernance intégration) | Documentation gratuite, résumé publié et préavis de changement : RTS 2018/389 art. 30(3)-(4) |
| Sécurité (gouvernance intégration) | Refus d'accès motivé et signalement immédiat à l'autorité : DSP2 art. 68(5) |
| Chiffrement TLS | Sécurité des canaux de communication : RTS 2018/389 art. 35 |
| Load Balancer | Parité de temps de réponse : RTS 2018/389 art. 32(1) ; seuil de 30 secondes : orientations EBA/GL/2018/07 |
| PCA | Continuité d'activité : DORA chapitre II ; mécanisme de contingence : RTS 2018/389 art. 33 |
| Supervision infra | Indicateurs de disponibilité et de performance : RTS 2018/389 art. 32(4) |
| Supervision applicative (Logs) | Messages d'erreur explicatifs aux tiers : RTS 2018/389 art. 36(2) |
| Crédits | Blocage pour risque de défaut accru : DSP2 art. 68(2) ; crédit accessoire à 12 mois : DSP2 art. 18(4) |
| Comptabilité | Dates de valeur, rétablissement du compte, prorata des frais : DSP2 art. 87, 73(1) et 55(2) |
| Datacenters, Serveurs, Stockage, Réseau | Socle physique et cloud : DORA, sans exigence technique propre au PSR |

**Déjà couvert par l'IPR (1 brique déclassée)**

| Brique | Raison |
|---|---|
| BI | La publication trimestrielle des statistiques d'interface relève des RTS 2018/389, et le reporting statistique de fraude de DSP2 art. 96(6) ; seuls des champs s'ajoutent |

Master Data Management reste coté 1, et non 0, parce que l'extension aux virements hors euro et aux
identifiants non-IBAN dépasse ce que l'IPR couvre. Aucune autre brique n'est rétrogradée au seul
motif de l'IPR.

## Exigences sans brique de rattachement

Inchangé par rapport à la V1. Ces exigences sont juridiques, contractuelles, prudentielles ou
adressées à un autre acteur que le Groupe ; elles n'ont pas de traduction SI directe et ne sont donc
pas cotées, sans être écartées.

| Domaine du référentiel | Exigences | Nature et renvoi |
|---|---|---|
| 1. Champ d'application et définitions | DSP3-EX-001 à DSP3-EX-029 | Champ, définitions, options nationales de transposition. Renvoi : qualification juridique du périmètre par entité, DSP3-H20. DSP3-EX-030 est rattachée au reporting prudentiel |
| 2. Information et transparence | DSP3-EX-032 à DSP3-EX-039, DSP3-EX-054 à DSP3-EX-058, DSP3-EX-062, DSP3-EX-063, DSP3-EX-065 | Clauses de contrat-cadre, préavis de modification, résiliation, options contractuelles et nationales. Renvoi : chantier juridique et conditions générales |
| 3. Frais et conversion | DSP3-EX-066 à DSP3-EX-075, DSP3-EX-078 à DSP3-EX-098 | Tarification, interdiction de surcharge, obligations des schemes et des entités de traitement, acte délégué frais acquéreurs. Renvoi : direction tarifaire et filière monétique acquéreur, DSP3-H20 |
| 4. Retrait d'espèces | DSP3-EX-099 à DSP3-EX-109 | Régime des exploitants de DAB et du cash en magasin. Renvoi : à réactiver si une entité exploite un parc DAB hors compte |
| 5. Accès aux systèmes de paiement | DSP3-EX-110 à DSP3-EX-117, DSP3-EX-124, DSP3-EX-127 | Obligations des opérateurs de systèmes et de schemes, modification de la directive 98/26/CE. Renvoi : DSP3-H19 |
| 6. Open banking, interfaces | DSP3-EX-161 à DSP3-EX-163, DSP3-EX-174 à DSP3-EX-179, DSP3-EX-181, DSP3-EX-182 | Dérogation d'interface, pouvoirs et moyens des autorités, mandats EBA. Renvoi : DSP3-H05, veille RTS |
| 8. Obligations des prestataires tiers | DSP3-EX-193 à DSP3-EX-214 | Obligations pesant sur les AISP et PISP. Le Groupe n'est pas tiers à titre principal : bloc à réactiver si une entité opère en AISP ou PISP |
| 9. Consentement et autorisation | DSP3-EX-215, DSP3-EX-219 à DSP3-EX-221, DSP3-EX-234 à DSP3-EX-236, DSP3-EX-243, DSP3-EX-245 à DSP3-EX-247 | Règles d'imputation du consentement, obligations pesant sur l'utilisateur ou le bénéficiaire, charge du risque d'envoi. Renvoi : contrat-cadre et politique de preuve |
| 11. Responsabilité et remboursement | DSP3-EX-266 à DSP3-EX-272, DSP3-EX-277 à DSP3-EX-326 hors DSP3-EX-327 | Franchise de 50 EUR, régime de responsabilité entre acteurs, recours contre prestataires techniques et hébergeurs. Renvoi : direction juridique et provisionnement, DSP3-H12 |
| 12. Fraude | DSP3-EX-328 à DSP3-EX-336, DSP3-EX-339 à DSP3-EX-343, DSP3-EX-361, DSP3-EX-363 à DSP3-EX-367, DSP3-EX-369 à DSP3-EX-373, DSP3-EX-375, DSP3-EX-376 | Obligations des fournisseurs de communications électroniques, des hébergeurs et des très grandes plateformes, plateforme antifraude de la Commission, mandats RTS et ITS. Renvoi : veille et représentation de place, DSP3-H24 |
| 13. Authentification forte | DSP3-EX-382, DSP3-EX-383, DSP3-EX-385 à DSP3-EX-393, DSP3-EX-395 à DSP3-EX-401, DSP3-EX-406 à DSP3-EX-412 | Périmètre d'exclusion de la SCA reconduit des RTS 2018/389, politique d'exemption, accord d'externalisation, ouverture FRAND des terminaux mobiles, mandats EBA. Renvoi : DSP3-H16, DSP3-H25 |
| 14. Exécution et dates de valeur | DSP3-EX-413 à DSP3-EX-417, DSP3-EX-419, DSP3-EX-423, DSP3-EX-424, DSP3-EX-427 à DSP3-EX-435, DSP3-EX-438 à DSP3-EX-441, DSP3-EX-443, DSP3-EX-444, DSP3-EX-448 à DSP3-EX-452, DSP3-EX-454 | Moment de réception, irrévocabilité, révocation, options contractuelles de délai, articulation avec la déclaration de soupçon. Renvoi : contrat-cadre et procédures LCB-FT, DSP3-H20 |
| 15. Protection des données | DSP3-EX-456, DSP3-EX-457 | Reconduction du standard RGPD. Renvoi : filière DPO |
| 16. Risque opérationnel | DSP3-EX-459 à DSP3-EX-461 | Cadre de risque opérationnel et gestion des incidents, sans préjudice du chapitre II de DORA. Renvoi : dispositif DORA existant |
| 17. Réclamations, litiges et sanctions | DSP3-EX-462 à DSP3-EX-478, DSP3-EX-480, DSP3-EX-483 à DSP3-EX-519 | Organisation des autorités, secret professionnel, règlement extrajudiciaire, barème de sanctions et astreintes. Renvoi : cartographie des risques et exposition de sanction, DSP3-H23 |
| 18. Agrément et supervision | DSP3-EX-520 à DSP3-EX-550, DSP3-EX-552 à DSP3-EX-555, DSP3-EX-557 à DSP3-EX-607 | Dossier d'agrément, participations qualifiées, agents et succursales, passeport, supervision transfrontière. Renvoi : filière juridique et conformité des filiales agréées, DSP3-H21 et DSP3-H22. Seules DSP3-EX-522, DSP3-EX-533, DSP3-EX-535, DSP3-EX-551 et DSP3-EX-556 ont une traduction SI et sont citées ci-dessus |
| 19. Fonds propres et cantonnement | DSP3-EX-608 à DSP3-EX-623, DSP3-EX-625 à DSP3-EX-630, DSP3-EX-632 à DSP3-EX-634, DSP3-EX-636 à DSP3-EX-639, DSP3-EX-641 à DSP3-EX-647 | Capital initial, méthodes de calcul, régime des dépôts et du crédit accessoire, options nationales. Renvoi : filière prudentielle et trésorerie, DSP3-H21 |
| 20. Exemptions et régime transitoire | DSP3-EX-648 à DSP3-EX-682 | Régime des petits établissements, enregistrement des prestataires d'information sur les comptes, réseaux limités, grandfathering de six mois. Renvoi : plan de redocumentation des agréments, DSP3-H22 |
| 21. Monnaie électronique et jetons | DSP3-EX-683 à DSP3-EX-700 | Émission et remboursement au pair, dérogations applicables aux jetons de monnaie électronique, articulation MiCA. Renvoi : DSP3-H28 |
| 22. Dispositions finales | DSP3-EX-701 à DSP3-EX-711 | Actes délégués, clauses de revoyure, calendrier d'application. Renvoi : DSP3-H26, le rétroplanning du GT dépend d'une date de publication non fixée |

## Points à sourcer

| Élément | Statut |
|---|---|
| Correspondances DSP2 et RTS 2018/389 citées dans la colonne « Déjà exigé » | `[SRC: à sourcer ⚠️]` : les numéros d'articles de la directive (UE) 2015/2366 et du règlement délégué (UE) 2018/389 sont à vérifier article par article dans PageIndex avant toute reprise en slide |
| Orientations EBA/GL/2018/07 (seuil de 5 requêtes sous 30 secondes) | `[SRC: à sourcer ⚠️]` : référence à confirmer, le seuil figurant également à l'Art. 38(1) du PSR |
| Existant Groupe des moyens de SCA non dépendants du smartphone | `[SRC: à sourcer ⚠️]` : recensement par entité à conduire, il conditionne la qualification (a) ou (b) de la brique MFA |
| Périmètre des entités disposant déjà d'un service de vérification du bénéficiaire au titre de l'IPR | `[SRC: à sourcer ⚠️]` : conditionne le chiffrage du delta Master Data Management, cf. DSP3-H08 |
