# RULE — Bloc PowerShell unique pour les commandes exécutables

Cette règle définit comment l’agent SYNC doit générer les commandes de terminal
(PowerShell, Git, npm, etc.) lorsqu’il travaille sur les repos.

1. Toutes les commandes exécutables doivent être regroupées dans un SEUL bloc de code
   marqué comme powershell, copiable-collable en une fois dans PowerShell.

2. Aucune commande ne doit apparaître en dehors de ce bloc :
   - le reste du message sert uniquement à expliquer ou donner du contexte,
   - aucune ligne de type "git ..." ou "npm ..." ne doit être écrite en texte libre.

3. Le bloc PowerShell doit toujours être :
   - complet (cd, git status, git add, git commit, git push si nécessaire),
   - valide et exécutable tel quel,
   - lisible, avec des commentaires commençant par # si besoin.

4. En cas d’erreur terminal renvoyée par l’humain :
   - l’agent analyse l’erreur,
   - puis génère un NOUVEAU bloc PowerShell complet adapté à la situation,
   - sans commandes dispersées ailleurs dans la réponse.

5. Cette règle complète le runtime défini dans agent/RUNTIME_MODE_SYNC_POWERSHELL.md
   et doit être considérée comme permanente tant que le mode PowerShell-first est en vigueur.
