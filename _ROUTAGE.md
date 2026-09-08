# Routage — quel fichier pour quelle demande

> Lu **avant toute recherche de fichier**. Donne le chemin de lecture par type de demande.
> La §2 liste les cas où aucun routage ne s'applique : les reconnaître évite de forcer un chemin approchant.
> Les chemins sont relatifs à `reglementations/<réglementation active>/` et `gt-seances/<réglementation active>/`.
> La réglementation active se lit dans `CLAUDE.md`.

## 1. Cas routés — chemin obligatoire

| Demande | Lire exactement, dans cet ordre | Ne pas ouvrir | Motif |
|---|---|---|---|
| **Question sur un article**<br>« que dit l'Art. 43 ? » | `sources.md` (repérage du texte), le PDF sur la plage de pages, `exigences/<domaine>.md` | Les autres fichiers de domaine, la matrice, le journal | La réponse tient dans un article et son exigence dérivée. Le reste ne porte que des renvois. |
| **Delta DSP2 → DSP3, impact SI, thématiques** | `cartographie/matrice-impacts-si.md` (sa synthèse est en tête), puis `sources.md` §Ligne de base | `exigences/` en entier | La matrice porte déjà les deux colonnes du delta, brique par brique, avec la ligne de base sourcée. |
| **Décliner un article en exigences** (`/exigence`) | Le PDF sur la plage, `exigences/_index.md`, le fichier de domaine cible, `exigences/99-annexes.md` | Les autres domaines, la matrice | L'index donne le prochain ID libre et le domaine d'accueil. Les annexes portent les hypothèses dérivées et les options. |
| **Traiter une réunion** (`/reunion`) | Le transcript, `_skills/compte-rendu-gt/SKILL.md`, `annuaire.md` en recherche ciblée sur les noms cités, le CR précédent de la même entité, le Fait n° de cette entité dans `faits.md` | La matrice, `exigences/`, le journal complet | Un CR est fidèle à la séance, pas à l'analyse. Le CR précédent évite de rouvrir une action déjà close. |
| **État des lieux** (`/brief`) | `_LISEZMOI.md`, les 40 dernières lignes de `journal.md`, `hypotheses.md`, la base Notion « Actions GT » | Tout le reste | Le `_LISEZMOI.md` est écrit pour cet usage. |
| **Préparer ou corriger un support** | `revue-GT11-registre-consolide.md`, **puis** `propositions-GT11-correctifs-Christel-2026-09-04.md`, **puis** le `.pptx` | `_archive/`, le voiceover sauf préparation de l'oral | Le registre a absorbé les revues archivées. L'ordre est normatif : les correctifs du 04/09 corrigent le registre du 31/08. |
| **Question sur une entité**<br>« qu'a dit BFB ? » | `faits.md` au Fait n° de l'entité, le CR de cette entité, `contributions-entites/<ET-xx>` | La matrice, `exigences/` | Les faits sont indexés par entité : Fait n°2 = BForBank, n°3 = héritage DSP2, n°4 = CATS. |
| **Re-synthétiser une sortie** (`/synthese`) | La cible désignée par l'utilisateur, et elle seule. Si la cible est ambiguë : lister les candidats, demander, ne rien lire avant la réponse | Les PDF, les autres maillons | La synthèse réduit un maillon existant. Ouvrir le texte reviendrait à re-décliner : c'est `/exigence`. |
| **Veille** (`/veille`) | `sources.md` §Attendus, la dernière entrée `[REG]` de `journal.md`, puis les sources officielles en ligne | Le reste du vault | La veille cherche un delta externe. Relire le vault ne lui apprend rien. |

## 2. Cas NON routés — navigation libre assumée

Ces demandes n'ont pas de chemin fixe. Partir du `_LISEZMOI.md` de la réglementation active et naviguer.

