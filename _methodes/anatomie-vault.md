# Anatomie du vault

> Descriptif de la structure. Ce fichier ne prescrit rien : les règles sont dans `CLAUDE.md`,
> les chemins d'accès dans `_ROUTAGE.md`.

```
vault-casa/
├── CLAUDE.md                        ← les règles. Seule autorité.
├── _ROUTAGE.md                      ← table de pointeurs : besoin → fichier
├── CHANGE.md                        ← incohérences relevées, à valider (lecture humaine)
├── NOUVEAUTES.md                    ← ce qui a changé dans le harnais (lecture humaine)
├── annuaire.md                      ← personnes & entités du Groupe
├── _methodes/                       ← méthodes détaillées appelées par les règles
├── _transverse/                     ← registres transverses à toutes les réglementations
│   └── stack-groupe.md              ← IDP et APIM du Groupe et des entités
├── _skills/                         ← documents de méthode (PAS des skills invocables)
│   ├── analyse-reglementaire/       ← LA méthode GT (3 phases, arbres)
│   ├── redaction-gt/                ← style de rédaction des livrables
│   └── compte-rendu-gt/             ← rédaction des CR d'ateliers
├── .claude/skills/                  ← les 8 commandes invocables
├── reglementations/<reg>/
│   ├── _LISEZMOI.md                 ← état du dossier et niveau de traitement courant
│   ├── sources.md                   ← registre des sources versionnées
│   ├── exigences.md                 ← référentiel d'exigences (REG-EX-NNN)
│   ├── faits.md                     ← les FAITS établis (Fn.m)
│   ├── hypotheses.md                ← registre d'hypothèses (REG-Hnn)
│   ├── conclusions.md               ← conclusions graduées (Cn.m)
│   ├── arbres.md                    ← peuplement des arbres de décision
│   ├── cartographie/                ← carto applicative, vues, glossaire, cinématiques (Mermaid)
│   ├── contributions-entites/       ← études reçues des entités, reproduites à l'identique
│   │                                  (réf. REG-ET-NN) ; elles engagent l'entité, pas le GT
│   └── journal.md                   ← log chronologique + rétroplanning
└── gt-seances/<reg>/                ← comptes rendus des GT et ateliers
```

Deux natures de fichiers, à ne pas confondre :

- **fichiers de règles** — `CLAUDE.md`, `_methodes/`, `_skills/`, `.claude/skills/`. Ils disent
  comment travailler.
- **fichiers de contenu** — exigences, faits, hypothèses, cartographie, journal, CR. Ils disent
  ce qu'on sait.

Écarts connus par rapport à cette structure : voir `CHANGE.md` A.9.

## Nouvelle réglementation

Créer le dossier selon la structure décrite dans `_methodes/anatomie-vault.md` — **y compris
son `_LISEZMOI.md`**, qui déclare le niveau de traitement — puis dérouler le skill
`analyse-reglementaire` depuis la Phase 0. Préfixe d'IDs propre (CRA-, DSP3-, FIDA-…).
