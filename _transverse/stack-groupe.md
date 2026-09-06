# Stack Groupe — IDP, APIM et briques transverses

> Registre **transverse à toutes les réglementations**. Alimente les arbitrages de mutualisation
> (arbre 1) et les cotations d'impacts SI, qui supposent tous de savoir ce qui existe déjà et où.
> Règle n°1 applicable : chaque ligne cite sa source, les points non vérifiés sont marqués ⚠️.

## Règle de lecture (à ne pas perdre de vue)

Il n'existe **pas de stack unique** dans le Groupe, ni même à l'intérieur d'une entité. Une entité
peut cumuler plusieurs IDP et plusieurs APIM selon les périmètres applicatifs, par exemple un WSO2
devant des API exposées via Kong, et d'autres IDP sur des périmètres applicatifs voisins. Toute
conclusion de mutualisation qui suppose un socle homogène est à écarter par défaut.
[SRC: apport Alex du 2026-08-24]

## Gestion des identités (IDP)

| Brique | Statut Groupe | Entités identifiées | Notes |
|--------|---------------|---------------------|-------|
| **Keycloak** | Pas une brique Groupe à date. Pourrait être proposé en offre Groupe | BFB | ⚠️ **La notion de scope n'existe que sur Keycloak.** Point d'attention pour tout pattern de consentement ou de révocation qui s'appuierait sur les scopes : il ne serait pas portable sur les autres IDP du Groupe. [SRC: apport Alex du 2026-08-24 ; atelier BForBank du 24/08/2026] |
| **xConnect** | IDP propre à CATS | CATS | CATS est le plus gros utilisateur en volume du Groupe. Une offre Groupe fondée sur Keycloak laisserait donc de côté le volume principal. [SRC: apport Alex du 2026-08-24] |
| **ILEX** | ⚠️ à confirmer | LCL ⚠️ | Information non vérifiée, relevée comme « askip ». [SRC: apport Alex du 2026-08-24] |
| Autres IDP | — | toutes | D'autres IDP existent sur des périmètres applicatifs à l'intérieur d'une même entité. [SRC: apport Alex du 2026-08-24] |

## Gestion des API (APIM)

| Brique | Statut Groupe | Entités identifiées | Notes |
|--------|---------------|---------------------|-------|
| **Kong** | Solution Groupe | ⚠️ à recenser | Non retenue par BFB. [SRC: atelier BForBank du 24/08/2026] |
| **Apigee** (APIM Google) | Alternative évoquée au niveau Groupe | ⚠️ à recenser | Étudiée puis écartée chez BFB il y a quelques années, motifs inconnus de l'architecte actuel ⚠️. [SRC: atelier BForBank du 24/08/2026] |
| **WSO2** | Choix d'entité | BFB | Hébergé sur AWS, chantier de migration vers GCP en cours : montée de version sur AWS réalisée et validée, bascule GCP recettée et en cours de mise en production. Objectif de fond : décommissionner AWS. [SRC: atelier BForBank du 24/08/2026] |

## Standards d'API open banking

STET est le standard en place depuis DSP2 ; le Berlin Group est la cible de place pressentie pour
DSP3. Arbitrage suivi dans `reglementations/dsp3/hypotheses.md` sous **DSP3-H02**. Aucune position de
place n'est descendue aux entités à date : BFB ne connaissait pas le sujet au 24/08/2026.
[SRC: atelier BForBank du 24/08/2026]

## Authentification et sécurité applicative — héritage DSP2

> Briques et cadres Groupe cités par le Booster DSP2 de CASA (2017). ⚠️ Aucun n'a été vérifié en 2026 :
> le document est antérieur à l'application de la DSP2, il établit une intention, pas un existant.

| Brique / cadre | Statut Groupe | Porteur | Notes |
|---|---|---|---|
| **SCAD — Service Centralisé d'Authentification Dynamique** | Composant mis à disposition du Groupe par une entité, cité comme appui technique DSP2 | CAPS | ⚠️ État 2026 inconnu : existe-t-il encore, qui l'utilise, quel périmètre d'authentification couvre-t-il. Précédent de mutualisation d'un service d'authentification à instruire avant tout arbitrage SCA. [SRC: DSP3-DSP2-02 §Technique] |
| **Standard SECAPI** | Cadre Groupe **obligatoire pour tous les projets**, développements spécifiques comme progiciels | Cellule SECAPI | Complété par une analyse de risques des appels de services REST inter-entités (2016, sous l'impulsion du GT normes d'intégration) et un guide de développement sécurisé mobile iOS/Android. ⚠️ Version 2026 à récupérer. [SRC: DSP3-DSP2-02 §Sécurité] |
| **MESARI** | Méthode Proportionnée d'Analyse des Risques | Cellule SECAPI | Appui possible pour les exigences de gestion du risque opérationnel et de sécurité du PSR. ⚠️ Toujours en vigueur ? [SRC: DSP3-DSP2-02 §Sécurité] |
| **Normes d'Intégration techniques du Groupe CA** | Cadre normatif Groupe | GT normes d'intégration | Cadre de même nature que la production du GT Architectures Réglementaires. ⚠️ À récupérer. [SRC: DSP3-DSP2-02 §Technique] |
| **Principes Groupe sur l'API Management** + « Booster API Management » de l'AEG | Doctrine Groupe antérieure à Kong | AEG / DSI Groupe | Le Booster DSP2 y renvoie pour la partie Achats. ⚠️ Rapport avec la doctrine Kong actuelle à établir. [SRC: DSP3-DSP2-02 §Technique, §Achats] |

## À compléter

- IDP et APIM de CAPS, LCL, CA Italia, CAGIP, et de CATS au-delà de xConnect
- Volumétries par IDP, pour objectiver un éventuel socle Groupe
- Confirmation d'ILEX chez LCL
- Rattachement à la piste transverse « constellation de composants » ouverte le 2026-08-17
  (API gateway, ID provider, traçabilité et observabilité, socle de reporting client)
