# GT11 — Propositions de contenu, section DSP3 / PSR

> ⚠️ **STATUT AU 2026-08-31 — note de travail largement appliquée, et non fiable en l'état.**
> Le support V2 (38 planches) a intégré la grande majorité de ces propositions. Voir le §8 de
> `revue-GT11-registre-consolide.md` pour ce qui reste à intégrer.
> **Deux corrections de cette note se sont révélées fausses à la vérification sur le PDF du PSR :**
> les 180 jours (l'art. 10 des RTS 2018/389 fixe 90 jours ; les 180 viennent du règlement délégué
> 2022/2360) et le destinataire de la notification de refus à 10 secondes (Art. 65(1) al. 3 : le
> **payeur**, information mise à disposition du **PISP** — et non le PSP du bénéficiaire).
> **Ne rien reprendre d'ici sans revérifier sur `PSR - compromis trilogue 2026-04 (ST-8221).pdf`.**


> Note de travail du 27/08/2026, produite à partir du support 36 planches, du référentiel
> `exigences/` (711 exigences), de `cartographie/matrice-impacts-si.md` (V2 du 19/08),
> de `_transverse/stack-groupe.md`, des faits n°1 à n°3, et d'une recherche externe datée du 27/08.
> **Contenu uniquement, pas de mise en forme.** Périmètre : section DSP3/PSR (planches 10 à 24 et
> annexes 29 à 36).
>
> Convention : ✅ vérifié dans le référentiel ou sur source primaire · ⚠️ à vérifier avant diffusion ·
> 🔎 lecture du GT, à présenter comme telle.

---

## 0. Trois constats de méthode, à traiter avant le fond

**0.1 — Le PDF du PSR (ST-8221) n'est plus dans le vault.** Seul `PSD3 … (ST-8222).pdf` est présent
dans `reglementations/dsp3/`, alors que `_LISEZMOI.md` et `sources.md` le déclarent tous deux déposé.
Conséquence pratique : aucune citation d'article du PSR n'est aujourd'hui re-vérifiable à la source,
PageIndex étant par ailleurs sans crédits. Toutes les vérifications ci-dessous s'appuient donc sur le
référentiel d'exigences comme source intermédiaire — sauf les points PSD3 (méthode D, cantonnement),
contrôlés sur le texte lui-même. **À faire avant diffusion du support : redéposer le PDF et corriger
`sources.md`.**

**0.2 — Le régime de sanctions du PSR est totalement absent du support.** Il est pourtant dans le
référentiel (domaine 17, DSP3-EX-488 à 510, Art. 96 à 102) et déjà documenté par CAPS (DSP3-ET-01).
Trois des cinq catégories expressément sanctionnées par l'Art. 97(1) portent exactement sur les
briques cotées 2 du support : l'accès des EP aux comptes (Art. 32), les mécanismes de prévention de la
fraude dont la SCA (Art. 85-87), et **le non-respect des délais d'indemnisation** (Art. 56(2), 57(2),
59(2), 63(2)). Autrement dit, les « 15 jours ouvrables » que le support présente comme un paramètre de
workflow sont amendables jusqu'à **10 % du chiffre d'affaires annuel total**, avec publication de la
décision. C'est l'argument le plus fort du paquet pour obtenir des moyens, et il n'est pas dit.
→ voir la planche proposée en **§4.6**.

