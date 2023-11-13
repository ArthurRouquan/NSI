# Introduction aux tableaux

!!! info "Liens Capytale"
    * Exercices : [:fontawesome-solid-link: Notebook Capytale 132b-2248053](https://capytale2.ac-paris.fr/web/c/132b-2248053)
    * Correction : Disponible plus tard !

## Limitations actuelles

Imaginons que vous ayez besoin de calculer la moyenne de 100 notes saisies par l'utilisateur. Actuellement, la seule option à votre disposition serait de réaliser 100 opérations `#!py input()` pour affecter les notes à 100 variables distinctes, puis de calculer la moyenne à partir de celles-ci. Cela serait clairement laborieux, d'où l'importance du concept de **tableau**.

## Définition

* Un **tableau** est une séquence ordonnée de valeurs de même type. Il peut se voir comme une séquence de « plusieurs variables ». 

<figure markdown>
![](ressources/tab-light.png#only-light){ width=400px }
![](ressources/tab-dark.png#only-dark){ width=400px }
<figcaption>Représentation usuelle d'un tableau de 6 entiers.</figcaption>
</figure>

* Les valeurs d'un tableau sont appelées **éléments** et sont accessibles par le biais de leur **indice**, c'est-à-dire leur position dans le tableau.

<figure markdown>
![](ressources/tab2-light.png#only-light){ width=400px }
![](ressources/tab2-dark.png#only-dark){ width=400px }
<figcaption>Il est important de noter que l'indice de départ est 0.</figcaption>
</figure>

* Pour un tableau `tab`, `tab[i]` désigne l'élément d'indice `i` du tableau `tab`. Sur l'exemple, `tab[3]` correspond à l'élément `42`.

* La **taille** ou **longueur** d'un tableau est le nombre d'éléments qu'il contient.

## Les tableaux en Python

* En Python, un tableau est de type `#!py list`. Un tableau est définit avec des crochets et on sépare ses éléments par des virgules. Par abus de langage, on parle parfois de liste plutôt que de tableau.

    ```py title="Création explicite d'un tableau"
    >>> tab = [4, 2, 1, 42, 78, 12]
    >>> type(tab)
    <class 'list'>
    >>> tab[3]
    42
    ```

* Il est possible de récupérer la longueur d'un tableau avec la fonction `#!py len` (de l'anglais *length*, longueur). À noter que cette fonction marche sur n'importe quel itérable, notamment les chaînes de caractères !
    ```py
    >>> len(tab)
    6
    >>> len("chat")
    4
    ```

??? question "Exercice 1"
    Sur une console Python, exécuter les instructions suivantes :
    
    ```py
    >>> tab = [4, 2, 1, 42, 78, 12]
    >>> len(tab)
    >>> tab[5]
    >>> tab[6]
    >>> tab[-1]
    >>> tab[-2]
    ```

    1. Pourquoi la 4ème instruction échoue ?
    2. Exprimer le dernier indice d'un tableau `tab` quelconque en fonction de `#!py len(tab)`.
    3. Surprenamment, Python supporte aussi les indices négatifs. Dans un tableau quelconque, quel élément est à l'indice `-1` ? Et `-2` ? Conclure.

## Modifier un tableau

En python, les tableaux `#!py list` sont modifiables – ou plutôt **mutables** – après leur initialisation.

### Modifier un élément à un indice particulier

Un tableau est semblable à une séquence de variables repérées par leurs indices. Il n'est pas surprenant de pouvoir modifier un élément du tableau grâce à une affectation :

```py
>>> famille = ["Bart", "Lisa", "Maggie"]
>>> famille[0] = "Bartholomew"
>>> famille
['Bartholomew', 'Lisa', 'Maggie']   
```

### Ajouter un élément en fin de liste

La méthode `append` (*ajouter* en anglais) permet d'ajouter un élément en fin de tableau. Ceci incrémente évidemment la taille du tableau :

```py
>>> famille = ["Bart", "Lisa", "Maggie"]
>>> famille.append("Homer")
>>> famille
['Bartholomew', 'Lisa', 'Maggie', 'Homer']
```

??? note "Une méthode ?"
    * Si `append` était une fonction classique, on aurait plutôt écrit `#!py append(tableau, nouvel_élément)`. Or `append` est une fonction *spécifique* aux objets de type `#!py list`. Ainsi, on appelle cette fonction – ou plutôt cette méthode – comme `#!py tableau.append(nouvel_élément)`.
    
    * Si ce genre de notation apparaîtra tout au long de l'année, il faudra attendre le programme de terminale pour la comprendre véritablement. 

### Supprimer un élément

* La méthode `remove` permet de supprimer la première occurrence (la première apparition) de l'élément (et seulement la première). À condition bien entendu que l'élément soit dans le tableau.

    ```py
    >>> matieres = ["nsi", "maths", "anglais", "français", "maths"]
    >>> matieres.remove("maths")
    >>> matieres
    ["nsi", "anglais", "français", "maths"]
    >>> matieres.remove("espagnol")
    Traceback (most recent call last):
    File "<pyshell>", line 1, in <module>
    ValueError: list.remove(x): x not in list
    ```

* La méthode `pop` permet de supprimer un élément à un indice précis.

    ```py
    >>> matieres = ["nsi", "maths", "anglais", "français", "maths"]
    >>> matieres.pop(4)
    >>> matieres
    ["nsi", "maths", "anglais", "français"]
    ```

??? question "Exercice 2"
    Dans la liste suivante :

    * Remplacer `#!py "Loki"` par `#!py "Thor"`
    * Ajouter `#!py "Dr. Strange"`
    * Supprimer l'intrus

    ```py
    avengers = ["Black Widow", "Captain America", "Loki", "Iron Man", "Hulk", "Batman", "Hawkeye"]
    ```

## Parcourir un tableau

Imaginons que vous vouliez déterminer la somme des nombres contenus dans un tableau. Il sera alors nécessaire de regarder un à un tous les éléments que contient ce tableau. On dit qu'on **parcourt** le tableau. Il existe deux manières de parcourir un tableau :

* Le parcours par **éléments**
  
* Le parcours par **indices**

Dans les deux cas, on utilisera une boucle `#!py for`.

### Parcours par éléments

Comme vu dans le chapitre sur la boucle `#!py for`, un tableau est un **itérable**, c'est-à-dire qu'on peut le décomposer comme la suite de ses éléments :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
    ``` {.py3 .no-copy title="Script - Parcours par éléments"} 
    famille = ["Bart", "Lisa", "Maggie"]
    for membre in famille:
        print(membre)
    ```

    ```{.pycon .no-copy title="Sortie"} 
    Bart
    Lisa
    Maggie
    ```
</div>


### Parcours par indices

* Le premier indice d'un tableau est `#!py 0` et son dernier indice est `#!py len(tab) - 1`. L'idée est de générer la séquence des indices `#!py 0`, `#!py 1`, `#!py 2`, ..., `#!py len(tab) - 1` grâce à `#!py range` :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
    ``` {.py3 .no-copy title="Script - Parcours par indices"} 
    famille = ["Bart", "Lisa", "Maggie"]
    for i in range(len(famille)):
        print(i, famille[i])
    ```

    ```{.pycon .no-copy title="Sortie"} 
    0 Bart
    1 Lisa
    2 Maggie
    ```
</div>

### Différence entre les parcours

* Le parcours par indices est donc plus **général** que le parcours par éléments. On parcourt par indices si on a besoin de l'indice dans le corps de la boucle. 

* Le parcours par indices est aussi plus **flexible** que le parcours par éléments : il permet par exemple de parcourir qu'une tranche du tableau, parcourir le tableau à l'envers, parcourir deux tableaux en même temps etc.

* ⚠️ Le parcours par éléments ne permet pas de modifier les éléments d'un tableau ! Un parcours par indice le peut.

??? question "Exercice 3"
    Trouvez le nombre qui est exactement à la même place dans la liste `list1` et dans la liste `list2`, sachant que :

    * Les deux listes ont la même taille.
    
    * Vous n'avez droit qu'à une seule boucle `#!py for`.

    ```py
    list1 = [8468, 4560, 3941, 3328, 7, 9910, 9208, 8400, 6502, 1076, 5921, 6720, 948, 9561, 7391, 7745, 9007, 9707, 4370, 9636, 5265, 2638, 8919, 7814, 5142, 1060, 6971, 4065, 4629, 4490, 2480, 9180, 5623, 6600, 1764, 9846, 7605, 8271, 4681, 2818, 832, 5280, 3170, 8965, 4332, 3198, 9454, 2025, 2373, 4067]
    list2 = [9093, 2559, 9664, 8075, 4525, 5847, 67, 8932, 5049, 5241, 5886, 1393, 9413, 8872, 2560, 4636, 9004, 7586, 1461, 350, 2627, 2187, 7778, 8933, 351, 7097, 356, 4110, 1393, 4864, 1088, 3904, 5623, 8040, 7273, 1114, 4394, 4108, 7123, 8001, 5715, 7215, 7460, 5829, 9513, 1256, 4052, 1585, 1608, 3941]
    ```

??? question "Exercice 4"
    Écrire la fonction `recherche`, prenant en paramètre un tableau non vide `tab` d'entiers et un entier `n`, et qui renvoie l'indice de la dernière occurrence (apparition) de l'élément cherché. Si l'élément n'est pas présent, la fonction renvoie la longueur du tableau. Exemples :

    ```py
    >>> recherche([5, 3], 1)
    2
    >>> recherche([2, 4], 2)
    0
    >>> recherche([2, 3, 5, 2, 4], 2)
    3
    ```



## Créer un tableau

### Initialisation explicite
  
```py
tab = [11, 19, 21, 29, 46]
```

### Éléments identiques

Il est souvent pratique d'initialiser un tableau de taille donnée en la remplissant de la même valeur. Par exemple, pour initialiser un tableau contenant 26 zéros :

```py
>>> tab = [0] * 26
>>> tab
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

??? question "Exercice 5"
    Construire une liste de 100 éléments tous égaux à 0. Puis remplacer tous les éléments d'indice impair par des 1.

### Avec une boucle `#!py for`

* On crée un tableau vide, puis on lui ajoute (`#!py append`) les éléments au fur et à mesure grâce à une boucle `#!py for`. Par exemple, pour générer la séquence des 10 premiers carrés :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
    ```{.py3 .no-copy title="Script"} 
    carrés = []
    for i in range(10):
        carrés.append(i * i)
    print(carrés)
    ```

    ```{.pycon .no-copy title="Sortie"} 
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    ```
</div>


* Le corps de la boucle peut être bien plus complexe ! Par exemple, la création d'un tableau contenant les entiers multiples de 3 et 7 inférieurs à 100 :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
    ```{.py3 .no-copy title="Script"} 
    multiples = []
    for i in range(101):
        if i % 3 == 0 and i % 7 == 0:
            multiples.append(i)
    print(multiples)
    ```

    ```{.pycon .no-copy title="Sortie"} 
    [0, 21, 42, 63, 84]
    ```
</div>

??? question "Exercice 6"
    On considère le tableau suivant :
    ```py
    tab = [11, 28, -16, -18, -10, 16, 10, 16, 2, 7, 23, 22, -4, -2, 19, 16, 22, -8, 18, -14, 29, -1, 16, 22, -5, 6, 2, -4, 9, -17, -13, 22, 14, 24, 22, -9, -18, -9, 25, -11, 17, 17, 25, -10, 2, -18, 29, 14, -16, 7]
    ```
    Construire la liste `tab_positif` qui ne contient que les éléments positifs de `tab`.
    <div></div>



### Liste en compréhension

#### Syntaxe de base

Cette dernière méthode de création de listes permet d'écrire moins de lignes de code, on parle de « sucre syntaxique » en programmation. La syntaxe la plus simple est :

```py
tableau = [expression for élément in itérable]
```

En reprenant l'exemple précédent :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
```{.py3 .no-copy title="Création classique"} 
carrés = []
for i in range(10):
    carrés.append(i * i)
```

```{.py3 .no-copy title="Liste en compréhension"} 
carrés = [i * i for i in range(10)]
```
</div>

L'idée est de « glisser la boucle `#!py for` entre les crochets ». 

??? tip "No limit"
    * `itérable` correspond à un itérable, cela peut être une séquence d'entiers `#!py range`, une chaîne de caractères, un autre tableau etc.

    * `expression` peut faire appel à une fonction si elle est trop complexe à écrire en un seul calcul.

#### Syntaxe avec filtre

La syntaxe d'une liste en compréhension avec filtre :

```py
tableau = [expression for élément in itérable if condition]
```

En reprenant l'exemple précédent (simplifié) :

<div style="display:flex; justify-content: center; align-items: center; gap: 10px;">
```{.py3 .no-copy title="Création classique"} 
multiples = []
for i in range(101):
    if i % 7 == 0:
        multiples.append(i)
```

```{.py3 .no-copy title="Liste en compréhension"} 
multiples = [i for i in range(101) if i % 7 == 0]
```
</div>

## Exercices

Répondre aux exercices restant sur le notebook Capytale, bon courage ! 👌