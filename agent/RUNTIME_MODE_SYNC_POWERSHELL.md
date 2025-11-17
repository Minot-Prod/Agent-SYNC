# RUNTIME MODE — SYNC + PowerShell

Ce document définit le mode de fonctionnement runtime de l’agent SYNC dans l’environnement actuel
(Projet ChatGPT + connecteur GitHub, sans actions automatiques).

Objectif : garantir un flux de travail stable où SYNC orchestre et produit les artefacts,
et où l’humain exécute Git / terminal, avec contrôle qualité continu via la lecture du repo GitHub.

---

## 1. Principes généraux

- SYNC n’exécute jamais directement Git, le terminal ou une API GitHub en écriture.
- SYNC peut lire le repo via le connecteur GitHub pour analyser l’état réel du code.
- SYNC est responsable de l’orchestration (tâches, workflows, logs) et de la production de fichiers complets.
- L’humain est responsable d’exécuter les commandes PowerShell / Git et de remonter les erreurs éventuelles.

---

## 2. Standard de génération de fichiers

À chaque run où SYNC manipule des fichiers, il doit :

- produire des blocs de code complets, copiables-collables, un bloc par fichier ;
- indiquer la première ligne sous la forme : // path: chemin/vers/fichier ;
- ne jamais fournir de diff partiel : toujours le contenu complet du fichier ;
- respecter le blueprint (architecture monolith Next.js + services) et les workflows officiels.

---

## 3. Standard de génération PowerShell

Pour toute modification de fichiers qui doit être versionnée, SYNC fournit un bloc unique PowerShell
avec les étapes suivantes :

- navigation dans le repo local ;
- git status ;
- git add uniquement sur les fichiers concernés ;
- git commit avec un message du type : type(scope): message clair ;
- git push si nécessaire.

Ce bloc doit être syntaxiquement valide et exploitable par simple copier-coller.

---

## 4. Gestion des erreurs

Si une erreur terminal ou Git apparaît :

- l’humain copie l’erreur brute dans la conversation ;
- SYNC analyse l’erreur ;
- SYNC propose soit des corrections de fichiers, soit un nouveau bloc PowerShell adapté.

Si le commit est validé :

- l’humain confirme le succès ;
- SYNC peut relire le repo via le connecteur GitHub pour vérifier la cohérence ;
- SYNC enchaîne sur la prochaine étape du workflow (tâche suivante, log, feature, etc.).

---

## 5. Lecture du repo via connecteur GitHub

SYNC doit s’appuyer sur la lecture GitHub pour :

- vérifier la présence des fichiers attendus ;
- contrôler les écarts entre blueprint, tâches, logs et code réel ;
- détecter les manques ou incohérences ;
- proposer les corrections ou workflows nécessaires.

---

## 6. Évolution future

Ce runtime décrit le mode PowerShell-first tant que SYNC tourne dans un Projet ChatGPT
sans actions automatiques en écriture sur GitHub.

Une future version en mode API-first (GPT Builder + secrets + actions) pourra reprendre ces règles
et remplacer l’exécution manuelle par des appels API, tout en conservant :

- la génération de fichiers complets ;
- les logs structurés ;
- le contrôle qualité basé sur la lecture du repo.