- **Question transverse à plusieurs domaines.** Exemple : « qu'est-ce qui touche l'open banking dans tout le paquet ». Par nature, elle traverse plusieurs fichiers. Cas d'emploi des sub-agents, cf. §5.
- **Question portant sur une réglementation non active.** Le routage vaut pour la réglementation active. Pour une autre, ouvrir son `_LISEZMOI.md` d'abord, qui déclare son état et ce qui est peuplé.
- **Recherche par mot-clé ou par nom.** Une personne dans `annuaire.md`, un identifiant `DSP3-Hnn`, un terme dans les faits : une recherche ciblée suffit, aucun routage n'est utile.
- **Arbitrage éditorial.** Exemple : « retiens 3 à 5 thématiques ». Ce n'est pas une recherche de fichier. Le regroupement ne figure dans aucun document et relève d'une décision, à demander.
- **Demande exploratoire ou méthodologique.** Comprendre la structure, auditer le vault, proposer une amélioration.

## 3. Règle par défaut

Si la demande ne correspond à aucun cas de la §1, **ne pas forcer le routage le moins éloigné**. Le dire explicitement, puis naviguer depuis le `_LISEZMOI.md` de la réglementation active.

Un routage appliqué à côté coûte plus cher qu'une absence de routage : il ferme des fichiers pertinents.

## 4. Ne jamais ouvrir, quelle que soit la demande

- `gt-seances/<reg>/_archive/` : contenu périmé, absorbé par `revue-GT11-registre-consolide.md`. Trois de ses cinq fichiers ne portent aucun avertissement.
- Tout fichier dont la première ligne porte `⚠️ OBSOLÈTE` ou `⚠️ VIDE`.
- `README.md` tant que sa réglementation n'est pas alignée sur `CLAUDE.md` (cf. `CHANGE.md` §A.1).

## 5. Contrat de sub-agent

Un sub-agent se justifie quand la source dépasse **20 Ko** et que l'extrait utile fait moins de **10 %** de la source. En dessous, la lecture directe coûte moins cher.

**Délégation recommandée :** `cartographie/matrice-impacts-si.md` (64 Ko), `exigences/` (270 Ko, un sub-agent par domaine, en parallèle), `contributions-entites/DSP3-ET-04` (98 Ko), `journal.md` (43 Ko) en recherche historique, `gt-seances/<reg>/` hors archive (115 Ko).

**Lecture directe :** `annuaire.md`, `_LISEZMOI.md`, `_transverse/stack-groupe.md`, `conclusions.md`, tout fichier de moins de 20 Ko.

Cinq règles, sans exception :

1. **Une source, une question.** Jamais « lis le dossier et remonte ce que tu trouves ». Toujours « dans tel fichier, quelles briques sont cotées 2 et pour quel motif ».
2. **Extraction, jamais interprétation.** Le sub-agent rapporte ce qui est écrit. Il ne conclut pas, ne priorise pas, ne reformule pas. La synthèse appartient à l'agent principal, seul à voir l'ensemble.
3. **Retour borné à 300 mots**, avec un `[SRC: …]` par affirmation. Un retour long annule le bénéfice.
4. **Le vide se dit.** Sans résultat, répondre « non trouvé dans ce fichier ». Ne jamais combler avec une connaissance générale, qui n'est pas sourçable et que rien ne distingue du reste.
5. **Périmètre fermé.** Le sub-agent lit la source qui lui est donnée, et rien d'autre. Pas de navigation libre, pas d'`_archive/`, pas de PDF non demandé.

## 6. Sélection des sources — lister, demander, ne jamais choisir seul

Le choix des sources décide du résultat de toute analyse d'impact. Claude ne le fait donc jamais seul :
il liste, il demande, il attend.

**La liste se construit, elle ne se recopie pas.** Procédure, valable pour toute réglementation :

1. Ouvrir `reglementations/<réglementation active>/sources.md`. C'est le seul fichier à lire
   pour établir la liste. Chaque réglementation du vault en a un.
