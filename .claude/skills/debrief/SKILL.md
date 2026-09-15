---
name: debrief
description: Vidage de contexte (débrief du soir) → routage dans le vault. Déclencher quand l'utilisateur tape /debrief, fait un « vidage » ou « débrief » de fin de journée, dicte ou colle un monologue de contexte en vrac (ce qu'il a en tête après des échanges, des lectures, des décisions informelles), et veut que ça peuple les bons fichiers du vault. Fonctionne que le contenu soit dicté (speech-to-text) ou tapé.
---
Vidage à traiter : $ARGUMENTS (si vide : demander à Alex de dicter ou coller son débrief).

Objectif : transformer un monologue brut en écritures propres et sourcées dans le vault, sans jamais
trahir la Règle n°1. Le vidage mélange forcément du sûr et du supposé : ton travail est de démêler.

0. FORMATS : lis `_methodes/ontologie.md` avant d'écrire quoi que ce soit. Elle donne, par type
   d'objet, le motif d'identifiant, l'emplacement, les champs obligatoires et les valeurs autorisées.
   Ne jamais écrire un identifiant de mémoire.

1. RÉGLEMENTATION CIBLE : lis la ligne « Réglementation active » de CLAUDE.md. Tout est routé vers le
   dossier de cette réglementation (sauf si Alex nomme explicitement une autre réglementation).
   Le préfixe d'identifiants est celui de cette réglementation (`DSP3-`, `AMLR-`…) : `REG-` est une
   notation de substitution, jamais une valeur à écrire.

2. DÉCOUPAGE + CLASSIFICATION : segmente le vidage en éléments discrets. Pour chacun, qualifie :
   - FAIT (vérifiable / attribué à une source) -> faits.md, format F<X>.<Y>.
   - HYPOTHÈSE (supposition, zone floue, à confirmer) -> hypotheses.md, statut 🟡 OUVERTE,
     ID <PRÉFIXE>-HNN, avec dépendances pressenties **nommées par identifiant**.
   - OPINION / position (« telle entité estime », « le GT penche pour ») -> à attribuer explicitement,
     jamais présentée comme un fait.
   - EXIGENCE naissante -> le fichier de domaine de `exigences/` si le référentiel est éclaté,
     sinon `exigences.md` (<PRÉFIXE>-EX-NNN, statut « déclinée »). Si elle prétend citer le
     texte, NE PAS inventer l'article : marquer « à localiser via /loi ».
   - DÉCISION / conclusion -> conclusions.md (graduée : Écarté / Acquis / À acter / À étudier / Hors périmètre).
   - ACTION (quelque chose à faire) -> base Notion « Actions GT » (Réglementation = active, Statut = À faire,
     Porteur, Échéance si mentionnée, Séance source = « Débrief du <date> »).
   - ARCHITECTURE (brique, cinématique décrite) -> cartographie/ (Mermaid), en liant aux exigences.

3. SOURCE : chaque élément écrit est tagué [SRC: débrief verbal du <date du jour>]. Un débrief n'est
   PAS une source primaire : les faits qui en sortent restent à consolider (croiser avec le texte via /loi,
   ou un atelier). Marque [SRC: à sourcer ⚠️] tout ce qui affirme sans base.

4. CHAÎNE DE TRAÇABILITÉ : respecte les renvois amont/aval. Une nouvelle hypothèse liste ses dépendances ;
   une conclusion cite ses faits/hypothèses. Si un élément impacte un maillon existant, signale-le.

5. DIFF AVANT ÉCRITURE : présente, fichier par fichier, ce que tu proposes d'ajouter/modifier, + la liste
   des actions Notion à créer. Alex valide. Aucune écriture avant validation (règle des deux surfaces).

6. APRÈS VALIDATION : écris dans les fichiers, crée les actions Notion, et ajoute UNE entrée de synthèse
   dans journal.md (AAAA-MM-JJ — [INIT/HYP/EX] — débrief : <résumé en une ligne>).

7. CLÔTURE : liste (a) ce qui reste [SRC: à sourcer ⚠️], (b) les hypothèses ouvertes créées à instruire,
   (c) les points où un /loi ou un atelier est nécessaire pour consolider. Sois sélectif, pas exhaustif.
