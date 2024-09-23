<p align="center">
    <img src="https://github.com/user-attachments/assets/3ba5a526-c617-49c7-8165-30c3f3505d5c" width="300" alt="TSP logo">
</p>

# CSC8567 - Architectures distribuées et applications web
## Projet Final Kubernetes

## Auteurs

- Timothée Mathubert (timothee.mathubert@telecom-sudparis.eu)
- Gatien Roujanski (gatien.roujanski@telecom-sudparis.eu)
- Arthur Jovart (arthur.jovart@telecom-sudparis.eu)

## Démarrage des projets

Pour cette partie du cours, vous aurez besoin d'installer le programme `kubectl`.
1. Veuillez suivre les instructions disponibles sur ce [tuto d'installation de `kubectl`](https://kubernetes.io/fr/docs/tasks/tools/install-kubectl/).
2. Venez ensuite voir un professeur : donnez la composition de votre groupe. Un namespace vous sera alors créé sur le cluster du cours (`groupe-X` où X est le numéro de votre groupe). Un compte vous sera aussi créé sur le cluster.
3. Une fois votre compte créé, [connectez-vous au site de gestion du cluster](https://kube.luxbulb.org) avec vos identifiants, et créez vous un mot de passe personnel.
4. Allez ensuite dans la rubrique "Cluster Management". 
5. Sélectionnez le cluster "csc8567", et cliquez sur "Download KubeConfig".
6. Déplacez le fichier téléchargé à l'adresse `~/.kube/config` (`config` n'est pas un répertoire, c'est bien le fichier de configuration que vous avez téléchargé : il faut le renommer).
7. Essayez la commande dans un terminal (en remplaçant le "X" par votre numéro de groupe) :
```
kubectl cluster-info -n groupe-X
```
*Pour info, la notion `-n groupe-X` permet de préciser que la commande est exécutée dans le namespace "groupe-X". Sans la mention du namespace, elle serait exécutée dans le namespace "default", auquel vous n'avez pas accès.*
Ceci devrait vous afficher une sortie :
```
Kubernetes control plane is running at https://kube.luxbulb.org/k8s/clusters/local

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```
Si vous avez une erreur, allez voir un professeur.
8. Une fois que la dernière commande à fonctionné, vous êtes fin prêts pour démarrer le projet !

## Premiers pas sur Kubernetes

Tout d'abord, nous allons lancer un premier Pod, qui contiendra simplement un site web affichant une page.

Un Pod, c'est plus ou moins la version Kubernetes d'un conteneur de Docker.

- Pour créer ce Pod, il faut créer un Deployment et préciser l'image (Docker en l'occurence) utilisée pour créer le Deployment.
- Pour faire simple, un Deployment, c'est un peu comme le fichier `docker-compose.yml` vu pendant la première partie de ce cours.
- Pour récupérer des images, il est possible de les publier sur [Docker Hub](https://hub.docker.com). Celle que nous allons utiliser se trouve à l'adresse https://hub.docker.com/xhelozs/csc8567. Elle porte le tag "v1".
- Le site tourne sur le port 5000 du Pod ainsi créé.

- Comparez votre objectif à la documentation pour réussir à créer le Pod : [votre premier Deployment](https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/).

- Ensuite, nous allons utiliser le `port-forward` permis par Kubernetes pour mapper le port 5000 du Pod du site sur un port de notre interface `localhost`.
```
kubectl port-foward pods/[Nom du Pod] [Port localhost]:[Port du Pod] -n groupe-X
```

Alors, le site devrait être visible depuis `localhost:[Port localhost]`. Si c'est bon, passez à la suite !

## Exposer son site

Création d'un NodePort pour accéder à webnodb
Ecriture d'un Deployment pour déployer les 2 en même temps

## 