2. Regrouper les lignes du registre par famille (textes primaires, ligne de base, contributions
   d'entités, héritage, cartographie dérivée…). Les familles se lisent dans le registre,
   elles ne sont pas figées ici.
3. Reporter l'état de vérifiabilité depuis la colonne « PDF local » : ✅ déposé = vérifiable,
   ☐ = **non vérifiable**, à annoncer comme tel.
4. Proposer un défaut motivé, puis attendre.

Un registre peut être quasi vide : sur AMLR, NIS2, CRA, `sources.md` ne porte qu'une ligne réelle
(le PDF du texte) et un attendu « études des entités à recenser en Phase 0 ». La liste fait alors
deux lignes. **Ce n'est pas un échec : c'est l'information utile.** Elle dit que rien d'autre n'est
déposé, et empêche le vide d'être comblé par la culture générale du modèle.

### Quand poser la question

Dans ces trois cas, et seulement dans ces trois cas :

1. Avant toute production qui compare l'existant au texte : delta, impact SI, cotation de brique,
   « ce qui change par rapport à la DSP2 ».
2. Avant tout livrable destiné à diffusion : slide, CR, note, email.
3. Quand deux sources portent le même fait avec des valeurs différentes.

### Quand ne pas la poser

Une question factuelle sur un article, un état des lieux, une recherche de contact, une veille.
Poser la question à chaque prompt la rend inutile.

### Comment la poser

Liste numérotée, une ligne par source, avec son état de vérifiabilité et une recommandation par défaut.
Puis attendre. **Ne rien produire avant la réponse.** Une réponse du type « 1, 2 et 5 » ou
« toutes sauf la ligne de base » suffit à engager la production.

**Exemple** — DSP3 au 2026-09. Les lignes ci-dessous sont celles du `sources.md` de DSP3 à cette
date ; sur une autre réglementation, ou après mise à jour du registre, elles sont différentes.

```
Sources disponibles pour <objet de la demande>. Lesquelles retenir ?

TEXTES PRIMAIRES
 1. DSP3-REG   PSR ST-8221, compromis 04/2026        PDF déposé, vérifiable
 2. DSP3-DIR   PSD3 ST-8222, compromis 04/2026       PDF déposé, vérifiable

LIGNE DE BASE (ce qui est déjà exigé aujourd'hui)
 3. BASE-IPR   Règl. 2024/886, VoP                   PDF déposé, vérifiable
 4. BASE-RTS   RTS 2018/389, SCA et API              non déposé, non vérifiable
 5. BASE-…     (les 7 autres)                        non déposés, non vérifiables

CONTRIBUTIONS D'ENTITÉS
 6. DSP3-ET-04 Étude CAPS, 49 slides                 versée, citations au § à contrôler
 7. DSP3-ET-02/03  Études BForBank                   versées, vérifiables
 8. DSP3-ET-01 Étude CAPS 07/07                      remplacée par ET-04

HÉRITAGE DSP2
 9. DSP3-DSP2-02  Booster DSP2 de 2017               intention de 2017, jamais un réalisé
10. DSP3-DSP2-01  Archives SharePoint 2018           statut contradictoire, cf. CHANGE.md A.5

Recommandation par défaut : 1, 2, 3, 6, 7.
Réserve à annoncer si 4 ou 5 sont retenues : huit des neuf textes de ligne de base
ne sont pas dans le vault. Toute affirmation « déjà exigé sous DSP2 » qui s'y appuie
est invérifiable et doit porter [SRC: à sourcer ⚠️].
```

### La règle qui ne se négocie pas

Une source écartée par l'utilisateur n'est **pas** remplacée par une connaissance générale du modèle.
Si le retrait d'une source rend une affirmation insourçable, l'affirmation disparaît du livrable
ou passe en `[SRC: à sourcer ⚠️]`. Elle n'est jamais maintenue sans source.
