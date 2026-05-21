# Rapport de déploiement – [NAILI]

## Liens du projet

- **Application en ligne :**  
  https://evaluation.osc-fr1.scalingo.io/

- **Dépôt GitHub :**  
  https://github.com/Samiha55/evaluation

---

# Procédure de déploiement pas à pas

## 1. Prérequis techniques

Avant de commencer le déploiement, il faut vérifier que les outils suivants sont installés et configurés :

### Environnement nécessaire

- PHP 8.4+
- Extension PHP :
  - `pdo_mysql`
- Composer installé
- Git installé
- Un compte Scalingo

---

# 2. Configuration de l’intégration continue (CI)

Le projet contient un système d’intégration continue permettant d’exécuter automatiquement des vérifications à chaque push GitHub.

Le fichier de configuration se trouve dans :


.github/workflows/ci.yaml


Cette configuration permet notamment :
- d’installer les dépendances ;
- de vérifier le bon fonctionnement du projet Symfony ;
- d’automatiser certains contrôles avant déploiement.

---

# 3. Déploiement sur Scalingo

## A. Initialisation de l’application sur Scalingo

### Étape 1 — Créer une application

1. Se connecter à :
   https://scalingo.com

2. Cliquer sur :

```text
Create an app
```

3. Donner un nom à l’application.

Exemple :

```text
evaluation
```

4. Choisir la région d’hébergement.

---

## B. Ajouter les variables d’environnement

Une fois l’application créée, il faut configurer les variables d’environnement nécessaires au fonctionnement de Symfony.

Dans Scalingo :


Dashboard → Environment Variables

Ajouter les variables suivantes :

### 1. APP_ENV


name : APP_ENV
valeur :prod  


Cette variable permet de lancer Symfony en mode production.

---

### 2. APP_SECRET

Générer une clé secrète avec la commande :

name : APP_SECRET

Puis ajouter la valeur générée dans :


APP_SECRET=(random_bytes(16));   (c'est un exemple)

Cette clé est utilisée pour :
- la sécurité ;
- les sessions ;
- le chiffrement des données Symfony.

---

# 4. Préparation du code avant déploiement

Avant l’envoi du projet sur Scalingo, il faut vérifier que tous les changements ont bien été enregistrés avec Git.

## Étape 1 — Vérifier les fichiers modifiés

```bash
git status
```

---

## Étape 2 — Ajouter les fichiers modifiés

```bash
git add .
```

---

## Étape 3 — Créer un commit

```bash
git commit -m "Mise à jour effectuée"
```

Le commit permet d’enregistrer une nouvelle version du projet.

---

# 5. Mise en ligne de l’application

## Étape 1 — Envoyer le code sur GitHub

```bash
git push
```

---

## Étape 2 — Déploiement automatique

Une fois le `git push` effectué :

- GitHub envoie le code ;
- Scalingo détecte automatiquement les changements ;
- le déploiement démarre automatiquement ;
- l’application est reconstruite puis mise en ligne.

---

# 6. Vérification du déploiement

Après le déploiement :

1. Ouvrir l’application dans le navigateur :

```text
https://evaluation.osc-fr1.scalingo.io/
```

2. Vérifier :
- que la page s’affiche correctement ;
- qu’aucune erreur Symfony n’apparaît.

---

# Conclusion

Le projet a été déployé avec succès sur Scalingo grâce à :
- la configuration des variables d’environnement ;
- l’utilisation de Git et GitHub ;
- l’intégration continue ;
- le déploiement automatique proposé par Scalingo.

L’application est désormais accessible en ligne et prête à être utilisée.