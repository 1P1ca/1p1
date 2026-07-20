# Assistant personnel — 1+1 Stratégie

Ce dépôt configure Claude Code comme assistant personnel de Philippe, branché sur l'ensemble des outils de travail de 1+1 Stratégie. Il suffit d'ouvrir une session Claude Code sur ce dépôt : l'assistant connaît son rôle, ses outils et ses garde-fous.

## Contenu

| Fichier | Rôle |
| --- | --- |
| `CLAUDE.md` | Mémoire permanente de l'assistant : rôle, outils, règles d'engagement, routines |
| `.claude/agents/assistant-personnel.md` | Agent généraliste multi-outils |
| `.claude/agents/triage-courriels.md` | Boîte Outlook et calendrier (Microsoft 365) |
| `.claude/agents/veille-crm.md` | Pipeline HubSpot et prospection Apollo.io |
| `.claude/agents/studio-marketing.md` | Mailchimp, Canva et Common Room |
| `.claude/settings.json` | Outils de lecture pré-approuvés (moins d'interruptions de permission) |

## Outils connectés

Microsoft 365 (Outlook, Teams, SharePoint) · HubSpot · Apollo.io · Mailchimp · Canva · Common Room · GitHub — par les connecteurs MCP de la session. Les connecteurs se gèrent dans les réglages de claude.ai (section « Connecteurs ») et doivent être autorisés dans chaque nouvel environnement.

## Exemples de demandes

- « Prépare ma journée : agenda, courriels prioritaires, rencontres à préparer. »
- « Résume mes courriels non lus et propose des projets de réponse. »
- « Fais la revue du pipeline HubSpot et signale les dossiers dormants. »
- « Trouve 20 dirigeants de PME manufacturières au Québec dans Apollo et prépare une liste d'approche. »
- « Monte l'infolettre du mois dans Mailchimp avec un visuel Canva conforme à la marque. »
- « Prépare ma rencontre de 14 h : fiche client, derniers échanges, points à couvrir. »

## Garde-fous

L'assistant lit et analyse librement, mais ne pose aucune action visible de l'extérieur sans confirmation : pas d'envoi de courriel ni de campagne, pas d'invitation, pas de publication, pas d'écriture en masse dans le CRM. La liste pré-approuvée dans `.claude/settings.json` ne contient que des outils de lecture; toute écriture continue de demander une permission.

## Routines

- `/morning` produit un brief matinal visuel.
- Des routines planifiées (brief quotidien, revue de pipeline hebdomadaire) peuvent être créées à la demande : « Planifie une revue de pipeline chaque vendredi à 15 h. »
