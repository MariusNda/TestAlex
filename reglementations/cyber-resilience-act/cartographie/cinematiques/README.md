# Cinématiques — CRA

> Maillon 3 de la chaîne. Un fichier .md par cinématique, diagramme de séquence Mermaid
> (sequenceDiagram), en-tête YAML : exigences couvertes (CRA-EX-NNN), rôles, source [SRC].
> Nommage : cin-NN-<nom-court>.md. Exemple type ci-dessous.

Exemple de squelette :

```markdown
---
cinematique: cin-01-notification-vulnerabilite-exploitee
exigences: [CRA-EX-0XX, CRA-EX-0YY]
roles: [Fabricant, ENISA, CSIRT national]
source: "[SRC: Règlement (UE) 2024/2847 §à localiser]"
---
​```mermaid
sequenceDiagram
  participant F as Fabricant (Groupe)
  participant C as CSIRT national
  participant E as ENISA
  F->>C: Alerte précoce (délai à confirmer via /loi)
  F->>E: Notification (plateforme unique)
​```
```
