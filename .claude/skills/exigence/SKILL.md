---
name: exigence
description: Décliner un article ou domaine du texte réglementaire en exigences fonctionnelles (REG-EX). Déclencher quand l'utilisateur tape /exigence, demande de décliner une portion du texte en exigences, ou d'alimenter le référentiel exigences.md (Phase 1).
---
Portion du texte à décliner : $ARGUMENTS

0. Lis la ligne « Réglementation active » de CLAUDE.md : elle donne le préfixe d'IDs et le dossier cible.
1. Localise la portion via PageIndex si le texte y est indexé. Sinon (crédits épuisés, cf. MODE-EMPLOI §4),
   lecture directe du PDF déposé dans le dossier de la réglementation. Jamais de mémoire, jamais
   d'article inventé. Cite chaque passage [SRC: texte §article].
2. Propose les exigences au format du référentiel : ID (<PRÉFIXE>-EX-NNN séquentiel, préfixe de la
   réglementation active), énoncé (une phrase, verbe d'obligation), source exacte, domaine fonctionnel,
   rôles concernés,
   briques pressenties (si la carto existe), statut d'analyse = « déclinée ».
3. Signale toute zone floue ou paramètre ouvert → propose la création d'une hypothèse.
4. PRÉSENTE le tableau proposé avant d'écrire. Destination : si le référentiel est éclaté (dossier
   exigences/), écrire dans le fichier de domaine concerné et mettre à jour exigences/_index.md ;
   sinon dans exigences.md. Après validation, écris et logge dans journal.md.
