# FAITS établis — Euro numérique wholesale

> Un fait cite sa source. Ce qui n'est pas sourcé est une hypothèse (voir hypotheses.md).

## F1 — Nature du dispositif
- **F1.1** L'euro numérique de gros n'est pas une réglementation : offre de service optionnelle de
  la BCE, construite à la demande de l'écosystème bancaire, sans obligation de l'utiliser ni de
  l'accepter. [SRC: ENW-S02]
- **F1.2** PONTES véhicule de la monnaie scripturale de banque centrale, de même valeur juridique
  que les balances TARGET2 et TIPS. C'est un module supplémentaire de l'écosystème TARGET.
  [SRC: ENW-S02]
- **F1.3** L'accès est réservé aux acteurs éligibles à TARGET2. Dans le Groupe : CACIB, CACEIS et
  CASA. [SRC: ENW-S02]
- **F1.4** Le sujet est disjoint de l'euro numérique retail. Lecture donnée par CACIB, et déjà
  donnée côté retail par CA Italia et CAPS. [SRC: ENW-S02 ; GT10]

## F2 — Mécanisme
- **F2.1** Usage principal : règlement livraison de titres tokenisés, y compris hébergés sur des
  plateformes non affiliées à la banque centrale, là où TARGET2-Securities suppose des titres
  référencés chez lui. [SRC: ENW-S02]
- **F2.2** Le protocole H-Link décorrèle le cash du titre tout en synchronisant la sécurité de la
  livraison : le vendeur pré-livre l'actif dans un coffre fort numérique, l'acheteur paie via PONTES
  et reçoit le code d'ouverture. Règlement en monnaie de banque centrale sans acteur central.
  [SRC: ENW-S02]
- **F2.3** Conséquence sur l'écosystème : une plateforme de titres ou un CSD n'a plus à gérer le
  cash, seulement la conservation et la mise à disposition du coffre. [SRC: ENW-S02]

## F3 — Calendrier BCE
- **F3.1** Initial Release, fin septembre 2026 : mise en production, onboarding (connexion
  utilisateurs, API), exploitation par interfaces graphiques uniquement, pas d'intégration technique
  avant 2027. [SRC: ENW-S02]
- **F3.2** Announced Product, milieu 2027, date non arrêtée : mise en conformité avec la directive
  Finalité, dont PONTES sort dans sa version de septembre 2026, et ouverture 22h sur 24.
  [SRC: ENW-S02]
- **F3.3** 2028 : fonctionnalités non encore listées, ouverture 24h sur 24 et 7 jours sur 7.
  [SRC: ENW-S02]

## F4 — Positions d'acteurs
- **F4.1** Euroclear a décidé de tokeniser le marché de l'ECP en se positionnant, en avance de
  phase, comme orchestrateur du règlement livraison dans PONTES. [SRC: ENW-S02]
- **F4.2** CACIB juge majeur d'intégrer progressivement PONTES dans ses chaînes. La connexion de
  CACEIS est en débat, avec un intérêt probable au titre du règlement livraison pour ses clients
  investisseurs ; pour les autres entités, l'intérêt est jugé moins probable. [SRC: ENW-S02]
- **F4.3** Le régime pilote, série de dérogations à CSDR, ouvre à des acteurs non CSD des fonctions
  de conservation et de règlement livraison en environnement DLT, ainsi que le cumul avec une
  plateforme de négociation, aujourd'hui exclu. [SRC: ENW-S02, à confirmer sur les textes]