**0.3 — L'annexe justifie les 28 briques cotées 1 ou 2, et aucune des 45 briques cotées 0.** Or c'est
le message de la planche 20 (« l'infrastructure et la gouvernance de la donnée sont peu touchées ») et
c'est la première question qui viendra en séance. La matrice a les justifications, l'annexe ne les
porte pas. → voir **§3.2**.

---

## 1. Corrections de l'annexe — les bloquants

Onze corrections à faire avant diffusion. Formulation de remplacement fournie, à reprendre telle
quelle ou à raccourcir.

### 1.1 — Planche 31, API : « la parité impose d'auditer chaque écran » est faux

Le PSR ne crée **aucune parité fonctionnelle**. La parité porte sur la disponibilité et la performance
(Art. 37(1), 38(2b)) et sur **l'information** mise à disposition : au moins la même information de
compte pour l'AISP, au moins la même information d'initiation et d'exécution, mises à jour de statut
incluses (Art. 37(2)-(3), DSP3-EX-153 à 155, 159). Le périmètre fonctionnel, lui, est fixé par la
liste minimale de l'Art. 36(4) et le jeu de données minimal de l'Art. 36(3).

> **Remplacement.** « L'exercice imposé est un diff de données et de statuts exposés — comparer ce que
> les interfaces client rendent disponible et ce que l'API rend disponible — auquel s'ajoute la liste
> minimale de fonctions de l'Art. 36(4). Ce n'est pas un audit d'iso-fonctionnalité écran par écran. »

En l'état, la planche crée une charge de travail que le texte ne demande pas.

### 1.2 — Planche 31, API : « seuils de performance » n'existe pas dans le PSR

Le PSR impose la **mesure** (Art. 35(5), DSP3-EX-140) et la **parité** ; il ne fixe aucun seuil. Le
seul seuil chiffré du corpus — présomption d'indisponibilité après 5 requêtes consécutives sans
réponse ou en erreur sous 30 secondes — vient des **orientations EBA/GL/2018/07**, donc de la ligne de
base, pas du texte. Le temps de rétablissement gradué est renvoyé à un RTS (Art. 38(5)(b)).

> **Remplacement.** « la définition imposée de la mesure de performance et la parité permanente, les
> seuils et le temps de rétablissement restant à fixer par RTS ».

⚠️ À reporter aussi sur la planche 18, parcours n°6, qui présente le seuil des 5 requêtes / 30 secondes
comme une nouveauté du texte.

### 1.3 — Planche 31, API : « plusieurs de ces fonctions n'existent dans aucune API STET » n'est pas sourçable

DSP3-H02 pose l'écart STET ↔ Art. 36(4) comme **à instruire**, il ne le caractérise pas. Le seul
existant documenté est F2.11 (composant STET de BFB intégré à la gateway WSO2). Affirmer un manque
STET en séance, devant BFB et CAPS, sans gap analysis, expose inutilement.

> **Remplacement.** « L'écart entre les spécifications STET en usage dans le Groupe et la liste de
> l'Art. 36(4) n'est pas encore instruit — c'est l'un des livrables attendus des entités (DSP3-H02). »

### 1.4 — Planche 31 / matrice : huit ou neuf fonctions d'initiation, la chaîne se contredit

L'énoncé de DSP3-EX-149 énumère **neuf** points lettrés — (a) ordre permanent, placement et
révocation, (b) paiement unique, (c) paiement à date future, initiation et révocation, (d) paiements
vers plusieurs bénéficiaires, (e) initiation que le bénéficiaire figure ou non sur la liste du payeur,
(f) communication sécurisée pour placer l'ordre et recevoir l'information, (g) vérification du nom du
titulaire avant initiation, (ha) choix de la procédure d'authentification, (hc) visualisation avant
initiation de l'identifiant, des noms associés et des devises — mais le champ « seuil » de la même
exigence dit 8, et la matrice dit 8. La lettrure discontinue (h et hb absents) signe une renumérotation
de trilogue.

⚠️ **Non arbitrable sans le PDF du PSR.** Relire l'Art. 36(4), puis recaler EX-149 **et** la matrice
**et** la planche. En attendant, écrire « la liste minimale de l'Art. 36(4) » sans chiffre.

À noter : (a) et (c) incluent la **révocation**, ce qui double la surface d'API par rapport à une
lecture rapide.

### 1.5 — Planche 30, Archivage : « quatre durées maximales avec suppression active » mélange deux natures opposées

Deux plafonds de conservation avec suppression active — 5 ans après la fin de la relation pour les
données de monitoring (Art. 83(2b), DSP3-EX-355), 5 ans après l'opération suspectée pour les données
reçues via le partage inter-PSP (Art. 83a(3), DSP3-EX-360) — et deux **planchers** de disponibilité :
2 ans d'historique des consentements retirés ou expirés (Art. 43(2)(d), DSP3-EX-184) et 18 mois de
mise à disposition de la preuve de notification (Art. 53(1), DSP3-EX-242). Sur ces deux derniers
objets, l'obligation est de **conserver**, pas de supprimer.

> **Remplacement.** « Quatre durées chiffrées apparaissent, de deux natures opposées : deux plafonds
> de conservation avec suppression active (5 ans / 5 ans) et deux planchers de disponibilité (2 ans
> d'historique de consentements, 18 mois de preuve de notification). Un plancher et un plafond ne se
> paramètrent pas de la même façon. »

Cinquième durée du paquet, à citer ou à exclure explicitement : suppression des logs d'accès du tiers
**3 ans** après création, débiteur AISP/PISP (Art. 45(2), DSP3-EX-195).

### 1.6 — Planche 29, MFA : la réserve de l'Art. 88(2) est omise

L'interdiction de faire dépendre la SCA du smartphone souffre une réserve : **sauf accord de
l'utilisateur pour une fourniture exclusivement via applications mobiles** (DSP3-EX-404). Elle ne vide
pas l'obligation — l'Art. 88(2) impose par ailleurs de développer plus d'un moyen (EX-405) — mais elle
change la population à couvrir, donc le chiffrage de DSP3-H15.

Deux précisions à ajouter dans la même bulle : les quatre déclencheurs de SCA nommés sont des
**illustrations d'une clause ouverte** (« toute autre action via un canal à distance susceptible
d'impliquer un risque de fraude ou d'abus », Art. 85(1)(d)) ; et « sanctionnée » doit être sourcé sur
les Art. 96-97 ou retiré.

### 1.7 — Planche 35, Conformité (KYC) : le cadrage manque, et il fait tout basculer

L'Art. 32 régit **l'accès des établissements de paiement, de leurs agents et des candidats à
l'agrément aux comptes ouverts chez un établissement de crédit** — le de-risking. Le référentiel le
classe d'ailleurs en domaine 5. Sous un intitulé « Conformité (KYC) » et sans nommer le demandeur,
toute la salle lira « refus d'ouverture de compte à un client retail ».

> **À mettre en tête de brique.** « Accès des établissements de paiement aux comptes ouverts chez un
> établissement de crédit (Art. 32) : le de-risking devient une décision opposable. »

Manque structurant à ajouter : **Art. 32(-1)** (DSP3-EX-118), l'obligation de fond dont tout le reste
découle — accès fourni sur une base objective, non discriminatoire et proportionnée, et « suffisamment
étendu pour permettre la fourniture des services de paiement de manière non entravée et efficace ».
Sans lui, la brique se réduit à un formalisme de notification. Deux précisions : les quatre motifs sont
lettrés (a)(b)(c)**(ea)** — (d) et (e) ont été supprimés au trilogue — et ni le délai de recours ni le
« préavis plus court » du régime AML ne sont chiffrés par le texte.

### 1.8 — Planche 34, Dépôts / Liquidité : « interdiction de fait » est faux (vérifié sur le texte)

PSD3 Art. 9(2) : « they shall avoid, **where appropriate**, concentration risk … they shall
**endeavour not to** safeguard all payment service users' funds with one credit institution ».
Obligation de moyens, doublement conditionnée, et applicable seulement aux EP recourant à la méthode de
cantonnement du §1(a). Aucune interdiction, même de fait. **La matrice porte la même erreur.**

> **Remplacement.** « éviter le risque de concentration lorsque c'est approprié, et s'efforcer de ne
> pas cantonner l'ensemble des fonds auprès d'un seul établissement de crédit ; les circonstances où
> l'évitement est approprié seront précisées par RTS (Art. 9(7) PSD3) ».

Même remarque sur le rapprochement des fonds cantonnés : **l'obligation naît du RTS**, elle n'est pas
dans le corps de l'Art. 9. Les planches 33 et 34 décrivent d'ailleurs ce même RTS différemment
(« le calcul et la périodicité » / « le cadre de gestion, la désignation et le calcul ») — retenir la
formulation du texte : ségrégation, désignation, rapprochement, calcul. La périodicité n'y figure pas.

### 1.9 — Planche 36, Téléphonie : mauvais article et mauvais débiteur

L'Art. 59(-1) (DSP3-EX-273) parle de « canaux de communication » sans mentionner ni la voix ni le
numéro affiché. L'obligation sur l'identifiant d'appelant est l'**Art. 59a(5)** (DSP3-EX-332) et son
débiteur est le **fournisseur de services de communications électroniques**. En l'état, la planche fait
porter au Groupe une obligation que le texte met sur les opérateurs télécoms.

> **Remplacement.** « garde-fous techniques contre le détournement des canaux de communication du PSP
> (Art. 59(-1)) ; la lutte contre la manipulation de l'identifiant d'appelant relève des opérateurs de
> communications électroniques (Art. 59a(5)), dont le PSP est bénéficiaire et non débiteur. »

Deuxième correction sur la même brique : le support fusionne deux obligations distinctes. L'Art. 53(1)(c)
porte le support **humain, gratuit, heures ouvrées** (écartable pour les instruments de faible valeur,
Art. 29(1)(a)) ; l'Art. 88(1) porte l'**assistance à la SCA**, sans gratuité ni horaires, et **exclut
explicitement la fourniture d'équipements**. Deux puces séparées.

### 1.10 — Planche 32, synthèse : « la charge de la preuve bascule sur la banque » est faux

Elle y est déjà, depuis DSP2 art. 72, reconduit à l'Art. 55(1) (DSP3-EX-257).

> **Remplacement.** « La charge de la preuve ne change pas de camp, elle change d'objet : la banque la
> portait déjà, mais l'authentification l'en déchargeait. Elle doit désormais prouver ce qu'elle a
> contrôlé, suspendu et retourné. »

Dans la même brique : l'Art. 55(2) écarte **trois** appuis et non un — ni l'authentification, même
forte, ni l'enregistrement, ni la comptabilisation ne suffisent (DSP3-EX-259) ; et il y a **quatre**
objets de preuve sans équivalent, le quatrième étant la preuve de la fraude ou de la négligence grave
du consommateur dans le régime d'usurpation (Art. 59(4), DSP3-EX-278).

### 1.11 — Trois phrases tronquées à la copie, qui privent deux briques cotées 2 de leur motif

- Planche 32 : « Capacité nouvelle **au sens** sur les objets de preuve » → la matrice écrit « au sens
  (a) ». Écrire « Capacité nouvelle : la fonction n'existe aujourd'hui dans aucune entité », ou
  supprimer le renvoi au barème, illisible hors matrice.
- Planche 35, Risque : la bulle commence par « **nouvelle :** » → la matrice écrit « Cumul de (a) et
  (b). Capacité nouvelle : … ». Écrire « Capacité nouvelle **et** changement de régime — la seule
  brique du SI qui cumule les deux ». C'est une information forte, actuellement perdue.
- Planche 34, Mobile : la matrice porte « aucune entité ne dispose aujourd'hui de la temporisation
  paramétrable par le client », qui disparaît. C'est le motif du 2.

---

## 2. Corrections de l'annexe — les précisions

Par planche, à intégrer sans réécriture lourde.

**Planche 29 — Gestion des identités et accès**

| Point | Correction |
|---|---|
| SSO, 180 jours | ✅ Exact, mais l'impact SI réel manque : l'AISP peut, pour sa SCA à 180 jours, **utiliser celle de l'ASPSP** (Art. 86(4), DSP3-EX-400). Le serveur d'autorisation doit donc rester appelable pour une SCA **déclenchée par le tiers**, hors premier accès. Ce n'est pas un simple transfert de charge. Ajouter aussi la réserve de l'Art. 86(3) : « sauf motifs raisonnables de suspecter une fraude ». ⚠️ Dans la matrice, la ligne de base des 180 jours est rattachée aux « RTS 2018/389 art. 30 à 32 » : c'est l'**art. 10**. |
| SSO, manque | Art. 36(2)(c) (DSP3-EX-147) : l'interface doit permettre au tiers d'utiliser de manière **non discriminatoire toute exemption d'authentification appliquée par l'ASPSP**. Exigence portée par le serveur d'autorisation, citée par la matrice, absente de la planche. |
| NHI | Ajouter le **nom** au triplet (Art. 18(7) PSD3, vérifié sur le texte : « the name and identifier … and their authorisation status »). Le débiteur est l'**EBA**, et **aucun délai n'est fixé** pour cette liste. La « consommation automatisée » est une lecture du GT 🔎 — et il faut distinguer vérifier un **statut d'agrément** (licite) de vérifier une **permission** donnée au tiers, que l'Art. 44(1)(c) **interdit** d'exiger. |
| MFA, manque | Art. 51(4a)-(4e) (DSP3-EX-377 à 381) : toute la cinématique d'activation d'application mobile est cotée sur la brique Mobile mais **pas rattachée à MFA**, ni dans la planche ni dans la colonne exigences de la matrice. Et l'augmentation de plafond est citée comme déclencheur de SCA sans son **délai de 4 heures** (Art. 51(1a)). |
| CIAM | **Six** données pivots et non quatre : ajouter le **nom du prestataire** et le **compte concerné** (Art. 43(2)(a)(i)-(ii), DSP3-EX-184). Ce sont précisément les deux en débat dans DSP3-H03. Et borner le périmètre : consentements donnés aux fins d'AIS ou de PIS **couvrant des paiements multiples ou récurrents** (Art. 43(1)). |
| CIAM / Usage et Consentement | La même obligation (Art. 43) est présentée comme capacité nouvelle **deux fois**, planche 29 et planche 30. Le lecteur compte deux créations. Ajouter une phrase de raccord : H03 = volet IHM et données pivots, H17 = registre et protocole d'échange avec les tiers. |

**Planche 30 — Données**

| Point | Correction |
|---|---|
| MDM, VoP | Le renvoi de l'Art. 50 porte sur les art. **5c(1) à (7) et 5b(2)** du règlement 260/2012. Ajouter l'**Art. 25(1)** à côté de l'Art. 16 pour l'identification par le nom commercial (deux points d'information, pas un). Ajouter surtout le paramètre de trajectoire n°1, absent : **application différée à +27 mois**. |
| MDM, mécanisme | ✅ « Le mécanisme opérationnel n'est pas reproduit dans le PSR » est la meilleure justification de l'annexe. À renforcer d'une phrase : le mécanisme a **trois issues** — concordance, **concordance approchante**, impossibilité technique (DSP3-EX-253) — avec obligation d'indiquer le nom associé en cas de concordance approchante. C'est le cœur du dimensionnement du référentiel de noms (DSP3-H07). Le délai « quelques secondes » ne figure qu'au **considérant 70** : non opposable, à ne pas citer comme exigence. |
| Référentiels | La question LCB-FT sur l'IBAN virtuel est une **hypothèse** du GT (DSP3-H06, H27) 🔎, aucune exigence du PSR ne la porte. À attribuer. |
| Usage et Consentement | « Registre » est une lecture d'architecture du GT 🔎 : le PSR impose l'affichage, l'historisation et les flux bidirectionnels, il ne nomme aucun registre. Le tiers transmet **les informations du §2(a)(i) à (v)**, donc aussi son nom et le compte concerné. Argument décisif disponible et non utilisé : l'**Art. 49(4)** (DSP3-EX-219) **interdit** à l'ASPSP de vérifier le consentement donné au tiers, tout en l'obligeant à l'afficher — c'est ce qui rend la capacité incontestablement nouvelle. |
| Synthèse | Supprimer le renvoi des **durées** au RGPD : il contredit la cotation 1 d'Archivage sur la même planche, qui repose justement sur le fait que le RGPD ne chiffre aucune durée. Écrire « le catalogue et la qualité relèvent du RGPD ; les durées, elles, sont chiffrées par le PSR là où le RGPD ne l'a jamais fait ». |

**Planche 31 — Intégration et interopérabilité**

| Point | Correction |
|---|---|
| ESB, comptage | Cinq flux et non quatre. Le cinquième est le plus lourd : la **preuve inter-PSP que la surveillance a été effectuée par les deux PSP** (Art. 83(1a), DSP3-EX-350), sans laquelle le PSP du payeur rembourse — c'est DSP3-H10, ⚫ bloquante, exposition financière à provisionner, sans véhicule de place existant. L'omettre retire du support l'aléa messaging le plus coûteux du paquet. |
| ESB, 10 secondes | Deux obligations distinctes, de sens inverse, à dédoubler : le PSP du **payeur** notifie le refus, ses motifs et la procédure de correction au payeur **et au PSP du bénéficiaire** (Art. 65(1) al. 2, DSP3-EX-426) ; le PSP du **bénéficiaire** notifie le retour de fonds et ses motifs au PSP du payeur (Art. 69(2d)(i), DSP3-EX-445). Les deux ne valent que pour le **virement instantané**, et le point de départ des 10 secondes est la **réception de l'ordre par le PSP du payeur**, pas la décision. |
| ESB, recréditation | Conditions omises : virement instantané **et** montant déjà crédité sur le compte du PSP du bénéficiaire (Art. 69(2d)(ii)). |
| ESB, partage fraude | C'est une **obligation** (« shall », Art. 83a(1)), pas une faculté, avec catégories **limitativement énumérées** et exclusion expresse des caractéristiques comportementales du payeur (DSP3-EX-358). Ajouter les deux conditions qui en font un chantier : déclenchement sur motifs objectivement justifiés, et **analyse d'impact conjointe préalable** à la conclusion du dispositif. |
| ESB, manque | Art. 69(2e) (DSP3-EX-447) : à réception de la notification de retour, le PSP du payeur **rétablit le compte dans son état antérieur** et informe gratuitement le payeur. Flux entrant qui déclenche une écriture. |
| API | « Douze obstacles **nommés**, liste explicitement non limitative » (Art. 44(1)). Le déclencheur de suppression immédiate n'est pas une « demande » de l'autorité mais **l'identification d'un obstacle, d'où qu'elle vienne, y compris sur signalement d'un tiers** (Art. 48(1), DSP3-EX-173/174). Retirer la publication trimestrielle de la liste des deltas : elle est dans la ligne de base (RTS 2018/389 art. 32(4)) et c'est le motif de la cotation 1 de la brique Monitoring, sur la même planche. |
| API, manques | Préavis de changement **ramené de 3 à 2 mois** (Art. 35(4), DSP3-EX-138) : présent dans la matrice, perdu à la planche, alors qu'il durcit directement le cycle de release. **DSP3-H04 ⚫ bloquante** : l'Art. 45(1) ouvre l'accès « exceptionnellement via une autre interface sûre et efficace » sans définition ni RTS, tandis que le fallback des RTS 2018/389 disparaît — aucune occurrence de « fallback » ou « contingency » dans tout le PSR. Portée déclarée : trajectoire API entière. Enfin, Art. 36(3) et 36(5a) (EX-148, EX-152) : jeu de données minimal AIS, et **nom du titulaire et identifiant de compte non qualifiés de données de paiement sensibles** — ce couple lève un blocage de conception ancien. |
| Batch | Nommer l'article : le régime batch découle de l'**Art. 110c(3)(b)**, donc des modifications du règlement 260/2012, pas du corps du PSR. Nommer les trois cas (concordance, concordance approchante, impossibilité technique). Ajouter le **droit de réactivation à tout moment** et le fait que, dans ce cadre, le PSP du payeur **n'est pas réputé responsable** au titre du §8 — argument de trajectoire. |
| Synthèse | « RTS 2018/389, **en application depuis septembre 2019** » : c'est plus fort (sept ans d'antériorité) et cohérent avec la matrice. Et « parité avec les **interfaces client** » au pluriel, web et mobile, pas « avec l'application ». |

**Planches 32 à 36 — Infrastructure, Monitoring, Applications métiers**

| Point | Correction |
|---|---|
| 32, PRA | Le RTS sur le temps de rétablissement est à soumettre **9 mois** après l'entrée en vigueur (Art. 38(5)), et non 12 comme le suggère la synthèse de la planche 33. ⚠️ L'annexe 99 relève que l'Art. 38(5)(b) renvoie à un « paragraph 3 » supprimé au trilogue : le mandat sur lequel repose toute la brique a un renvoi cassé. |
| 32, traçabilité | Ajouter la contrainte qui interdit tout refus automatisé : l'utilisateur est invité à documenter les évènements antérieurs, sa réponse est intégrée à l'analyse, et **l'absence de réponse ne peut à elle seule fonder la conclusion** (Art. 55(2a), DSP3-EX-260). |
| 33, SOC | Le mécanisme de réception **existe** côté hébergeur au titre du DSA depuis 2024 (art. 16, notice and action ; art. 22, signaleurs de confiance). Ce qui n'existe pas, c'est le **processus sortant du PSP**. Écrire : « le mécanisme de réception existe côté hébergeur au titre du DSA ; c'est la chaîne de notification sortante du PSP, sa qualification éventuelle en signaleur de confiance et son instrumentation qui n'existent pas » 🔎. |
| 33, méthode D | ✅ Vérifié sur le PDF PSD3, Art. 8(2)-(3). La parenthèse « existe déjà en substance » est trop prudente : c'est **littéralement** la méthode D de la directive 2009/110/CE, art. 5(3), même nom, même taux. À affirmer. Ajouter la règle plus opérante pour le Groupe : les établissements qui font à la fois émission et services (1) à (5) **additionnent** les deux exigences (Art. 8(4)), avec option de « portion représentative » (Art. 8(5)). Rattacher DSP3-H21 : le périmètre des filiales concernées n'est pas connu. |
| 33, synthèse | Retirer « champs supplémentaires dans la déclaration de fraude » : c'est exactement le motif par lequel la V2 a rétrogradé **BI de 1 à 0**. Le réimporter en synthèse contredit la cotation. Et corriger « douze mois » : aucun RTS pour la notification DSA (le format est celui du DSA, disponible aujourd'hui) ; douze mois est une date de **soumission de l'EBA à la Commission** ; les échéances réelles sont hétérogènes (9, 12, 18 mois). |
| 34, plafonds | Ajouter le piège d'implémentation : l'ajustement ou le retrait de la temporisation est **lui-même soumis au délai en vigueur** — on ne peut pas désactiver les 4 heures immédiatement. Et trois manques : réévaluation d'un blocage **sous 2 jours ouvrables** (Art. 51(3), présent dans la matrice, coupé de la planche), interdiction d'exécuter un ordre dépassant le plafond **avec information du client** (Art. 51(1c)), garantie de pouvoir modifier le plafond **avant** de passer un ordre (Art. 51(1) al. 3). Ne pas citer un « Art. 51(1b) », qui n'existe pas : la séquence réelle est 1, 1a, 1c, 2, 3, 4, 4a. |
| 34, suspension | Deux étages, la planche n'en montre qu'un : **faculté** sur soupçon objectivement justifié (Art. 69(2a) al. 1) et **obligation** seulement si les motifs sont clairs et incontestables (al. 2). Le premier étage est le cas courant et celui qui coûte en arbitrage. Ajouter la borne qui structure le moteur : **le résultat de la VoP ne peut jamais fonder seul le soupçon**. Et retourner la formulation « l'exception d'un caractère inhabituel est écartée » : ce n'est pas une exception qu'on écarte, c'est un fondement qu'on interdit, **des deux côtés** (Art. 65(-1a) al. 8 et Art. 69(2a) al. 5). |
| 34, manques | Art. 65(-1a) al. 7 : **la notification après suspension ne s'applique pas aux virements instantanés** — exclusion de périmètre majeure, elle supprime la reprise de contact sur le canal le plus volumétrique. Art. 65(-1a) al. 3 : le payeur ne supporte **aucune perte** si le PSP, ayant des motifs justifiés, n'a pas suspendu — c'est ce qui fait de la suspension une obligation de résultat. Art. 51(4e) : les §4a à 4c **ne s'appliquent ni à l'entrée en relation initiale par application mobile, ni à l'activation en agence**. |
| 35, remboursement Art. 59 | Le support le présente comme un remboursement intégral sous 15 jours ouvrables : exact sur le quantum et le délai, **faux par omission sur le déclenchement**. Six conditions cumulatives : consommateur (les professionnels sont hors champ), opération **autorisée**, manipulation par un tiers, ce tiers se faisant passer pour **son propre PSP**, sur des **canaux attribués à ce PSP**, et notification sans retard indu **avec dépôt de plainte**. Deux exclusions seulement, fraude ou négligence grave, **dont la preuve incombe au PSP**. Ni franchise de 50 € ni plafond. Les 15 jours courent à compter de la notification **et** du rapport de police. |
| 35, reprise de contact | Deux articles fusionnés, à séparer : reprise de contact après suspension (Art. 65(-1a) al. 5 — informations attendues du payeur, éléments suffisants pour comprendre les risques, efforts raisonnables de contact, moyen d'être joint en retour) et notification de **refus** (Art. 65(1) al. 1 — motifs précis et procédure de correction, au payeur et au PSP du bénéficiaire). |
| 35, Risque | Inverser le sens : l'Art. 83(2a) **limite** le traitement à quatre catégories, il ne prescrit pas un jeu d'alimentation. C'est un plafond de licéité, pas une spécification d'entrée — l'inversion compte pour la conception du moteur et pour le RGPD. Et ajouter le pendant, absent : les **cinq facteurs de risque minimaux** de l'Art. 83(2b) (éléments d'authentification compromis, montant, scénarios de fraude connus, signes d'infection par malware, journal d'usage anormal), qui s'imposent à **tous** les PSP. Quatre catégories limitatives côté bénéficiaire, cinq facteurs minimaux pour tous : les deux chiffres apparaissent ensemble ou aucun. C'est la seule spécification fonctionnelle chiffrée du moteur de fraude dans tout le texte, et elle sert de motif au 0 du SIEM. |
| 36, Ticketing | Ajouter l'articulation, sans laquelle la planche laisse croire que le remboursement peut attendre 15 jours : **le remboursement est dû immédiatement et au plus tard fin du jour ouvrable suivant** (Art. 56(1)) ; les 15 jours ouvrables ne sont le délai que de la décision après investigation. Et le manque : le **droit inconditionnel au remboursement des prélèvements** passe de **10 jours ouvrables (DSP2 art. 76(2)) à 15** (Art. 63(2), DSP3-EX-298) — c'est le seul délai que le texte **allonge**, et il manque aussi dans la matrice. |
| 36, Messagerie | « L'obligation vise l'authentification des expéditeurs et l'intégrité des gabarits » n'est pas dans le texte : c'est une lecture technique du GT 🔎, à attribuer. Manque : Art. 84(1), alerter les clients **par tous moyens appropriés lors de l'apparition de nouvelles formes de fraude, en tenant compte des publics vulnérables** — cité par la matrice, coupé de la planche. |
| 34-35-36 | Les trois planches portent le **même** message de synthèse. Voir §3.3. |
| Note commune | Art. 59(-1), 65(-1a), 69(2a), 51(1a) sont des **numéros d'insertion de compromis**, promis à recalage au stade juriste-linguiste. Une note de bas de page évite que le support devienne inutilisable à la publication au JOUE. |

---

## 3. Trois corrections structurelles de l'annexe

### 3.1 — Séparer la nature du changement et la charge de travail

C'est l'incohérence la plus visible du support, et elle est déjà signalée dans le vault : la brique API
est cotée **1** dans la matrice, coloriée **2** sur la planche 20, et la planche 21 en fait « le
chantier le plus lourd du paquet ». Les trois peuvent être vrais en même temps, mais seulement si la
distinction est explicitée. Aujourd'hui elle n'est nulle part.

> **À ajouter à la légende.** « La cotation dit la **nature** du changement — capacité nouvelle,
> adaptation, reconduction — pas la **charge**. Une brique cotée 1 peut porter un chantier lourd si
> l'adaptation est large : l'API en est l'exemple. À l'inverse, une capacité nouvelle peut être
> légère. Le chiffrage ne se déduit pas de la couleur. »

Et corriger le paragraphe 3 de la brique API planche 31, qui énonce mot pour mot le critère du niveau 2
(« obligation de résultat opposable, mesurée, publiée ») deux paragraphes après avoir écrit « ni
changement de régime ». Formulation d'alignement : « le mode d'exploitation ne change pas de nature — il
était déjà mesuré et publié —, ce qui change est la définition des indicateurs et l'ajout d'un objectif
de rétablissement ».

⚠️ Méthode : contrôler le coloriage de la planche 20 par analyse des couleurs du rendu (`pdftoppm` puis
comptage des pixels par teinte), pas à l'œil. C'est ce qui a révélé l'écart sur l'API.

### 3.2 — Ajouter une planche d'annexe qui justifie les zéros

Titre-message proposé : **« Les deux tiers du SI sortent du périmètre, et c'est un résultat d'analyse,
pas un défaut de couverture »**.

Contenu, quatre familles, avec le texte qui porte déjà l'exigence :

- **IAM interne, habilitations, PKI, HSM, secrets** → RGPD art. 32 et DORA. L'Art. 80 du PSR reprend
  le standard RGPD sans exigence technique propre. Réserve à afficher : la PKI peut remonter à la
  publication des RTS de l'Art. 89(1)(e).
- **Gouvernance de la donnée : catalogue, qualité, lineage, data lake, BI** → RGPD (registre des
  traitements, minimisation, limitation de finalité) et, pour le reporting de fraude, DSP2 art. 96(6)
  et EBA/GL/2018/05.
- **Infrastructure, cloud, réseau, PCA, sauvegarde, supervision, SIEM** → DORA, plus RTS 2018/389 pour
  la parité de temps de réponse et les orientations EBA/GL/2018/07 pour le seuil des 30 secondes.
- **Briques sollicitées sans exigence propre : CRM, ERP, comptabilité, crédits, RH** → dates de valeur,
  rétablissement du compte et remboursement au prorata sont repris à l'identique de DSP2 ; un programme
  de formation n'est pas un impact SI.

Puis la règle, qui vaut mieux que la liste : **« est rétrogradée à 0 toute brique dont la seule
justification serait vraie de n'importe quelle réglementation — nouveaux champs, flux d'alimentation,
catalogage, volumétrie de logs. »**

⚠️ Deux dettes à solder sur cette planche : la ligne de base annoncée à la planche 20 **omet DORA**,
qui fonde plusieurs zéros ; et aucun des textes de la ligne de base (RTS 2018/389, IPR, EBA/GL/2018/07,
RGPD, DORA) n'est enregistré dans `sources.md`.

### 3.3 — Donner à chaque planche métier sa propre conclusion

Le message actuel est répété trois fois, ne couvre pas la planche 36, et laisse de côté les deux vrais
enseignements. Propositions :

- **Planche 34** — conserver l'existant en remplaçant le dernier exemple, qui appartient à 35 : « Le
  PSR entre dans le déroulement de l'opération, là où la DSP2 s'arrêtait à l'accès et à
  l'authentification : suspension d'un virement suspect avec rappel du client, retour de fonds à
  l'arrivée, plafonds fixés par le client, activation d'application temporisée. »
- **Planche 35** — « Le middle et le back-office passent de l'obligation de moyens à l'obligation de
  résultat opposable : le monitoring engage la responsabilité du PSP qui ne l'exécute pas, la
  surveillance côté bénéficiaire n'existe nulle part, et le refus d'accès d'un établissement de
  paiement devient une décision motivée, notifiée à l'autorité et attaquable. »
- **Planche 36** — « L'obligation sort du SI transactionnel et se porte sur les canaux : les canaux de
  communication du PSP doivent devenir infalsifiables, la voix doit offrir un humain gratuit, et la
  réclamation doit produire une décision motivée, tracée et transmissible à l'autorité. »

---

## 4. Planches nouvelles

### 4.1 — Une réglementation, deux textes, quatre étages de normes

**Titre-message.** « DSP3 et PSR ne sont pas deux versions du même texte : l'un s'adresse aux États,
l'autre s'adresse directement à nous »

**Chapô.** Le paquet porte un seul sujet mais deux instruments juridiques de nature différente, et
cette différence décide de deux choses très concrètes pour un architecte : où il va lire l'exigence
qu'il doit implémenter, et à quelle date elle devient opposable. S'y ajoute que le niveau 1 ne dit pas
tout : une part des paramètres qui conditionnent nos développements n'est pas encore écrite.

**Bloc 1 — Directive contre règlement, la seule différence qui compte pour nous**

| | **DSP3 — une directive** | **PSR — un règlement** |
|---|---|---|
| S'adresse à | aux 27 États membres | directement aux PSP |
| Devient du droit applicable | par **transposition** — en France, une ordonnance modifiant le code monétaire et financier, comme la DSP2 en 2017 | **tel quel**, aucun acte national nécessaire |
| Ce que je cite dans mes spécifications | l'article du **CMF**, pas celui de la directive | l'article du **PSR**, opposable partout en Europe |
| Marge nationale | réelle : options, exemptions, seuils, véhicules de transposition différents d'un pays à l'autre | quasi nulle : c'est le but du basculement |
| Porte | agrément, fonds propres, cantonnement, supervision des EP et des EME | règles de conduite : SCA, fraude, VoP, open banking, transparence, accès aux comptes |
| Pour le Groupe | pilotage **entité par entité**, autant de dossiers que d'entités agréées | cadre normatif et briques **mutualisables** |

**Bloc 2 — Trois exemples, trois endroits où on lit la réponse**

1. « Mon écran de virement doit-il afficher le nom du bénéficiaire ? » → **règlement**, Art. 50 du PSR,
   même règle à Paris et à Milan. Mais le **mécanisme** est dans le règlement SEPA 260/2012 tel que
   modifié, et le protocole d'échange est un **standard de place**, le rulebook VoP de l'EPC.
   Trois étages pour une seule exigence.
2. « Ma filiale établissement de paiement doit-elle redéposer un agrément ? » → **directive**, la
   réponse sera dans le CMF après ordonnance, et dans la doctrine de l'ACPR. Geler une spécification
   sur le texte de la directive aujourd'hui, c'est spécifier sur un brouillon.
3. « De combien de temps disposé-je pour rétablir mon API après incident ? » → **le texte ne le dit
   pas**. Il renvoie à un RTS de l'EBA, à soumettre 9 mois après l'entrée en vigueur. La réponse
   n'existe pas encore, et aucun chiffrage ne peut la présupposer.

**Bloc 3 — Les quatre étages, et ce qu'ils valent**

| Étage | Qui l'écrit | Exemples dans notre paquet | Ce que ça vaut |
|---|---|---|---|
| **1 — Niveau 1** | Parlement et Conseil | PSR, DSP3 | opposable, sanctionné |
| **2 — Niveau 2** | Commission sur projet EBA, par RTS/ITS ou acte délégué | KPI et temps de rétablissement d'interface, format des refus de compte, cantonnement, indépendance des facteurs de SCA, format du reporting de fraude | opposable, mais **pas encore écrit** — plus de 50 mandats annoncés, l'essentiel à +12/+18 mois |
| **3 — Niveau 3** | EBA, orientations | exemptions de SCA, double inhérence, application de l'exclusion « réseau limité » | « comply or explain », en pratique suivi |
| **4 — Standards de place** | EPC, STET, Berlin Group, PCI SSC, schemes cartes | rulebook VoP, spécifications d'API, PCI-DSS 4.x, 3-D Secure | **pas du droit** : contractuel, sanctionné par pénalités de réseau, pas par l'autorité |

**La phrase à retenir.** Ce qui fait l'essentiel de la charge SI est dans un **règlement**, donc
uniforme, opposable et mutualisable ; mais une partie des paramètres qui conditionnent le chiffrage est
au **niveau 2**, donc pas encore écrite ; et une partie des mécanismes opérationnels est au **niveau 4**,
donc négociée entre acteurs de place, pas imposée par le législateur.

⚠️ Précision utile en séance : le mot « réglementation » désigne dans nos travaux le **sujet** traité
par le GT ; « texte » désigne l'instrument. La réglementation traitée est **DSP3/PSR**, jamais DSP3
seule — le centre de gravité SI est le PSR. La DSP2 disparaît, la directive monnaie électronique
2009/110/CE aussi.

### 4.2 — STET et Berlin Group : de quoi parle-t-on exactement

**Titre-message.** « Deux objets de nature différente : une spécification française gelée depuis 2022,
et un cadre européen encore vivant »

**Chapô.** Notre open banking DSP2 repose sur STET. La cible de place pressentie pour DSP3 est le
Berlin Group. Avant de parler de bascule, il faut voir que la comparaison n'est pas symétrique : ce ne
sont ni le même type d'acteur, ni le même rythme de maintenance, ni le même modèle technique.

| | **STET** | **Berlin Group** |
|---|---|---|
| Nature | société de place française, créée en 2004 par six banques, opérateur de CORE(FR). Publie une spécification, **n'est pas un organisme de normalisation** | organisme de normalisation technique européen, une quarantaine de banques et associations, BCE observatrice. Structure : openFinance Taskforce + Advisory Board |
| Périmètre géographique | France et Belgique | revendiqué par **plus de 75 % des banques européennes** ; socle technique du schéma allemand giroAPI (plus de 100 adhérents) |
| Dernière version | **1.6.3, du 6 octobre 2022** | NextGenPSD2, guides d'implémentation **V1.3.15 du 20 juin 2025** ; intégré depuis 2021 dans l'**openFinance Framework**, V2.0 depuis octobre 2023, **plan de travail 2026** en cours |
| Face à DSP3/PSR | **aucune mention, aucune roadmap** ; la spécification indique elle-même que l'extension hors DSP2 « n'est pas dans le mandat » | **analyse d'écart PSR déjà réalisée**, analyse d'écart FIDA planifiée |
| Signal de convergence | la spécification STET indique que certains éléments ont été « étudiés en commun avec le Berlin Group, dans une stratégie de convergence des initiatives européennes » | l'EPC écrit que l'openFinance du Berlin Group est « la seule initiative de normalisation ayant produit des spécifications d'API pertinentes » pour le schéma SPAA |
| Modèle technique | **token-centrique et hypermédia** : le périmètre d'accès se déduit du jeton OAuth2 et des liens HAL exposés. Pas de ressource de consentement à cycle de vie | **consentement comme ressource de premier rang** : `consentId`, lecture, statut, **suppression**. Sous-ressources d'autorisation, 4 approches de SCA, ressources séparées pour bulk et ordres permanents, ISO 20022 |

**Le point d'architecture, en une phrase 🔎.** Toute la mécanique du tableau de bord de l'Art. 43 —
voir chaque autorisation, la révoquer, la rétablir sous 48 heures, en garder l'historique deux ans — se
greffe naturellement sur un consentement **adressable et interrogeable**, et beaucoup moins sur un
modèle où le périmètre se déduit d'un jeton.

**Ce qu'il faut dire pour ne pas induire en erreur** : ⚠️ le silence de STET depuis quatre ans est un
**fait**, son arrêt est une **inférence**. Aucune annonce publique d'arrêt, de reprise ou de
convergence formelle n'existe, ni de STET, ni de la FBF, ni du CFONB, ni de la Banque de France, ni de
la Commission, ni de l'EBA. Rester sur STET reste parfaitement légal.

### 4.3 — Basculer maintenant, ou basculer avec DSP3

**Titre-message.** « Le PSR n'impose aucun standard : la bascule est un choix d'architecture, et son
seul bon moment est celui où un jalon réglementaire la rend opposable aux tiers »

**Bloc 1 — Ce que le texte dit, et ne dit pas**

Le PSR n'impose ni STET ni Berlin Group. Il exige que l'interface s'appuie sur des standards de
communication émis par des organismes de normalisation européens ou internationaux (CEN, ISO « ou
équivalent »), et il impose des **obligations de résultat** : au moins une interface dédiée avec sa
documentation, parité de disponibilité, de performance et d'information, liste d'obstacles interdits,
tableau de bord des autorisations, statistiques publiées chaque trimestre, facilité de test,
interdiction définitive du scraping. Le cadre de sécurité des API de l'EPC (EPC164-22 v2.1, mars 2026)
est lui-même **délibérément agnostique** : il ne cite aucun standard.

→ **Il n'y a pas d'obligation de place, il y a une gravitation institutionnelle.**

**Bloc 2 — Pourquoi la question se pose quand même**

- Les fonctions minimales de l'Art. 36(4) et les métriques de l'Art. 35(5) doivent être **spécifiées
  quelque part**. Berlin Group les modélise et les maintient ; STET n'a pas bougé depuis 2022.
- L'écosystème des tiers intègre déjà massivement Berlin Group. Rester seuls, c'est porter seuls le
  coût de spécification et de support.
- **FIDA est le vrai déclencheur** : le non-paper de la Commission du 6 avril 2026 délègue la
  normalisation d'interface aux **schemes** de partage de données, avec un filet d'acte délégué. Le
  standard ne sera donc pas choisi par le régulateur mais par le scheme auquel on adhère — et le seul
  acteur qui a produit des spécifications pertinentes pour ce type de scheme est le Berlin Group. Le
  périmètre openFinance V2 (épargne, crédit, titres, Request-to-Pay, réservation de fonds) recouvre
  déjà largement les premières phases de FIDA ; STET, par construction, n'est pas un point de départ.

**Bloc 3 — Pourquoi c'est difficile**

- **Ce n'est pas un remplacement d'API, c'est une réintégration avec chaque tiers connecté.** Le coût
  est externe et subi : il dépend du calendrier des TPP, pas du nôtre.
- **Le double run est long.** Seul cadre public qui chiffre ce type d'exercice, le référentiel
  opérationnel britannique impose, pour un changement de **version** : préavis de 3 mois, au moins deux
  versions en production simultanément, double run d'au moins 6 mois, sandbox disponible 6 mois avant.
  🔎 Transposé à un changement de **standard**, le plancher raisonnable est de 12 à 18 mois. Le PSR
  reprend d'ailleurs un préavis de changement, **ramené à 2 mois** (Art. 35(4)).
- **Le modèle de consentement diffère**, et le serveur d'autorisation, les codes d'erreur et les
  parcours de redirection y sont couplés. Ce n'est pas un mapping de champs.
- **La dégradation devient publique.** Pendant la migration, le PSR oblige à publier chaque trimestre
  des statistiques comparées à l'interface client, sous un régime où douze obstacles sont nommés et
  sanctionnés. Toute dégradation du taux d'échec est opposable au moment où elle survient.
- ⚠️ **Aucun retour d'expérience public et chiffré** d'une banque ayant changé de standard DSP2 n'a été
  trouvé, chez aucun éditeur ni cabinet. Tout chiffrage présenté en séance est une hypothèse GT, pas un
  benchmark.

**Bloc 4 — Ce que la bascule ne résout pas**

- Aucun des deux standards ne couvre les **trois vraies nouveautés** du PSR : la vérification du nom
  avant initiation, le tableau de bord des autorisations, et les statistiques normalisées — ces
  dernières seront tranchées par un RTS de l'EBA, pas par un standard de place.
- Le problème français documenté n'est pas le standard, c'est son implémentation : une étude commandée
  par quatre TPP français en janvier 2024 mesure un **taux d'acceptation des paiements initiés via PISP
  de 44 %**, et relève un usage impropre des niveaux de statut recommandés par STET. Changer de
  syntaxe sans changer la discipline d'implémentation ne corrige pas cela.
- L'ACPR conclut en septembre 2025 que l'open banking par API des six premiers groupes français reste
  **modeste**, l'AIS dominant, le PIS peu générateur de revenus. L'assiette de valeur est faible : la
  bascule est un coût de conformité, sauf à la justifier par FIDA.

**Bloc 5 — L'intuition du GT, à valider en séance 🔎**

Préparer maintenant, basculer avec DSP3. Préparer signifie trois choses, toutes utiles même si la
bascule n'a pas lieu : instruire l'écart STET ↔ Art. 36(4) entité par entité (DSP3-H02) ; construire le
référentiel de consentements de manière **indépendante du standard d'API**, puisque l'Art. 43 l'exige
de toute façon ; et durcir la qualité et l'observabilité sous STET, puisque les KPI seront publiés quel
que soit le standard.

**Bloc 6 — Les questions à trancher avant de décider**

1. Obtient-on de STET une position écrite sur la maintenance de sa spécification après 2022 et sur son
   intention face au PSR ? Sans cela, « rester » est un pari sur un silence de quatre ans.
2. Qui, au CFONB, à la FBF ou au CNPS, est mandaté pour porter une position de place française sur
   l'après-STET ? Le GT doit-il provoquer cette clarification ? ⚠️ Constat de terrain : **aucune
   position de place n'est descendue aux entités** — BFB ne connaissait pas le sujet au 24/08/2026.
3. Adhérera-t-on à SPAA, et à quel scheme FIDA ? Si oui, le standard est déjà tranché par le scheme et
   la seule variable restante est la date.
4. Le Groupe entre-t-il dans l'openFinance Taskforce pour peser, ou subit-il les versions ?
5. Le modèle consent-resource est-il **nécessaire** pour tenir l'Art. 43, ou peut-on le construire
   au-dessus de STET par un référentiel interne ? **C'est la question d'architecture pivot.**
6. Quel modèle STET exposons-nous, entité par entité — celui où l'ASPSP ne reçoit aucun détail de
   consentement, ou celui où il l'applique ? Le premier rend la bascule bien plus lourde.
7. Combien de TPP sont réellement intégrés, lesquels pèsent l'essentiel du trafic, lesquels accepteront
   de redévelopper, et qui porte le coût de leur réintégration ?
8. Bascule complète, ou façade Berlin Group devant un back STET ? Le coût de l'adaptateur est-il
   inférieur à celui de la dette qu'il crée ?
9. Bascule par entité ou en Groupe ? ⚠️ Rappel de `stack-groupe.md` : il n'existe **pas de stack
   unique**, ni même à l'intérieur d'une entité. BFB expose via WSO2, en migration AWS vers GCP, avec
   Keycloak et un composant STET intégré à la gateway ; Kong est la solution Groupe mais n'a pas été
   retenue par BFB ; CATS a son propre IDP, xConnect, et porte le plus gros volume du Groupe. Une
   bascule est autant une occasion de convergence interne qu'un multiplicateur de coût.

### 4.4 — Articulations avec les autres textes

**Titre-message.** « Trois textes atterrissent avant le PSR sur les mêmes briques : les décisions qui
détermineront le coût du PSR se prennent dans des chantiers déjà ouverts »

**Chapô.** Le classement par date d'application ne donne pas l'ordre des chantiers. DORA est déjà là,
l'AMLR arrive en juillet 2027, l'obligation d'accepter le portefeuille européen d'identité en décembre
2027 — le PSR, lui, mord vers 2028. Dans les trois cas, la brique est la même et la décision
d'architecture se prend ailleurs, portée par une autre filière.

**Bloc 1 — Les cinq articulations qui coûtent, si elles sont traitées en silo**

| Texte | Le recouvrement | Ce que ça coûte en silo | La cible |
|---|---|---|---|
| **IPR** (2024/886) — VoP en production depuis le 09/10/2025 | même obligation nue de vérifier nom contre identifiant, gratuitement. Le PSR l'étend hors euro et hors périmètre SEPA (+27 mois), et y **attache un régime de responsabilité** que l'IPR n'a pas | le composant VoP livré pour l'IPR est scopé euro/SEPA et sa sortie est un affichage. En silo, second projet : multi-devises, hors SEPA, et bascule d'une logique d'affichage vers une logique de **décision** | concevoir dès maintenant le composant VoP comme un **service paramétrable par devise, canal et scheme, avec une sortie de décision**, pas comme une fonction de l'écran de virement SEPA |
| **DORA** (2022/2554) — applicable depuis le 17/01/2025 | l'Art. 81 du PSR reprend le gène de l'art. 95 DSP2. Le précédent est **déjà tranché** : à l'arrivée de DORA, l'EBA a réduit ses orientations ICT au seul volet « relation avec l'utilisateur » et **abrogé** ses orientations sur la déclaration d'incidents DSP2 | un incident de fraude massive est simultanément un incident de fraude au sens du reporting PSR et, possiblement, un incident majeur TIC au sens de DORA — seuils, horloges et destinataires différents, deux déclarations incohérentes remontant **à la même autorité** | **une qualification unique en amont, deux robinets de sortie en aval**. Décision à prendre dans le chantier DORA existant, pas dans un futur chantier PSR |
| **AMLR** (2024/1624) — applicable le 10/07/2027, donc **avant** le PSR | l'interdiction de divulgation (art. 73) heurte deux obligations du PSR : motiver un refus ou une clôture de compte à un EP, et partager des données de fraude entre PSP. La dérogation du §73(5) ne couvre que les entités concernées par **une même transaction** — pas les typologies, ni les listes d'IBAN signalés | soit la filière fraude partage une information qui trahit une analyse LCB-FT en cours, soit la filière LCB-FT verrouille tout et la banque ne motive pas ses clôtures. Les deux sont des manquements | un **modèle de données de suspicion à double étiquette** — suspicion LCB-FT non divulgable, suspicion de fraude partageable — avec règles de propagation, arbitré conjointement. Sujet d'architecture de données, pas de process |
| **FIDA** — trilogue bloqué depuis juin 2025, séquence proposée à +18/+24/+36/+48 mois | **le recouvrement le plus net du paquet** : tableau de bord des autorisations dans le PSR, permission dashboards dans FIDA. Même objet vu par le client, deux périmètres de données disjoints, et **deux régimes tarifaires opposés** — accès gratuit sous le PSR, accès compensé sous FIDA. Le PSR contient une clause de revoyure sur cette interaction à +7 ans : le législateur n'a pas réconcilié | deux écrans de consentement dans la même banque en ligne, double coût de run, défaut de transparence | un **hub de permissions unique**, agnostique au produit, avec un attribut « régime » (PSR gratuit / FIDA compensé) sur l'objet consentement. Excellent candidat à la mutualisation Groupe : la brique est identique pour toutes les entités |
| **eIDAS 2** (2024/1183) — acceptation obligatoire par les banques en **décembre 2027** | l'art. 5f impose à quiconque est déjà tenu d'appliquer la SCA d'**accepter le portefeuille européen** comme moyen d'authentification. Cohérent avec l'assouplissement du PSR sur l'indépendance des facteurs | on construit deux fois : un connecteur portefeuille pour eIDAS 2 en 2027, puis une refonte SCA pour le PSR en 2028 | **une seule refonte du socle d'authentification, en 2027**, spécifiée d'emblée pour l'art. 5f et pour la SCA du PSR. L'AMLR fait converger KYC et authentification à la même date : trois textes, une brique, une fenêtre |

**Bloc 2 — Deux articulations qui ouvrent un trou, pas un doublon**

- **DSA** (2022/2065). Le PSR ne fait pas que renvoyer au DSA : il **branche une créance** dessus. Une
  plateforme informée d'un contenu frauduleux et qui ne le retire pas doit rembourser au PSP
  l'intégralité de ce que celui-ci a remboursé à la victime. La capacité à construire est une **chaîne
  de notification sortante** produisant une notification recevable au sens du DSA et **conservant la
  preuve** que la plateforme a été informée — puisque c'est cette preuve qui fonde la créance. Sans
  elle, le droit existe et est inexploitable. Personne ne porte naturellement ce sujet : ni le
  paiement, ni la cyber, ni le juridique seuls. **À flécher explicitement.**
- **DMA et NFC.** Ce n'est pas un sujet de conformité, c'est un arbitrage de trajectoire. ⚠️ Et
  l'ouverture de la puce NFC de l'iPhone dans l'EEE **ne résulte pas du DMA** : elle résulte
  d'engagements rendus obligatoires par la Commission le 11/07/2024 au titre de l'abus de position
  dominante, pour dix ans — accès gratuit au mode Host Card Emulation, application par défaut au choix
  de l'utilisateur, **suppression de l'exigence de licence PSP**. Le DMA ne joue qu'à l'égard des
  contrôleurs d'accès désignés ; le PSR viserait tout fabricant, sans seuil. La fenêtre est donc
  ouverte depuis deux ans et le restera jusqu'en 2034 : **il n'y a pas d'urgence réglementaire, il y a
  une urgence concurrentielle.**

**Bloc 3 — Ce qui recoupe moins qu'on ne le croit**

- **NIS2** : pour un établissement de crédit, l'art. 4(1) de NIS2 s'efface devant DORA sur les mesures
  de sécurité et la notification d'incidents. Reste l'obligation d'enregistrement de l'art. 27. Le
  risque du silo n'est donc pas la duplication dans la banque, c'est l'**angle mort** : une entité du
  Groupe qui n'est pas une entité DORA et qui héberge une brique de la chaîne de paiement reste sous
  NIS2 en plein, avec une autre autorité et un autre régime de notification.
- **PCI-DSS et 3-D Secure** : standards **contractuels**, imposés par les schemes, sanctionnés par des
  pénalités de réseau, supervisés par aucune autorité prudentielle. Exactement l'inverse du PSR. Mais
  trois gouvernances convergent sur le même ACS : PCI conditionne l'environnement de données carte, le
  PSR la logique d'authentification, DORA la relation avec le prestataire d'authentification déléguée —
  l'authentification déléguée restant permise, mais **comme prestation externalisée**.
- **MiCA** : le transfert de jetons de monnaie électronique est matériellement un service de paiement.
  L'EBA a comblé le vide par une no-action letter, éteinte le 02/03/2026, en la présentant explicitement
  comme un pont vers le PSR. Il existe donc aujourd'hui, pour deux ans, un régime prétorien fondé sur
  un avis. Si une entité du Groupe émet ou distribue des EMT, ses rails deviennent des rails de
  paiement soumis au PSR. ⚠️ Non établi : la VoP s'applique-t-elle aux transferts d'EMT, dont
  l'identifiant unique n'est pas un IBAN ?
- **Euro numérique** : le Parlement a autorisé l'ouverture des négociations le 09/07/2026, la BCE vise
  de premières transactions dès mi-2027 et une première émission possible en 2029. ⚠️ Non établi :
  quelles obligations du PSR s'appliqueraient par renvoi. Tension conceptuelle à documenter : le mode
  hors ligne et les preuves à divulgation nulle de connaissance se marient mal avec un monitoring
  temps réel et une VoP fondée sur un annuaire. Le matériel €N du GT redevient actif ici.
- **RGPD**, et un fait français que le support doit porter : le **fichier national des comptes signalés
  pour risque de fraude** est en production depuis le **07/05/2026**, géré par la Banque de France,
  créé par la loi du 06/11/2025, avec avis CNIL du 16/04/2026 et une conservation de **13 mois**. Le
  partage de fraude du PSR prévoit **5 ans**. Traité en silo, on obtient deux référentiels d'IBAN
  signalés, deux gouvernances, deux durées, et une incohérence garantie. Cible : **un référentiel
  unique d'identifiants signalés**, portant par enregistrement son régime juridique, sa source et sa
  date de purge, avec deux canaux de publication. Nuance Groupe : le fichier est **français**, les
  filiales étrangères n'y ont pas accès. Enfin, l'EDPB (statement 2/2024) rappelle qu'une
  **permission accordée dans le tableau de bord n'est pas un consentement RGPD** — ne pas les
  confondre dans le même champ.

### 4.5 — Un même règlement, deux régimes de mise en œuvre : national et international

**Titre-message.** « Le PSR s'applique à l'identique à toutes les entités ; ce qui diffère, c'est
l'infrastructure de place sur laquelle chacune s'appuie »

**Chapô.** L'intuition « règlement donc uniforme, directive donc divergent » est juste mais
insuffisante. Les deux divergences les plus coûteuses pour un groupe à filiales ne viennent ni du PSR
ni de la DSP3 : elles viennent d'infrastructures nationales préexistantes que le PSR ne corrige pas.

**Bloc 1 — La ligne de partage**

- Le **PSR** harmonise les règles de conduite : mêmes obligations VoP, SCA, fraude, open banking et
  tableau de bord dans les 27 États. → **la conformité conduite est mutualisable à l'échelle du
  Groupe** : un même corpus d'exigences, un même cadre d'architecture, des briques communes possibles.
- La **DSP3** conserve l'agrément, les fonds propres, le cantonnement et la supervision. → **pilotage
  entité par entité** : autant de dossiers, de calculs et de dialogues de supervision que d'entités
  agréées. Rappel utile : les établissements de crédit du Groupe **ne sont pas soumis à l'agrément
  DSP3** ; leur charge vient presque entièrement du PSR. Seules les entités agréées EP ou EME portent
  en plus le volet DSP3 et son réexamen d'agrément, avec un régime transitoire à +27 mois.
- Le PSR est **fondé sur les rôles**, pas sur les entités : ASPSP, PSP du payeur, PSP du bénéficiaire,
  AISP/PISP. Une entité n'est impactée qu'au titre des rôles qu'elle exerce — c'est la clé de lecture
  qui évite d'attribuer à tous une charge qui n'appartient qu'à certains.

**Bloc 2 — Le cas national : le levier est industriel**

Pour les entités servies par un opérateur informatique mutualisé du Groupe, l'exigence est unique et le
socle est largement commun : la question posée est celle du **plan de charge d'une fabrique**, du
séquencement des versions et de la propagation à un parc homogène. C'est là que la mutualisation
Groupe est la plus facile — et c'est aussi là que le volume est : ⚠️ CATS porte le plus gros volume
d'authentification du Groupe avec son propre IDP, xConnect, ce qui signifie qu'une offre Groupe fondée
sur une autre brique laisserait de côté le volume principal.

⚠️ À noter comme point d'attention technique, tiré de `stack-groupe.md` : la notion de **scope**
n'existe que sur Keycloak. Tout pattern de consentement ou de révocation qui s'appuierait sur les
scopes ne serait pas portable sur les autres IDP du Groupe.

**Bloc 3 — Le cas international : le levier est le marché local**

L'exemple italien est le plus parlant, et il inverse le raisonnement habituel.

- L'Italie dispose d'un **utilitaire de place mutualisé**, CBI Globe, revendiquant plus de 80 % de
  l'industrie financière italienne et l'accès à 100 % des comptes courants italiens. Il délivre les
  API réglementaires, **distribue les certificats eIDAS** aux prestataires tiers, opère un service
  Check IBAN (IBAN contre code fiscal ou numéro de TVA, plus de 25 millions d'appels d'API — **sans
  équivalent français**), et est reconnu par l'EPC comme **mécanisme qualifié de routage et de
  vérification pour la VoP**, en service depuis le 09/10/2025, avec une capacité annoncée d'environ
  5 000 PSP en Europe. Il propose enfin deux modèles de valeur ajoutée, l'un mutualisé, l'autre
  propriétaire.
- La France ne dispose de rien d'équivalent : STET est un standard et un opérateur de compensation,
  pas une passerelle mutualisée ; chaque banque opère sa propre interface, avec des implémentations
  techniques divergentes d'un établissement à l'autre.

**Conséquences, à porter en séance**

1. **Pour une exigence réglementaire identique, la conformité de la filiale italienne sera livrée en
   grande partie par un utilitaire de place, celle de la maison mère en interne.** Deux structures de
   coûts, deux calendriers, deux niveaux de dépendance fournisseur.
2. **Le make-or-buy ne se pose pas de la même façon des deux côtés des Alpes.** En Italie, la question
   est « quel niveau de service souscrire chez CBI » ; en France, « construire ou recourir à une
   plateforme d'open banking » — ces plateformes que l'ACPR qualifie déjà d'acteurs structurants.
3. **Risque de gouvernance Groupe** : une décision « une seule brique VoP mutualisée » peut être
   économiquement absurde en Italie, où la brique est déjà achetée en mutualisé. → **La mutualisation
   Groupe pertinente se situe au-dessus des composants nationaux, pas à leur place** : référentiel de
   suspicion, hub de permissions, couche de mesure et de reporting de performance d'interface,
   taxonomie d'incidents, corpus d'exigences et cadre d'architecture. Pas les connecteurs.
4. **Pour les entités hors zone euro, le décalage est structurel et il ne vient pas du PSR** : le
   calendrier de l'IPR distingue zone euro et hors zone euro. Réception, émission, VoP et égalité des
   frais s'y appliquent avec près de deux ans de retard — VoP au 09/07/2027 contre le 09/10/2025 en
   zone euro. Puis le PSR remet tout le monde à la même date. Conséquence : une entité qui n'aura
   jamais livré la VoP IPR devra livrer directement la VoP PSR, plus large, **sans passer par la marche
   intermédiaire**. Profil de risque projet radicalement différent de celui de la maison mère.
5. **Les marges nationales existent aussi côté DSP3**, et elles touchent le prudentiel : l'option de
   cantonnement en banque centrale dépend de l'offre de la banque centrale nationale (disponible en
   France, art. L. 522-17 CMF, et en Allemagne, § 17 ZAG ; pas disponible comme option autonome en
   Espagne) ; l'autorité compétente garde la main sur les méthodes de fonds propres exigibles ; les
   États membres peuvent prévoir des astreintes **supérieures** au plancher du PSR ; un plafond de
   retrait chez les commerçants peut être abaissé jusqu'à 100 €. ⚠️ Aucun État membre n'a annoncé
   d'option à ce jour, ce qui est logique : la transposition n'a pas commencé.

**Question ouverte à poser en séance.** Qui porte la conformité PSR d'une filiale étrangère — l'entité,
sous sa supervision locale, ou le Groupe, au titre du cadre d'architecture ? Et quel est le livrable
Groupe attendu : un corpus d'exigences, un cadre d'architecture, une brique, ou un programme ?

### 4.6 — Le régime de sanctions

**Titre-message.** « Ce que le support présente comme des délais de workflow est amendable jusqu'à 10 %
du chiffre d'affaires annuel total »

**Bloc 1 — Ce que le PSR sanctionne expressément** (Art. 97(1), cinq catégories)

1. L'accès des établissements de paiement aux comptes ouverts chez un établissement de crédit
   (Art. 32) → brique de-risking.
2. Les règles applicables aux services d'information sur les comptes et d'initiation de paiement.
3. L'organisation et l'exécution des mécanismes de prévention de la fraude, **SCA incluse**
   (Art. 85 à 87) → briques Risque et MFA.
4. La transparence des frais de retrait aux distributeurs.
5. **Le non-respect des délais d'indemnisation** — Art. 56(2), 57(2), 59(2), 63(2) → les « 15 jours
   ouvrables » des planches 35 et 36.

**Bloc 2 — Les montants**

- Amendes maximales d'**au moins 10 % du chiffre d'affaires annuel total** pour une personne morale,
  **3 000 000 €** pour une personne physique, ou **le double des profits retirés ou des pertes
  évitées** — ce dernier montant pouvant **dépasser les deux plafonds**.
- **Astreintes journalières** jusqu'au rétablissement de la conformité, **six mois au maximum**, d'au
  moins **3 % du chiffre d'affaires journalier moyen** ou 30 000 €. Les États membres peuvent aller
  au-delà.
- Sanctions applicables aux **membres de l'organe de direction** et aux personnes physiques
  responsables.
- **Publication de chaque décision de sanction** sur le site de l'autorité, sans retard indu, avec
  description du manquement, et compte rendu à l'EBA.
- Douze critères de modulation, dont la coopération et les mesures correctrices prises.

**Bloc 3 — Pourquoi c'est une planche d'architecture et pas une planche juridique 🔎**

Trois des cinq catégories sanctionnées portent exactement sur les briques que le support cote 2. Un
délai de workflow non instrumenté n'est plus un risque opérationnel, c'est une assiette de sanction
avec publication nominative. C'est l'argument qui transforme une exigence de conformité en priorité de
chiffrage. À rattacher à DSP3-H23, aujourd'hui classée dans les exigences sans brique de rattachement.

### 4.7 — Ce que le GT attend des entités

**Titre-message.** « Cette séance ouvre le recueil : voici précisément ce que nous venons chercher, et
auprès de qui »

C'est le manque le plus coûteux du support, signalé deux fois dans les revues précédentes : une séance
de lancement dont l'objet est de récolter ne récolte rien sans demande explicite. Le prochain incrément
de valeur annoncé en planche 24 est la cartographie du delta DSP2 → DSP3 ; elle est impossible sans
l'existant.

**Bloc 1 — Ce que nous demandons, par thème**

| Thème | Ce que nous cherchons |
|---|---|
| Open banking, existant | standard et version exposés, modèle de consentement retenu, APIM et IDP, composants maison, nombre de TPP intégrés et concentration du trafic, durées de vie des jetons |
| Open banking, qualité | taux d'échec par type d'appel, statistiques de disponibilité et de performance publiées aujourd'hui — **et comment elles sont alimentées**. ⚠️ Point d'attention documenté : chez une entité, le reporting trimestriel public était alimenté par des valeurs simulées jusqu'au début 2026 |
| Consentement | où vit l'objet consentement, quels attributs il porte, ce qui manque pour révoquer, qui en est propriétaire dans l'organisation |
| VoP | existe-t-il un composant VoP en production au titre de l'IPR, comment est-il scopé (devise, canal, scheme), sa sortie est-elle un affichage ou une décision |
| SCA | moyens d'authentification en place, dépendance au smartphone, existence de moyens non mobiles et trajectoire de décommissionnement, état du service d'authentification mutualisé cité par les travaux DSP2 de 2017 |
| Fraude | moteur de surveillance côté payeur, existence de quoi que ce soit côté bénéficiaire, participation à des dispositifs de partage, raccordement au fichier national des comptes signalés |
| Cadres et normes | version en vigueur des standards de sécurité applicative et des normes d'intégration du Groupe cités par l'héritage DSP2, et leur caractère obligatoire aujourd'hui |
| Chantiers | tout chantier en cours qui recoupe le PSR **sans être porté comme chantier DSP3** — c'est là que se trouve l'essentiel : intégration de la VoP à un parcours d'initiation, pistes d'audit sur les virements initiés par un tiers, révocation d'accès |

**Bloc 2 — Ce que nous rendons en échange**, et à quelle échéance : matrice d'impacts par brique avec
ses justifications, delta DSP2 → DSP3 consolidé, opportunités de mutualisation instruites, cadre
d'architecture.

**Bloc 3 — Le calendrier de recueil et les interlocuteurs** — à compléter avec les noms et les dates
d'ateliers.

### 4.8 — Les questions ouvertes qui bloquent la suite

**Titre-message.** « Sept questions dont la réponse conditionne le chiffrage, et qu'aucune lecture du
texte ne permet de trancher »

1. **Le « no match » de la VoP est-il informatif ou bloquant ?** L'IPR restitue le résultat au payeur,
   qui décide. Le communiqué du Parlement décrit le PSR comme imposant de **refuser** le paiement en
   cas d'écart. Si cette lecture se confirme, on passe d'un écran d'avertissement à un rejet avec
   gestion d'exception, recours client et réclamation. ⚠️ **La question la plus lourde de conséquences
   du paquet, et elle se lit en une page du texte.**
2. **Le véhicule inter-PSP de la preuve de surveillance n'existe pas** (Art. 83(1a)). Le texte crée
   l'obligation de prouver que **les deux** PSP ont exécuté la surveillance, et fait rembourser le PSP
   du payeur à défaut. Aucun dispositif de place ne porte cet échange. DSP3-H10, exposition financière
   à provisionner.
3. **Que devient l'accès « exceptionnellement via une autre interface sûre et efficace » ?**
   (Art. 45(1)). Le mécanisme de secours des RTS de 2018 disparaît, aucune définition ni RTS ne le
   remplace. Portée : trajectoire API entière. DSP3-H04.
4. **Quel référentiel de noms expose-t-on, et avec quelle logique de concordance approchante ?**
   Nom commercial, raison sociale, nom complet ? DSP3-H07 et H08.
5. **Que deviennent les certificats qualifiés QWAC et QSEAL en open banking ?** ⚠️ Aucune source n'a
   permis d'établir si le PSR conserve, modifie ou supprime l'exigence des RTS de 2018. Impact fort
   pour les ASPSP et pour les utilitaires de place qui distribuent ces certificats.
6. **Les dispositions open banking ont-elles une date d'application différée propre ?** ⚠️ Aucune
   source ne le mentionne : seul le différé de la VoP est documenté. Si les obligations d'interface
   mordent à +21 mois comme le reste, le plan de charge change. **À vérifier dans les dispositions
   finales du PSR.**
7. **Quel est l'existant DSP2 du Groupe, réellement ?** Les travaux de 2018 sont archivés et
   disponibles sur demande ; le seul matériel remonté à ce jour est un kit d'accompagnement d'août
   2017, antérieur à l'application de la DSP2 — il établit une intention, pas un existant. Tant que le
   delta n'est pas mesuré, toute cotation d'impact repose sur une ligne de base supposée.

---

## 5. Corrections sur le corps du support

**Planche 12 — calendrier.** Le support annonce « deux échéances à tenir ». Il y en a **quatre** :
entrée en vigueur (T+0, vingt jours après publication) ; **T+21 mois**, application générale du PSR et
échéance de transposition de la DSP3 ; **T+27 mois**, vérification du bénéficiaire ; **T+27 mois**,
fin du régime transitoire des agréments d'établissements de paiement et de monnaie électronique, avec
suspension des services pour les EME non conformes. Ce dernier régime n'apparaît pas du tout et il
concerne directement les entités agréées du Groupe.

Autres corrections sur la même planche :

- Le premier mandat de l'EBA échoit à **+9 mois** (RTS de l'Art. 38(5) sur les KPI et le temps de
  rétablissement), pas +12.
