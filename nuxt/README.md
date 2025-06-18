# Déploiement Nuxt 3 – Templates CI/CD & Docker

Ce dossier contient des templates prêts à l’emploi pour le build, le déploiement et l’exécution d’une application Nuxt 3 en production, avec Docker et CI/CD (GitLab CI & GitHub Actions).

## Structure des fichiers

- **Dockerfile.prod**  
  Dockerfile de production pour builder et lancer l’application Nuxt 3 à partir du dossier `.output`.

- **docker-compose.prod.yml**  
  Compose file pour lancer le conteneur Nuxt 3 en production, avec gestion du réseau, des variables d’environnement et healthcheck.

- **.gitlab-ci.yml**  
  Template GitLab CI pour builder, transférer et déployer automatiquement l’application sur un serveur distant via SSH et Docker.

- **build-and-deploy-frontend.yml**  
  Workflow GitHub Actions réutilisable pour builder et déployer le frontend Nuxt 3 sur un VPS via SSH et Docker.

## Utilisation

- **Important :** Si vous utilisez GitLab, assurez-vous de hacher la clé SSH privée en base64.
- **Important :** Configurer les variables d'environnement dans le fichier `.env` ou dans le système de gestion des secrets de son CI/CD.
- **Important :** Adapter les chemins et les configurations selon votre projet et votre environnement de production. Des drois d'accès peuvent être nécessaires pour le chemin absolu de déploiement.

### 1. Build & Déploiement avec Docker

```sh
# Build de l’image
docker build -f Dockerfile.prod -t app-prod .

# Lancement avec docker-compose
docker compose -f docker-compose.prod.yml up -d
```
