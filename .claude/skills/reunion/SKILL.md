---
name: reunion
description: Ingérer un enregistrement de réunion (Notion AI meeting notes) → CR Notion + vault + actions Notion. Déclencher quand l'utilisateur tape /reunion, demande de traiter une réunion, un atelier ou un GT enregistré, ou d'en produire le CR et les actions.
---
Réunion à traiter : $ARGUMENTS (si vide : le plus récent enregistrement non traité)

0. RÉGLEMENTATION CIBLE : lis la ligne « Réglementation active » de CLAUDE.md. Elle détermine la
   page Notion parente, le dossier gt-seances/ et la valeur de l'attribut Réglementation.

1. Via le MCP Notion (outil meeting notes / recherche), récupère l'enregistrement.
   Si plusieurs candidats, liste-les et demande lequel.
1bis. MÉTADONNÉES : demande (ou déduis de l'enregistrement) le titre de la séance, le type
   (GT plénier / atelier), les participants et leurs entités. Une question groupée, pas un
   interrogatoire.
2. Applique le skill _skills/compte-rendu-gt/SKILL.md (fidélité aux positions, élicitation si besoin).
3. Rédige le CR en appliquant `_skills/redaction-gt/SKILL.md` (**lire le fichier** ;
   ce n'est pas un skill invocable).
4. PRÉSENTE le CR + le diff vault + la liste des actions extraites (porteur, échéance) AVANT toute écriture.
5. Après validation :
   - Page Notion CR : sous-page de la page de la réglementation active, sous « 🖊️ Comptes rendus ».
     DSP3/PSR → page « 📋 DSP3 », page_id 3bf852cc7e1580158d26cb6170da092f (consigne Alex 2026-08-17).
     ⚠️ Ne JAMAIS cibler un bloc toggle : l'API répond 200 sans rien écrire. Toujours relire la page
     après écriture pour confirmer que le contenu est bien là.
     Si une page de séance existe déjà (préparation, questions préparatoires, transcript), l'enrichir
     plutôt que d'en créer une seconde.
     Nommage : « JJ/MM - <type de séance> x <entité ou personne> (@Prénom N.) », suffixe « (CR) ».
     Date non fixée → garder le préfixe littéral JJ/MM. S'appuyer sur le template
     « JJ/MM - Template (CR) » (section Ressources utiles de la page mission).
   - Fichier dans gt-seances/<réglementation active>/ + diff vault (exigences/faits/hypotheses/conclusions/journal)
   - ACTIONS : base Notion « Actions GT », data source ea98e4b8-cace-460e-a4f7-ef9014868332.
     Propriétés : Action (titre) · Réglementation (= active) · Porteur (Alex / Autre entité) ·
     Échéance (date) · Statut = À faire · Séance source (texte) · Lien CR (URL de la page CR).
     Il n'existe pas de propriété de relation : le lien vers le CR est l'URL « Lien CR ».
     SÉLECTIVITÉ : ne proposer que les actions qui feront l'objet d'un suivi réel. Une liste courte
     vaut mieux qu'un inventaire. Marquer distinctement celles dont Alex est porteur.
   - Liste les [SRC: à sourcer ⚠️] et [attribution à confirmer] restants.