- « Premiers RTS/ITS (+12 mois) » : préciser qu'il s'agit d'une date de **soumission de l'EBA à la
  Commission**, pas de disponibilité de la norme. Le programme de travail 2026 de l'EBA annonce
  **plus de 50 mandats et tâches** au titre de DSP3, PSR et FIDA, et une feuille de route de mise en
  œuvre prévue au deuxième trimestre 2026 — ⚠️ dont aucune trace de publication n'a été trouvée à ce
  jour, non plus qu'aucune consultation.
- ⚠️ Si l'entrée en vigueur est fin 2026, +27 mois tombe au **premier trimestre 2029**, pas au
  deuxième. Le support écrit T2 2029.
- Statut du texte, à corriger : le paquet a été approuvé en commission ECON le **05/05/2026** et est
  « close to adoption », mais **il ne figure pas parmi les actes adoptés en session plénière de juillet
  2026**. Restent : adoption formelle par le Conseil, approbation en seconde lecture, signature,
  publication. **Aucune date de plénière n'est connue.** Toutes les dates absolues du support restent
  donc des dates relatives, et la mention « glissement à septembre évoqué en place » (planche 22) est
  à remplacer par « aucune date de publication n'est acquise ».
- Piège de vocabulaire à ne pas reproduire : plusieurs cabinets titrent « PSD3 and PSR published ». Il
  s'agit de la publication des **textes de compromis du Conseil** en avril 2026, pas du Journal
  officiel.
