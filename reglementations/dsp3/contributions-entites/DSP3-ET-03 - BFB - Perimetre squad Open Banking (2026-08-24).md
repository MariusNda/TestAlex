# Note de périmètre — Squad Open Banking BForBank

> **Contribution d'entité, document non produit par le GT. Reproduit à l'identique.**
> Réf. source : **DSP3-ET-03** · Émetteur : BForBank, squad Open Banking · Auteur : Benjamin Henique
> Reçu le 2026-08-24 (atelier de lancement DSP3 x BFB), en accompagnement de DSP3-ET-02.
> Nature : page de référence interne BFB (périmètre de la squad, inventaire de composants,
> portefeuille de projets en cours et à venir). Document descriptif de l'existant DSP2, non un livrable DSP3.
> Les affirmations de ce document engagent BFB, pas le GT. Citer en `[SRC: DSP3-ET-03 §<section>]`.
>
> **Fidélité de la reproduction** : texte non modifié, hiérarchie de titres rétablie en markdown.
> Les liens internes BFB (Confluence, Jira, Datadog, Figma, environnements de dev) sont conservés
> tels quels : ils ne sont pas accessibles depuis le vault et servent de traçabilité, pas de source.

## Explications

Dans le cadre du deuxième volet de la Directive sur les Services de Paiement (DSP2), BforBank met son portail d'APIs bancaire à disposition des Prestataires de Services de Tiers (TPPs).

BforBank met à disposition des TPPs (tels que les initiateurs de paiement et les agrégateurs de comptes), des APIs réglementaires ainsi que la documentation et le jeu d'essai.

Les principales fonctions de l'API :

- utiliser des mécanismes de sécurité renforcés pour les échanges de données
- mettre à disposition les données sur les comptes de paiements (soldes et opérations)
- permettre d'initier des virements depuis des applications des acteurs du marché

## Squad Open-Banking

### Périmètre

- Exposer les APIs réglementaires et les maintenir :
  - pour AISP (Account Information Service Providers : les prestataires de services d'information sur les comptes)
  - pour PISP (Payment Initiator Service Providers : les prestataires de services d'initiation de paiement)
- Mise à disposition d'une Sandbox pour les TPP
- Maintenir le référentiel des TPPs : liste des TPPs reconnus et autorisés à consommer les APIs DSP2 à l'échelle européenne
- Communication vers les TPPs : permet de communiquer aux TPPs enrôlés des informations sur la disponibilités des services fournis par les APIs
- Reporting trimestriel : un rapport trimestriel est produit et mis à la disposition des TPPs (réglementation DSP2), afin de mettre en évidence qu'un canal n'est pas plus favorisé qu'un autre canal (canaux client vs canaux TPPs)
- Maintenir les Critical User Journeys
- Suivre les évolutions européennes (DSP3 …)
- Migration des services vers l'infra GCP (et monde bleu) : MS on-prem
- Décomissionnement de certains services suite à la migration

### Composants dans le périmètre de la Squad Open-Banking

- **Authorization** : frontend et backend d'authentification (demande des TPP -> access-management) (on-prem, lié à WSO2)
- **Enrolment** : gestion de nos partenaires qui pourraient être amené à consommer nos APIs DSP2 (fournit login/mdp)
- **TPP Directory** : référentiels de droits et de rôles des TPPs (alimentés auprès de SRC, services allemand)
- **TPP API** : proxy BNA pour restitution des comptes, des balances et des transactions et la liste des bénéficiaires associée a un compte
- **TPP Monitoring** : génération et publication du rapport trimestriel de performance canaux client vs canaux TPPs, dans le cadre de la réglementation DSP2
  - [Réglementation DSP2 : services tiers, API - Espace BforBank](https://www.bforbank.com/dsp2)
- **TPP Communication** : frontend + backend de communication aux TPP sur la maintenance programmée et sur les interruptions de service de nos API DSP2
- **STET** : service permettant l'exposition des API bancaires nécessaires à l'implémentation de la directive DSP2 dans le monde bleu (intégré dans WSO2)
- **Payment Core** : gère le cycle de vie d'une demande de paiement dans le cadre de l'initiation de paiement par un TPP avec les API DSP2 PISP

Documentation vers le [Microservices OB](https://bforbank.atlassian.net/wiki/spaces/RDS/pages/729677838) et l'architecture générale [AG-OB-Open Banking](https://bforbank.atlassian.net/wiki/spaces/RDS/pages/585269512).

### Demo TPP Linxo (PISP)

- TPP Communication
  - https://gtw-internalapps.dev.gcp.bforbank.gca/open-banking/open-banking-tpp-communication-front/
- Aggrégateur de compte Linxo
  - [Linxo](https://wwws.linxo.com/auth.page)
- Critical User Journeys
  - https://app.datadoghq.eu/slo/manage?query=team%3Aopen-banking&limit=50&sort=errorBudgetRemaining-desc

### Figma

- https://www.figma.com/board/gELnaCJThRMW8gZTCws4Ff/TPP-in-app?node-id=0-1
- https://www.figma.com/design/KRtcMGZTHkarCVZnn3aTlA/Transfers-Master?node-id=12692-5255

### Projets récents/en cours

- traçabilité d'actions sensibles, mise en place de pistes d'audit virement depuis un TPP : [lien](https://bforbank.atlassian.net/wiki/spaces/ARCHI/pages/2534342727)
- intégrer la VOP (Verification Of Payee) dans le processus PISP : [lien](https://bforbank.atlassian.net/wiki/spaces/SOB/pages/513146932)
- migration service TPP communication (monde marron -> monde bleu, en utilisant le hub de notifications) : [lien](https://bforbank.atlassian.net/wiki/spaces/ARCHI/pages/1834844231)
- scope offline dans le token jwt pour PISP et AISP pour éviter de forcer l'utilisateur à se reconnecter sur le TPP suite à un logout : [lien](https://bforbank.atlassian.net/browse/DSP-989)

### Projets à venir

- critical user journey en source pour la génération des indicateurs de performance et disponibilité des APIs (données réelles de prod plutot que données simulation)
  - → [lien](https://www.bforbank.com/dsp2)
  - → suppression des simulations DataDog, ex : [lien](https://app.datadoghq.eu/synthetics/multi-step/steps/i79-uqp-jj4)
  - → suppression de services/lib legacy (ex: Signature Generator)
- fallback login web monde bleu depuis les TPP (via webview pour Mobile)
  - → retrait de la webapp legacy authentifcation-front : [lien](https://secure.bforbank.com/connexion-client/service/fallbackTpp)
- migration des services Sandbox DSP2 du marron vers monde bleu (wiremock standalone)
- migration gateway WSO2 (aws -> gcp)

## FAQ

**Que signifie "DSP2" ?** Directive révisée sur les Services de Paiement, qui revoit le cadre réglementaire des paiements en Europe

**Que signifie "TPP" ?** Third Party Provider (prestataires de services, agrégateur de comptes ou initiateur de paiement)
