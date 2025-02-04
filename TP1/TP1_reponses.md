
Noms des auteurs :  Thomas CISERANE
Date de réalisation : xx/02/2025


## 1. Premier container

### 1.1. Hello World 

Pouvez-vous expliquer avec vos mots ce qui s'est passé suite à l'exécution de cette commande? 

L'image "hello-world" n'était pas initialement installé alors Docker a installé  celle-ci automatiquement dans sa version la plus récente puis à créé un container avec cette image et l'a exécuté.

<img src="./sceenshots/part1/1_1.png" alt="Output de la commande docker run hello-world" style="width:40%">

### 1.2.  Observer un container

Résulat obtenu après l'exécution de la commande "docker container ls -a" :

<img src="./sceenshots/part1/1_2.png" alt="Output de la commande docker container ls -a" style="width:70%">

Retrouvez les informations suivantes sur le container lancé précédemment : 
1. Quel est son identifiant ? 

    Son ID est **7807bde91dba**d736e1b92888ec5562026425f99ace51feaa46fbf2dd7086b2de, soit **7807bde91dba** sur l'image.

2. Quel est son nom ?

    Son nom est priceless_goodall.

3. Quel est son état ?

    Exited car l'execution du container s'est terminée 5 minutes plus tard.

4. Quel est le nom de son image?  Avez-vous vu au point 1.1. d''où cette image provenait?

    Le nom de son image est hello-world.

5. Quelle commande le container a-t-il exécuté?

    Il a exécuté la commande "/hello".

6. Si vous avez installer Docker Desktop, pouvez-vous retrouver ces mêmes informations dans l'interface graphique?

    <img src="./sceenshots/part1/1_2_6.png" alt="Menu des containers" style="width:75%">

    Pour trouver la dernière information soit celle de la commande, il faut rentrer dans le container, aller dans l'option "Inspect" puis trouver la commande dans le JSON.
    <img src="./sceenshots/part1/1_2_6bis.png" alt="Champs CMD issu du json" style="width:30%">


### 1.3. Les images 

1. Quelles informations voyez-vous?  Quel est le lien avec ce que vous avez observé auparavant?

    On retrouve le nom de l'image, sa version, son ID, Date de création et sa taille.
    En dehors des attributs cités juste avant, en rentrant dans l'image, on retrouve les étapes de comment celle-ci a été contruite et exécutée (commande "/hello").

    <img src="./sceenshots/part1/1_3df.png" alt="Dockerfile" style="width:50%">

    Le lien pourrait être que le container a utilisé cette image lors de sa création pour exécuter la commande "/hello".

2. Comparez l'output de cette commande avec la vue correspondante de l'interface graphique.

    On retrouve les mêmes informations que ceux de l'interface graphique.

    <img src="./sceenshots/part1/1_3.png" alt="Output de la commande 'docker image ls'" style="width:50%">
    <img src="./sceenshots/part1/1_3bis.png" alt="Menu des images" style="width:70%">

3. Essayez de trouver la commande qui vous permettra de supprimer cette image.  C'est une bonne idée de ne pas conserver les images non utilisées sur votre système de fichiers : même avec la mutualisation de couches, elles prennent de l'espace sur le disque!

    Pour supprimer une image on peut utiliser la commande "docker image rm -f" ou "docker rmi -f" avec "-f" pour forcer la suppression.

### 1.4. Les volumes

## 2. Utiliser un container

### 2.1. Interagir avec un container

1. A quoi servent les options ```i``` et ```t```dans la commande ci-dessus? 

    Les options ```i``` et ```t``` servent respectivement à maintenir l'entrée standard (stdin) ouverte, permettant d'interagir avec le conteneur et permettant d'avoir les fonctionnalités d'un terminal toujours dans l'interaction, comme par exemple le mot de passe ne s'affiche pas quand on le rentre, sans l'option ```t```, il s'afficherait.

2. Chaque container Docker est destiné à exécuter une commande unique.  Quelle est-elle dans ce cas-ci?

    Dans ce cas ci c'est la commande bash.

3. Dans le container, quels sont les processus présents?  Et leurs PIDs? 

    <img src="./sceenshots/part2/2_1_3.png" alt="Output de la commande ps" style="width:50%">

    Bash avec un PID de 1

4. Avec quel utilisateur êtes-vous loggé?

    Avec l'utilisateur root.

5. Votre container a-t'il accès à Internet?  Qui est son résolveur?

    Oui le conatiner a accès à internet :

    <img src="./sceenshots/part2/2_1_5.png" alt="Output ping google" style="width:45%">

    Et son resolveur est: 192.168.65.7

    <img src="./sceenshots/part2/2_1_5bis.png" alt="Résolveur" style="width:45%">

### 2.2. Inspecter un container


1. Chaque container dispose d'une interface réseau.  Quelle est l'adresse **IP** de l'interface de votre container? 
2.  Votre container a-t'il des **ports** ouverts?  


### 2.3. Faire tourner un service dans un container



- Qu'avez-vous observé au niveau des "ports" ?  Expliquez et illustrez votre réponse avec des screenshots. 


## 3. Construire des images

### 3.1. Figer un container 


### 3.2. Créer une image sur base d'un Dockerfile


## Exercices récapitulatifs

Documentez ici la réalisation des exercices, via des explications et des snapshots. 
### 4.1. Démarrer un serveur Web Apache


### 4.2. Lancer un résolveur Bind dans un container Docker

1. Quelle configuration avez-vous effectuée au niveau des ports ? 
2. Qu'avez-vous observé dans la trace Wireshark qui prouve que la configuration est correcte?  Illustrez avec un screenshot de la capture. 

### 4.3. Container avec script Python