- ⚠️ Toute la littérature antérieure à avril 2026 est périmée sur les délais : on y lit encore 18 mois
  d'application et 24 à 30 mois pour le ré-agrément. Le compromis dit **21 et 27**.

**Planche 14 — fraude.** Trois corrections :

- La VoP est rattachée à l'Art. 50, qui porte l'**extension du champ** ; le **mécanisme** est dans le
  règlement 260/2012 tel que modifié par l'**Art. 110c**, et la **responsabilité** associée est à
  l'Art. 57. Trois articles, trois objets.
- Le mécanisme n'est pas binaire : trois issues, dont la **concordance approchante**, avec obligation
  d'indiquer le nom associé à l'identifiant. Une VoP présentée en oui/non serait fausse.
- L'Art. 59 n'est pas un remboursement automatique : six conditions cumulatives, deux exclusions,
  charge de la preuve sur la banque. Reprendre la formulation de §2, planche 35. La ligne « pour les
  entités » du tableau doit dire ce que cela implique : un parcours à construire **et une position à
  prendre sur les critères de négligence grave**.

**Planche 15 — SCA.** Ajouter la réserve de l'Art. 88(2) (accord de l'utilisateur pour une fourniture
exclusivement mobile). ✅ La formulation sur l'Art. 88a est juste : c'est bien une contrainte qui se
lève, l'article n'impose rien à la banque, il oblige les fabricants et les opérateurs.

