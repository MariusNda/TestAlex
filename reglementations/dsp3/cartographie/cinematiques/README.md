# Cinématiques — DSP3 / PSR

> Maillon 3 de la chaîne. Un fichier .md par cinématique, diagramme de séquence Mermaid
> (sequenceDiagram), en-tête YAML : exigences couvertes (DSP3-EX-NNN), rôles, source [SRC].
> Nommage : cin-NN-<nom-court>.md. Exemple type ci-dessous.

Exemple de squelette :

```markdown
---
cinematique: cin-01-<nom-court>
exigences: [DSP3-EX-0XX, DSP3-EX-0YY]
roles: [PSP, Client, TPP]
source: "[SRC: à localiser via /loi]"
---
​```mermaid
sequenceDiagram
  participant C as Client
  participant P as PSP (Groupe)
  participant T as TPP
  C->>P: (étape à modéliser)
​```
```
