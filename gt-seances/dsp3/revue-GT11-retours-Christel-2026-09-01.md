# GT11 — Retours de Christel Body sur le support (atelier du 01/09/2026)

> Source : transcript de la réunion de cadrage DSP3 du 01/09 (Notion,
> « Réunion de cadrage DSP3 — GT Architecture & Christelle »).
> Support passé en revue : `GT11 - Lancement DSP3-PSR V2` (38 planches), numérotation de cette version.
> ⚠️ Le résumé IA de la page Notion porte des années fausses (« 2025 ») : se fier au transcript.
>
> Ce fichier ne rejuge pas le support : il liste ce que Christel a dit, planche par planche, et
> distingue ce qui est à appliquer de ce qui est à arbitrer contre le texte (Règle n°3).

## A. À appliquer — corrections factuelles nettes

| # | Planche | Ce qui est écrit | Ce que dit Christel | Action |
|---|---|---|---|---|
| A1 | 15 (titre) | « LE PSR **REFOND** LE SOCLE DE LA SCA » | « Ah non, on ne peut pas dire ça. Ils ne refont pas, au contraire ils gardent tous les principes. » | Remplacer par **« aménage »** / « aménagement de l'authentification forte ». Idem colonne 1 : « Redéfinir le socle » → autre verbe (préciser / aménager) |
| A2 | 10 (frise) | « Premiers RTS/ITS (+9 à 12 mois) » | « Le calendrier des RTS est mal présenté : c'est le calendrier que doit respecter l'ABE. Projet de RTS, 9 à 18 mois. » | Reformuler en **mandat EBA** (« projets de RTS à soumettre par l'EBA, 9 à 18 mois »), pas en jalon de publication |
| A3 | 10 (frise) | « nouvelles exigences VoP (+27 mois) » | « Il n'y a qu'un seul sujet à 27 mois. C'est pas une nouvelle exigence, c'est une **extension du périmètre** — les mêmes exigences étendues à tous les virements. » | Renommer le jalon ; préciser « extension à tous les virements, au sein de l'UE » |
| A4 | 10 (frise) | « Les établissements existants doivent être en conformité » | « Ça n'apporte pas grand-chose, tu peux l'enlever. » | Supprimer |
| A5 | 10 (frise) | « ≈T3 2028 application du PSR » | « C'est glissant en fonction de l'entrée en vigueur. Tu peux rajouter T4 2028. » | Écrire **T3/T4 2028**, et dire explicitement que la frise glisse avec l'entrée en vigueur (attendue T4 2026 / T1 2027, texte en retard : attendu septembre, désormais décembre) |
| A6 | 10 (bandeau objectifs) | « Harmoniser les règles applicables au secteur des services de paiement pour favoriser la concurrence » | « Ça n'a rien à voir avec l'open banking, c'est l'ouverture de compte et l'accès à la compensation. Micro-sujet, moi je l'enlèverais. » | Supprimer la phrase, ou l'assumer comme renvoi à la planche 17 |
| A7 | 10 (bandeau objectifs) | « Accroître la compétitivité des services d'Open Banking » | « La compétitivité, ce n'est pas le bon terme. » | Reformuler en **performance / développement de l'open banking** |
| A7a | **9** (chapeau) | « Remise en question de la DSP1… / de la DSP2… » | « C'est un peu fort. On ne remet pas en question la réglementation, ça s'appelle le **bilan**. » (clause de révision quinquennale) | Renommer les deux jalons |
| A7b | **9** (puce 1) | « Des API bancaires encore hétérogènes : … les fintechs doivent composer avec des implémentations différentes (Berlin Group, STET, interfaces propriétaires) » | « Oh là là non, ça ne me plaît pas, parce que nous on va militer pour la STET. » / « Ça m'embête, la fintech, de proposer des implémentations : c'est leur problème. » | Deux griefs : citer STET et Berlin Group sur le même plan préempte un arbitrage non rendu ; et présenter l'hétérogénéité comme une limite subie par les fintechs adopte leur point de vue. Reformuler en constat de place sans nommer de cible, ou renvoyer à la planche 22. Cf. §D |
| A7c | **9** (puce 2) | « … de nombreux freins à l'adoption de l'Open Banking » | « Même pas un nombre de freins. Il n'y a pas d'engouement pour le service. Si tu écoutes les TPP il n'y a que des freins, mais le sujet c'est l'absence d'usage. C'est un fiasco : moins la qualité de service que la rencontre avec le marché. » | Faire porter la puce sur **l'absence d'usage** ; les frictions techniques en facteur second, identifiées comme le discours des TPP |
| A7d | **9** (puce 3 / chapeau du bloc) | « Évolution de la fraude et limites de la SCA : spoofing, ingénierie sociale, faux conseiller » | « Ça, ce n'est pas trop sur l'open banking. » puis, après explication : « ce paragraphe, on va l'ordonner pour que ce ne soit pas si axé sur… » | La puce est juste : c'est le chapeau qui induit en erreur. Annoncer que les limites relevées dépassent l'open banking et couvrent le paquet DSP3/PSR |
| A8 | 14 (ligne DSP2, colonne 1) | « La banque ne contrôle que l'IBAN » | « Ça fait mal. Je verrais tout ce qu'il y a comme indicateurs et modèles de détection. » | Reformuler : le contrôle nom/IBAN n'existait pas, mais la détection de fraude, oui |
| A9 | 14 (ligne DSP2, colonne 2) | « Chaque PSP surveille seul, sans vision des schémas de fraude du marché » | « Si, quand même, ils se causent. » | Nuancer : pas d'obligation ni de cadre formalisé, mais des échanges existent |
| A10 | 15 (colonne 3, DSP2) | « Les PSP dépendent des fabricants d'OS **pour le sans contact** » | « Non, le sans contact il n'y a pas d'authentification forte. Il faut enlever le sans-contact. » | Retirer la mention sans contact de la ligne DSP2 |
| A11 | 16 (colonne 3) | « Tableau de bord unique dans **l'application bancaire** » | « L'application bancaire, en général c'est l'application mobile. C'est restrictif : il vaut mieux mettre **la banque en ligne**. » | Corriger ici, dans l'exemple 2 et dans le schéma (« interface client : banque en ligne **ou** mobile ») |
| A12 | 16 (colonne 3) | « voir, **gérer** et révoquer toutes les autorisations » | « Gérer c'est abusif : c'est voir et révoquer, et éventuellement annuler la révocation sous 48 h s'il s'est trompé. » | Remplacer « gérer » ; ajouter la fenêtre d'annulation |
| A13 | 16 (colonne 3, « Pour les entités ») | « Brique front nouvelle, à construire dans chaque banque en ligne et application mobile » | « Non, ça existe déjà. » (B4Bank travaille déjà sur ce tableau de bord dans le cadre de ses travaux DSP3) | Reformuler : brique existante à étendre / à généraliser, pas création ex nihilo. ⚠️ recoupe le bloquant **V2·A6** du registre consolidé (périmètre AIS/PIS récurrents, nature back-office) |
| A14 | 16 (colonne 2, DSP2) | « Frictions **tolérées** dans les parcours d'accès » | « Ah non ! Elles n'étaient pas tolérées, c'est l'ACPR qui avait défini les frictions, elles étaient déjà connues. » | Reformuler : obstacles déjà encadrés, la nouveauté est la **liste explicite d'obstacles interdits** |
| A15 | 16 (colonne 1) | « statistiques de **disponibilité** publiées chaque trimestre » (et exemple 1 : « disponibilité et performance ») | « La disponibilité était déjà donnée chaque trimestre. Ce qu'il faut, c'est les **taux de réussite** : accès au compte, virements initiés, et les interruptions non prévues. » | Remplacer le contenu des statistiques : taux de réussite + interruptions non planifiées |
| A16 | 16 (colonne 2) | « Recours à l'interface client admis en cas de panne » → « devient exceptionnel et strictement encadré » | « Non, il devient carrément **interdit**. On a réussi à ce qu'il n'y ait pas d'API de secours : l'API devient le seul canal. Le web-scrapping pourra être bloqué sur la partie paiement. » | Durcir : interdiction du recours à l'interface client, disparition du fallback, API canal unique |
| A17 | 12 (encadré 3) | « socle groupe **international** » (formulation orale relevée) | « International, tout à l'heure, c'est plutôt **européen**. » | Corriger le périmètre |

## B. À arbitrer contre le texte avant d'appliquer (Règle n°3)

| # | Planche | Point | Position Christel | Pourquoi arbitrer |
|---|---|---|---|---|
| B1 | 16 | « champ de données exposées **enrichi** » | « Pas d'élargissement fonctionnel : les API DSP3 donnent accès aux mêmes données que DSP2 — comptes, historique, initiation de virements. Ça ne change pas. » | Contredit frontalement la planche. Trancher sur le texte du PSR (art. 35 s.) avant de réécrire, puis propager à l'exemple 1 et au schéma |
| B2 | 16 | « La parité de données devient la règle » | « Non, la parité était déjà là. On le respecte, les TPP nous dénoncent à l'ACPR sinon. » | Le registre consolidé note déjà que la parité porte sur disponibilité / performance / information. La nouveauté à qualifier précisément |
| B3 | 15 | « Exemptions **redéfinies** », « Tous les parcours alignés sur les exemptions de 2018 sont à réinstruire » | « Réinstruire, non, pas forcément. La Banque de France est très contente des exemptions actuelles. Mais le RTS de 2019 est à moitié déversé dans le PSR, il faudra en faire quelque chose. » | Ni « réinstruire » ni « inchangé » : formuler au conditionnel, un RTS est attendu |
| B4 | 15 | Ligne « ouvrir l'accès » (NFC) | « L'ouverture de la puce, je ne maîtrise pas, je ne m'aventurerai pas. Je ne peux pas confirmer. » | Pas de validation métier : à sourcer sur le texte (art. 88a) avant la séance |
| B5 | 15 | Accessibilité / inclusion | « À part les deux facteurs d'inhérence, le reste n'est pas un sujet. Le canal alternatif au smartphone existe déjà dans le Groupe (SVI renforcé, code sur téléphone fixe) et CAPS l'a validé conforme. » | Le « Pour les entités » (« canal à concevoir et maintenir ») est faux pour le Groupe : à requalifier en modernisation éventuelle, non prioritaire |
| B6 | 15 | Point que le support **ne porte pas** et que Christel juge le vrai enjeu | « Le PSR permet deux facteurs d'**inhérence**, sous conditions et avec RTS dédié. Ça nous embête : Visa/Mastercard pourront créer leurs solutions, la SCA nous échappe — or le parcours SCA alimente le scoring GDR (GDR carte, GDR virement, GDR authentification) et permet de bloquer l'initiation. » | **À ajouter**. C'est le seul point où elle voit un risque stratégique pour le Groupe |
| B7 | 17 | Planche de-risking | « Ce n'est pas notre sujet, c'est celui des schemes et systèmes de paiement, une question de concurrence. Ça concerne CACI, pas les entités. Je ne la traiterais pas. » | Alex a maintenu la planche comme overview du texte, sans déclinaison en chantier. Décider : garder telle quelle avec une mention explicite « hors périmètre GT », ou basculer en annexe |
| B8 | 11 | Deux instruments juridiques | « Il est beau ce slide. Sinon vous le mettez en annexe. » (public d'architectes = argument retenu pour le garder) | Arbitrage assumé : garder dans le corps. Rien à faire, tracé ici pour mémoire |
| B9 | 12 | Bloc « piloter / maîtriser / arbitrer » | « Ça c'est plus votre truc, je n'ai pas trop de valeur ajoutée. Mais au-delà, c'est pas un peu redondant tout ça ? » | Signal de longueur, pas de fond. À recouper avec la remarque de lisibilité déjà au registre |

## C. Contenu manquant, à créer

| # | Objet | Ce qu'elle a dit | Où |
|---|---|---|---|
| C1 | **Communication client** comme axe de prévention | « Prévenir, c'est plus de la sensibilisation. Il y a beaucoup de communication client : à chaque fois qu'on surveille, qu'on bloque une opération, on devra communiquer. C'est ça que j'aurais mis, plus que le contrôle de l'IBAN. » Un considérant du PSR invite à créer un **canal de communication sécurisé** bidirectionnel banque ↔ client (le SMS n'est pas sécurisé) | Planche 14, colonne « prévenir ». Impact architecture explicite relevé en séance : lier supervision, alerting et interfaces |
| C2 | **Archivage des échanges client** | « Il faudra recueillir sa réponse et l'archiver. L'archivage est légal, c'est la preuve. Sans ça on ne peut pas négocier le remboursement — négligence grave. Les caisses régionales n'archivent pas les SMS d'alerte, LCL le fait. » | Planche 14 (réparer) et annexe 2 (données opérationnelles / preuve) |
| C3 | **GDR côté bénéficiaire** | « Le gros du sujet c'est la fraude, avec les fameux GDR — il va falloir en créer un côté bénéficiaire pour les mouvements reçus. » | Planche 20/25 (impacts) — chantier structurant non identifié aujourd'hui |
| C4 | **Partage de données de fraude entre PSP** | Confirmé par elle comme obligation du texte, au-delà de la VoP | Déjà en planche 14 colonne 2 : à ne pas diluer, c'est ce qui justifie que la fraude ≠ VoP |
| C5 | **Argument budgétaire** | « J'ai envoyé un mail la semaine dernière aux entités : mettez des jours dans vos budgets. S'ils n'ont pas le budget, ils ne regardent pas le sujet. Et les sanctions sont là pour que les patrons donnent les budgets. » | Renforce la planche 24 (fenêtre courte) et le volet **sanctions** déjà noté absent au registre (V2·A7) |

## D. Posture — hors correction de planche

- **STET / Berlin Group** : réaction immédiate et non ambiguë — « nous on va militer pour la STET » ;
  « ça m'embête que la FinTech propose des implémentations, c'est leur problème ». Elle attend
  toujours le retour du B-Comp sur le papier alimenté par Hatim. La planche 22 présente la cible
  Berlin Group comme « pressentie » : à confronter à cette position avant la séance
  (cf. DSP3-H02, action du 10/09 auprès d'elle).
- **Ton général** : « je suis un peu pointilleuse, mais c'est pour qu'on ne soit pas en contradiction.
  Ne vous engagez pas sur des sujets sans maîtrise parfaite. » Le support est validé dans son
  intention (« c'est bien, tu pars de la DSP2 et tu emmènes vers la DSP3 »), les réserves portent
  sur les formulations non maîtrisées.

## Recoupements avec le registre consolidé

- Renforcent des bloquants déjà ouverts : **V2·A2** (calendrier, cf. A2/A3/A5), **V2·A6** (tableau
  de bord Art. 43, cf. A13), **V2·A7** (sanctions, cf. C5).
- Nouveaux, non couverts par le registre : A1, A6→A10 (dont A7a→A7d, planche 9), A14→A17, B1→B7, C1→C3.