**Planche 16 — open banking.** « Le mécanisme de secours des RTS de 2018 disparaît » ✅ est exact et
c'est l'un des points les plus lourds du paquet — le lier explicitement à la question ouverte n°3 de la
planche §4.8, car en l'état le support annonce une disparition sans dire que rien ne la remplace.

**Planche 18 — les neuf parcours.** ✅ Excellente planche, deux réserves : le seuil « cinq requêtes en
échec ou sans réponse sous 30 secondes » vient des orientations EBA, pas du PSR (parcours 6) ; et le
parcours 4 doit porter les conditions cumulatives, non le seul « remboursement intégral ».

**Planches 20 et 21 — API.** Trancher le coloriage (cf. §3.1), et corriger l'affirmation sur STET
(cf. §1.3). Le tableau « ce que le texte dit / pourquoi la question se pose / pourquoi c'est
difficile » de la planche 21 est bon et peut être conservé tel quel en amorce, la planche §4.3 le
développant.

**Planche 23 — les cinq domaines.** Ajouter deux lignes : **sanctions et délais opposables**, et
**articulations** (IPR, DORA, AMLR, eIDAS 2, FIDA, DSA) — sans quoi la synthèse laisse croire que le
sujet est refermé sur lui-même. Et corriger la ligne SCA : « attendre les RTS pour figer » est vrai
pour les exemptions, faux pour l'accessibilité et l'activation d'application mobile, qui sont dans le
règlement et ne dépendent d'aucun RTS.

