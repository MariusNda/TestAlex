# Le vault CASA — mode d'emploi

Bienvenue. Ce dossier est l'outil de travail du GT Architectures Réglementaires.
Cette page explique ce que c'est et comment s'en servir. Compte dix minutes.

---

## D'abord, c'est quoi

Un **harnais**, c'est un dossier de fichiers qui apprend à Claude comment travailler
sur un sujet précis. Sans lui, Claude est un assistant généraliste. Avec lui, il connaît
nos règles, nos dossiers, notre vocabulaire, et il s'y tient.

**Comment ça marche.** Tu ouvres Claude Code à la racine de ce dossier. Il lit
automatiquement `CLAUDE.md`, qui contient les règles. Ensuite tu lui parles normalement,
ou tu tapes une commande qui commence par `/`. Il travaille dans les fichiers du dossier,
et il te montre toujours ce qu'il veut écrire **avant** de l'écrire.

Il n'y a pas de magie et pas d'interface : c'est du texte, des dossiers, et des règles
écrites en français que tu peux lire et modifier toi-même.

---

## Démarrer

1. Ouvre un terminal dans ce dossier, lance `claude`.
2. Tape `/brief` — il te donne l'état du dossier et ce qui est en cours. C'est sans risque,
   il ne fait que lire.
3. Pose-lui une question. `/loi Que dit le texte sur le tableau de bord des consentements ?`
   est un bon premier essai.

Si quelque chose n'est pas clair, demande-lui. Il a lu les règles, il peut les expliquer.

---

## Ce qu'il y a dans le dossier

```
CLAUDE.md          ← les règles. C'est le fichier qui commande tout.
_ROUTAGE.md        ← « j'ai besoin de X, il est où ? »
_methodes/         ← les méthodes détaillées, appelées par les règles
_skills/           ← comment rédiger (style, comptes rendus, méthode du GT)
.claude/skills/    ← les commandes, celles qui commencent par /
annuaire.md        ← qui est qui, dans quelle entité, on le tutoie ou pas

reglementations/   ← le contenu : un dossier par réglementation
gt-seances/        ← les comptes rendus de séance et les supports
```

Deux natures de fichiers, à ne jamais confondre : **les règles** disent comment travailler,
**le contenu** dit ce qu'on sait. Les règles ne changent pas tous les jours ; le contenu, si.

### `CLAUDE.md`, le fichier qui commande

C'est le seul fichier que Claude lit systématiquement au démarrage. Il contient sept règles
et la liste des commandes. La plus importante en tête : **rien ne s'affirme sans source**.

Il contient aussi la **réglementation active** — aujourd'hui DSP3/PSR. C'est un interrupteur :
quand tu tapes une commande sans préciser, elle s'applique à celle-là. Change cette ligne et
tout le harnais bascule sur un autre texte.

### `reglementations/`, le contenu

Un dossier par texte européen : DSP3/PSR, AMLR, NIS2, Cyber Resilience Act, euro numérique.
Chacun contient le PDF du texte officiel — 431 pages pour le PSR — plus ce qu'on en a tiré.

Commence toujours par le `_LISEZMOI.md` du dossier : il dit où on en est.

### `exigences/`, le cœur du travail

Un texte de loi de 431 pages n'est pas exploitable tel quel. On le découpe donc en
**exigences** : une obligation = une ligne, avec qui la porte, sous quel délai, et surtout
l'article exact d'où elle vient. Sur DSP3 il y en a 711, rangées dans 22 fichiers thématiques
(open banking, authentification forte, remboursement…).

C'est là que se joue l'astuce du dossier. Plutôt que de brancher un moteur de recherche sur
le PDF, on a **découpé le texte en fichiers nommés**. Claude ouvre directement le bon fichier,
comme on ouvrirait le bon chapitre d'un classeur. C'est plus simple, moins cher, et surtout
tu peux vérifier toi-même ce qu'il a lu — il te le dit.

### La chaîne

Tout ce qu'on produit descend le long d'une chaîne, et chaque étage cite celui du dessus :

```
TEXTE → EXIGENCES → CINÉMATIQUES → CARTOGRAPHIE → FAITS / HYPOTHÈSES
      → ARBRES → CONCLUSIONS → SLIDES
```

Une slide cite ses conclusions, une conclusion cite ses faits, un fait cite sa source.
Si on te demande « d'où sort ce chiffre ? », la réponse doit toujours exister.

Trois mots à distinguer, tu les verras partout :

- **fait** — sourcé et vérifié. Sans source, il n'existe pas.
- **hypothèse** — une supposition, avec un statut (🟡 ouverte, 🟢 tranchée, 🔴 obsolète,
  ⚫ bloquée par un facteur extérieur).
- **opinion** — une position, toujours attribuée à quelqu'un. « CAPS considère que… »

---

## Les commandes

