# Étude BForBank — Dashboard TPP de révocation des consentements (PSR Art. 43)

> **Contribution d'entité, document non produit par le GT. Reproduit à l'identique.**
> Réf. source : **DSP3-ET-02** · Émetteur : BForBank, squad Open Banking · Auteur : Benjamin Henique
> Reçu le 2026-08-24 (atelier de lancement DSP3 x BFB) · Statut déclaré par BFB : étude non aboutie,
> engagée à la demande du PM produit (Mickaël Ravez), sans commande formelle ni échéance.
> Les affirmations de ce document engagent BFB, pas le GT. Citer en `[SRC: DSP3-ET-02 §<section>]`.
> Lecture GT et écarts relevés : `gt-seances/dsp3/2026-08-24 - Lancement DSP3 x BFB (CR).md` et `faits.md` Fait n°2.
>
> **Fidélité de la reproduction** : texte non modifié. Seules la hiérarchie de titres et les deux
> tableaux d'attributs ont été rétablis en markdown, la copie reçue les ayant aplatis. Les liens et
> les captures d'écran de l'original ne sont pas repris (dont la capture « image (1).png » des
> maquettes de la concurrence, et le renvoi vers l'étude « 202605 - [SOO] Simplification/Split
> Access-Management | Open Banking Service »).

## Sommaire de l'original

```
1 Introduction
  1.1 Contexte
  1.2 Problem to be solved
    1.2.1 Functional needs
    1.2.2 Non Functional needs
2 AS-IS
  2.1 Software Architecture
  2.2 Consentement
  2.3 Violation du principe de responsabilité unique (SRP)
3 TO-BE
  3.1 Dashboard permettant la révocation des accès
    3.1.1 Données à présentées au client
    3.1.2 Maquettes d'écran de la concurrence
  3.2 Open Banking Consent Management
    3.2.1 Gestion du consentement
    3.2.2 Association tokens d'accès par client (3.2.2.1 AISP / 3.2.2.2 PISP)
    3.2.3 Microservice TPP Consent Management (I. Gestion des Consentements / II. Échange de Jetons / III. Espace Partage de Données)
  3.3 Service de révocation de tokens (3.3.1 Keycloak / 3.3.2 Access-Management)
  3.4 Récupération des TPP d'un client
4 Questions en suspens
```

## 1. Introduction

### 1.1 Contexte

Le paquet législatif européen DSP3 / PSR (Directive sur les services de paiement 3 et Règlement sur les services de paiement) est une réforme majeure destinée à moderniser le cadre des paiement, à renforcer la sécurité et à lutter contre la fraude en Europe.

Le texte de compromis final du futur PSR, confirmé au Conseil en 2026, prévoit explicitement à l'article 43 qu'une banque teneuse de compte doit mettre à disposition du client un tableau de bord intégré à son interface utilisateur pour consulter et gérer les consentements donnés aux prestataires Open Banking.

Le texte n'est toutefois pas encore définitivement adopté à ce jour : le dossier est toujours indiqué comme étant en attente de la position du Conseil en première lecture.

### 1.2 Problem to be solved

#### 1.2.1 Functional needs

- être en conformité avec la réglementation européenne DSP3 / PSR qui entre en vigueur courant 2026
- invalider les jetons d'accès client fournies aux TPPs

#### 1.2.2 Non Functional needs

- isoler fonctionnellement la gestion de consentement dans un composant dédié à l'open-banking
- retirer le couplage fort entre access-management et payment-core lié aux consentements
- mise en place d'un service de révocation d'accès

## 2. AS-IS

### 2.1 Software Architecture

Le TPP peut dialoguer avec les services exposés Open-Banking par le biais d'un jeton d'accès (token) qu'il nous demande explicitement. Actuellement ce token d'accès est généré par Access-Management (en exploitant Keycloak), le endpoint est le suivant : `POST /v1/token`.

Selon les credentials demandés, la durée de vie du Refresh Token généré :

- est de 6 mois pour AISP : permet d'accéder aux soldes et historique des comptes
- est de 9 mois pour PISP : permet d'effectuer des virements

La durée de vie de l'Access Token est de 30 minutes.

