
Noms des auteurs :  Thomas CISERANE
Date de réalisation : xx/02/2025


## 1. Premier container

### 1.1. Hello World 

Pouvez-vous expliquer avec vos mots ce qui s'est passé suite à l'exécution de cette commande? 

<span style="color:#22eeb1">L'image "hello-world" n'était pas initialement installé alors Docker a installé  celle-ci automatiquement dans sa version la plus récente puis à créé un container avec cette image et l'a exécuté.</span>

<img src="./sceenshots/part1/1_1.png" alt="Output de la commande docker run hello-world" style="width:40%">

### 1.2.  Observer un container

Résultat obtenu après l'exécution de la commande "docker container ls -a" :

<img src="./sceenshots/part1/1_2.png" alt="Output de la commande docker container ls -a" style="width:70%">

Retrouvez les informations suivantes sur le container lancé précédemment : 
1. Quel est son identifiant ? 

    <span style="color:#22eeb1">Son ID est **7807bde91dba**d736e1b92888ec5562026425f99ace51feaa46fbf2dd7086b2de, soit **7807bde91dba** sur l'image.</span>

2. Quel est son nom ?

    <span style="color:#22eeb1">Son nom est priceless_goodall.</span>

3. Quel est son état ?

    <span style="color:#22eeb1">Son état est Exited car l'execution du container s'est terminée 5 minutes plus tard</span>

4. Quel est le nom de son image?  Avez-vous vu au point 1.1. d''où cette image provenait?

    <span style="color:#22eeb1">Le nom de son image est hello-world.</span>

5. Quelle commande le container a-t-il exécuté?

    <span style="color:#22eeb1">Il a exécuté la commande "/hello".</span>

6. Si vous avez installer Docker Desktop, pouvez-vous retrouver ces mêmes informations dans l'interface graphique?

    <img src="./sceenshots/part1/1_2_6.png" alt="Menu des containers" style="width:75%">

    <span style="color:#22eeb1">Pour trouver la dernière information soit celle de la commande, il faut rentrer dans le container, aller dans l'option "Inspect" puis trouver la commande dans le JSON.</span>

    <img src="./sceenshots/part1/1_2_6bis.png" alt="Champs CMD issu du json" style="width:30%">


### 1.3. Les images 

1. Quelles informations voyez-vous?  Quel est le lien avec ce que vous avez observé auparavant?

    <span style="color:#22eeb1">On retrouve le nom de l'image, sa version, son ID, Date de création et sa taille.
    En dehors des attributs cités juste avant, en rentrant dans l'image, on retrouve les étapes de comment celle-ci a été contruite et exécutée (commande "/hello").</span>

    <img src="./sceenshots/part1/1_3df.png" alt="Dockerfile" style="width:50%">

    <span style="color:#22eeb1">Le lien pourrait être que le container a utilisé cette image lors de sa création pour exécuter la commande "/hello".</span>

2. Comparez l'output de cette commande avec la vue correspondante de l'interface graphique.

    <span style="color:#22eeb1">On retrouve les mêmes informations que ceux de l'interface graphique.</span>

    <img src="./sceenshots/part1/1_3.png" alt="Output de la commande 'docker image ls'" style="width:50%">
    <img src="./sceenshots/part1/1_3bis.png" alt="Menu des images" style="width:70%">

3. Essayez de trouver la commande qui vous permettra de supprimer cette image.  C'est une bonne idée de ne pas conserver les images non utilisées sur votre système de fichiers : même avec la mutualisation de couches, elles prennent de l'espace sur le disque!

    <span style="color:#22eeb1">Pour supprimer une image on peut utiliser la commande "docker image rm -f" ou "docker rmi -f" avec "-f" pour forcer la suppression.</span>

### 1.4. Les volumes

## 2. Utiliser un container

### 2.1. Interagir avec un container

1. A quoi servent les options ```i``` et ```t```dans la commande ci-dessus? 

    <span style="color:#22eeb1">Les options ```i``` et ```t``` servent respectivement à maintenir l'entrée standard (stdin) ouverte, permettant d'interagir avec le conteneur et permettant d'avoir les fonctionnalités d'un terminal toujours dans l'interaction, comme par exemple le mot de passe ne s'affiche pas quand on le rentre, sans l'option ```t```, il s'afficherait.</span>

2. Chaque container Docker est destiné à exécuter une commande unique.  Quelle est-elle dans ce cas-ci?

    <span style="color:#22eeb1">La commande est "/bin/bash".</span>

3. Dans le container, quels sont les processus présents?  Et leurs PIDs? 

    <img src="./sceenshots/part2/2_1_3.png" alt="Output de la commande ps" style="width:50%">

    <span style="color:#22eeb1">Le processus est "bash" et son PID est 1</span>

4. Avec quel utilisateur êtes-vous loggé?

    <span style="color:#22eeb1">L'utilisateur est "root".</span>

5. Votre container a-t'il accès à Internet?  Qui est son résolveur?

    <span style="color:#22eeb1">Oui le conatiner a accès à internet :

    <img src="./sceenshots/part2/2_1_5.png" alt="Output ping google" style="width:45%">

    <span style="color:#22eeb1">Et son resolveur est: 192.168.65.7

    <img src="./sceenshots/part2/2_1_5bis.png" alt="Résolveur" style="width:45%">