Tape `/` et le nom. Aucune n'écrit sans te montrer d'abord ce qu'elle veut écrire.

| | |
|---|---|
| `/brief` | L'état du jour : tes actions ouvertes, les hypothèses qui dorment, les prochains jalons. Lecture seule. Pour commencer la journée. |
| `/loi <question>` | Une question sur ce que dit le texte. Il va chercher dans le PDF et cite l'article exact. S'il ne trouve pas, il le dit — il n'invente jamais une référence. |
| `/exigence <article>` | Découpe une partie du texte en exigences et les range au bon endroit. C'est ce qui a produit les 711 exigences DSP3. |
| `/synthese` | Tu as une sortie du vault trop longue à relire ? Il en fait une version courte, groupée par sujet, où chaque phrase garde sa source. Il ne relit pas le PDF : il résume ce qui existe déjà. |
| `/veille` | Est-ce que le texte a bougé depuis la dernière fois ? Nouvelle version, date d'application, standards publiés. Il compare à ce qu'on savait déjà et sort seulement la différence. |
| `/reunion` | Prend un enregistrement de réunion et en fait un compte rendu, plus les actions à suivre. |
| `/debrief` | Tu dictes en vrac ce que tu as en tête en fin de journée, il range chaque morceau au bon endroit en séparant ce qui est sûr de ce qui est supposé. |
| `/mail` | Transforme un compte rendu en email prêt à envoyer, débarrassé du jargon interne. Il prépare, il n'envoie pas. |
| `/lint` | Vérifie que le dossier se tient : références qui pointent dans le vide, sources manquantes, incohérences. À lancer après une grosse session d'écriture. |
| `/revue-support` | Relit un support PowerPoint contre le dossier : chaque affirmation d'une planche est-elle rattachable à une exigence ou un fait ? Il signale, il ne réécrit pas. |

---

## Les quelques règles qui comptent vraiment

**Rien sans source.** Toute affirmation porte un `[SRC: …]` qui dit d'où elle vient. Si la source
manque, on écrit `[SRC: à sourcer ⚠️]` et on le signale. **On ne comble jamais un trou** avec ce
que le modèle croit savoir. C'est la règle qui ne cède devant aucune autre.

**C'est toi qui choisis les sources.** Avant de produire une analyse, Claude te présente la liste
des documents sur lesquels il compte s'appuyer, et il attend ta réponse. Ce n'est pas une formalité :
regarde la liste, écarte ce qui n'a pas sa place.

**Rien ne s'écrit sans ton accord.** Il te montre le diff, tu valides, il écrit. Toujours.

**On ne supprime pas une hypothèse.** Elle change de statut, on garde l'historique en dessous.

---

## Les pièges à éviter

**`_skills/` n'est pas invocable.** Ce dossier contient des documents de méthode, pas des commandes.
Seul `.claude/skills/` porte les `/`. Si tu demandes à Claude de « lancer le skill redaction-gt »,
ça échoue — il faut lui dire de **lire le fichier**.

**Une hypothèse n'est pas une source.** Tu ne peux pas écrire dans un livrable une affirmation qui
repose sur une hypothèse encore 🟡 ouverte, même si elle te paraît évidente. Si tu la cites, tu
cites la réserve avec.

**Un document sous réserve ne se cite pas.** Si l'en-tête d'un fichier dit « intuitions » ou
« non stabilisé », son contenu n'est pas citable en source. Lis les en-têtes.

**Relire, c'est rouvrir l'original.** Ne demande jamais à Claude de corriger un texte à partir de
la version qu'il vient de produire. On repart toujours du fichier source, sinon les erreurs se
recopient de version en version.

**Les deux euro numérique sont deux sujets différents.** `euro-numerique` et
`euro-numerique-wholesale` n'ont que le nom en commun. Ne jamais les mélanger.

**Vérifie la réglementation active** avant de lancer une commande. Si tu travailles sur AMLR alors
que l'interrupteur est sur DSP3, tu écriras au mauvais endroit.

---

## Pour aller plus loin

Le meilleur réflexe : **demande à Claude**. Il a lu les règles, il peut t'expliquer pourquoi
elles existent et te montrer où trouver quoi.

Si tu préfères lire :

- `_ROUTAGE.md` — la table « j'ai besoin de X, il est où ? »
- `_methodes/glossaire-vault.md` — le sens exact des mots qu'on emploie
- `_methodes/pourquoi-ces-regles.md` — chaque règle vient d'un problème réel, il est raconté ici
- `_skills/analyse-reglementaire/SKILL.md` — la méthode complète du GT, en trois phases
- `_methodes/ontologie.md` — le format de chaque objet, si tu veux modifier le harnais

Et si une règle te gêne ou te paraît fausse : elle est écrite en français dans un fichier texte,
elle se discute et elle se change. C'est fait pour.
