# Des mini-jeux !

Deux mini-jeux à programmer sur Thonny, le jeu du Plus ou Moins et le jeu des allumettes ! Les deux mini-jeux seront à rendre. Sur 20 points :

* 5 points pour chaque code de base complété.
     
* Des points supplémentaires suivant les améliorations apportées. 

## Prérequis

??? tip "Tirer un nombre aléatoire"
    En programmation, une **bibliothèque** est une collection de fonctions prêtes à l'emploi. Par exemple, la bibliothèque nommée `random` (*aléatoire* en anglais) regroupe des fonctions pour générer des nombres pseudo-aléatoires. En l’occurrence, la fonction `randint` (*random integer*, *entier aléatoire*) de cette bibliothèque permet de tirer aléatoirement un entier entre deux bornes : 

    ```py
    import random  # on importe la bibliothèque random pour utiliser ses fonctions

    valeur = random.randint(1, 6)  # la variable reçoit un nombre aléatoire entre 1 et 6 (inclus)
    ```

    Pour éviter d'écrire le nom de la bibliothèque à chaque appel, on peut importer spécifiquement `randint` de cette manière :

    ```py
    from random import randint  # depuis random importer randint
    
    valeur = randint(1, 6)
    ```

    Ou importer toutes les fonctions de la bibliothèque :

    ```py
    from random import *  # l'étoile veut dire « tout »
    
    valeur = randint(1, 6)
    ```

    Il est généralement recommandé d'utiliser `#!py import nom_de_la_bibliothèque` afin d'éviter d'éventuels conflits. En effet, il peut arriver que deux bibliothèques aient des fonctions portant le même nom, ce qui pourrait causer des problèmes.


## Le jeu du Plus ou Moins

### Description

1. Le programme détermine un nombre mystère aléatoire entre 1 et 100.
2. Le joueur doit deviner ce nombre en proposant des valeurs.
3. Après chaque proposition, le programme indique si la valeur donnée par le joueur est plus petite ou plus grande que le nombre à deviner.

```title="Exemple de jeu"
Bienvenue au jeu du Plus ou Moins !
Le nombre mystère entre 1 et 100 a été tiré !

Devine le nombre ? 30
C'est plus !

Devine le nombre ? 70
C'est moins !

Devine le nombre ? 42
Félicitations ! Tu as deviné le nombre 42 !
```

```py title="Code à compléter"
print("Bienvenue au jeu du Plus ou Moins !")

nombre_mystère = ...
print("Le nombre mystère entre 1 et 100 a été tiré !")

continuer = True
while continuer:
    proposition = ...

    if proposition < ...:
        print(...)
    elif ...:
        print(...)
    else:
        print(...)
        continuer = False

print("Fin du jeu")
```

### Améliorations

* Le joueur a un nombre limité d'essais pour deviner le nombre, par exemple 5. (1 point)

* Le programme propose une nouvelle partie au joueur (déplacer la boucle de jeu dans une fonction !). (1 point)

* Le programme affiche le nombre de coups du joueur. (1 point)

* Le programme conserve le meilleur score et le nom du joueur. (1 point)

* Le programme dispose de trois niveaux de difficulté : (1 point)
  
    * Facile : 5 coups pour déterminer un nombre entre 1 et 100.
  
    * Intermédiaire : 9 coups pour déterminer un nombre entre 1 et 1000.
  
    * Difficile : 16 coups pour déterminer un nombre entre 1 et 10000.



## Le jeu des allumettes

### Description

1. Le jeu commence avec un certain nombre d'allumettes, par exemple 21.
2. Les joueurs humains jouent à tour de rôle.
3. À chaque tour, un joueur peut prendre 1, 2 ou 3 allumettes.
4. Le joueur qui prend la dernière allumette perd la partie.

```title="Exemple"
Tour du joueur 1
Il reste 21 allumettes.
Combien d'allumettes voulez-vous retirer (1 à 3) ? 3

Tour du joueur 2
Il reste 18 allumettes.
Combien d'allumettes voulez-vous retirer (1 à 3) ? 4
Choix invalide. Veuillez choisir 1 à 3 allumettes.
Combien d'allumettes voulez-vous retirer (1 à 3) ? 2

Tour du joueur 1
Il reste 16 allumettes.
Combien d'allumettes voulez-vous retirer (1 à 3) ?
```

```py title="Code à compléter"
def demander_allumettes(allumettes_restantes, joueur):
    """ Demande à l'utilisateur un nombre d'allumettes à retirer,
    jusqu'à que ce que ce nombre soit valide. """
    while True:
        choix = int(input("Combien d'allumettes voulez-vous prendre (1 à 3) ? "))
        if ...:
            print("Choix invalide. Veuillez choisir 1 à 3 allumettes.")
        elif ...:
            print("Choix invalide. Il n'y a pas assez d'allumettes à retirer.")
        else:
            return ...


def jeu_allumettes():
    """ Joue au jeu des allumettes. """
    allumettes_restantes = 21
    joueur = 1

    # boucle de jeu
    while ...:
        print(...)
        print(...)

        choix = ...
        allumettes_restantes = ...

        # change le joueur courant
        if ...:
            joueur = ...
        else:
            joueur = ...

    # fin du jeu, un des joueurs à gagner
    ...


jeu_allumettes()
```

### Améliorations

* Afficher les allumettes restantes de manière plus élégante : (1 point)
    ```
    Il reste 16 allumettes :
        ┃┃┃┃┃┃┃┃┃┃┃┃┃┃┃┃
    ```
* Le programme dispose d'un mode « Combat contre l'ordinateur » : l'ordinateur est bête et retire un nombre aléatoire d'allumettes. (2 points)
* Améliorer cette intelligence artificielle pour que l'ordinateur donne le coup optimal si le nombre d'allumettes est inférieur ou égal à 4. (2 points)


