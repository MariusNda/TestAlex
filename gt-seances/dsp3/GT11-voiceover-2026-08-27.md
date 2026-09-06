# GT11 du 16/09/2026 — Voiceover, slide par slide

> À lire à voix haute une fois avant la séance. Chaque planche a le texte à dire, puis les questions
> qui peuvent tomber et la réponse. Écrit pour être dit, pas pour être lu à l'écran.

---

## Avant de commencer : les huit phrases qui te rendent inattaquable

1. **Le paquet, c'est deux textes.** Une directive, la DSP3, qui s'adresse aux États et sera transposée
   en droit français. Un règlement, le PSR, qui s'applique directement à nous, sans passer par le droit
   national. **Presque toute la charge informatique est dans le règlement.**
2. **Le texte n'est pas encore publié.** Accord politique fin novembre 2025, textes de compromis publiés
   en avril 2026, approuvés en commission parlementaire le 5 mai. Il reste l'adoption formelle et la
   publication au Journal officiel européen. **Donc aucune date absolue n'est acquise** : on ne raisonne
   qu'en « entrée en vigueur + X mois ».
3. **Trois échéances.** L'entrée en vigueur, vingt jours après la publication. Puis +21 mois :
   application générale du règlement, et date à laquelle les États doivent avoir transposé la directive.
   Puis +27 mois : la vérification du nom du bénéficiaire sur tous les virements, et la fin du régime
   transitoire des agréments.
4. **Une partie du texte n'est pas encore écrite.** Le règlement renvoie plus de cinquante sujets à des
   normes techniques que l'Autorité bancaire européenne doit produire, la première à +9 mois, l'essentiel
   entre +12 et +18 mois. Certains paramètres qui conditionnent nos chiffrages n'existent donc pas encore.
5. **Le vrai sujet du PSR, c'est la fraude par manipulation.** La DSP2 protégeait le client contre
   l'opération qu'il n'avait pas validée. Le PSR s'attaque à celle qu'il a validée lui-même parce qu'on
   l'a trompé.
6. **Rien de tout cela n'arrive sur un terrain vierge.** Six textes portent déjà une grande partie des
   exigences : la DSP2, les normes techniques de 2018, le règlement sur les virements instantanés, le
   RGPD, DORA et le règlement SEPA. C'est ce qu'on appelle la ligne de base, et c'est ce qui explique que
   les deux tiers du SI ressortent hors périmètre.
7. **Le PSR n'impose aucun standard d'API.** Rester sur STET est parfaitement légal. Le débat
   STET / Berlin Group est un choix d'architecture, pas une contrainte réglementaire.
8. **Et la phrase qui sauve toutes les questions difficiles** : « c'est justement ce qu'on vient chercher
   avec vous ». Ce GT est une séance de lancement, pas une restitution.

## Le vocabulaire, en une phrase chacun

- **PSP** — prestataire de services de paiement. Nous en sommes un, une fintech aussi.
- **Banque teneuse de compte** (on dit aussi ASPSP) — celle qui détient le compte du client et doit
  l'ouvrir aux tiers.
- **AISP** — un service qui **lit** les comptes, par exemple un agrégateur.
- **PISP** — un service qui **déclenche** un paiement depuis le compte, sans carte.
- **TPP** — le terme générique pour ces tiers.
- **SCA** — authentification forte : au moins deux facteurs, ce que je sais, ce que j'ai, ce que je suis.
- **VoP** — vérification du bénéficiaire : on compare le nom saisi au titulaire réel de l'IBAN.
- **IPR** — le règlement sur les virements instantanés, qui a déjà imposé la VoP en octobre 2025.
- **RTS** — norme technique européenne : le niveau de détail que le règlement délègue à l'EBA.
- **EBA** — l'Autorité bancaire européenne, qui écrit ces normes. **ACPR** — notre superviseur français.
- **DORA** — le règlement sur la résilience informatique du secteur financier, applicable depuis
  janvier 2025.
- **FIDA** — le futur règlement qui étendra l'open banking à tous les produits financiers.

---

# Ouverture

## Slide 1 — Couverture

> Bonjour à tous. Onzième atelier du GT Architectures réglementaires. Une séance un peu particulière :
> on ouvre un nouveau texte, le paquet DSP3 / PSR, et l'objectif de cette séance est d'abord de vous
> mettre tous au même niveau de compréhension, puis de vous dire ce dont on a besoin de vous. On a aussi
> deux points de suivi, l'euro numérique en début de séance et une intervention de CATS sur PCI-DSS à la
> fin.

## Slide 2 — Agenda

> Le déroulé. On commence par un rappel rapide de ce que fait ce GT, pour ceux qui nous rejoignent. Puis
> l'actualité de l'euro numérique, dix minutes. Ensuite le cœur de la séance en trois temps sur
> DSP3/PSR : comprendre le paquet, ce qu'il change fonctionnellement, et nos premières projections
> d'impact sur le système d'information. On termine par les étapes suivantes, et CATS prend la main sur
> PCI-DSS.
>
> Une précision utile dès maintenant : sur DSP3/PSR, cette séance n'est pas une restitution. C'est un
> lancement. Je viens vous partager un socle de connaissances et une première lecture d'impact, et je
> viens chercher votre existant.

## Slide 3 — Carton : rappel des objectifs du GT

> Trois minutes de rappel, pour que tout le monde sache ce qu'on attend de ce groupe de travail.

## Slide 4 — Les trois objectifs du GT

> Le constat de départ est simple : les chantiers réglementaires se multiplient, et ils sont tous
> transverses. Chaque entité les traite dans son coin, avec les mêmes questions et souvent les mêmes
> réponses. Ce GT sert à trois choses.
>
> Un, **repérer ce qui peut être mutualisé**. Quand deux textes ou deux entités demandent la même chose,
> autant partager la solution, le coût et le risque.
>
> Deux, **orienter les stratégies de mise en œuvre**. Composant par composant : est-ce qu'on construit,
> est-ce qu'on achète, est-ce qu'on fait évoluer l'existant.
>
> Trois, **accompagner la définition des architectures cibles**, en produisant un cadre de référence —
> des patterns, des standards — qui évite à chaque entité de repartir de zéro.
>
> On ne fait pas la conformité à la place des entités. On éclaire les décisions d'architecture.

