# Revue GT11 V1, slides 10 à 28 — contrôle de conformité au texte

> Revue du 2026-08-19 sur « GT11 - Lancement DSP3-PSR - 16092026.pdf », 32 pages.
> Objectif déclaré : niveau direction, confiance et exhaustivité maximales.
> Vérification par lecture directe des PDF de compromis trilogue du 23/04/2026.
> Réserve de méthode : le règlement délégué (UE) 2018/389 (RTS SCA) n'est pas dans le vault.
> Les comparaisons avec cette ligne de base sont donc signalées comme non tranchées.

---

## A. BLOQUANT AVANT PRÉSENTATION EN DIRECTION

| # | Slide | Problème | Correction |
|---|-------|----------|------------|
| **A1** | 20 | Le titre annonce « **trois zones de concentration de l'impact, nouvelles données, intégrations et gestion des accès** ». La matrice affichée dit l'inverse : Applications métiers porte 6 briques en impact fort, Intégration en porte **zéro**. Le titre contredit la slide qu'il surplombe. Vestige d'une version antérieure. | Remplacer par un titre conforme, par exemple : « L'IMPACT SE CONCENTRE SUR LES APPLICATIONS MÉTIERS ; L'INFRASTRUCTURE ET LA GOUVERNANCE DE LA DONNÉE SONT PEU TOUCHÉES ». |
| **A2** | 20 | Note de travail imprimée sur la slide : « **(+ y'a déjà plein de trucs qui existent donc c'est surtout un delta avec l'existant)** ». Registre incompatible avec une lecture en direction. | Reformuler en phrase de méthode : « Cotation en écart avec l'existant : DSP2, RTS 2018/389, IPR, RGPD. » |
| **A3** | 20 et 8 slides suivantes | Légende : « **(0) Impact faible / modifications marginals** ». Coquille sur « marginales », répétée sur neuf slides. Surtout, « Impact faible » contredit la méthode du delta : le niveau 0 signifie hors périmètre, pas faible. | « (0) Hors périmètre : déjà couvert par la ligne de base, ou effet générique de second ordre ». |

---

## B. CORRECTIONS FACTUELLES VÉRIFIÉES CONTRE LE TEXTE

Six affirmations sont inexactes. Chacune est vérifiable par un lecteur averti en séance.

| # | Slide | Ce qui est écrit | Ce que dit le texte | Correction |
|---|-------|------------------|---------------------|------------|
| **B1** | 22 (API) | « **Huit fonctions** d'initiation minimales sont désormais imposées » | L'Art. 36(4) énumère **neuf** points, de (a) à (hc), la numérotation sautant (h) et (hb) supprimés. La formule est « *at a minimum* ». | « Neuf fonctions d'initiation au minimum » |
| **B2** | 18 (parcours 7) | « Reporting de fraude **annuel** » | Art. 82(1) : « *at least on an annual basis* ». L'annuel est un plancher, l'autorité pouvant exiger davantage. | « au moins annuel » |
| **B3** | 22 et 26 | « notification de refus **dans les 10 secondes** pour un virement instantané » puis « recréditation en 10 secondes sur virement instantané » | Art. 69(2d)(i) : les 10 secondes portent sur la **notification au PSP du payeur**, uniquement pour un virement **instantané**. La recréditation, elle, est « *immediately* » (2d(ii)), et la remise en état du compte du payeur « *immediately upon receiving the notification* » (2e). | Dissocier : notification à 10 secondes, recréditation immédiate. La slide 26 confond les deux. |
| **B4** | 28 (Téléphonie) | « support humain gratuit (…) **incluant l'assistance à la réalisation de la SCA** » | Art. 53(1)(c) : le support humain gratuit, en langue officielle, aux heures ouvrées, couvre **la notification et le déblocage d'un instrument**, pas la SCA. L'assistance SCA relève de l'Art. 88(1), sans aucun de ces qualificatifs. | Dissocier les deux obligations. En l'état, la slide crée une obligation qui n'existe pas. |
| **B5** | 21 (NHI) | « liste centrale lisible par machine **des prestataires** » | Art. 18(7) PSD3 : la liste ne couvre que les prestataires offrant les services des **points 6 et 7 de l'annexe I**, soit l'initiation de paiement et l'information sur les comptes. Le registre général reste l'Art. 18(1). | « des prestataires d'initiation et d'information sur les comptes » |
| **B6** | 21 (SSO) | « La SCA n'est plus applicable qu'au premier accès d'un AISP donné, **et non plus tous les 180 jours côté ASPSP** » | Art. 86(3) : exact côté ASPSP. **Mais** l'Art. 86(4) maintient les 180 jours **côté AISP**. L'obligation n'est pas supprimée, elle est transférée. | Ajouter : « l'obligation des 180 jours est transférée à l'AISP, elle ne disparaît pas ». Point sensible : un participant venant d'une fintech le relèvera. |

### Point en suspens, à sourcer avant diffusion

| # | Slide | Affirmation | État |
|---|-------|-------------|------|
| **B7** | 22 (API) | « Le préavis de changement passe **de 3 à 2 mois** » | Le PSR fixe bien 2 mois (Art. 35(4)). Le « 3 mois » attribué à la ligne de base relève des RTS 2018/389, absents du vault. La trajectoire 3 → 2 n'est donc **pas vérifiée**. Soit sourcer les RTS, soit écrire « préavis de 2 mois » sans la comparaison. |

### Nuances à ajouter, sans erreur mais avec risque de contradiction en séance

| # | Slide | Nuance manquante |
|---|-------|------------------|
| N1 | 22 (API) | « Douze obstacles nommés » est exact, mais l'Art. 44(1) dit « *shall include, but not be limited to* ». La liste n'est pas fermée. Présenter douze obstacles comme un périmètre borné serait inexact. |
| N2 | 22 (API) | « la parité était déjà une obligation de résultat mesurée et publiée » : l'Art. 37 est intitulé « *Data access parity* » mais son §1 porte sur la **disponibilité et la performance**, les §2 et §3 sur les **données**. La réduction à la seule parité de données est imprécise. |
| N3 | 24 (Reporting financier) | La méthode D existe déjà en substance sous la directive monnaie électronique. Parler d'« ajout » vaut au regard de la seule DSP2, pas du droit existant. À préciser sous peine de contradiction. |
| N4 | 21 (Archivage) | Les deux ans portent sur les consentements **retirés ou expirés** (Art. 43(2)(d)), pas sur l'historique des consentements en général. |

### Affirmations vérifiées et confirmées

Temporisation de quatre heures ajustable et désactivable par le client, sur la hausse de plafond comme sur l'activation d'application mobile (Art. 51(1a) et 51(4b)) · plafonds fixés par le client, non modifiables unilatéralement par le PSP, granularité par moyen de paiement, instrument, opération ou période (Art. 51(1)) · publication trimestrielle des statistiques avec comparaison à l'interface client (Art. 35(5)) · RTS statistiques et temps de rétablissement à +9 mois (Art. 38(5)), RTS SCA à +1 an (Art. 89), acte délégué schemes à +15 mois (Art. 31a(4)) · temps de rétablissement optimal gradué par sévérité (Art. 38(2a) et 38(5)(b)) · retour de fonds obligatoire côté bénéficiaire si les motifs sont clairs et incontestables (Art. 69(2a)) · durées de conservation 5 ans monitoring (Art. 83(2b)), 5 ans partage de fraude (Art. 83a(3)), 18 mois preuve de notification (Art. 53(1)) · notification aux hébergeurs selon la procédure DSA (Art. 59a(-1)) · garde-fous techniques contre l'usurpation des canaux (Art. 59(-1)) · méthode D à 2 % (Art. 8(2) et 8(3) PSD3) · évitement du risque de concentration et rapprochement par RTS (Art. 9(2) et 9(7) PSD3) · blocage de montant inconnu subordonné à l'accord du client, étendu au virement (Art. 61(1)) · entité de règlement extrajudiciaire sur site, application, agence et conditions générales (Art. 94(3) et 94(4)).

---

## C. EXHAUSTIVITÉ : CE QUI MANQUE POUR UN NIVEAU DIRECTION

| Priorité | Manque | Pourquoi c'est bloquant à ce niveau |
|----------|--------|-------------------------------------|
| **1** | **Sanctions** | Amendes jusqu'à **10 % du chiffre d'affaires annuel total**, assiette calculée sur les comptes consolidés de **l'entreprise mère ultime** (Art. 97(2) et 97(3)), astreintes à 3 % du chiffre d'affaires journalier moyen (Art. 98). Les manquements visés incluent l'Art. 32 (comptes des établissements de paiement), l'open banking et la SCA, soit trois des quatre axes présentés. Une direction qui découvre l'exposition après la séance considérera que le cadrage a manqué son objet. |
| **2** | **Volet PSD3** | Fusion des statuts établissement de paiement et monnaie électronique, capital initial recalibré, cantonnement renforcé, et surtout **fenêtre de redocumentation d'agrément** pour les filiales existantes. Le support y consacre deux lignes sur la slide 11. Or ce volet concerne directement des filiales du Groupe. |
| **3** | **Ce que le GT attend des entités** | Le support explique la réglementation mais ne formule aucune demande, aucun jalon, aucun engagement attendu. Une présentation en direction sans attendu explicite se conclut sans décision. |
| 4 | **Positionnement vis-à-vis des autres textes** | IPR, DORA, FIDA, AMLR, DMA et MiCA se recoupent avec le paquet. Le DMA est cité en source sur la SCA sans être expliqué. Une slide de positionnement éviterait la question « et par rapport à DORA ? » posée sans réponse préparée. |
| 5 | **Glossaire** | PSP, ASPSP, AISP, PISP, SCA, VoP, RTS, EBA, FRAND sont employés sans définition. En direction, ce n'est pas acquis. |

---

## D. COHÉRENCE ET FORME

| # | Slide | Point |
|---|-------|-------|
| D1 | 11 | « Les jalons clés des textes : **deux échéances à retenir**, mi-2028 et début 2029 » suivi de **quatre** jalons affichés. Incohérence déjà signalée, non corrigée. |
| D2 | 11 | « Règlement qui s'applique, **tel que** dans chaque état » : lire « tel quel dans chaque État ». Deux fautes dans la même ligne. |
| D3 | 10 | « Mise en place de l'authentification forte du client (SCA) **et du 3DSecure** » : 3-D Secure est un protocole de scheme antérieur à la DSP2. La DSP2 a imposé la SCA, ce qui a généralisé 3-D Secure v2. |
| D4 | 15 | Titre de colonne : « INCLURE TOUS LES **CLIENS** ». |
| D5 | 17 | « Le parcours de **decision** » et « du **coté** de l'établissement » : accents manquants. |
| D6 | 25 | « **Dépots** / Liquidité » : accent manquant. |
| D7 | 21 à 28 | Les briques cotées 2 et 1 sont listées ensemble sans marqueur visuel de niveau. Le lecteur ne distingue le niveau qu'en repérant la mention « capacité nouvelle au sens (a) » ou « changement de régime au sens (b) » dans le corps du texte. Ajouter une pastille de couleur devant chaque nom de brique. |
| D8 | 18 | « Neuf parcours **suffisent** à couvrir l'essentiel du paquet » : affirmation forte pour 711 obligations. « Neuf parcours donnent une lecture concrète de l'essentiel du paquet » serait défendable sans exposer le GT à la contradiction. |
| D9 | 14 | La ligne des échéances par front (prévenir à +27 mois, détecter et réparer à +21 mois) a disparu. C'est l'information la plus directement exploitable pour planifier. |

---

## E. CE QUI EST SOLIDE

La structure en trois fronts par axe fonctionne et se lit en diagonale. Le tableau à trois colonnes avec la ligne « pour les entités » est exactement ce qu'attend une direction : la conséquence, pas seulement la règle. Les blocs de sources en pied de page sont précis et au bon niveau de granularité. Les neuf parcours de la slide 18 sont une excellente idée pédagogique. La matrice d'impacts, une fois recotée en delta, donne une priorisation défendable, et son niveau de justification par brique est très au-dessus de la pratique courante.

Les six corrections factuelles de la section B sont ponctuelles et ne remettent en cause ni la structure ni les conclusions.
