# Compte-rendu de Lab : Les bases de Git
**Date :** 27 Janvier 2026

---

## 🎯 1. Fonction et Objectif
> *En résumé, à quoi sert ce lab et quel est le but final ?*

### Objectif du lab (à rédiger)

    Perform the GitHub Desktop Tutorial
    Create a repository and clone it on your computer
    Create a branch and navigate between branches
    Modify a file in the repository and push the modifications
    Manage conflicts
    Redo the lab using command line interface (CLI)


Ce lab consistait à mettre en place **[Objectif principal]** afin de comprendre le fonctionnement de **[Concept clé]**. L'idée était de simuler un environnement où [détail rapide].

### APPLICATION DANS LE MONDE REEL (entreprise)


### ETAPE DANS LE CYCLE DEVops (voir schéma)

---

## 🛠️ 2. Réalisation (Ce qu'on a fait)
*Étapes principales de la manipulation :*

1. **Préparation :** Installation des outils [Outils utilisés] et configuration du réseau.
2. **Implémentation :** Écriture du code / Branchement des composants pour [Action précise].
3. **Tests :** Vérification du bon fonctionnement via [Méthode de test].

---

## 3. Problèmes Rencontrés & Erreurs
*C'est ici que tu notes ce qui a coincé.*

| Problème | Cause de l'erreur | Solution trouvée |
| :--- | :--- | :--- |
| **Erreur de compilation** | Oubli d'un point-virgule ou version obsolète. | Mise à jour de la lib et re-test. |
| **Pas de connexion** | Mauvaise adresse IP configurée. | Vérification via `ipconfig` et correction. |
| **[Bug X]** | [Pourquoi ça n'a pas marché] | [Comment tu l'as réparé] |

---

## Finalité du LAB 
- 📝 **Note :** Ne pas oublier de sauvegarder la config avant de redémarrer.
- 🔗 **Lien utile :** [Documentation ou tutoriel]
- ⭐ **Rappel :** La commande `[commande spécifique]` fait gagner un temps fou.

---

## LAB 3 — Continuous Testing

- **Titre :** LAB 3 — Continuous Testing

- **Objectifs :**
    - Exécuter la suite de tests fournie et s'assurer qu'elle passe.
    - Utiliser la démarche TDD pour implémenter la fonctionnalité GET `user` (contrôleur + route).
    - Vérifier le fonctionnement de l'API via tests unitaires et tests d'API.

- **Applications en entreprise :**
    - Intégrer des tests automatisés dans les pipelines CI/CD pour détecter les régressions tôt.
    - Améliorer la qualité logicielle et réduire les risques lors des mises en production.
    - Permettre le « shift-left testing » : tester dès les premières étapes du développement.

- **Étapes dans le cycle DevOps (contexte de ce TP) :**
    1. Plan / Code — écrire la fonctionnalité et les tests.
    2. Build — installer dépendances (`npm install`).
    3. Test — exécuter `npm test` (tests unitaires et d'API).
    4. Release / Deploy — démarrer l'application (`npm start`) et vérifications manuelles.
    5. Operate / Monitor — vérifier que le service répond aux requêtes.

- **Réalisation (installation → exécution) :**
    - Installer Node.js et Redis.
    - Lancer `redis-server.exe` (ou `redis-server` sur macOS/Linux). Vérifier avec `redis-cli ping` → `PONG`.
    - Depuis le dossier du lab : `npm install`.
    - Implémentation via TDD : ajout de tests unitaires (`test/user.controller.js`) et tests d'API (`test/user.router.js`).
    - Ajout de la méthode `get` dans `src/controllers/user.js` et de la route GET dans `src/routes/user.js`.
    - Exécution des tests : `npm test` (tous les tests automatisés passent).
    - Démarrage du serveur : `npm start` puis tests manuels avec `curl.exe` ou `Invoke-WebRequest` (PowerShell).

- **Problèmes rencontrés & solutions :**
    - Redis non démarré → démarrer `redis-server.exe` avant d'exécuter l'application.
    - Port `3000` occupé (EADDRINUSE) → identifier le PID (`netstat -ano | findstr :3000`) et arrêter le processus (`taskkill /PID <PID> /F`) ou `taskkill /IM node.exe /F`.
    - Différences PowerShell / bash pour `curl` : utiliser `curl.exe` ou `Invoke-WebRequest` ; avec `Invoke-WebRequest`, ajouter `-UseBasicParsing` pour éviter l'analyse HTML interactive.
    - Lors des tests automatisés, s'assurer qu'aucun serveur Node antérieur n'est resté en écoute (sinon, tuer les processus Node) pour éviter les conflits de port.

---

**Commandes utiles :**

```powershell
# Installer dépendances
npm install

# Lancer la suite de tests
npm test

# Démarrer le serveur
npm start

# Exemple PowerShell : créer un utilisateur
$body = @{ username = "test"; firstname = "John"; lastname = "Doe" } | ConvertTo-Json
Invoke-WebRequest -Uri "http://localhost:3000/user" -Method POST -Headers @{"Content-Type"="application/json"} -Body $body

# Récupérer un utilisateur
Invoke-WebRequest -Uri "http://localhost:3000/user/test" -Method GET -UseBasicParsing
```