**Si on te demande « et qui décide, au bout ? »** → Les entités décident, chacune sur son périmètre.
Le GT produit l'analyse partagée, les options et les recommandations. Là où un arbitrage Groupe est
nécessaire, on l'identifie et on le remonte.

## Slide 5 — La démarche en trois étapes

> Quand on traite un texte en profondeur, on procède en trois étapes, toujours les mêmes.
>
> D'abord on **analyse les impacts sur les capacités du SI** : on cartographie les exigences, on regarde
> l'existant, et on esquisse une macro-architecture cible avec les entités les plus avancées.
>
> Ensuite on **évalue les capacités techniques**, couche par couche, composant par composant.
>
> Enfin on **produit les réponses** : on accompagne les entités dans leur évaluation, on identifie ce qui
> peut être mutualisé, et on complète le cadre d'architecture du Groupe.
>
> Sur DSP3, on ambitionne d'être plus opérationnels que sur les textes précédents, pour une raison
> simple : il y a déjà un existant DSP2 dans toutes les entités. On ne partira pas d'une page blanche,
> on partira d'un delta.

## Slide 6 — Le cycle de traitement

> Comment ça s'organise dans le temps. Le GT se réunit une fois par mois, et entre deux séances on
> travaille en ateliers avec les entités.
>
> Le premier GT — c'est aujourd'hui — sert à l'acculturation : on aligne tout le monde et on identifie
> les entités volontaires et leurs référents. Entre les deux, on fait le cadrage réglementaire, un état
> des lieux entité par entité en bilatéral, et l'étude d'impact. Le deuxième GT est un point d'étape sur
> ce qui remonte du terrain. Puis on produit les réponses d'architecture, et le troisième GT conclut,
> avec une décision assumée : on continue ou on arrête.
>
> Compter environ deux mois pour traiter le cœur d'un texte.

**Si on te demande « deux mois pour un texte de 400 pages, sérieusement ? »** → Deux mois pour le cœur :
les impacts d'architecture et les opportunités de mutualisation. Pas pour la mise en conformité, qui
est un programme de deux ans et qui appartient aux entités.

## Slide 7 — Carton : euro numérique

> On enchaîne sur l'actualité de l'euro numérique.

*(Suivi porté hors de cette note.)*

---

# Partie 1 — Comprendre le paquet (≈15 min)

## Slide 8 — Carton : comprendre le paquet réglementaire

> On attaque DSP3/PSR. Je vous propose de commencer par le contexte : d'où on vient, pourquoi ce texte
> arrive, et surtout comment il est construit — parce que sa construction a des conséquences très
> concrètes sur ce que nous, architectes, avons à faire.

## Slide 9 — D'où on vient : DSP1, DSP2

> Petit retour en arrière, parce que le PSR ne s'explique que comme une réponse aux limites du texte
> précédent.
>
> **Avant 2007**, chaque pays régulait les paiements à sa façon. La **DSP1** crée un marché unique et
> ouvre le jeu : elle invente le statut d'établissement de paiement, qui permet à des acteurs non
> bancaires de proposer des services de paiement dans un cadre régulé. C'est ce qui a rendu possibles les
> Adyen, les Worldline.
>
> **Vers 2015**, ce cadre ne suffit plus : les fintechs se multiplient, les paiements en ligne explosent,
> la fraude suit.
>
> **La DSP2, en 2018**, fait deux choses majeures. Elle crée l'**open banking** : une banque doit ouvrir
> les comptes de ses clients à des tiers agréés, via des API. Deux nouveaux métiers apparaissent — les
> agrégateurs de comptes et les initiateurs de paiement. Et elle impose l'**authentification forte**,
> ce fameux double facteur qu'on connaît tous depuis.
>
> **Et vers 2022**, on constate trois limites. Les API sont hétérogènes d'une banque et d'un pays à
> l'autre — les fintechs doivent s'adapter à chacun. L'expérience utilisateur reste mauvaise :
> redirections, authentifications répétées. Et surtout, la fraude a changé de nature : elle ne consiste
> plus à contourner l'authentification, mais à convaincre le client de la faire lui-même. C'est le faux
> conseiller.
>
> DSP3 et PSR répondent à ces trois limites.

**Si on te demande « la DSP2 a-t-elle échoué ? »** → Non. Elle a créé l'open banking et l'authentification
forte, qui ont fait chuter la fraude à la carte. Elle n'a simplement pas anticipé deux choses : que la
qualité des API ne se décrète pas, et que le fraudeur s'adapterait en attaquant l'humain plutôt que la
technique.

## Slide 10 — Ce que DSP3/PSR vient moderniser, et le calendrier

> Les objectifs affichés sont au nombre de quatre : rendre l'open banking plus compétitif avec des API
> plus performantes, harmoniser les règles pour favoriser la concurrence, mieux lutter contre la fraude,
> et protéger les droits des consommateurs.
>
> Un chiffre pour mesurer l'urgence : au premier semestre 2025, en France, la fraude par manipulation —
> le client qu'on trompe pour qu'il valide lui-même — a progressé de 37 %, à 245 millions d'euros,
> pendant que la fraude à la carte reculait de près de 10 %. Le déplacement du problème est là.
>
> Sur le calendrier, la règle à retenir : **on ne connaît aucune date absolue**. Le texte est agréé mais
> pas encore publié au Journal officiel européen. Tant qu'il ne l'est pas, tout se compte en « entrée en
> vigueur plus X mois ».
>
> À la publication, entrée en vigueur vingt jours après. Puis **+9 à 12 mois**, les premières normes
> techniques de l'EBA. Puis **+21 mois**, le règlement s'applique partout en Europe et les États doivent
> avoir transposé la directive — la DSP2 disparaît à ce moment-là. Puis **+27 mois**, deux choses : la
> vérification du nom du bénéficiaire s'étend à tous les virements, et le régime transitoire des
> agréments prend fin.
>
> Et la raison pour laquelle on ouvre le sujet aujourd'hui : comptez six mois de cadrage plus dix-huit
> mois de développement, on est à vingt-quatre mois. C'est presque toute la fenêtre. Si on attend la
> publication pour commencer, on est en retard le jour où elle arrive.

