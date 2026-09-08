# Sélection des sources

> Méthode appelée par la **Règle n°6** de `CLAUDE.md`. La règle fait autorité ; ce fichier
> ne fait que la détailler.

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
