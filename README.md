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
*Pour info, la notion `-n groupe-X` permet de préciser que la commande est exécutée dans l'espace de noms "groupe-X". Sans la mention de ce dernier, elle serait exécutée dans le namespace "default", auquel vous n'avez pas accès. Probablement une info utile pour la suite !*
Ceci devrait vous afficher une sortie :
```
Kubernetes control plane is running at https://kube.luxbulb.org/k8s/clusters/local

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```
Si vous avez une erreur, allez voir un professeur pour résoudre le problème.
8. Une fois que la dernière commande à fonctionné, vous êtes fin prêts pour démarrer le projet !

## Modalités de rendu & soutenance

Vous êtes répartis en groupes de 2 ou 3 personnes, et vous partagez l'espace de noms associé à votre groupe.
Le rendu final sera commun au membres du groupe : une seule personne du groupe le rendra sur Moodle, et précisera les noms des membres du groupe.
La note se basera sur votre avancée dans les **Défis** listés ci-après.

Chaque Défi contient deux sections. Il faut les compléter pour réussir chaque Défi.
- Contenu : les tâches à réaliser.
- Questions : les questions auxquelles il faut répondre.

Votre rendu sera une archive `zip` ou `tar.gz` contenant, **pour chaque Défi** :
- Dans le cas où seules des commandes étaient utiles à la réalisation du Défi, un fichier contenant ligne par ligne les commandes que vous avez exécutées pour réussir le Contenu.
- Les fichiers de configuration que vous avez appliqués pour réussir un Défi. *Dans le cas où des fichiers de configurations ont été utilisés, il n'est pas nécessaire de repréciser les commandes que vous avez exécutées pour les appliquer.*
- Un schéma d'infrastructure représentant tous les composants réseau participant au fonctionnement du service.
- Les réponses aux questions de chaque Défi.

Pour la soutenance, vous devez laisser sur le cluster du cours et dans votre espace de noms tous les déploiements que vous avez fait. **Ne les supprimez pas après avoir rendu l'archive !!**

## Premiers pas sur Kubernetes (Défi 1)

### Consignes
Tout d'abord, nous allons lancer un premier Pod, qui contiendra simplement un site web affichant une page.

Un Pod, c'est plus ou moins la version Kubernetes d'un conteneur de Docker.

- Pour créer ce Pod, il faut créer un Deployment et préciser l'image (Docker en l'occurence) utilisée pour créer le Deployment.
- La commande suivante vous permet de créer un Deployment :
```
kubectl create deployment [Nom du Deployment] --image=[chemin/vers/l'image/sur/Docker/Hub:tag]
```
- Pour faire simple, un Deployment, c'est un peu comme le fichier `docker-compose` vu pendant la première partie de ce cours, sauf que ça n'est dédié au déploiement que d'un seul service à la fois.
- Pour récupérer des images, il est possible de les publier sur [Docker Hub](https://hub.docker.com). Celle que nous allons utiliser se trouve à l'adresse https://hub.docker.com/xhelozs/csc8567. Elle porte le tag "v1".
- Les informations sur la construction de l'image sont disponibles dans le dossier `csc8567-web-nodb` de ce même répo.
- Comparez votre objectif à la documentation pour réussir à créer le Pod : [votre premier Deployment](https://kubernetes.io/docs/tutorials/kubernetes-basics/deploy-app/deploy-intro/).
- Ensuite, nous allons utiliser le `port-forward` permis par Kubernetes pour mapper le port du Pod du site sur un port de notre interface `localhost`.
```
kubectl port-foward pods/[Nom du Pod] [Port localhost]:[Port du Pod]
```
Alors, le site devrait être visible depuis `localhost:[Port localhost]`. Si c'est bon, passez à la suite !

## Deuxièmes pas sur Kubernetes (ça se dit pas ?) (Défi 2)

Sur Kubernetes, il existe différents types de Services :
 - ClusterIP
 - NodePort
 - ExternalName
 - LoadBalancer
 - Headless

On souhaite 
Ecriture d'un Deployment
Création d'un ClusterIP pour le pod de webnodb
Création d'un NodePort pour accéder au pod de webnodb


## 