**Si on te demande « pourquoi 21 mois et pas 18, j'avais lu 18 ? »** → Les analyses d'avant avril 2026
disaient 18 mois. Les textes de compromis publiés en avril disent 21, et 27 pour la vérification du
bénéficiaire. Toute la documentation antérieure est périmée sur les délais.

**Si on te demande « quand sera-t-il publié ? »** → Personne ne le sait. Il n'est pas passé en séance
plénière en juillet. C'est précisément pour ça qu'on ne met que des dates relatives.

## Slide 11 — Un paquet, deux instruments juridiques

> C'est la slide la plus importante pour un architecte, et je vais prendre une minute dessus.
>
> Un **règlement** européen s'applique **directement**. Il n'y a pas de loi française à écrire : le jour
> où il s'applique, l'article du règlement est opposable, et c'est le même texte à Paris, à Milan et à
> Varsovie. Une **directive**, elle, s'adresse aux États : chacun doit la transposer dans son droit
> national, en France par une ordonnance qui modifie le code monétaire et financier. Elle peut laisser
> des marges d'appréciation, donc des différences entre pays.
>
> Ce que ça change concrètement pour nous : le PSR, je peux le **citer directement dans une
> spécification**. La DSP3, non — je devrai attendre l'ordonnance française et la doctrine de l'ACPR, et
> geler des développements sur le texte de la directive aujourd'hui, c'est spécifier sur un brouillon.
>
> Et la répartition est très nette : la directive porte l'**agrément, les fonds propres et la
> supervision** des établissements de paiement. Le règlement porte les **règles de conduite** —
> l'authentification, la fraude, la vérification du bénéficiaire, l'open banking, la transparence. C'est
> donc **le règlement qui contient presque toute notre charge informatique**.
>
> À droite, le parcours d'un texte européen, pour situer où on en est : la Commission propose, le
> Parlement et le Conseil prennent position, on négocie en trilogue, les deux institutions adoptent
> formellement, et le texte est publié au Journal officiel. **Nous sommes juste après le trilogue** :
> l'accord existe, l'adoption formelle n'a pas eu lieu.
>
> Et le mouvement d'ensemble à retenir : ce qui était dans une directive en 2018 passe dans un règlement
> en 2026. C'est une réaction directe à l'hétérogénéité d'application de la DSP2.

**Si on te demande « donc la DSP3 ne nous concerne pas ? »** → Pour nos établissements de crédit,
quasiment pas : ils ne sont pas soumis à l'agrément DSP3, leur charge vient du règlement. En revanche
les entités agréées établissement de paiement ou monnaie électronique portent le volet directive, avec
un réexamen de leur agrément à +27 mois.

**Si on te demande « un règlement, ça veut dire zéro adaptation nationale ? »** → En pratique, il reste
des ajustements de textes nationaux et des options ouvertes aux États, notamment sur les sanctions et
sur certains plafonds. Mais l'essentiel du corpus opérationnel devient uniforme.

## Slide 12 — Ce que ça change pour le Groupe

> Conséquence directe pour un groupe à entités multiples, et il y a deux niveaux.
>
> Le niveau juridique, celui qu'on vient de voir : le PSR nous donne un **socle commun** — mêmes
> exigences pour toutes les entités, dans tous les pays. Donc un même corpus d'exigences, un même cadre
> d'architecture, et des briques potentiellement mutualisables. La DSP3, elle, se pilote entité par
> entité.
>
> Mais il y a un second niveau, moins évident et souvent plus coûteux : **les infrastructures de place**.
> Un même règlement peut être mis en œuvre de façons très différentes selon le marché. L'exemple italien
> est parlant : il existe là-bas un utilitaire de place mutualisé, CBI Globe, qui couvre plus de 80 % de
> l'industrie financière italienne et qui fournit déjà les API réglementaires, les certificats, la
> vérification du bénéficiaire. En France, il n'y a pas d'équivalent : chaque banque opère sa propre
> interface.
>
> Donc, pour une exigence réglementaire strictement identique, la conformité sera partiellement achetée
> en mutualisé d'un côté des Alpes, et construite en interne de l'autre. Deux structures de coûts, deux
> calendriers, deux niveaux de dépendance fournisseur.
>
> D'où les trois enjeux à droite : piloter des trajectoires différenciées, maîtriser la complexité des
> écosystèmes locaux, et arbitrer entre standardisation Groupe et adaptation locale. Et une conclusion
> qu'on peut déjà tirer : **la mutualisation pertinente se situe souvent au-dessus des composants
> nationaux** — les exigences, les processus, la gouvernance — plutôt que dans l'imposition d'une même
> brique technique partout.

**Si on te demande « donc on ne peut rien mutualiser ? »** → Au contraire, mais pas au niveau où on
l'imagine spontanément. Un connecteur national ne se mutualise pas. Un référentiel de consentements, une
taxonomie d'incidents, un corpus d'exigences, une couche de mesure de performance : oui.

---

# Partie 2 — Les évolutions fonctionnelles (≈15 min)

## Slide 13 — Carton : principales évolutions fonctionnelles

> On passe au contenu. Je vous propose quatre grands blocs — la fraude, l'authentification, l'open
> banking et l'accès des établissements de paiement aux comptes — puis une lecture par parcours
> concrets.

