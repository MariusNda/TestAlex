---
name: exigence
description: Décliner un texte réglementaire en exigences fonctionnelles (<PRÉFIXE>-EX-NNN) — un article ou un domaine en lecture directe, ou le texte entier en passe complète répartie entre sous-agents. Déclencher quand l'utilisateur tape /exigence, demande de décliner une portion du texte en exigences, de lancer la passe d'exigences sur une réglementation, ou d'alimenter le référentiel exigences (Phase 1).
---
Portion à décliner : $ARGUMENTS

## 0. Avant tout

Lis la ligne « Réglementation active » de `CLAUDE.md` — elle donne le préfixe d'identifiants et le
dossier cible. Puis `_methodes/ontologie.md` § Exigence — colonnes du référentiel et valeurs de statut.
**Le format du référentiel fait foi, jamais ta mémoire du format.**

### Si $ARGUMENTS nomme déjà la réglementation et le périmètre

Pars directement. `/exigence dsp3 Art. 50` ne pose aucune question.

### Sinon, deux questions, dans cet ordre, en attendant la réponse à chaque fois

**1. Quelle réglementation ?** Afficher la table de `CLAUDE.md` telle quelle — c'est le registre
unique, ne jamais recopier une liste ici — en marquant l'active. **Attendre.**

```
Quelle réglementation ?

  <un dossier par ligne, avec son niveau de traitement ; « (active) » sur l'active>
```

**2. Quel périmètre ?** Une fois la réglementation connue, ouvrir son `_LISEZMOI.md` et son
référentiel pour dire **où on en est** — c'est ce qui rend la question utile — puis proposer :

```
<REG> — <N> exigences déjà déclinées, Art. <X> à <Y> couverts.
        <ou : référentiel vide, gabarit seul.>

Quel périmètre ?

  tout le texte          passe complète, <N> agents  (≈ <N> × 50 Ko)
  un domaine             <liste des domaines existants, s'il y en a>
  un ou plusieurs articles
```

**Attendre.** Ne rien lire d'autre avant la réponse.

### Le mode découle du périmètre

| Périmètre choisi | Mode | Délégation |
|---|---|---|
| un article, quelques articles, un domaine | **portion** | non — lecture directe (Règle n°7, cas 1) |
| tout le texte | **passe complète** | oui — §2 |

Une portion ne lance jamais de sous-agents : le texte à lire est petit, déléguer coûterait plus
que de lire. En mode portion, saute au §3.

---

## 1. Passe complète — la carte du texte

**Toujours en premier, avant toute extraction.** On ne peut pas répartir ce qu'on n'a pas mesuré.

Extraire le texte du PDF et localiser les articles :

```sh
pdftotext -layout "<le PDF>" /tmp/texte.txt
grep -nE "^\s*Article\s+[0-9]+[a-z]?\s*$" /tmp/texte.txt
```

Produire une **carte** : une ligne par article — numéro, titre, position, domaine pressenti.

⚠️ **Les articles à suffixe lettre sont des articles à part entière** (`31a`, `83b`, `110c`…).
Le PSR en compte 14. Un découpage qui raisonne en entiers les perd ou les duplique.

⚠️ **Les considérants ne produisent pas d'exigences.** Sur le PSR ils pèsent 270 des 639 Ko :
les inclure double le travail pour rien. Les exigences viennent du dispositif, pas du préambule.

**Les domaines fonctionnels sortent d'ici.** Ils ne sont pas donnés d'avance et leur nombre n'a
rien de fixe : DSP3 en compte 22 parce que son texte s'est découpé ainsi. Regroupe les articles
par objet fonctionnel — pas par chapitre du texte, un domaine peut piocher dans plusieurs
chapitres — **propose la liste et attends la validation** avant d'extraire. C'est une décision,
elle se trace.

---

## 2. Passe complète — répartir, puis extraire

### Le calcul de répartition

Un article n'est **jamais** coupé en deux : c'est l'unité dans laquelle la loi est écrite et
l'unité que cite le `[SRC:]`. Le kilo-octet ne sert qu'à décider combien d'articles par paquet.