> ⚠️ (avertissement de l'original) Seul le parcours AISP génère des tokens appartenant au client, celui pour le parcours PISP est un token technique machine-to-machine

### 2.2 Consentement

Aujourd'hui, l'objet consentement est géré et stocké dans Access-Management, et possède les caractéristiques suivantes :

| Nom de l'attribut | Type Java | Brève Explication (Rôle actuel) |
|---|---|---|
| id | UUID | L'identifiant unique du consentement en base de données BforBank. |
| clientId | String | L'identifiant technique de l'application TPP (l'agrégateur tiers) à l'origine de la demande. |
| userUuid | UUID | L'identifiant unique du client BforBank propriétaire des comptes ou initiant le virement. |
| scope | Scope | Type d'accès demandé. Énumération : AISP (comptes), PISP (virements) ou CBPII. |
| status | ConsentStatus | État actuel du cycle de vie du consentement (CREATED, ACCEPTED, TOKEN_EXCHANGED, etc.). |
| createdAt | Instant | Horodatage de la création initiale de la demande de consentement. |
| updatedAt | Instant | Horodatage de la dernière mise à jour de statut de la demande. |
| redirectUri | String | URL vers laquelle rediriger le navigateur du client après un succès de la validation d'accès. |
| unsuccessfulRedirectUri | String | URL vers laquelle rediriger le navigateur du client si l'authentification échoue ou est annulée. |
| state | String | Jeton opaque OAuth2 standard fourni par le TPP pour se prémunir des attaques de type CSRF. |
| authorizationCode | String | (AISP uniquement) Code temporaire généré après validation de la SCA et transmis au TPP pour l'échange de token. |
| refreshTokenSessionId | String | (AISP uniquement) Identifiant de la session globale Keycloak (sid du jeton) utilisé pour révoquer l'accès global. |
| paymentConsentDetails | PaymentConsentDetails | (PISP uniquement) Détails du virement relié (identifiant de paiement, type de paiement, montant, etc.). |
| thirdPartyProvider | ThirdPartyProvider | Référence vers l'entité TPP contenant le profil enregistré du tiers. |

### 2.3 Violation du principe de responsabilité unique (SRP)

Dans le parcours PISP, lors de l'acceptation du consentement par l'utilisateur, Access-Management appelle en direct un service du microservice Payment-Core (du scope open-banking) afin de mettre à jour la demande initiale de paiement, ce couplage fort est non-recommandé, je le considère comme une dette technique actuelle, qui sera traité dans ce sujet en sortant la gestion de consentement open-banking d'access-management.

## 3. TO-BE

### 3.1 Dashboard permettant la révocation des accès

L'article 43 demande que le dashboard montre notamment le prestataire concerné, le compte concerné, la finalité du consentement, sa période de validité, sa date d'octroi, les catégories de données partagées et les dates auxquelles les données du compte ont été consultées.

L'exhaustivité des informations à afficher pour notre cas n'est pas encore définie entièrement.

#### 3.1.1 Données à présentées au client

Voici le genre d'informations à présenter aux clients (non exhaustif) :

```
Services connectés à mes comptes

Bankin'
  Accès à : Compte courant *****1234
  Autorisé à consulter :
    solde
    identité du compte
    opérations
  Autorisé le : 12/06/2026
  Expire le : 12/12/2026
  Dernier accès : aujourd'hui à 08:42
  Gérer l'accès

Service X
  Initiation de paiements récurrents
  Compte : *****5678
  Autorisé depuis le : 02/05/2026
  Gérer l'accès
```

#### 3.1.2 Maquettes d'écran de la concurrence

A date de l'étude les maquettes Figma BforBank sont inexistantes, voici ce que propose ceux qui ont déjà adopté la demande : *(capture `image (1).png` de l'original, non reprise)*

Avec ces écrans, l'application BforBank deviendra le centre de contrôle de ces accès.

### 3.2 Open Banking Consent Management

Certaines caractéristiques métiers du consentement sont actuellement manquantes pour répondre au mieux à cette nouvelle réglementation :

| Nom de l'attribut | Type Java | Brève Explication (Usage DSP3 / Dashboard) |
|---|---|---|
| expiresAt | Instant | Date de fin de validité réglementaire de l'accès (ex: +180j après la SCA). Permet d'afficher la date limite d'accès au client. |
| lastAccessedAt | Instant | Horodatage du dernier appel API réel effectué par le TPP en tâche de fond. Permet de montrer l'activité en temps réel du tiers. |
| accessCount | Integer | Compteur du nombre de synchronisations effectuées par le TPP. Transparence d'audit exigée par la DSP3. |
| authorizedDataCategories | List&lt;String&gt; | Catégories de données précises autorisées (ex: ["BALANCES", "RIB", "TRANSACTIONS"]). Permet d'éviter le "tout ou rien". |
| revokedAt | Instant | Horodatage du moment exact où le consentement a été interrompu (par le client, le TPP ou le système). |
| revokedBy | Enum / String | Origine de l'arrêt du consentement. Valeurs : CUSTOMER (clic bouton), TPP (résiliation tiers), ou SYSTEM_EXPIRATION. |

L'objet consentement entre les TPP et la banque devient un objet métier à part entière appartenant au scope Open-Banking et doit sortir du périmètre où il est actuellement géré (AM), cela concorde avec les conclusions de l'étude récente sur Access-Management : *202605 - [SOO] Simplification/Split Access-Management | Open Banking Service (Service Open Banking)*.

Nommons ce nouveau microservice `open-banking-consent-management`, les tokens finaux du client restent générés par Keycloak.

#### 3.2.1 Gestion du consentement

Un nouveau service `open-banking-consent-management` doit être créé et utilisé pour remplacer les appels effectués aujourd'hui vers access-management afin de centraliser la gestion des consentements du client.

Pour le cas PISP, lors de l'acceptation du consentement, le lien vers Payment-Core se fait à présent depuis ce nouveau micro-service de consentement lié à l'open-banking, on reste dans le même périmètre fonctionnel ce qui permet au passage de retirer le couplage fort existant avec AM (celui mentionné dans le AS-IS plus haut).

#### 3.2.2 Association tokens d'accès par client

##### 3.2.2.1 AISP

Lors de l'acceptation du consentement, un code d'autorisation (authorization-code) est généré afin qu'il puisse servir ensuite au TPP pour l'échanger contre les tokens finaux appartenant au client.

**Génération et Stockage.** C'est le nouveau service `open-banking-consent-service` qui génère le code d'autorisation temporaire (ex: un UUID ou une chaîne cryptographique) lors de l'acceptation du consentement et le stocke dans sa BDD de consentements. Il redirige ensuite le client vers le TPP avec ce code.

**Exposition de l'endpoint d'échange de token (`POST /v1/token`).** C'est le nouveau service qui expose l'endpoint d'échange `/v1/token` à destination des TPPs. Lorsque le TPP appelle `/v1/token` avec le code, le nouveau service valide le code dans sa propre base de données de consentements.

**Récupération des Tokens réels.** Une fois le code validé, le nouveau service doit récupérer des jetons d'accès réels pour le client auprès de l'IdP. Pour cela, il effectue un appel au service Token Exchange sécurisé de access-management en lui fournissant simplement le userUuid associé au consentement. Le nouveau service enregistre le refreshTokenSessionId pour pouvoir révoquer la session plus tard en cas de retrait du consentement, et retourne les jetons d'accès au TPP.

##### 3.2.2.2 PISP

Il n'y a aucune délivrance de tokens appartenant au client dans ce mode, ce n'est qu'un token technique qui est certes réutilisable mais nécessitera à chaque utilisation la création d'un nouveau consentement et la confirmation de celui-ci par le client au travers de son application mobile.

Le TPP ne possède donc aucun token client, il n'y a donc rien à stocker ni rien à révoquer pour être en conformité DSP3.

#### 3.2.3 Microservice TPP Consent Management

##### I. Domaine : Gestion des Consentements (APIs TPPs & Clients)

Ce domaine gère l'enregistrement réglementaire, le suivi du statut et la validation des autorisations d'accès aux comptes ou d'initiation de virement.

**`POST /v1/consents` — Initialisation de Consentement.** Ce service permet à un TPP d'ouvrir une demande de consentement (AISP pour lire les comptes, ou PISP pour faire un virement). Le service valide le tiers, génère un consentId unique et enregistre la demande en statut CREATED avec les détails requis (comme l'ID du virement pour le PISP).

