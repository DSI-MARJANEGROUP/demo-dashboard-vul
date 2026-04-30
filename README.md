# 🛡️ Tableau de Bord Sécurité — DSI MarjaneGroup

Tableau de bord consolidé pour visualiser les vulnérabilités de l'ensemble des dépôts GitHub de l'organisation.

## 🚀 Déploiement en 3 étapes

### Étape 1 — Créer un token GitHub (PAT)

1. Aller sur https://github.com/settings/tokens → **Generate new token (classic)**
2. Cocher les scopes : **`repo`**, **`workflow`**, **`security_events`**, **`read:org`**
3. Copier le token généré

### Étape 2 — Ajouter le token comme secret du dépôt

1. Aller dans **Settings → Secrets and variables → Actions** de ce dépôt
2. Créer un secret nommé **`SECURITY_SCANNER_TOKEN`** avec le token de l'étape 1

### Étape 3 — Activer GitHub Pages

1. Aller dans **Settings → Pages**
2. Source : **GitHub Actions**
3. Sauvegarder

### Étape 4 — Activer le workflow de collecte (via l'interface GitHub)

1. Aller dans ce dépôt sur GitHub.com
2. Cliquer **"Add file"** → **"Create new file"**
3. Dans le champ de nom, taper : `.github/workflows/scrape-vulnerabilities.yml`
4. Copier-coller le contenu du fichier **`workflow-template.yml`** présent dans ce dépôt
5. Cliquer **"Commit changes"**

Le workflow s'exécutera automatiquement et le tableau de bord se mettra à jour !

---

## 📊 Ce que montre le tableau de bord

| Indicateur | Description |
|---|---|
| 🔴 Critique | Vulnérabilités nécessitant une action immédiate |
| 🟠 Élevée | À traiter en priorité |
| 🟡 Modérée | Planifier le traitement |
| 🔵 Faible | À surveiller |
| 📦 Dépendances | Packages tiers vulnérables (Dependabot) |
| 🔍 Code | Failles dans le code source (Code Scanning) |
| 🔑 Secrets | Credentials exposés dans le code (Secret Scanning) |

## 🔄 Mise à jour automatique

Le workflow s'exécute **tous les jours à 6h UTC** et met à jour le fichier `data/vulnerabilities.json` automatiquement.

---

*Tableau de bord généré par GitHub Copilot — DSI MarjaneGroup*