1. Mesurer la taille de chaque article (début de l'article → début du suivant).
2. `N = total / 50 Ko`, arrondi, **plafonné à 10 agents**.
3. `cible = total / N` — et répartir en **plages contiguës** en visant cette part.
4. Un article plus gros que la cible part seul dans son paquet.

```python
total = sum(tailles.values()); N = min(10, max(1, round(total / (50*1024)))); cible = total / N
# ouvrir un nouveau paquet quand ajouter l'article éloigne de la cible plus que s'arrêter là
```

Viser l'équilibre, pas le remplissage : un découpage glouton laisse le dernier agent à moitié
vide. Sur le PSR (369 Ko d'articles), l'équilibrage donne **7 agents de 51 à 56 Ko**, contre
37 à 50 Ko en glouton.

**Annoncer la répartition avant de lancer** — nombre d'agents et plage de chacun (Règle n°7).

### Ce que chaque agent reçoit

Sa plage d'articles, et rien d'autre. Son contrat, non négociable :

- **Extraction, jamais interprétation.** Ce que le texte dit, pas ce qu'il implique.
- **Un `[SRC:]` par exigence**, avec l'article exact. Jamais de retour fusionné.
- **Aucun identifiant.** L'agent rend ses exigences **ordonnées par article**, sans numéro :
  huit agents qui numérotent en parallèle produisent huit collisions. La numérotation est faite
  au §3, par toi, à la fin.
- **Le vide se dit.** Un article qui ne porte aucune obligation se signale comme tel — c'est ce
  qui rend le contrôle de couverture possible.
- **Une zone floue devient une hypothèse**, pas une exigence inventée. L'agent la signale.

---

## 3. Numéroter, ranger, indexer

1. **Numéroter** dans l'ordre du texte, en reprenant au prochain ID libre de `exigences/_index.md`.
   Les identifiants sont séquentiels sur toute la réglementation, jamais par domaine, jamais réutilisés.
2. **Ranger** chaque exigence dans son fichier de domaine, d'après la carte du §1.
3. **Mettre à jour `_index.md`**.

Si une exigence porte déjà sur le même article et dit la même chose, ne pas la dupliquer :
la signaler comme déjà déclinée.

### La ligne d'exigence

Sept colonnes, dans cet ordre :

```
| ID | Exigence | Source | Débiteur | Délai / seuil | Paramètre ouvert | Statut |
```

- **Exigence** — une phrase, un verbe d'obligation (« doit », « ne peut »). Les articles de
  définition et de champ d'application font exception : ils énoncent, ils n'obligent pas.
- **Source** — `[SRC: <texte> §Art. X]`, l'article exact. **Si tu ne peux pas localiser l'article,
  tu ne l'écris pas** : `[SRC: à sourcer ⚠️]` et tu le remontes. Jamais de référence de mémoire.
- **Débiteur** — qui porte l'obligation (PSP du payeur, PSP du bénéficiaire, EBA, colégislateur…).
- **Délai / seuil** — le chiffre du texte, ou `—`.
- **Paramètre ouvert** — ce que le texte laisse à trancher, ou `—`. C'est ce qui alimente les hypothèses.
- **Statut** — `déclinée` à la création. Cycle : déclinée → cinématisée → cartographiée → évaluée → conclue.

### L'en-tête d'un fichier de domaine

C'est ce qui permet de trouver le bon fichier sans les ouvrir tous. Trois lignes, toujours :

```markdown
# <Nom du domaine>

> Domaine <NN> du référentiel <REG>. <N> exigences, <PRÉFIXE>-EX-<début> à <PRÉFIXE>-EX-<fin>.
> Articles couverts : Art. X à Y.
> Mots-clés : <5 à 10 termes qu'on emploierait pour chercher ce sujet>
> Retour à l'index : [_index.md](_index.md)
```

Les **mots-clés** sont ce qui rend la recherche directe. Un titre de domaine dit « Open banking —
consentement et tableau de bord » ; quelqu'un cherche « révocation », « 48 heures »,
« rétablissement d'accès ». Mets les mots de la recherche, pas ceux du titre.

### `_index.md`

Une ligne par domaine : numéro · nom · nombre d'exigences · plage d'IDs · articles couverts ·
mots-clés · texte source. Plus, en tête, le **prochain ID libre**.

---

## 4. Contrôle de couverture

**Dernière étape d'une passe complète, jamais facultative.** Comparer la carte du §1 aux articles
réellement cités en `[SRC:]`, et lister les articles qui n'ont produit aucune exigence :

```sh
grep -rhoE "Art\. [0-9]+[a-z]?" exigences/ | sort -u
```

Pour chacun, dire lequel : **rien à décliner** (article de procédure, renvoi, disposition finale)
ou **non traité**. Un article non traité en silence est le seul vrai défaut d'une passe.

Puis écrire l'entrée `journal.md` : `AAAA-MM-JJ — [EX] — <N> exigences déclinées, Art. X à Y, <n> articles sans exigence`.

---

## Interdits

- **Rien de mémoire.** Jamais un numéro d'article, une valeur ou un délai qui ne vient pas du texte lu.
- **Rien n'est écrit sans validation.** Présenter le tableau, attendre, puis écrire.
- **Pas d'exigence dérivée.** « Donc il faudra un microservice » n'est pas une exigence : c'est une
  hypothèse ou un impact SI. L'exigence dit ce que le texte impose, pas ce qu'on en déduit.
