# labo-indexation-ai-docker

[![Docker Pulls](https://img.shields.io/docker/pulls/abesesr/labo-indexation-ai.svg)](https://hub.docker.com/r/abesesr/labo-indexation-ai/)

Configuration docker 🐳 pour déployer l'[image docker JupyterLab](https://github.com/abes-esr/labo-indexation-ai-jupyterlab) du projet Abes labo-indexation-ia dont les notebooks sont versionnés ici : https://github.com/abes-esr/labo-indexation-ai

## URLs de jupyterlab

Les URLs correspondantes aux déploiements en local de labo-indexation-ai-docker sont les suivantes :

- local :
  - http://127.0.0.1:16080/ : URL locale de jupyterlab
- dev :
  - http://jupyter-labo.v212.abes.fr:16080/ : URL de dev de jupyterlab

## Prérequis

Disposer de :
- ``docker``
- ``docker-compose``

## Installation

Déployer la configuration docker dans un répertoire :
```bash
# adaptez /opt/pod/ avec l'emplacement où vous souhaitez déployer l'application
cd /opt/pod/
git clone https://github.com/abes-esr/labo-indexation-ai-docker.git
```

Configurer l'application depuis l'exemple du [fichier ``.env-dist``](./.env-dist) (ce fichier contient la liste des variables avec des explications et des exemples de valeurs) :
```bash
cd /opt/pod/labo-indexation-ai-docker/
cp .env-dist .env
# personnaliser alors le contenu du .env
```

Démarrer l'application :
```bash
cd /opt/pod/labo-indexation-ai-docker/
docker-compose up -d
```

## Démarrage et arrêt

```bash
# pour démarrer l'application (ou pour appliquer des modifications 
# faites dans /opt/pod/labo-indexation-ai-docker/.env)
cd /opt/pod/labo-indexation-ai-docker/
docker-compose up -d
```

Remarque : retirer le ``-d`` pour voir passer les logs dans le terminal et utiliser alors CTRL+C pour stopper l'application

```bash
# pour stopper l'application
cd /opt/pod/labo-indexation-ai-docker/
docker-compose stop


# pour redémarrer l'application
cd /opt/pod/labo-indexation-ai-docker/
docker-compose restart
```

## Supervision

```bash
# pour visualiser les logs de l'appli
cd /opt/pod/labo-indexation-ai-docker/
docker-compose logs -f --tail=100
```

Cela va afficher les 100 dernière lignes de logs générées par l'application et toutes les suivantes jusqu'au CTRL+C qui stoppera l'affichage temps réel des logs.


## Sauvegardes

Les éléments suivants sont à sauvegarder:
- ``/opt/pod/labo-indexation-ai-docker/.env`` : contient la configuration spécifique de notre déploiement
- ``/opt/pod/labo-indexation-ai-docker/volumes/labo-indexation-ai/`` : contient le travail en cours édité avec l'interface web du jupyterlab (qui n'est pas forcément envoyé sur git si jamais le travail est en cours)