## Slide 14 — Fraude : le PSR réalloue une partie du risque vers la banque

> Le bloc le plus lourd, et le plus facile à comprendre.
>
> La DSP2 a traité la fraude sous un seul angle : **l'opération non autorisée**, celle que le client n'a
> pas validée. Sa réponse a été l'authentification forte, et ça a marché. Mais ça ne résiste pas quand le
> client valide lui-même, parce qu'un fraudeur l'a manipulé. Le PSR attaque ce nouvel angle sur trois
> fronts.
>
> **Prévenir.** Aujourd'hui, quand vous faites un virement, seul l'IBAN compte. Vous pouvez saisir
> n'importe quel nom, le virement part. Le PSR généralise la **vérification du bénéficiaire** : on
> compare le nom saisi au titulaire réel du compte. Bonne nouvelle pour nous : ce dispositif existe déjà
> depuis octobre 2025 pour les virements instantanés en euro, imposé par un autre règlement. **Le delta
> porte sur le périmètre, pas sur le mécanisme.**
>
> **Détecter.** Chaque banque surveille aujourd'hui ses propres flux, sans voir les schémas de fraude du
> marché. Le PSR rend la surveillance obligatoire et surtout rend obligatoire le **partage
> d'informations sur la fraude entre banques**. Ce sont de nouveaux flux entre établissements, à
> construire, sous contrainte du RGPD.
>
> **Réparer.** Et c'est le vrai changement. Aujourd'hui, si le client a validé, l'opération est autorisée
> et il n'y a pas de remboursement. Demain, si un fraudeur s'est fait passer pour la banque, sur les
> canaux de la banque, et que le client a porté plainte, **la banque rembourse l'intégralité, sous
> quinze jours ouvrables**. C'est un motif de remboursement entièrement nouveau, à outiller du parcours
> de réclamation jusqu'aux provisions comptables.
>
> Le schéma en bas à gauche montre la mécanique de vérification : le client saisit, notre banque
> interroge la banque du bénéficiaire, on compare, et on décide. Trois issues possibles : ça concorde et
> le virement suit son cours ; ça concorde approximativement et on présente au payeur le nom réellement
> associé à l'IBAN ; ça ne concorde pas ou la vérification est impossible, et on alerte avant
> confirmation.

**Si on te demande « on rembourse tout le monde, tout le temps ? »** → Non, et c'est important. Le
dispositif est réservé aux **consommateurs** — pas aux entreprises. Il faut que le fraudeur se soit fait
passer pour **notre** banque, sur **nos** canaux. Il faut que le client ait notifié sans retard **et**
déposé plainte. Et deux exclusions restent : la fraude du client et sa négligence grave. Le point dur,
c'est que **la preuve de cette négligence grave nous incombe**.

**Si on te demande « la vérification du bénéficiaire, on l'a déjà, non ? »** → Oui, en production depuis
le 9 octobre 2025, mais sur un périmètre étroit : les virements SEPA en euro. Le PSR l'étend à tous les
virements de son champ, y compris hors euro et hors IBAN, à +27 mois. Et il y ajoute un régime de
responsabilité que le règlement virements instantanés n'avait pas.

**Si on te demande « le partage de données de fraude, c'est légal ? »** → Le PSR l'impose et l'encadre :
catégories de données limitativement énumérées, analyse d'impact conjointe préalable. Mais il y a un
point d'attention réel avec l'anti-blanchiment, qui interdit de divulguer qu'une analyse est en cours.
C'est un des sujets qu'on devra instruire.

## Slide 15 — Authentification forte : deux dépendances qui sautent

> La DSP2 a créé l'authentification forte : au moins deux facteurs parmi ce que je sais, ce que j'ai et
> ce que je suis, indépendants l'un de l'autre. Huit ans plus tard, deux constats.
>
> Premier constat : **tout s'est construit autour du smartphone**. Le PSR y met une limite. Il faut
> désormais offrir **au moins un moyen gratuit et adapté** aux clients en situation de handicap, âgés,
> peu à l'aise avec le numérique ou sans accès numérique. Et on ne peut plus faire dépendre
> l'authentification de la possession d'un smartphone — sauf si le client l'accepte explicitement. Pour
> nous, ça veut dire un canal alternatif à concevoir **et à maintenir dans la durée**, et ça remet en
> cause les trajectoires de décommissionnement des moyens non mobiles.
>
> Deuxième constat : **l'accès aux fonctions du téléphone dépend du fabricant**. Si nous voulons proposer
> notre propre solution sans contact, il faut que le fabricant nous ouvre la puce NFC. Le PSR impose que
> cet accès soit loyal, raisonnable et non discriminatoire. Attention à la lecture : cet article
> **n'impose rien à la banque**, il impose quelque chose aux fabricants et aux opérateurs. C'est une
> contrainte qui se lève, pas une charge qui arrive.
>
> Troisième front, plus technique : le champ de l'authentification est **précisé et étendu**. Quatre
> nouveaux déclencheurs sont nommés, qui ne sont pas des paiements : créer ou remplacer une carte
> tokenisée, augmenter un plafond, changer son mot de passe en ligne, changer ses coordonnées. Et les
> exemptions de 2018 sont redéfinies par de nouvelles normes techniques. Donc tous les parcours calés sur
> les exemptions actuelles sont à réinstruire.

**Si on te demande « on doit ressortir les boîtiers ? »** → C'est exactement la question ouverte. Le
texte impose un résultat — plus d'un moyen, dont un gratuit et adapté — pas une technologie. Un code par
serveur vocal peut suffire. Ce qu'il interdit, c'est de n'avoir que le smartphone.

**Si on te demande « et les RTS, ça change quoi ? »** → Les exemptions, les seuils et l'indépendance des
facteurs seront précisés par des normes techniques attendues jusqu'à douze mois après l'entrée en
vigueur. C'est pour ça qu'on recommande de ne pas figer la refonte de l'authentification tout de suite —
sauf sur l'accessibilité, qui est dans le règlement et ne dépend d'aucune norme.

