---
name: compte-rendu-gt
description: Rédaction des comptes rendus d'ateliers et de GT à partir des enregistrements AI meeting notes Notion ou d'un transcript brut. Format court imposé, traçabilité renvoyée au vault.
---

# Skill : Compte rendu GT/atelier

## Entrée
Un enregistrement AI meeting notes Notion (via le MCP Notion), ou un transcript brut fourni par
l'utilisateur.

## Avant de rédiger (élicitation, si l'information manque)
- ANNUAIRE : consulter annuaire.md (racine du vault) pour l'orthographe exacte des noms, les
  rattachements aux entités et le contexte des interlocuteurs. Personne ou entité absente ou
  incomplète → proposer l'ajout ou la mise à jour (avec validation).
- Type de séance : GT plénier, atelier entité, synchro de pilotage ? Quelle réglementation ?
- Interlocuteurs : entités représentées, rôles (référent, architecte, métier).
- Positions sensibles : vérifier l'attribution exacte (qui a dit quoi) avant d'écrire.
- Demander ce qui a déjà été traité depuis la séance, pour ne pas créer d'action déjà faite.

## FORMAT DU CR (arbitrage Alex du 2026-08-24, non négociable)

Le CR est **court**. Il tient en une page. Un CR de 200 lignes est un CR raté.

Structure, dans cet ordre et sans rien y ajouter :

1. Titre `JJ/MM - <objet> (CR)`, puis deux lignes de contexte : date, type de séance, objet.
2. **Participants** : liste à puces, ordre alphabétique, entité et rôle entre parenthèses.
   Alexandre Linck toujours en dernier, cité une seule fois.
3. **Points clés discutés** : **cinq blocs thématiques maximum**. Si la séance déborde, un bloc
   égale une catégorie logique. Chaque bloc ouvre sur un titre court et factuel, suivi de
   sous-points indentés d'une à trois lignes.
4. **Décisions prises**.
5. **Actions et prochaines étapes** : liste libre, `- <Porteur> : <action>. Échéance : JJ/MM ou N/A`.

## Règles de rédaction
- Lire `_skills/redaction-gt/SKILL.md` (fichier, pas skill invocable) : pas de tiret long, pas de « il faut », pas de « nous » ni de « je ».
- **Pas de tableau**, sauf demande explicite de l'utilisateur.
- **Pas d'emoji** dans le corps du CR.
- Pas de chiffre qui n'est pas un sujet primaire de discussion.
- Information absente : « N/A ». Ne pas meubler.
- FIDÉLITÉ AUX POSITIONS : ne jamais durcir ni adoucir une position prise en séance.
  « CAPS considère » n'est pas « le GT a acté ». En cas de doute, marquer [attribution à confirmer].
- Ne jamais présenter comme un constat de séance ce qui est une déduction. Une déduction se rédige
  au conditionnel, sur le modèle « en creusant un peu, il semblerait que… et donc que… », et se
  termine par ce qui reste à confirmer.
- Renvois d'articles **inline entre parenthèses** (« Art. 43(2)(c) ») partout où le texte tranche un
  point soulevé en séance. Pas de balise `[SRC: …]` dans le CR.

## Ce qui NE VA PAS dans le CR
Les faits sourcés, les hypothèses, les graduations (Écarté / Acquis / À acter / À étudier / Hors
périmètre), les balises `[SRC: …]` et la liste des points à sourcer **ne figurent pas dans le CR**.
Ils vont dans le vault : `faits.md`, `hypotheses.md`, `conclusions.md`, `journal.md`. La Règle n°1
reste tenue, mais hors du CR, qui est un document de diffusion.

L'en-tête « Bonjour à tous » et la phrase de clôture appartiennent au skill `/mail`, jamais au CR.

## Sortie (double)
1. **Page Notion**, dans la page de la réglementation sous « 🖊️ Comptes rendus ». Si une page de
   séance existe déjà (préparation, questions préparatoires, transcript), enrichir cette page plutôt
   que d'en créer une seconde.
2. **Vault** : fichier dans `gt-seances/<reg>/`, puis extraction vers le vault (hypothèses, faits,
   conclusions, journal).

TOUJOURS présenter le CR, le diff vault et la liste d'actions à l'utilisateur AVANT d'écrire.