---

## 6. À faire avant diffusion

1. Redéposer le PDF du PSR dans `reglementations/dsp3/` et corriger `sources.md`.
2. Trancher « huit ou neuf fonctions d'initiation » sur l'Art. 36(4), puis recaler DSP3-EX-149, la
   matrice et la planche.
3. Corriger la matrice sur les trois points où elle porte l'erreur en amont du support : ancrage des
   180 jours (art. 10 des RTS 2018/389), « interdiction de fait » du cantonnement mono-domicilié
   (PSD3 Art. 9(2)), et les deux obligations à 10 secondes présentées comme une seule.
4. Ajouter à la matrice les trois exigences manquantes identifiées : remboursement des prélèvements
   passant de 10 à 15 jours ouvrables (Art. 63(2)), cinématique d'activation d'application mobile
   rattachée à MFA (Art. 51(4a)-(4e)), et les cinq facteurs de risque minimaux (Art. 83(2b)).
5. Enregistrer dans `sources.md` les textes de la ligne de base : RTS 2018/389, IPR, EBA/GL/2018/07,
   RGPD, DORA. Sans eux, aucun « déjà exigé » n'est sourcé.
6. Lire l'Art. 50 pour trancher la question du « no match », et les dispositions finales pour trancher
   l'existence d'un différé propre à l'open banking.
