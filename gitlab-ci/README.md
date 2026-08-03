# Mini projet GitLab CI

Ce mini-projet montre comment mettre en place un pipeline GitLab CI pour automatiser la construction, le test, la publication et le déploiement d’une application conteneurisée.

## Contenu du projet

Ce dossier contient :

- .gitlab-ci.yml : définition du pipeline GitLab CI
- Dockerfile : configuration de l’image Docker de l’application
- README.md : documentation du projet

## Fonctionnement du pipeline

Le pipeline est divisé en quatre étapes principales :

1. Build
   - construction de l’image Docker
   - sauvegarde de l’image sous forme d’archive

2. Test
   - chargement de l’image
   - exécution du conteneur
   - vérification de la réponse HTTP

3. Release
   - connexion à Docker Hub
   - publication de l’image

4. Deploy
   - déploiement sur un serveur distant via SSH

## Structure du projet

```text
gitlab-ci/
├── .gitlab-ci.yml
├── Dockerfile
└── README.md
```

## Technologie utilisée

- GitLab CI/CD
- Docker
- Docker-in-Docker
- Nginx
- SSH pour le déploiement

## Prérequis

Pour faire fonctionner ce projet, il faut :

- un runner GitLab avec accès Docker
- Docker installé sur le runner
- les variables suivantes définies dans GitLab CI :
  - IMAGE_TAG
  - IMAGE_NAME
  - DOCKER_USERNAME
  - DOCKER_PASSWORD
  - SSH_PRIVATE_KEY
  - SERVER_IP

## Construction locale

Vous pouvez tester l’image localement avec les commandes suivantes :

```bash
docker build -t mini-projet-gitlab-ci:v1.0 .
docker run -p 80:80 mini-projet-gitlab-ci:v1.0
```

Ensuite, ouvrez votre navigateur à l’adresse :

```text
http://localhost
```

## Résumé

Ce projet permet d’apprendre les bases d’un pipeline CI/CD moderne avec GitLab CI, Docker et le déploiement automatisé d’une application web.
