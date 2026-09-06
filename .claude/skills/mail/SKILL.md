---
name: mail
description: Transformer un CR (vault, Notion ou fourni) en email prêt à envoyer. Déclencher quand l'utilisateur tape /mail, demande de « préparer le mail du CR », d'« envoyer le CR par mail », ou de mettre en forme un compte rendu pour diffusion email.
---
CR à transformer : $ARGUMENTS (si vide : le dernier CR produit dans la session, sinon demander)

1. DESTINATAIRE : vérifier dans annuaire.md (orthographe exacte, entité, registre tu/vous).
   Si absent ou registre inconnu ⚠️ : demander, puis proposer l'ajout à annuaire.md (avec validation).
2. STYLE : fond selon _skills/redaction-gt/SKILL.md (objet = message, premier paragraphe = chapo,
   pas de tiret long, pas de « il faut ») ; registre email assoupli : « je » et « tu » admis
   selon l'annuaire, ton cordial.
3. STRUCTURE (template validé par Alex, 2026-07-09) :
   - Objet : `[CASA x <REG>] Compte-rendu : <objet de la séance>` (casse normale)
   - `Bonjour <Prénom>,`
   - Remerciement pour l'échange + une phrase de contexte positive
   - « Tu trouveras ci-dessous un compte-rendu de nos discussions. N'hésite pas à le compléter si besoin. »
   - `Points clés discutés :` puces hiérarchisées thème → détails, fidèles au CR
   - `Actions / prochaines étapes :` une puce par action au format `[Porteur] action`
   - `Bonne journée,` / `Cordialement,`
4. NETTOYAGE : retirer tout le jargon interne du vault (IDs <PRÉFIXE>-EX-NNN, <PRÉFIXE>-Hnn, Fn.m, statuts
   🟡🟢, mentions [SRC: …]) ; reformuler en langage destinataire. Les positions restent fidèles
   au CR : rien d'ajouté, rien d'adouci.
5. SORTIE : draft en chat, prêt à copier. AUCUNE écriture (ni vault, ni Notion, ni envoi).
