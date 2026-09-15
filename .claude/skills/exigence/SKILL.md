---
name: exigence
description: Décliner un article ou domaine du texte réglementaire en exigences fonctionnelles (REG-EX). Déclencher quand l'utilisateur tape /exigence, demande de décliner une portion du texte en exigences, ou d'alimenter le référentiel exigences.md (Phase 1).
---
Portion du texte à décliner : $ARGUMENTS

0. Lis la ligne « Réglementation active » de CLAUDE.md : elle donne le préfixe d'IDs et le dossier cible.
   Puis lis `_methodes/ontologie.md` § Exigence : motif d'identifiant, colonnes du référentiel et
   valeurs de statut. Les colonnes du tableau font foi, pas ta mémoire du format.
1. Localise la portion via PageIndex si le texte y est indexé. Sinon (crédits épuisés depuis le 2026-07-17, cf. Règle n°1 de CLAUDE.md),
   lecture directe du PDF déposé dans le dossier de la réglementation. Jamais de mémoire, jamais
   d'article inventé. Cite chaque passage [SRC: texte §article].
2. Propose les exigences au format du référentiel, colonnes dans l'ordre déclaré par l'ontologie :
   `ID` (<PRÉFIXE>-EX-NNN séquentiel sur toute la réglementation, prochain libre dans
   `exigences/_index.md`) · `Exigence` (une phrase, verbe d'obligation) · `Source` ([SRC:] exact) ·
   `Débiteur` (qui porte l'obligation) · `Délai / seuil` · `Paramètre ouvert` · `Statut` = « déclinée ».
   Le domaine fonctionnel n'est pas une colonne : il est porté par le fichier de destination.
3. Signale toute zone floue ou paramètre ouvert → propose la création d'une hypothèse.
4. PRÉSENTE le tableau proposé avant d'écrire. Destination : si le référentiel est éclaté (dossier
   exigences/), écrire dans le fichier de domaine concerné et mettre à jour exigences/_index.md ;
   sinon dans exigences.md. Après validation, écris et logge dans journal.md.