## Slide 16 — Open banking : ouvrir ne suffit plus

> La DSP2 nous a obligés à ouvrir les comptes aux tiers. Le PSR s'attaque à la qualité de cette
> ouverture, sur trois fronts.
>
> **Garantir la qualité.** Aujourd'hui, une API peut légalement offrir moins que l'application de la
> banque. Demain, il faut une **parité** : mêmes données disponibles, même niveau de disponibilité et de
> performance qu'à nos propres clients. Et des indicateurs dont la **définition est imposée** par le
> texte, publiés chaque trimestre avec la comparaison à nos interfaces client. Autrement dit, l'API
> cesse d'être un sujet de conformité pour devenir un **service exploité avec des engagements publics**.
>
> **Supprimer les frictions.** Le texte nomme douze obstacles interdits — étapes ajoutées,
> authentification plus stricte que sur notre propre canal, et d'autres. La liste n'est pas limitative,
> et tout obstacle identifié doit être supprimé immédiatement, avec sanction à la clé. Point important :
> le mécanisme de secours prévu en 2018, qui permettait aux tiers de repasser par l'interface client en
> cas de panne, **disparaît** — sans que le texte définisse clairement ce qui le remplace. La
> disponibilité de notre interface dédiée devient donc critique.
>
> **Rendre la main au client.** Aujourd'hui, un client qui a connecté trois applications à son compte
> doit aller gérer chacune séparément. Demain, il doit trouver dans **son** application bancaire un
> tableau de bord unique qui liste ses autorisations et lui permet de les révoquer. C'est une brique
> nouvelle, et sa difficulté n'est pas l'écran : c'est que nous devons afficher une information que
> **nous ne détenons pas** — elle viendra des tiers eux-mêmes.

**Si on te demande « on publie déjà nos statistiques, non ? »** → Oui, depuis 2019. Le delta n'est pas la
publication, c'est la **définition imposée** des indicateurs et la comparaison obligatoire avec nos
interfaces client. Aujourd'hui chacun mesure à sa façon ; demain les chiffres sont comparables d'une
banque à l'autre.

**Si on te demande « le tableau de bord, c'est juste un écran ? »** → Non, et c'est le piège. L'écran est
la partie visible. Derrière, il faut un référentiel d'autorisations alimenté par les tiers et
resynchronisé dans les deux sens, avec un rétablissement d'accès sous 48 heures et deux ans
d'historique. Ce protocole d'échange n'existe dans aucun standard d'API aujourd'hui.

## Slide 17 — Le de-risking encadré

> Un bloc dont on parle moins, et sur lequel **nous sommes du côté de celui qui doit justifier**.
>
> Un établissement de paiement a besoin d'un compte dans une banque pour exercer. La DSP2 était muette
> sur le sujet, et le problème est apparu après coup : des refus et des clôtures sans justification, qui
> coupent ces acteurs du système dont dépend leur activité.
>
> Le PSR encadre trois choses. L'**accès aux systèmes de paiement**, qui devient possible sur critères
> objectifs, sans discrimination fondée sur le statut — donc plus de concurrence sur les rails.
> L'**obtention et le maintien d'un compte** : un refus n'est plus possible que pour quatre motifs
> limitatifs, il doit être motivé de façon spécifique, notifié au demandeur et à l'autorité sous un mois,
> une clôture demande quatre mois de préavis, et il y a un droit de recours. Et la **transparence des
> conditions tarifaires** des schemes cartes.
>
> Pour nous, concrètement : une décision aujourd'hui discrétionnaire devient une décision **opposable**.
> Il faut un processus outillé — motifs normés, horloges, traçabilité de l'instruction, notification à
> deux destinataires, et un format harmonisé qui viendra par norme technique.

**Si on te demande « ça concerne le refus de compte à un particulier ? »** → Non, absolument pas. Cet
article porte sur les comptes ouverts **aux établissements de paiement**. Le refus d'entrée en relation
avec un client final reste régi par d'autres règles.

## Slide 18 — Neuf parcours pour rendre tout ça concret

> Plutôt qu'un catalogue d'articles, voilà neuf situations réelles, et ce que le texte y change. Je n'en
> commente que trois, vous lirez les autres.
>
> **Parcours 1**, un client vire 2 000 euros à quelqu'un qu'il n'a jamais payé : vérification du nom,
> plafond que le client a lui-même fixé, authentification liée au montant et au bénéficiaire,
> surveillance avant exécution, et crédit au plus tard le jour ouvrable suivant. Cinq exigences dans un
> seul geste banal.
>
> **Parcours 5**, un virement frauduleux arrive chez nous : c'est le plus nouveau. Aujourd'hui, une
> banque qui reçoit un virement le crédite. Demain, elle doit surveiller **avant** de mettre les fonds à
> disposition, et si le soupçon est incontestable, elle doit ne pas créditer et retourner les fonds. Ce
> volet n'existe nulle part dans nos systèmes.
>
> **Parcours 6**, une fintech appelle notre interface à trois heures du matin puis publie que nous sommes
> indisponibles : le texte définit précisément ce qu'est une indisponibilité — cinq requêtes en échec ou
> sans réponse sous trente secondes —, impose une fenêtre de maintenance entre minuit et six heures
> annoncée un mois avant, et la publication trimestrielle des statistiques.
>
> Et la note du bas est importante : l'essentiel des exigences de parcours est déjà dans le règlement.
> Ce sont les détails techniques qui viendront plus tard, par les normes de l'EBA.

**Si on te demande « d'où viennent ces chiffres, cinq requêtes, trente secondes ? »** → Des orientations
européennes déjà en vigueur, pas du PSR lui-même. Le règlement, lui, impose la mesure et la parité ; les
seuils viendront des normes techniques.

---

