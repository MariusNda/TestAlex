# DSP3-DSP2-02 — Booster DSP2 (AEG / CASA, 25/08/2017)

> **Provenance.** Document interne Crédit Agricole S.A., « Booster DSP2 », dernière modification
> **25/08/2017**, demandes de modification adressées à Jérôme LEGER. Transmis à Alex le 2026-08-25,
> reçu sous forme de **neuf photographies d'écran** (planches reproduites dans `planches/`).
> Le fichier natif n'a pas été récupéré.
>
> **Ce document engage CASA en 2017, pas le GT en 2026.** Il décrit un dispositif **attendu**,
> rédigé quatre mois avant l'entrée en application de la DSP2 et deux ans avant celle des RTS :
> rien de ce qu'il annonce ne vaut constat de réalisation. Toute reprise en livrable passe par une
> vérification de l'état 2026 auprès de l'entité concernée.
>
> **Forme de citation dans le vault** : `[SRC: DSP3-DSP2-02 §<planche>]`.
> Les planches sont désignées par leur titre : Présentation générale, User eXperience 1/3 à 3/3,
> Technique, Sécurité, Juridique, Initiatives dans le Groupe, Achats.
>
> **Contacts volontairement non repris** dans l'annuaire du vault : neuf ans après, les personnes
> et les rattachements cités sont périmés. Ils restent dans la transcription pour la fidélité au
> document. [SRC: arbitrage Alex du 2026-08-25]

## 0. Ce qu'est le document

Un « **Booster AEG** » : kit d'accompagnement de l'Architecture d'Entreprise Groupe « pour
l'utilisation de Solutions digitales en mode Quick & Clean, basés sur les Initiatives du groupe,
les Best Practices et les Contacts à privilégier ».

Support interactif organisé en **roue à six domaines** — Technique, Sécurité, User eXperience,
Achats, Initiatives dans le Groupe, Juridique — posée sur un **parcours d'adoption** en cinq temps :
Exploration, Considération, Conversion, Usages, Recommandation. Navigation par clic sur les
secteurs de la roue ou sur le menu d'icônes en haut à droite. Chaque planche porte le même pied de
page : contact à privilégier, liens utiles (certains sous habilitation), date de dernière
modification.

Le format lui-même est un précédent réutilisable : c'est un **kit d'accompagnement d'entités sur une
réglementation**, exactement l'objet que le GT produit aujourd'hui.

## 1. Présentation générale

> La DSP2 est une directive européenne. Son objet est d'**encadrer juridiquement les nouveaux acteurs
> intervenant sur le marché des paiements** en ligne, et non régulés à ce jour : les third party
> provider ou TPP. En proposant d'accorder un agrément à ces nouveaux entrants, la Commission
> européenne poursuit l'objectif d'accroître la concurrence et l'innovation sur ce marché.
>
> Pour atteindre cet objectif, la mise en œuvre de la DSP2 sera facilitée par la mise en œuvre
> d'**échanges normalisés entre les différents acteurs**, notamment par la définition d'API spécifiant
> les échanges entre TPP et ASPSP (Account Service & Payment Service Provider). Les modalités
> pratiques de mise en œuvre seront définies par l'Autorité Bancaire Européenne (ABE) pour assurer la
> sécurité nécessaire au bon fonctionnement des moyens de paiements. Ces nouveaux entrants proposent,
> en effet, des services qui nécessitent l'accès aux données bancaires de leurs clients.
>
> La **transposition de la PSD2 en droit national doit être achevée le 13 janvier 2018**. La mise en
> application sera donc effective le 14 janvier 2018 pour l'ensemble des articles à l'exception de
> ceux qui renvoient à des standards techniques (**Regulatory Technical Standards : RTS**) publiés par
> l'Autorité Bancaire Européenne (European Banking Authority : EBA) et qui deviendront applicables
> **18 mois après leur adoption par la Commission, à un horizon estimé sur S1 2019**.

