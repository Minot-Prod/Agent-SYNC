# Workflow de Travail — Agent SYNC

## Boucle de base

1. Lire ou rafraîchir le contexte :
   - lueprints/BLUEPRINT_SYNC_MVP.md
   - knowledge/SYNC_CONTEXT.md
   - knowledge/SYNC_SALES_SYSTEM_ROADMAP.md

2. Choisir une tâche prioritaire dans 	asks/ :
   - commencer par la plus petite tâche non terminée,
   - mettre à jour le statut dans le fichier de tâche.

3. Travailler dans le repo chantier (ex. sync-gpt-hub-mvp) :
   - créer/modifier des fichiers,
   - respecter les conventions de 	emplates/.

4. Mettre à jour la trace :
   - créer ou compléter une entrée dans logs/,
   - si besoin, enrichir knowledge/ (nouveaux learnings).

5. S’arrêter avec un état propre :
   - code compilable,
   - instructions claires pour la prochaine itération dans les logs.

## Ordre recommandé des tâches

1. 	asks/TASK_01_DISCOVERY.md
2. 	asks/TASK_02_ARCHI_MVP.md
3. 	asks/TASK_03_IMPLEMENTATION_MVP.md
4. 	asks/TASK_04_QA_MVP.md
5. 	asks/TASK_05_HANDOVER_VINCENT.md
"@ | Set-Content -Encoding UTF8 -Path ".\agent\WORKFLOW_SYNC_MVP.md"
# ===============================
# blueprints/BLUEPRINT_SYNC_MVP.md
# ===============================
@"
# Blueprint — MVP SYNC (Sync GPT Hub / Sales AI)

## Goal

Construire un **MVP fonctionnel** du hub SYNC qui permet :
- aux commerciaux d’accéder à un **assistant IA de vente** centralisé,
- d’exécuter des tâches clés : préparation d’appels, analyse d’entreprise, rédaction de scripts, coaching,
- avec une interface simple mais propre.

## Scope (MVP)

### Inclure

- **Architecture :**
  - Monolith **Next.js**.
  - Pages principales :
    - / (dashboard simple),
    - /deals ou /opps (placeholder liste opportunités),
    - /assistant (chat IA central).

- **Back logique :**
  - API routes Next pour orchestrer les appels vers les modèles IA.
  - Structure de services dans src/lib/services.
  - Base de données simulée en **JSON local** (palier A) pour stocker :
    - faux comptes,
    - faux deals,
    - faux historiques de requêtes.

- **IA :**
  - Orchestration simple :
    - 1 endpoint “assistant” qui route vers plusieurs prompts pré-définis (prospection, script, analyse).
  - Pas besoin d’intégrations CRM réelles au MVP.

### Exclure (pour plus tard)

- Intégration CRM temps réel (HubSpot / autre).
- Auth complexe multi-tenant.
- Dashboard analytics avancé.
- Système complet de scoring et de reporting.

## Acceptance Criteria

Le MVP est considéré “OK” si :

1. Le projet se lance en local avec :
   `ash
   npm install
   npm run dev
# ===============================
# 2. CONTENU DES FICHIERS RESTANTS
# ===============================

# ---- blueprints/BLUEPRINT_SYNC_MVP.md ----
@"
# Blueprint — MVP SYNC (Sync GPT Hub / Sales AI)

## Goal
Construire un **MVP fonctionnel** du hub SYNC qui permet :
- aux commerciaux d’accéder à un **assistant IA centralisé**,
- d’exécuter des tâches clés : préparation d’appels, analyse entreprise, rédaction scripts, coaching,
- avec une interface simple mais propre.

## Scope (MVP)
Inclure :
- Monolith **Next.js**
- Pages :
  - /
  - /assistant
  - /deals (mock)
- API routes pour l’IA
- Données mock (JSON local)
- Assistant IA avec prompts pré-définis

Exclure :
- CRM réel
- Auth complexe
- Dashboard avancé

## Acceptance Criteria
- Le projet démarre en 
pm run dev
- Dashboard OK
- Assistant IA OK
- Données mock affichées
- README technique présent