**`GET /v1/consents/{consentId}` — Lecture d'état du Consentement.** Permet au TPP de vérifier à tout moment si le client a bien validé son authentification forte (SCA) et de suivre l'évolution du statut (ex: savoir si le consentement est expiré, accepté ou révoqué).

**`PATCH /v1/consents/sca/{consentId}` — Validation Forte de Consentement (SCA).** Appelé par les canaux internes (BFF web/mobile) après que le client a réussi sa SCA (Saisie de code de sécurité, biométrie). En AISP : ce service valide le jeton de preuve de SCA, passe le consentement à ACCEPTED et génère le code d'autorisation temporaire (l'authorization code métier). En PISP : il valide la SCA et appelle immédiatement le cœur de paiement (payment-core) pour déclencher le virement réel de manière synchrone.

##### II. Domaine : Échange de Jetons Open Banking (APIs TPPs)

Ce domaine est la passerelle d'authentification OAuth2/OIDC propre à l'Open Banking pour délivrer les accès applicatifs.

**`POST /v1/tokens` — Échange & Génération de Token.** L'endpoint universel d'authentification OAuth2 pour les TPPs. En AISP : le TPP fournit l'authorization-code obtenu après la SCA. Le service vérifie le code en base, et via le mécanisme de Token Exchange (RFC 8693), demande à Keycloak des jetons d'accès et de rafraîchissement au nom de l'utilisateur. En PISP : le TPP s'identifie en client_credentials pour récupérer un jeton purement applicatif ("technique") pour appeler les APIs d'initiation de virement.