### 2.2. Inspecter un container

1. Chaque container dispose d'une interface réseau.  Quelle est l'adresse **IP** de l'interface de votre container? 

    L'adresse IP est **172.17.0.2**.

    <img src="./sceenshots/part2/2_2_1.png" alt="Output de la commande docker inspect" style="width:40%">

2. Votre container a-t'il des **ports** ouverts?  

    Non, aucun port n'est ouvert.

    <img src="./sceenshots/part2/2_2_2.png" alt="Output de la commande docker inspect" style="width:55%">

### 2.3. Faire tourner un service dans un container

- Qu'avez-vous observé au niveau des "ports" ?  Expliquez et illustrez votre réponse avec des screenshots.

    Ici on voit que nginx tourne sur le port 80 utilisant le protocole TCP mais pas encore accessible en dehors de la machine.

    <img src="./sceenshots/part2/2_3_1.png" alt="Output de la commande docker inspect" style="width:30%">

    Après avoir exécuté la commande suivante: ```docker run -p80:80 --name=mon-serveur-web2b nginx```  et lancé le container, on voit qu'il est accessible en dehors de la machine car on préciser le port de la machine sur lequel il est lancé.

    <img src="./sceenshots/part2/2_3_2.png" alt="Output de la commande docker inspect" style="width:30%">

## 3. Construire des images

### 3.1. Figer un container

Après avoir utilisé les commandes:

<img src="./sceenshots/part3/3_1.png" alt="Après modification du index.html" style="width:50%">

<br>

Après la modification de l'index.html:

<img src="./sceenshots/part3/3_1bis.png" alt="Après modification du index.html" style="width:50%">

<br>

Sauvegarde de l'image modifiée à l'aide de la commande: ```docker container commit mon-serveur-web2b myweb```

<img src="./sceenshots/part3/3_1ter.png" alt="Après sauvegarde de l'image" style="width:50%">

### 3.2. Créer une image sur base d'un Dockerfile

Après la création du Dockerfile et du fichier index.html, j'ai créé l'image suivante:

<img src="./sceenshots/part3/3_2.png" alt="" style="width:50%">
<img src="./sceenshots/part3/3_2bis.png" alt="" style="width:50%">

Puis pour un test j'ai crréé un container sur base de cette image avec la commande suivante: ```docker run --name=web -p80:80 myweb2```

<img src="./sceenshots/part3/3_2ter.png" alt="" style="width:50%">

Puis j'ai lancé le container et j'ai observé qu'il est accessible en dehors de la machine.

<img src="./sceenshots/part3/3_2quater.png" alt="" style="width:50%">

## Exercices récapitulatifs

Documentez ici la réalisation des exercices, via des explications et des snapshots. 
### 4.1. Démarrer un serveur Web Apache

Pour l'image Apache, j'ai choisi "httpd" que j'ai installé en utilisant : ```docker pull httpd```

<img src="./sceenshots/part4/4_1.png" alt="Pull de l'image" style="width:40%">

J'ai ensuite démarré un premier container sur le port 80 de ma machine avec: ```docker run --name=myapache -p80:80 httpd```

Puis un deuxième container sur le port 8080 de ma machine avec: ```docker run --name=myapache2 -p8080:80 httpd```

<img src="./sceenshots/part4/4_1bis.png" alt="Menu des containers montrant les containers myapache et myapache2" style="width:55%">

Pour renter dans  chaque container, j'ai utilisé la commande suivante: ```docker exec -it [nom du container] bash``` avec pour nom du container **"myapache"** et **"myapache2"**

Puis j'ai fait un ```apt update``` et ```apt install -y nano``` puis j'ai modifié le fichier html pour chaque comme suit:

<img src="./sceenshots/part4/4_1ter.png" alt="Modification du fichier html pour le container myapache" style="width:20%">

<img src="./sceenshots/part4/4_1quater.png" alt="Modification du fichier html pour le container myapache2" style="width:20%">

Dans un répertoire, j'ai créé un dossier avec un fichier **Dockerfile** à l'interieur contenant les commandes suivantes:

```
FROM httpd:latest
RUN apt update && apt install -y nano
COPY index.html /usr/local/apache2/htdocs
```

Puis j'ai construit l'image avec la commande suivante: ```docker build -t myhttpd .```

<img src="./sceenshots/part4/4_1quin.png" alt="Construction de l'image" style="width:50%">

<img src="./sceenshots/part4/4_1quinbis.png" alt="Construction de l'image" style="width:80%">

Pour terminer, j'ai créé un container à partir de cette image avec la commande suivante: ```docker run --name=myapache3 -p1411:80 myhttpd``` puis je l'ai lancé et j'ai observé qu'il est accessible en dehors de la machine.

<img src="./sceenshots/part4/4_1quinter.png" alt="Page web de myapache3" style="width:30%">

### 4.2. Lancer un résolveur Bind dans un container Docker

1. Quelle configuration avez-vous effectuée au niveau des ports ?
2. Qu'avez-vous observé dans la trace Wireshark qui prouve que la configuration est correcte?  Illustrez avec un screenshot de la capture.

### 4.3. Container avec script Python
