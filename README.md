# Agent-SYNC — Cerveau de l’Agent IA pour le MVP SYNC

Ce dépôt sert de **cerveau** à l’agent IA chargé de construire et faire évoluer le MVP SYNC (Sync GPT Hub / système de vente IA).

Il ne contient PAS le code de prod, mais :
- le contexte,
- les blueprints,
- les tâches,
- les playbooks,
- les templates,
- les logs.

Le code applicatif vit dans un autre dépôt (ex. sync-gpt-hub-mvp).

## Règles d’utilisation par l’agent

1. Toujours commencer par lire :
   - lueprints/BLUEPRINT_SYNC_MVP.md
   - gent/AGENT_PROFILE.md
   - gent/WORKFLOW_SYNC_MVP.md

2. Utiliser ce dépôt comme **référence** :
   - pour comprendre le projet,
   - pour savoir quelles tâches exécuter,
   - pour savoir comment livrer (qualité, format, convention git).

3. Ne jamais écrire de code applicatif ici.
   - Le code vit dans le repo chantier (ex. sync-gpt-hub-mvp).
   - Ici, l’agent ne modifie que :
     - logs/,
     - 	asks/ (cases cochées, statuts),
     - éventuellement knowledge/ (ajout de contexte).

## Convention

- Langue principale : **français**
- Style : clair, concis, orienté production
- Stack cible MVP : **Next.js monolith + API routes** (voir roadmap Sync dans knowledge/).