**`DELETE /v1/tokens/refresh-token` — Révocation à l'initiative du TPP.** Permet à un TPP de révoquer volontairement et proprement son accès (par exemple si l'utilisateur supprime son compte sur l'application de l'agrégateur). Le service supprime/révoque la session dans Keycloak et met à jour la base locale.

##### III. Domaine : Espace Partage de Données (APIs Client BforBank)

Ce domaine expose les fonctionnalités permettant d'alimenter le Dashboard de l'Espace Client BforBank afin de lui donner le contrôle sur ses données partagées.

**`GET /v1/consents` — Liste des accès autorisés (Dashboard).** Ce service permet d'alimenter l'écran client "Gestion des connexions tiers". Il recherche en base de données tous les consentements liés à l'userUuid du client connecté. Il retourne des informations conviviales : le nom du tiers (ex: Bankin'), la date d'expiration de l'accès et les types de données partagées (soldes, historiques).

**`POST /v1/consents/{consentId}/revoke` — Révocation par le Client.** L'action souveraine du client. Lorsqu'il clique sur "Couper l'accès" depuis son application mobile BforBank, ce service passe le statut du consentement à REVOKED en base locale et appelle l'API d'invalidation de session Keycloak via le refreshSessionId. L'accès du tiers est coupé instantanément et définitivement.

**`DELETE /v1/tokens/sessions/{refreshSessionId}` — Nettoyage Technique de Session.** Endpoint d'administration technique interne pour forcer la fermeture d'une session de jeton Keycloak de l'extérieur sans passer par le cycle classique (utilisé pour les outils de support, de lutte contre la fraude ou de synchronisation d'état).

*(L'original renvoie ici vers une ébauche de contrat OpenAPI 3.0, non reprise.)*

### 3.3 Service de révocation de tokens

#### 3.3.1 Keycloak

AM demandant la création des jetons à notre provider Keycloak, il fera le proxy vers le service de révocation mis à disposition par Keycloak : `/realms/{realm-name}/protocol/openid-connect/revoke`

Lors de la révocation d'un jeton Refresh, le consentement de l'utilisateur pour le client correspondant est également révoqué.

#### 3.3.2 Access-Management

Le nouveau service de suppression des jetons que nous devons créer, fera proxy vers le service de révocation décrit ci-dessus en fournissant uniquement l'identifiant de session du Refresh Token du client.

Nouveau service a crée : `DELETE /v1/refresh-token`.

> ⚠️ (avertissement de l'original) Des points de contrôle sont à prévoir pour autoriser l'accès à ce nouveau service.

### 3.4 Récupération des TPP d'un client

Il faut être en capacité de récupérer les Third Party Provider qui ont été autorisé par un compte client afin de pouvoir les présenter sur un écran du client.

Pour cela nous devons récupérer les consentements Open-Banking de l'utilisateur par le biais du microservice "open-banking-consent-management" détaillé ci-dessus puis coupler avec la listes des TPP enrôlés est accessible grâce à l'API du composant "open-banking enrolment" dont voici le swagger.

Ce couplage permettra à coup sûr d'afficher suffisamment d'informations au client dans son dashboard, à confirmer.

## 4. Questions en suspens

Points à clarifier avec @Ravez Mickael

- L'historisation des accès TPP est-il obligatoire ?
  - à priori oui → conservation obligatoire des consentements retirés ou expirés pendant deux ans (Art. 43(2)(d))
- Le dashboard doit-il être déployé aussi sur le Web ?
- Un workflow de révocation / restauration est-il à mettre en place ?
  - à priori oui → le tableau de bord doit permettre de rétablir un accès retiré dans les 48 heures suivant le retrait (Art. 43(2)(c)), et le tiers ne supprime pas les données avant ce délai (Art. 43(2b))
- Lorsque le client révoque ces accès, le TPP doit-il être informé ?
- Migration groupe STET vers Berlin Group ?