# Partie 3 — Premières projections d'impact IT (≈5 min)

## Slide 19 — Carton : premières projections des impacts IT

> On passe à la lecture système d'information. Trois avertissements avant : c'est une première analyse,
> elle est faite depuis le texte et pas depuis votre existant, et c'est précisément pour ça que je viens
> vous chercher.

## Slide 20 — La matrice d'impacts

> Voilà notre grille de lecture du SI, en six domaines, et notre première cotation.
>
> Le point de méthode qui explique tout : **on ne cote pas l'état d'arrivée réglementaire, on cote
> l'écart**. Une exigence du PSR qui reconduit ce que le droit nous impose déjà ne compte pas. Et ce
> « déjà », c'est six textes : la DSP2, les normes techniques de 2018, le règlement virements instantanés,
> le RGPD, DORA et le règlement SEPA.
>
> Trois niveaux. **Impact fort**, en rose foncé : soit la fonction n'existe nulle part chez nous, soit
> elle existe mais passe d'une obligation de moyens à une obligation de résultat mesurée, publiée ou
> sanctionnée. **Impact modéré** : un changement réel, mais absorbé par une brique existante. **Impact
> faible** : reconduction, ou effet de second ordre.
>
> Le résultat, et c'est le message de la slide : **dix briques en refonte, dix-huit en adaptation, et
> quarante-cinq hors périmètre**. Les impacts se concentrent sur les applications métiers.
> L'infrastructure et la gouvernance de la donnée sont peu touchées — non pas parce que le texte les
> ignore, mais parce que leurs exigences sont déjà portées par le RGPD, DORA et les normes de 2018.
>
> Une précision pour éviter un contresens : **cette cotation dit la nature du changement, pas la charge
> de travail**. Une brique cotée modérée peut porter un chantier lourd si l'adaptation est large. Le cas
> typique, c'est l'API, et j'y viens tout de suite.
>
> Le détail brique par brique est en annexe, avec la justification de chaque cotation.

**Si on te demande « pourquoi telle brique et pas celle-là ? »** → La justification est en annexe, brique
par brique, avec l'article qui la porte. Et le test qu'on s'est imposé : est rétrogradée toute
justification qui serait vraie de n'importe quelle réglementation — « il y aura de nouveaux champs »,
« les flux évoluent ». Ce sont des conséquences, pas des impacts attribuables au texte.

**Si on te demande « c'est valable pour toutes les entités ? »** → Non, et c'est une limite assumée. Le
PSR raisonne par **rôle** : banque teneuse de compte, banque du payeur, banque du bénéficiaire,
prestataire tiers. Une entité n'est concernée qu'au titre des rôles qu'elle exerce.

## Slide 21 — Focus API : la bascule ne se limite pas à l'API

> Je m'arrête sur l'open banking, parce que c'est le poste le plus lourd du paquet et le plus mal
> compris.
>
> L'interface dédiée existe depuis 2018 : le PSR **ne crée pas la brique**. Mais il change son contenu,
> son niveau de service et son régime de contrôle, sur trois fronts.
>
> **Construire** : une liste de fonctions devient obligatoire. Placer et révoquer un ordre permanent, un
> paiement à date future, des paiements vers plusieurs bénéficiaires, la vérification du nom du titulaire
> avant initiation, le choix de la méthode d'authentification présentée au payeur. Ce ne sont pas des
> paramètres, ce sont des fonctions à développer.
>
> **Prouver** : des indicateurs imposés, publiés chaque trimestre avec comparaison à nos interfaces
> client, et un objectif de rétablissement après incident qui sera fixé par norme technique.
>
> **Supprimer** : douze obstacles nommés, la liste n'étant pas fermée, avec suppression immédiate et
> sanction. Et le préavis de changement de nos spécifications techniques passe de trois à deux mois.
>
> La phrase à retenir : **la nature du changement est une adaptation, la charge est celle d'une
> refonte.**
>
> Et un point de clarification, parce qu'il y a une confusion fréquente sur ce sujet : **le PSR n'impose
> aucun standard d'API**. Il impose des propriétés — la parité, la performance publiée, le tableau de
> bord, l'absence d'obstacles. Rester sur STET est parfaitement légal. La question de la bascule vers le
> Berlin Group se pose pour d'autres raisons : l'écosystème, le coût de spécification, l'harmonisation.

**Si on te demande « c'est quoi STET, c'est quoi Berlin Group ? »** → STET est le standard d'API français,
publié par une société de place ; sa dernière version date d'octobre 2022 et il est utilisé
essentiellement en France et en Belgique. Le Berlin Group est un organisme de normalisation européen,
dont le cadre est revendiqué par plus de 75 % des banques européennes, encore activement maintenu, et qui
a déjà réalisé une analyse d'écart par rapport au PSR.

**Si on te demande « le régulateur va bien finir par imposer un standard ? »** → Le texte renvoie à des
normes émises par les organismes européens ou internationaux type CEN ou ISO, « ou équivalent ». Il ne
désigne personne. En revanche le standard de fait se décide ailleurs, dans les schemes de place — et là,
la gravitation est du côté du Berlin Group.

## Slide 22 — Quand basculer, et comment coexister

