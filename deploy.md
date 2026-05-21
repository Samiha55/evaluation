# Rapport de déploiement - [NAILI]
## Liens- **Application en ligne :** [https://evaluation.osc-fr1.scalingo.io/](https://evaluation.osc-fr1.scalingo.io/)]- **Dépôt de code :** [https://github.com/Samiha55]

## Procédure de déploiement pas à pas


## Prérequis techniques
1. Prérequis techniques
PHP 8.4+ avec l'extension pdo_msql
Composer installé
Un compte Scalingo

server_version: '5.7'
3. Fichier de configuration CI
Le fichier de configuration de l'intégration continue se trouve dans : .github/workflows/ci.yaml

Procédure de déploiement pas à pas
A. Initialisation sur Scalingo
1. Créer l'application

B. Ajout de variables d'environnement
Ajouter des variables d'environnement sur Scalingo
1. APP_ENV = prod
2. APP_SECRET = (par exemple copier la valeur de : echo bin2hex(random_bytes(16)) )

C. Préparation du code


3. Commit des changement git commit -m "Mise à jour effectuée"
D. Mise en ligne
1. Push des commits : git push