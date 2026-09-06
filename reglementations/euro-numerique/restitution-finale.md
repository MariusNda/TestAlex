# Restitution finale €N — GT10 (synthèse d'archive)

> Synthèse de référence du livrable final €N, pour comparaison de méthode et de forme avec les
> réglementations suivantes (CRA…). Source unique : [SRC: GT10 Restitution finale €N, 08/07/2026]
> (PDF archivé dans ce dossier, 76 slides). Les renvois « sl. n » pointent vers les slides du PDF.

## Plan de la restitution (structure type d'un livrable final GT)

1. Executive summary en 4 slides (sl. 1-4) : cadre de référence → méthode → état des lieux →
   enseignements → avis du GT → prochaines actions
2. Cadre fonctionnel de référence (sl. 7-12) : fondamentaux nécessaires à la lecture
3. Méthodologie et cadre d'analyse (sl. 13-18) : les 3 étapes, critères et arbres de décision
4. Cartographie cible (sl. 19-33) : carto applicative existant vs nouveau, zooms par zone, glossaire (4 sl.)
5. Impacts SI (sl. 34-42) : map d'impacts colorée, zooms, éditeurs, transfert de risques
6. Projection par typologies d'acteurs et d'entités (sl. 43-55) : vues PSP €N / CoBM,
   distributeur vs producteur, scénarios de tenue de compte
7. Principaux enseignements (sl. 56-65) : FAITS puis HYPOTHÈSES, recap section
8. Avis du GT (sl. 66-71) : CONCLUSIONS graduées + cible de mutualisation + slide d'avis
9. Prochaines étapes (sl. 72-75) : rétroplanning, actions court terme

Signatures de forme : titres = messages complets en majuscules ; slides « [Ce qu'il faut retenir] » ;
« [RECAP SECTION n] » ; encarts chapo ; annexes séparées pour ne pas alourdir (couverture
fonctionnelle complète du Rulebook hors corps principal, sl. 10).

## Les 5 faits établis (sl. 57-60, 65)

- **F1** : l'€N n'est pas un moyen de paiement de plus mais une nouvelle forme de monnaie de banque
  centrale, à gérer comme un produit à part entière (multimonnaie, shadow ledger, holding limit,
  waterfall/reverse waterfall, modèle à 6 coins, rôles PSP €N / CoBM PSP).
- **F2** : impact SI transverse et massif, ~moitié briques nouvelles / moitié adaptations, cœur de
  difficulté = tenue de compte ; ~30 % des applications touchées (ordre de grandeur CA Italia).
- **F3** : coûts dupliqués si chacun construit seul (~19 M€ CA Italia, ~182 M€ banque taille CA,
  PwC 2024 à actualiser) ; le Groupe a déjà un opérateur mutualisé de rails (CAPS).
- **F4** : la BCE impose un service uniforme aux exigences très élevées (99,85-99,95 % dispo,
  < 300 ms/transaction, ~2 s bout en bout, 16 à 40 échanges) ; les SI deviennent intégrateurs de
  composants BCE certifiés déjà attribués (app officielle, SDK, offline).
- **F5** : trois angles morts stratégiques : gouvernance Groupe inexistante, valeur recherchée non
  arbitrée (conformité vs DEaaS), capacité/charge non allouée.

## Les 6 hypothèses de travail (sl. 61-64, 65)

- **H1** : qui porte les rôles centraux (tenue de compte €N : distributeur vs producteur, arguments
  vers le producteur ; connexion DESP : CAPS candidat naturel ; make/buy/hybride à écarter
  explicitement, maturité éditeurs insuffisante).
- **H2** : quoi mutualiser et jusqu'où (mutualiser le back, laisser le front, à valider composant
  par composant ; 4 conditions nécessaires non instruites : capacité, gouvernance/refacturation,
  acceptabilité entités européennes, chiffrage).
- **H3** : architecture modulaire (pas de monolithe), socle commun Groupe décliné par pays.
- **H4** : cadre non figé à surveiller : multi-comptes (v0.91 = compte unique vs règlement UE =
  multi possible, point le plus sensible), offline, reporting BCE → concevoir avec réversibilité.
- **H5** : opportunité Digital Euro as a Service (~3000 banques en France, précédent facture
  électronique, concurrence Worldline/Nexi déjà positionnée).
- **H6** : calendrier : ~2 ans pour construire un rail (estimation CAPS), Rulebook final en 2028,
  échéance 2029 → impossible d'attendre.

## Les 7 conclusions (sl. 67-69)

- **C1** : l'€N est une nouvelle infrastructure monétaire Groupe ; la mutualisation est la voie la
  plus soutenable (orientation à confirmer par analyses d'impact approfondies).
- **C2** : préalable = gouvernance Groupe, aujourd'hui inexistante (instance métier + IT, hors GT).
- **C3** : chantier sans regret = socle commun d'exigences (niveau plancher, pas une cible).
- **C4** : trois questions à instruire : périmètre commun/spécifique, make vs buy (question de
  capacités d'abord), impacts les plus lourds (tenue de compte, moteur de transaction, gateway
  DESP, fraude/KYC, SDK/offline).
- **C5** : instruire l'opportunité DEaaS (transformer un coût de conformité en relais de croissance).
- **C6** : cible = services monétaires mutualisés de niveau Groupe opérés par une entité désignée,
  CAPS l'option la plus cohérente (sous réserve gouvernance + analyses d'impact).
- **C7** : démarrer maintenant avec des marges de réversibilité ; analyse d'impact détaillée de
  09/2026 à mi-2027 ; porter le dossier en instance Groupe (COSI, COMEX).

## Frontière des décisions (sl. 70) — exemple de sortie d'arbre graduée

Pour les briques nouvelles : niveau 0 **déconseillé** ; niveau 1 (socle commun d'exigences)
**recommandé**, minimum sans regret ; niveau 2 (build commun) **à acter**, convergence des ateliers
vers « au moins niveau 2, voire supérieur » ; au-delà : **à étudier** S2 2026 / S1 2027, toute montée
de niveau exige une justification argumentée et chiffrée.

## Prochaines étapes actées (sl. 73-75)

Trois actions dès la rentrée 2026 : porter le dossier en comité de direction Groupe (enjeux,
caractère obligatoire, urgence), mettre en place une gouvernance/programme €N Groupe (rôles des
entités, instances), initier les analyses d'impact approfondies et le chiffrage (alimenter les
budgets 2027). Rétroplanning : rulebook v1 + fin de pilote 2028, déploiement grand public 2029.

## Ce que la méthode CRA doit répliquer (leçons de forme)

Chaîne visible de bout en bout dans le livrable : fondamentaux pédagogiques → sources entités
(condition sine qua non, sl. 10) → carto existant/nouveau → map d'impacts → vues par rôle →
FAITS numérotés → HYPOTHÈSES numérotées → recap de convergence → CONCLUSIONS graduées →
avis du GT en une slide → frontière des décisions → rétroplanning → actions comités.