> Puisque la cible se dessine, la vraie question n'est plus « quel standard » mais **« quand et
> comment »**.
>
> Aujourd'hui : STET est notre socle historique, sa dernière version publiée date de 2022, tout notre
> écosystème de tiers est intégré dessus, et aucun impératif réglementaire n'impose à lui seul une
> bascule immédiate.
>
> La cible : un standard européen largement adopté, activement maintenu, et mieux aligné avec la suite —
> l'open finance, le futur règlement FIDA.
>
> Ce que je veux qu'on retienne, c'est pourquoi c'est difficile. **Ce n'est pas un remplacement d'API,
> c'est une réintégration avec chaque tiers connecté.** Le coût est externe et subi : il dépend du
> calendrier de nos partenaires, pas du nôtre. Il faut faire tourner les deux standards en parallèle
> pendant la transition. Et le modèle de consentement diffère, ce qui embarque le serveur
> d'autorisation, les codes d'erreur et les parcours de redirection.
>
> Alors quatre questions, et je n'attends pas de réponse aujourd'hui. **Quand** basculer, quel événement
> déclenche. **Quoi** migrer, jusqu'où va le périmètre. **Comment coexister** pendant la transition. Et
> surtout : **quelles décisions peut-on prendre dès maintenant, indépendamment de la date ?** Parce
> qu'il y en a — le référentiel de consentements, l'inventaire de nos tiers, les exigences d'API — et
> elles sont utiles quelle que soit la trajectoire.
>
> La recommandation : ne pas choisir une date aujourd'hui, mais sécuriser les conditions qui permettront
> de la déclencher au bon moment.

**Si on te demande « la bascule règle-t-elle nos problèmes de qualité d'API ? »** → Non, et il faut être
honnête là-dessus. Une étude commandée par quatre acteurs français en 2024 mesurait un taux
d'acceptation des paiements initiés par des tiers de 44 %, et pointait un usage hétérogène des codes de
statut. Le problème documenté est l'implémentation, pas la spécification. Changer de standard sans
changer la discipline ne corrige pas ça.

**Si on te demande « combien ça coûte ? »** → Aucun retour d'expérience public et chiffré n'existe sur une
migration entre standards. Ce qu'on peut borner, c'est la durée : sur un simple changement de version, le
référentiel britannique impose trois mois de préavis, deux versions en production et six mois de double
run. Pour un changement de standard, on est plutôt à douze à dix-huit mois de coexistence.

## Slide 23 — Ce qui doit être anticipé dans les chantiers en cours

> Et c'est peut-être le message le plus utile de la séance.
>
> Plusieurs capacités que le PSR va exiger sont **déjà en construction ailleurs**, dans d'autres
> chantiers réglementaires. La vérification du bénéficiaire, on la construit pour le règlement virements
> instantanés. L'authentification, elle bouge pour le portefeuille européen d'identité, avec une échéance
> fin 2027 — **avant** le PSR. La gestion des permissions, elle arrive avec FIDA. La fraude et les
> incidents, avec DORA et l'anti-blanchiment, dont l'échéance est juillet 2027. La preuve et la
> traçabilité, avec DORA, le RGPD et le règlement sur les services numériques.
>
> Autrement dit : **il n'y a pas de « chantier PSR » à ouvrir en 2027. Il y a des chantiers en cours à
> instruire dès maintenant avec le PSR dans les exigences.** Trois textes atterrissent avant lui sur les
> mêmes briques, et dans les trois cas la décision d'architecture qui déterminera le coût du PSR se
> prend dans un chantier antérieur, porté par une autre filière.
>
> D'où trois principes : aligner les roadmaps, concevoir des briques transverses plutôt que des
> implémentations en silo, et n'arbitrer comme spécifique que ce qui doit l'être.
>
> L'exemple le plus parlant : si on construit la vérification du bénéficiaire comme une fonctionnalité de
> l'écran de virement SEPA, on la refera pour le PSR. Si on la construit comme un service de vérification
> paramétrable par devise et par canal, avec une sortie de décision, on ne la refait pas.

**Si on te demande « le tableau de bord PSR et celui de FIDA, c'est le même ? »** → Fonctionnellement oui,
juridiquement non : périmètres de données différents et régimes tarifaires opposés — accès gratuit sous
le PSR, accès compensé sous FIDA. Le législateur ne les a pas réconciliés. Si on les livre séparément, le
client aura deux écrans de consentement dans la même banque en ligne.

## Slide 24 — Les cinq enjeux

> Ce qui rend l'exercice difficile, en cinq points.
>
> **Une fenêtre courte** : vingt et un mois pour l'essentiel, vingt-sept pour la vérification du
> bénéficiaire et la fin du régime transitoire des agréments.
>
> **Une dépendance aux normes techniques** : une partie du cadrage sera figée jusqu'à douze mois après
> l'entrée en vigueur, donc plus tard que le reste.
>
> **Une hétérogénéité de départ** : chaque entité porte un existant DSP2 différent — API, moteurs de
> fraude, dispositifs d'authentification.
>
> **Une articulation à sécuriser** : quatre autres textes se recoupent avec le PSR ; traités en silo, on
> obtient soit de la redondance, soit un trou de couverture.
>
> **Et un calendrier encore incertain** : le texte n'est pas publié, et aucune date de publication n'est
> acquise à ce jour.

**Si on te demande « comment on planifie avec ça ? »** → En raisonnant en délais relatifs, et en
séquençant par ce qui ne dépend pas des normes techniques. L'accessibilité de l'authentification, le
tableau de bord, la surveillance côté bénéficiaire : c'est dans le règlement, c'est stable, on peut le
travailler. Les exemptions d'authentification et les seuils d'interface : on attend.

## Slide 25 — Le résumé

> En synthèse, les domaines qui portent l'essentiel des impacts, et pour chacun notre première intuition
> de mutualisation.
>
> Deux à potentiel élevé : la vérification du bénéficiaire, où on capitalise sur l'existant, et la
> fraude, où le moteur et les échanges de place ont vocation à être partagés. L'authentification, on
> attend les normes techniques avant de figer. L'open banking est mixte : un socle mutualisable, mais un
> tableau de bord probablement par entité. L'accès aux systèmes de paiement, c'est de l'outillage de
> workflow. La monétique reste à instruire avec les spécialistes. Et le standard d'API : les prérequis se
> mutualisent, la bascule elle-même restera par entité.

## Slide 26 — Les étapes suivantes

