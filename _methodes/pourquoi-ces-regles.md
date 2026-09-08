# Pourquoi ces règles existent

> Ce fichier porte les justifications, pour que `CLAUDE.md` n'ait à porter que les contraintes.
> Chaque règle du harnais a été écrite après un incident précis, tracé dans le vault.

## Règle n°1 — provenance

**Avant le harnais, Claude mélangeait les deux natures d'information.** Alexandre, en séance du
04/09/2026 : « à un moment il y a un type, il a dit un truc, il l'a considéré comme un article et
il dit, c'est une source de vérité. » Ce qui est écrit dans un article est factuellement vrai et le
reste ; une hypothèse d'atelier est vraie au jour 1 et fausse à J+7.

**Le sous-cas « document de travail ».** Au test du 04/09, `cours-dsp3-psr.md` — un support de
formation daté du 17/07 — a été cité **9 fois**, contre une seule citation d'exigence, et aucun des
22 fichiers de domaine ouvert. Le fichier portait sa propre réserve en tête (« intuitions de
cadrage, pas des conclusions du GT ») et cette réserve a été citée trois fois **sous forme de
balise `[SRC:]`** : une précaution d'auteur ressortie en source de vérité. Le `journal.md` du 17/08
notait déjà la même contamination trois semaines plus tôt. Le fichier a été supprimé le 07/09.

D'où les deux clauses : une conséquence tirée d'un article n'est pas sourçable, et un document
portant une réserve dans son en-tête ne peut pas être cité.

## Règle n°5 — relecture

Trois occurrences de la même mécanique dans le vault, toutes documentées :

- le registre consolidé du 31/08 : « cinq constats de la revue V1 ont survécu à la V2 en migrant du
  corps du support vers les annexes : le texte a été déplacé, pas relu » ;
- le constat C10 de la revue V2, « DSP3-H17 n'existe pas », était **faux** — H17 vivait dans
  `exigences/99-annexes.md`, un fichier jamais ouvert ;
- la note de propositions du 27/08 s'ouvre sur « deux corrections de cette note se sont révélées
  fausses à la vérification ».

Une seule cause : **une passe qui relit une passe précédente au lieu de relire la source.**

## Règle n°6 — sélection des sources

Demande explicite d'Alexandre : que Claude liste les bases candidates et que ce soit lui qui
choisisse. Le choix des sources décide du résultat de toute analyse d'impact.

**Le test qui l'a validée.** Sur une demande de delta DSP2 → DSP3, l'utilisateur a répondu « tout
sauf cartographie » — écartant ainsi la seule source où le delta était déjà sourcé. La clause de
clôture a tenu : la sortie a écrit « aucun texte de ligne de base n'est déposé dans le vault sur ce
thème `[SRC: à sourcer ⚠️]` » au lieu de combler avec une connaissance générale.

**Ce que ce test a révélé sur le contenu**, et qui vaut plus que le test : le delta DSP2 → DSP3
n'est pas calculable en l'état, huit des neuf textes de ligne de base n'étant pas déposés.

## Préséance des règles

Sur trois passes du même prompt, le comportement a varié : deux fois la liste des sources a été
posée, une fois la production est partie directement. Ce n'était pas un manquement mais une
**ambiguïté** — l'ancien `_ROUTAGE.md` nommait les fichiers à ouvrir pour ce type de demande, la
règle de sélection exigeait d'attendre. Deux consignes, deux réponses possibles.

D'où deux corrections : `_ROUTAGE.md` est redevenu une simple table de pointeurs qui ne prescrit
rien, et une règle de préséance dit désormais qu'une contradiction se **signale** avant de produire,
au lieu d'être tranchée en silence.

## Règle n°7 — délégation

Le vault fait environ 1 Mo de markdown : tout charger est impossible, et **tout ce qui est lu
reste** — un fichier ouvert par erreur en début de session influence tout ce qui suit.

Un sous-agent démarre avec un contexte vierge, lit ce qu'on lui donne, renvoie son extrait, et le
reste meurt avec lui. Mais il recharge `CLAUDE.md` au démarrage, ne peut pas poser de question, et
sans format de retour imposé il renvoie un pavé — le problème est alors seulement déplacé.

**Le dimensionnement a été corrigé deux fois.** D'abord « un agent par fichier », qui donnait 22
agents sur `exigences/`, soit 22 amorçages du harnais pour 270 Ko de source. Puis un critère
indécidable (« moins de 10 % d'extrait utile »), qu'on ne connaît qu'après avoir lu. La formulation
actuelle raisonne sur la largeur de la question et sur deux plafonds, tous connus avant d'ouvrir
le premier fichier.