Liens utiles cités : Glossaire DSP2 (en anglais) · texte complet de la DSP2 · les RTS SCC & SCA
(SCC & SCA : Secure Common Communication & Strong Customer Authentication) · **Espace de partage
Groupe CA sur DSP2** · **Booster API Management de l'AEG**.
Contact : Jérôme LEGER (Responsable du Program API — Direction Systèmes d'Information Groupe, CASA).

## 2. User eXperience (3 planches)

### 2.1 Planche 1/3 — acteurs et niveaux d'impact

> On distingue 2 principaux types de **nouveaux acteurs régulés** :
> - Les **AISP** : agrégateurs de comptes
> - Les **PISP** : initiateurs de paiements
>
> Leur régulation et la définition de leurs modalités de communication avec les clients bancaires et
> les banques induisent des impacts sur l'expérience utilisateur (PSU, TPP, ASPSP) à au moins
> 3 niveaux :
> - La nécessité pour les AISP et PISP de **s'enregistrer auprès d'une autorité de régulation**
> - La nécessité de **sécuriser la communication des données clients** : secrets, infos de comptes…
> - La nécessité de **renforcer les mécanismes d'authentification** des clients bancaires
>
> De façon plus détaillée, l'expérience du client bancaire sera impactée par la définition et la mise
> en œuvre de la DSP2 et des RTS sur SCC & SCA DSP2, et l'expérience des AISP et PISP le sera par ces
> mêmes RTS et aussi par la mise en œuvre des Guides Lines sur le **Registre national ou européen**.
>
> Ces normes techniques européennes indiqueront les modalités de communication détaillée entre les
> acteurs de l'écosystème, et notamment l'utilisation des secrets des clients bancaires et les cas
> d'authentification forte et d'exemptions à l'application d'une authentification forte.
>
> **A fin août 2017 ces modalités sont encore en discussion au niveau européen.** Les éléments qui
> suivent sont donc volontairement macroscopiques et fournis à titre indicatifs.

### 2.2 Planche 2/3 — cinématique AISP

Titre : « Fonctionnement d'un AISP prévu par la DSP2 (après enregistrement auprès de l'Autorité et
enrollement auprès de l'ASPSP) ». Schéma à quatre temps, un PSU, un AISP, trois ASPSP (A, B, C) :

1. Lancement de l'application (PSU → AISP)
2. Requêtes (AISP → ASPSP_A, ASPSP_B, ASPSP_C)
3. Réponses (ASPSP → AISP)
4. Informations consolidées (AISP → PSU)

Liens utiles cités : Fiches réglementaires « RELATION CLIENT » · **Acteurs et cas d'usages de l'API
AISP et PISP interbancaire française (STET)**.

### 2.3 Planche 3/3 — cinématique PISP

Titre : « Fonctionnement d'un PISP prévu par la DSP2 (après enregistrement auprès de l'Autorité et
enrollement auprès de l'ASPSP) ». Cinq temps, acteurs : Client (PSU), Bénéficiaire, PISP, Banque
client (ASPSP), Banque bénéficiaire (ASPSP) :

1. Le PSU souhaite réaliser un achat en ligne (PSU → Bénéficiaire)
2. Il sélectionne un PISP sur la page de paiement et fournit ses identifiants
3. Le PISP se connecte à la banque et initie le paiement pour le compte du PSU, **via une interface
   dédiée** (mention portée sur le connecteur du schéma)
4. Le PISP confirme la demande de paiement (PISP → Bénéficiaire)
5. Compensation de la transaction de paiement (Banque client ↔ Banque bénéficiaire)

Liens utiles cités : Fiches réglementaires « RELATION CLIENT » · **Analyse Groupe CA des cas d'usages
de paiements et leur transposition PISP**.

## 3. Technique

> Pour les banques la mise en œuvre technique de la directive DSP2 passe par l'**implémentation des
> spécifications d'accès par les TPP** aux informations des comptes de paiement de leurs clients et à
> l'initiation de paiement décrites dans le **Regulatory Technical Standards DSP2 on Secure and Common
> Communication & Strong Customer Authentication**. On se reportera aux éléments ci-dessous qui aident
> à la mise en œuvre technique :
> - Les **spécifications inter bancaires STET**
> - Les **composants techniques mis à disposition du Groupe Crédit Agricole par une Entité**
>   - Le **SCAD - Service Centralisé d'Authentification Dynamique** de **CAPS**
> - Les **principes à appliquer au sein du Groupe Crédit Agricole relativement à l'API Management**
> - Les **Normes d'Intégration techniques du Groupe Crédit Agricole**

## 4. Sécurité

> La cellule **SECAPI** qui s'emploie à démocratiser la sécurité applicative au niveau du Groupe CA a
> entrepris un certain nombre de travaux qui s'inscrivent pleinement dans la démarche de
> transformation digitale dans laquelle le Groupe s'inscrit aujourd'hui.
>
> Ainsi, elle élabore en 2016, sous l'impulsion du **GT normes d'intégration**, un **cadre de sécurité
> permettant de sécuriser les appels de services REST inter-entité**.
>
> Au delà des spécificités liées à ces nouvelles architectures, les développements liés aux API
> doivent bien entendu respecter les principes génériques de sécurité applicative qui sont éclairés
> par le standard SECAPI.
>
> Pour tenir compte de l'essor des mobiles et tablettes, un **guide de développement sécurisé**
> spécifique met en avant des mesures de sécurité tenant compte de la particularité de ces terminaux.
>
> Prendre connaissance de la procédure **MESARI**, la Méthode Proportionnée d'Analyse des Risques.
> Découvrir le **WIKI SECAPI** qui référence l'ensemble des livrables traitant de sécurité applicative
> et en particulier :
> - Le **Standard SECAPI** qui présente les activités, règles et mesures de sécurité applicative
>   incontournables et **obligatoires pour tous les projets** (développements spécifiques ou
>   acquisitions de progiciels).
> - **L'analyse de risques des appels de services REST inter entités** présentant les mesures de
>   sécurité à mettre en œuvre.
> - Le guide de développement sécurisé spécifique aux **applications mobiles** (iOS et Android).

Contact : boîte aux lettres de la cellule d'expertise SECAPI.

## 5. Juridique

> La **directive européenne DSP2** établit les principes et modalités d'accès aux informations du
> Client détenues par la Banque. En ce sens sa mise en œuvre est **indissociable de la réglementation
> GDPR** sur la protection des données personnelles.
>
> Le document **Période transitoire DSP2** indique les éléments principaux à connaître et qui
> s'appliqueront pendant une période transitoire, entre la date d'entrée en vigueur de la DSP2
> (13 janvier 2018) et la date d'application des RTS DSP2 sur Secure Common Communication & Strong
> Customer Authentication. Ils concernent :
> - Les **obligations d'agrément ou d'enregistrement** comme PSP
> - Les **modalités d'accès aux comptes en pratique**
> - Le **régime de responsabilité des PSP**
>
> Cette partie pourra être complétée.

Liens utiles cités : texte complet de la GDPR · **cartographie simplifiée des données et de leurs
conditions de diffusion** · Charte des données personnelles du Groupe Crédit Agricole · Charte
éthique commune au Groupe Crédit Agricole.
Contacts : Stéphane HENRY (Responsable GDPR, Direction des Affaires Juridiques, CASA) ·
Sébastien MAS (affaires juridiques, CAPS) · Jérôme LEGER.

## 6. Initiatives dans le Groupe

> La **mise en œuvre de la DSP2 dans le Groupe CA est suivie dans le cadre du comité de pilotage
> opérationnel Nouvelle Banque au Quotidien.**
>
> Dans le cadre de ce comité un **suivi mensuel** est effectué relativement à l'implémentation des RTS
> SCC & SCA DSP2. Il prend comme base les éléments issus des entités du Groupe CA et fournis par les
> **référents de chaque entité** (voir liens utiles). Ce suivi est **piloté par CASA (Jérôme LEGER)**,
> il couvre :
> - la consolidation des retro-planning
> - la surveillance des dépendances
> - le suivi de l'avancement
> - la remontée des alertes

Liens utiles cités : **la liste des référents mise en œuvre DSP2 pour chaque entité** · **la synthèse
du suivi de la mise en œuvre des RTS SCC et SCA DSP2**.

## 7. Achats

> **Rien de spécifique à DSP2.** On se reportera au **Booster API Management** pour les conditions
> d'Achats relatives à l'API Management.

## 8. Chemin d'accès relevé sur une planche

Une planche laisse apparaître, sous la fenêtre, une portion de chemin SharePoint :
`…/maia-collab/communaute des architectes/api/Ouverture des SI/API Réglementaires/DSP2/2 - Direction…`
Piste de localisation des archives DSP2 du Groupe, à recouper avec DSP3-DSP2-01 (archives SharePoint
2018 signalées par Hatim Benamar). ⚠️ Chemin partiellement masqué, non vérifié.

## 9. Documents cités et non détenus

Inventaire des pièces auxquelles le Booster renvoie, toutes à récupérer si le diff DSP2 → DSP3 les
appelle :

| Document cité | Émetteur | Intérêt pour DSP3 |
|---|---|---|
| Booster API Management de l'AEG | AEG | Doctrine API Groupe et conditions d'achat associées |
| Principes Groupe CA sur l'API Management | AEG / DSI Groupe | Cadre normatif d'exposition d'API, antérieur à Kong |
| Normes d'Intégration techniques du Groupe CA | GT normes d'intégration | Cadre normatif, ancêtre de la production du GT |
| Standard SECAPI + analyse de risques REST inter-entités | SECAPI | Sécurité applicative obligatoire, appui pour l'Art. 16 PSR |
| Procédure MESARI | SECAPI | Méthode d'analyse de risques proportionnée |
| SCAD — Service Centralisé d'Authentification Dynamique | CAPS | Précédent de brique d'authentification mutualisée Groupe |
| Période transitoire DSP2 | CASA (juridique) | Précédent de traitement d'un régime transitoire |
| Liste des référents DSP2 par entité | CASA | Précédent de réseau de correspondants entités |
| Synthèse du suivi RTS SCC & SCA | CASA | Précédent de reporting d'avancement Groupe |
| Cartographie simplifiée des données et conditions de diffusion | DAJ CASA | À rapprocher du catalogue des consentements CASA |
| Analyse Groupe CA des cas d'usages de paiements et transposition PISP | Groupe CA | Cas d'usages PISP, matière pour les cinématiques |
| Fiches réglementaires « RELATION CLIENT » | Groupe CA | — |
| Espace de partage Groupe CA sur DSP2 | CASA | Point d'entrée probable des archives |
