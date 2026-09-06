---
name: loi
description: Question juridique sourcée sur un texte réglementaire (PageIndex, ou lecture directe du PDF ; citations §exactes). Déclencher quand l'utilisateur tape /loi ou pose toute question sur ce que dit le texte nécessitant une réponse sourcée. Porte par défaut sur la réglementation active du vault ; un argument peut cibler une autre réglementation.
---
Question juridique : $ARGUMENTS

1. Identifie le(s) texte(s) concerné(s) dans le registre sources.md de la réglementation.
2. Interroge PageIndex pour localiser les sections pertinentes (navigation par l'arbre, pas de supposition).
   Si le texte n'y est pas indexé (crédits épuisés, cf. MODE-EMPLOI §4), lis directement le PDF déposé dans
   le dossier de la réglementation et cite [SRC: <doc> §Art. X].
3. Cite chaque passage au format [SRC: document version §section]. Si tu ne peux pas localiser la section exacte : dis-le, ne l'invente JAMAIS.
4. Croise avec hypotheses.md : la réponse confirme, infirme ou crée-t-elle une hypothèse ? Propose la mise à jour (sans l'écrire avant validation).
5. Distingue explicitement : ce que dit le texte / ce qui reste à interpréter / ce que le GT a décidé.
