# Les valeurs booléennes

## Un peu d'histoire

**George Boole** (1815-1864) est un mathématicien et logicien britannique connu pour avoir créé la logique moderne, appelée **algèbre de Boole**.

Cette algèbre binaire n'accepte que deux valeurs, Vrai ou Faux, 0 et 1, et a donc d'importantes et nombreuses applications en informatique.

## Introduction

Pour rappel, en mathématiques, une **proposition** est une phrase qui est soit **vraie**, soit **fausse**. Par exemple, la proposition "1 plus 1 égal 11" est fausse, tandis que la proposition "7 plus 2 égal 9" est vraie. Pas les deux à la fois, c'est le principe du **tiers-exclus**.

Par exemple, que diriez-vous de ces phrases ?

* A : Vous êtes en classe de première.

* B : Antoine de Saint-Exupéry a écrit *Le Petit Prince*.

* C : La Terre est plate.

* D : $3 \cdot 4 = 12$.

* E : La lettre `#!python 'e'` est dans le mot `#!python 'abracadabra'`.

* F : Georges Perec a écrit un roman de près de 300 pages sans aucune lettre e.

* G : $2^{10} < 10^3$.

* H : La couleur orange est la plus belle des couleurs.

* I : Dieu existe.

## Algèbre de Boole

### Les booléens

L'algèbre de Boole consiste à étudier des opérations sur un ensemble uniquement constitué de deux éléments qu'on appelle **booléens**. Selon le contexte, ces deux élements sont notés :

* Faux / Vrai

* 0 / 1

*  `#!python False` / `#!python True` en Python

* :x: / :white_check_mark:

* etc.

### Les opérateurs logiques

Les opérations fondamentales sur cet ensemble de valeurs sont les opératations logiques (l'opération d'addition ou de multiplication ne fait pas sens ici). En posant $x$ et $y$ deux booléens, on a les opérations suivantes :

* La **négation**, que l'on note $\bar{x}$, ou plus simplement "NON x", `#!python not x` en Python.

* La **conjonction**, que l'on note $x \land  y$, ou plus simplement "x ET y", `#!python x and y` en Python.

* La **disjonction**, que l'on note $x \lor  y$, ou plus simplement "x OU y", `#!python x or y` en Python

Le résultat de ces opérateurs entre booléens est un booléen. On peut définir une **table de vérité** pour définir toutes les possibilités :

=== "Négation (NON)"
    | $x$ | $\bar x$ |
    | :---: | :---: |
    | :x: | :white_check_mark: |
    | :white_check_mark: | :x: |

    Ainsi, par exemple en Python :

    ``` py
    >>> not False
    True
    >>> not True
    False
    ```

=== "Conjonction (ET)"
    | $x$ | $y$ | $x \land y$ |
    | :---: | :---: | :---: |
    | :x: | :x: | :x: | 
    | :x: | :white_check_mark: | :x: | 
    | :white_check_mark: | :x: | :x: | 
    | :white_check_mark: | :white_check_mark: | :white_check_mark: |

    Ainsi, par exemple en Python :

    ``` py
    >>> True and False
    False
    >>> True and True
    True
    ```


=== "Conjonction (OU)"
    | $x$ | $y$ | $x \lor y$ |
    | :---: | :---: | :---: |
    | :x: | :x: | :x: | 
    | :x: | :white_check_mark: | :white_check_mark: | 
    | :white_check_mark: | :x: | :white_check_mark: | 
    | :white_check_mark: | :white_check_mark: | :white_check_mark: |

    Ainsi, par exemple en Python :

    ``` py
    >>> True and False
    True
    >>> True and True
    True
    ```

## Python

### Type `#!python bool` et opérateurs de comparaison

On rappelle qu'il existe un type booléen en Python `#!python bool`. Une variable de ce type ne peut prendre que deux valeurs, soit `#!python False` soit `#!python True`.

``` py
>>> type(True)
<class 'bool'>
>>> x = False
>>> x
False
>>> type(x)
<class 'bool'>
```

| Opérateur | Signification | Symbole mathématiques | 
| --- | :--- | --- |
| `#!python ==` | "est égale à" | $=$ |
| `#!python !=` | "est différent de" | $\ne$ |
| `#!python <` | "est inférieur à" | $<$ |
| `#!python <=` | "est inférieur ou égale à" | $\leq$ |
| `#!python >` | "est supérieur à" | $>$ |
| `#!python >=` | "est supérieur ou égale à" | $\geq$ |

On peut aussi rajouter l'opérateur d'appartenance `#!python in` qui renvoie un booléen :

| Opérateur | Signification | Symbole mathématiques | 
| --- | :--- | --- |
| `#!python in` | "appartient à" | $\in$ |
| `#!python not in` | "n'appartient pas à" | $\notin$ |

### Exemples

``` py
>>> a = 2
>>> a == 3
False
>>> a == 2
True
>>> a != 1
True
>>> a > 2
False
>>> a <= 5
True
>>> a % 2 == 0
True
>>> x = (0 == 1)
>>> x
False
>>> y = (3 + 2 == 5)
>>> y
True
>>> 'e' in 'abracadabra'
False
>>> 'b' in 'abracadabra'
True
>>> 'A' not in 'abracadabra'
True
>>> not True
False
>>> True and False
False
>>> True and True
True
>>> False or True
True
```

## Exercices

!!! exemple "Exercice 1 - Savoir évaluer"
    Prédire si les variables suivantes contiennent le booléen `True` ou le booléen `False` :

    ``` py
    a = (2 > 1)
    b = (3 == 1+2)
    c = (1 < 0)
    d = (2 != 5/2)
    e = (2 != 5//2)
    f = ('a' == 'A')
    g = not a
    h = b and c
    i = b or c
    j = not c and (d or e)
    ```

!!! exemple "Exercice 2 - Une table pour les gouverner tous"

    Construire la table de vérité de l'expression $(x \lor y) \land z$ où $x$, $y$ et $z$ sont trois booléens.


!!! exemple "Exercice 3 - Une formule mathématique en algèbre de Boole"

    À l'aide de tables de vérité, démontrer **les lois de De Morgan** :

    * $\overline{x \lor y} = \overline{x} \land \overline{y}$

    * $\overline{x \land y} = \overline{x} \lor \overline{y}$

    

!!! exemple "Exercice 4 - Ou Exclusif"
    Une autre opération logique importante est le **ou exclusif**, ou **disjonction exclusive**.

    C'est le sens du mot "ou" dans le langage commun. Quand on vous demande "Fromage *ou* dessert ?", c'est soit l'un, soit l'autre. Pas les deux? On note l'opérateur $\oplus$, ou `xor`. En Python, il se note `^`.
    
    Voici sa table de vérité :

    | $x$ | $y$ | $x \oplus y$ |
    | :---: | :---: | :---: |
    | :x: | :x: | :x: | 
    | :x: | :white_check_mark: | :white_check_mark: | 
    | :white_check_mark: | :x: | :white_check_mark: | 
    | :white_check_mark: | :white_check_mark: | :x: |

    * Qu'est-ce qui change par rapport à la table de vérité du ou logique ?

    * Sauriez-vous écrire $x \oplus y$ en fonctions des trois opérateurs logiques de base ?

<!-- !!! exemple "Exercice 5 - Notre premier circuit logique"

    Grâce aux transistors, on peut réaliser ce qu'on appelle des **portes logiques**, c'est-à-dire des circuits électroniques qui permettent de manipuler le courant suivant l'algèbre de Boole. 

    ![](./images/gates.jpg)

     -->