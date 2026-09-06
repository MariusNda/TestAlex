---
name: veille
description: Veille réglementaire sur un texte du vault. Déclencher quand l'utilisateur tape /veille, demande l'actualité d'une réglementation, le calendrier législatif, une nouvelle version du texte, la date d'entrée en vigueur ou d'application, les actes délégués / d'exécution, RTS/ITS, standards harmonisés ou guidances (EBA, ENISA, ANSSI, EDPB…). Par défaut porte sur la réglementation active ; un argument peut cibler une autre réglementation.
---
Réglementation à surveiller : $ARGUMENTS (si vide : lire la ligne « Réglementation active » de CLAUDE.md).

Objectif : détecter ce qui a CHANGÉ depuis la dernière veille, pas répéter ce qu'on sait déjà. Applique la Règle n°3.

1. BASELINE (ce qu'on sait déjà) : lis, dans le dossier de la réglementation, `sources.md` (version de référence
   en cours + section « Attendus ») et `journal.md` (dernière entrée [REG]/veille et sa date). C'est le point de
   comparaison : tu cherches les nouveautés POSTÉRIEURES à cette date.

2. RECHERCHE (sources officielles d'abord) :
   - Statut & calendrier législatif : EUR-Lex, registres du Conseil et du Parlement (Legislative Observatory / Legislative Train), Journal officiel de l'UE.
   - Textes de niveau 2 & guidances selon le domaine : EBA (paiements/AML), ENISA & ANSSI (cyber/NIS2), EDPB, actes délégués/d'exécution, RTS/ITS, standards harmonisés (CEN/CENELEC).
   - Presse spécialisée / cabinets (secondaire) uniquement pour confirmer ou dater, jamais comme source primaire.
   Cite CHAQUE information avec URL + date de publication. Ne JAMAIS inventer une référence d'article ou une date.

3. CE QUE TU CHERCHES : nouvelle version consolidée du texte ; date d'entrée en vigueur / d'application (et jalons intermédiaires) ; publication au JO ; nouveaux actes délégués/d'exécution, RTS/ITS, standards, guidances ; actualité notable (avis d'autorité, report, contentieux).

4. DELTA : distingue clairement (a) CONFIRMÉ par source officielle vs (b) ANNONCÉ / rumeur presse ; et surtout ce qui est NOUVEAU depuis la dernière veille vs déjà connu. Mets en tête les nouveautés et les alertes.

5. RÈGLE N°3 — SI nouvelle version / acte / standard / guidance trouvé :
   - recommande de l'ajouter à `sources.md` (avec nom de fichier PDF/PageIndex selon la convention) et de l'indexer / déposer ;
   - signale un diff à faire vs la version courante, et les exigences/hypothèses potentiellement impactées (chaîne remontée) ;
   - propose les actions correspondantes.

6. ÉCRITURE (diff à valider) : propose la mise à jour de `sources.md` (section « Attendus » / version), une entrée
   `journal.md` (`AAAA-MM-JJ — [REG] — veille : <synthèse>`), et si besoin des actions dans « Actions GT »
   (Réglementation = celle surveillée). PRÉSENTE le diff avant d'écrire. Aucune écriture sans validation.

7. RENDU : rapport de veille court et scannable —
   - **Calendrier à jour** (entrée en vigueur / application, prochain jalon) ;
   - **Nouveautés depuis la dernière veille** (le delta, sourcé) ;
   - **Alertes** (nouvelle version / acte → diff à faire) ;
   - **Actions recommandées**.
   Termine par une ligne « Sources : » (URLs officielles utilisées). S'il n'y a rien de neuf, dis-le en une ligne.
