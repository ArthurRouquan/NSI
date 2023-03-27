# TP Shell 

![](images/shell.png)

La rédaction du document réponse Capytale est en cours... notez vos réponses dans un fichier texte pour l'instant.

## Introduction :material-console:

Les premiers systèmes d'exploitation étaient dépourvus d'interface graphique. Il n'y avait pas de fenêtres ni de curseur de souris pour interagir avec l'ordinateur. Au lieu de cela, les utilisateurs devaient communiquer avec le système d'exploitation en utilisant des **lignes de commandes**, qui sont du texte saisi via un programme appelé **shell**. Le Shell est une <b>interface</b> entre le noyau et l'utilisateur :

<figure markdown>
![](images/walnut-dark.png#only-dark){ width=200 }
![](images/walnut-light.png#only-light){ width=200 }
</figure>

Le shell permet à l'utilisateur d'exécuter des commandes et des scripts pour interagir avec le système d'exploitation (exécuter des programmes, gérer des fichiers et des répertoires, contrôler les processus en cours etc.). Le shell est toujours disponible dans les OS actuels et encore très utilisé de nos jours. On se propose dans ce TP de découvrir les commandes de base du shell.

??? note "Différence entre shell et terminal"
    Le **terminal** et le **shell** sont souvent confondus dans le langage courant.

    * Le **terminal** est un programme permet à l'utilisateur de **saisir des commandes** et de les exécuter en mode texte,
    sans avoir besoin d'une interface graphique. Il exécute par défaut un shell.

    * Le **shell** est le programme qui s'exécute à l'intérieur du terminal et qui **interprète** les commandes saisies par l'utilisateur et qui permet d'interagir avec le système d'exploitation.

    Comme il n'est généralement pas possible d'interagir avec le shell sans utiliser un terminal, les deux termes sont confondus. Le terminal est l'interface du shell qui est l'interface du noyau qui est l'interface du matériel. Vous suivez ?

## L'arborescence des dossiers et des fichiers :material-family-tree:

Dans les systèmes d'exploitation basés sur UNIX (par exemple Linux ou macOS), nous avons un système de fichiers et de dossiers en arborescence :

![](images/folder-light.png#only-light)
![](images/folder-dark.png#only-dark)

### Chemins absolus

On peut accéder à n'importe quel dossier ou fichier grâce à un **chemin**. Par exemple, `/home/joel/images/photo1.jpg` permet d'accéder au fichier `photo1.jpg`. Quand le chemin part de le **racine** `/`, on parle de **chemin absolu**.

### Chemins relatifs

On peut aussi accéder à un fichier ou à un dossier grâce à un **chemin relatif**. Par exemple, si l'on **se situe** dans le dossier `/home/joel`, on peut accéder à `luge.mp4` grâce au chemin relatif `./images/ski/luge.mp4` : `.` fait référence au répertoire (dossier) **courant**. Il est d'ailleurs facultatif.

Il est courant aussi de vouloir revenir en arrière. Par exemple, si l'on se situe dans le dossier `/home/joel` et que l'on souhaite accéder à `rapport.txt`, on écrit alors `../ellie/documents/rapport.txt` : `..` fait référence au répertoire **parent**.

??? question "Questions 1"
    1. Quel est le chemin absolu pour accéder au fichier `hello.py` ? 
    
    2. On se situe dans le dossier `travail` de ce fichier `hello.py`. Quel est alors le chemin relatif à ce répertoire pour accéder à `photo1.jpg` ? 

## Les commandes de base :material-console:

Découvrons les commandes UNIX les plus courantes grâce à au petit jeu [Terminux](http://luffah.xyz/bidules/Terminus/) ! Prêt pour l'aventure ?

<figure markdown>
[![terminus-light](images/terminus-light.png#only-light){ width=200 .wiggle }](http://luffah.xyz/bidules/Terminus/)
[![terminus-dark ](images/terminus-dark.png#only-dark){ width=200 .wiggle }](http://luffah.xyz/bidules/Terminus/)
</figure>

Dans ce jeu, les différents **lieux** correspondent à des **dossiers** et les différents **objets et personnages** à des **fichiers** !

??? question "Questions 2"
    Au fur et à mesure de l'aventure :

    1. Noter les **commandes** découvertes et leur fonction :

        | Nom de la commande | Description                     | Utilisation                                                              |
        | ------------------ | ------------------------------- | ------------------------------------------------------------------------ |
        | `ls`               | Lister le contenu d'un dossier. | `ls` puis ++enter++ pour lister </br>les fichiers du répertoire courant. |
        | ...                | ...                             | ...                                                                      |

    2. Remplir aussi le tableau des **raccourcis claviers** :

        | Nom de la commande | Description |
        | ------------------ | ----------- |
        | ++up++  ++down++   | ...         |
        | ++tab++            | ...         |

    3. Réaliser le plan du jeu de manière **collaborative** ! 

        ![](images/diagram-light.png#only-light)
        ![](images/diagram-dark.png#only-dark)

        Le lien du diagramme partagé est [disponible ici](https://drive.google.com/file/d/1H8hnVY5u4CxBjOosMU2_zL_8lOb2tAIa/view?usp=sharing). Il faudra alors vous connectez à votre compte Google du lycée @lyceecivray.net et ouvrir le fichier avec l'application Diagrams. Veuillez respecter le **code couleur** (copier-coller simplement les nœuds du diagramme) !

## Compléments sur les commandes

## La gestion des droits et permission d'accès aux fichiers :material-file:


<!-- 
```console
$ cd /home
$ cd /mes_photos
$ cd -
```


++ctrl+r++

++up++


https://betterprogramming.pub/the-most-productive-shell-commands-and-command-line-tricks-ec1415283259

https://www.reddit.com/r/linux/comments/b4khut/basic_linux_commands/ -->