> Et donc, concrètement, la suite — dans cet ordre, parce que l'ordre a un sens.
>
> **Un, l'étude de l'existant DSP2.** C'est le prochain incrément de valeur, et c'est ce que je viens
> chercher aujourd'hui. Quels travaux ont été menés, ce qui est déjà mutualisé, où sont les points de
> douleur. Tant qu'on n'a pas mesuré ce delta, notre matrice repose sur un existant supposé.
>
> **Deux, l'identification des initiatives en cours** dans le Groupe et chez vous, et la confirmation des
> entités volontaires pour co-construire. Un point d'attention : les chantiers qui recoupent le PSR ne
> sont pas forcément étiquetés « DSP3 ». Chez une entité, on a trouvé deux chantiers pertinents portés
> sous d'autres noms.
>
> **Trois, l'analyse des impacts sur l'architecture**, composant par composant.
>
> **Quatre, l'évaluation des capacités techniques requises**, avec les niveaux d'impact, de complexité,
> d'effort et de risque.
>
> Ce dont j'ai besoin de vous, très concrètement : un référent par entité, et une demi-journée pour un
> premier atelier bilatéral. On vient avec nos questions, vous venez avec votre existant.

**Si on te demande « qu'est-ce que vous attendez exactement de nous ? »** → Sept choses, et je peux les
lister : le standard et la version d'API que vous exposez, votre APIM et votre fournisseur d'identité,
vos taux d'échec et comment vos statistiques publiées sont alimentées, où vit votre objet consentement et
ce qu'il porte, si vous avez un composant de vérification du bénéficiaire et comment il est scopé, vos
moyens d'authentification et votre dépendance au smartphone, et tout chantier en cours qui recoupe le PSR
sans être étiqueté DSP3.

## Slide 27 — Carton : étapes suivantes

> *(Attention à l'ordre : ce carton est actuellement placé après la slide des étapes suivantes. Si tu ne
> le déplaces pas, enchaîne simplement :)* Voilà pour DSP3/PSR. Je passe la main à CATS pour PCI-DSS.

## Slides 28-29 — PCI-DSS, puis fin

> Merci. CATS, à toi.

---

# Les annexes : quoi dire si on les ouvre

Elles ne se présentent pas, elles se dégainent. Une phrase d'introduction commune :
« Le détail est en annexe, brique par brique : ce que le SI doit déjà porter, ce que le texte impose, et
ce que ça change. »

**Annexe 1, identités et accès.** Deux sujets seulement : l'authentification du client, et les accès
qu'il donne à des tiers. Tout le reste de la gestion des identités — annuaire, habilitations,
certificats, secrets — est déjà couvert par le RGPD et DORA. Le point le plus contre-intuitif :
l'authentification forte des agrégateurs passe du rythme des 180 jours imposé par la banque à une seule
authentification au premier accès, l'obligation étant transférée au tiers.

**Annexe 2, données.** Une seule vraie création : le référentiel des autorisations données aux tiers. Le
reste de la gouvernance de la donnée relève du RGPD. Le point à connaître : le PSR chiffre quatre durées
de conservation, de deux natures opposées — deux où il faut supprimer, deux où il faut conserver.

**Annexe 3, intégration.** Aucune brique nouvelle, mais le plus gros poste de charge. À retenir : cinq
nouveaux messages entre banques à router, dont deux sous contrainte de dix secondes sur les virements
instantanés — et un sixième que le texte exige sans que le dispositif de place existe.

**Annexe 4, infrastructure.** Quasi hors périmètre, une exception : la traçabilité. La charge de la
preuve ne change pas de camp — elle était déjà sur nous — elle change d'objet. L'authentification ne nous
décharge plus ; il faut prouver ce qu'on a contrôlé, suspendu et retourné. Donc journaliser des
décisions, pas seulement des transactions.

**Annexe 5, monitoring et reporting.** Deux procédures ajoutées. La plus étonnante : nous devrons
notifier aux hébergeurs les contenus frauduleux à l'origine d'une fraude — et la plateforme informée qui
n'agit pas doit nous rembourser ce que nous avons remboursé à la victime. Encore faut-il pouvoir prouver
qu'elle a été informée.

**Annexe 6, applications métiers, en trois planches.** C'est là que le texte se concentre. Premier volet,
le cœur bancaire : le plafond devient un paramètre du client, et il faut savoir suspendre un virement en
cours puis retourner des fonds déjà reçus. Deuxième volet, le middle et le back-office : le remboursement
du client manipulé, le refus d'accès devenu décision opposable, et la surveillance côté bénéficiaire qui
n'existe nulle part. Troisième volet, les canaux : la réclamation, la voix et la messagerie entrent dans
le périmètre de conformité.

---

# Trois questions difficiles, et comment y répondre

**« Vous nous présentez un texte qui n'est pas publié. On perd notre temps ? »**
> Non, l'inverse. Le texte est agréé, son contenu ne bougera plus qu'à la marge — la renumérotation des
> articles, pas les obligations. Ce qui n'est pas figé, c'est la date de départ. Et comme la mise en
> conformité prend environ vingt-quatre mois pour une fenêtre de vingt et un, attendre la publication,
> c'est démarrer en retard. Ce qu'on fait aujourd'hui — comprendre le texte, mesurer notre existant,
> aligner les chantiers en cours — ne dépend d'aucune date.

**« Combien ça coûte ? »**
> Je ne le sais pas, et je ne vais pas l'inventer. Nous savons quelles briques sont touchées et à quel
> titre : dix en refonte, dix-huit en adaptation. Le chiffrage demande deux choses que nous n'avons pas
> encore : votre existant, et les normes techniques de l'EBA. C'est exactement la raison de cette
> séance.

**« Le Groupe va-t-il imposer une solution ? »**
> Le GT ne l'impose pas, il éclaire. Et notre première conviction, c'est que la bonne maille de
> mutualisation est souvent au-dessus des composants techniques : les exigences, la gouvernance, les
> référentiels partagés. Là où les infrastructures de place diffèrent — l'Italie et la France, par
> exemple — imposer une même brique serait économiquement absurde.
