# Les fonctions

:warning: [Activité Capytale à rendre jusqu'au 12 octobre](https://capytale2.ac-paris.fr/web/c/3e70-741354/mlc) :warning:

Une fonction est un bloc d'instruction qui ne s'exécute que lorsqu'il est appelé. Vous pouvez transmettre des données, appelées arguments, à une fonction. Une fonction peut renvoyer des données comme résultat.

Une fonction en programmation est donc semblable au concept de fonctions en mathématiques.

<div style="text-align:center"><img src="../images/fonction.png" /></div>

Vous avez déjà en fait manipuler tout un tas de fonctions : `#!python print`, `#!python input`, `#!python int`, `#!python type` etc.

!!! note "Exemple"
    La fonction `#!python bin` prend un nombre entier (type `#!python int`) comme **argument** et **renvoie** son écriture binaire :

    ``` py
    >>> bin(42)
    '0b101010'
    ```



Une fonction permet donc d'**organiser** son code en le découpant en sous-programmes qui ont une tâche bien précises. Non seulement cela vous permet de réutiliser une fonction à tout moment dans un programme, mais aussi de rendre votre code plus lisible, plus facile à modifier et à corriger.

!!! note "Tester les exemples"
    Lire simplement les programmes ne suffit pas ! Copier le code dans une console Python, sur Pyzo, sur l'IDLE Python, sur un éditeur quelconque... éxecute-le et n'hésitez pas à le modifier pour comprendre ce qu'il se passe !

## Syntaxe

### Créer une fonction

En python, une fonction se crée avec le mot-clef `#!python def` :

``` py
def ma_fonction():
    print('Bonjour depuis une fonction :)')
```

Une fois le code de ma fonction écrit, il ne s'exécute pas directement. Pour cela, il faut explicitement l'appeler !

### Appeler une fonction

Pour appeler une fonction dans le programme, on l'appelle grâce à son nom suivi de sa liste d'arguments entre parenthèses. Ici, la fonction ne demande aucun argument, ni ne renvoie de valeur.


``` py
def ma_fonction():
    print('Bonjour depuis une fonction :)')

ma_fonction()
```

### Passer des arguments

On peut transmettre des données aux fonctions par le biais d'arguments. Les arguments sont spécifiés après le nom de la fonction, à l'intérieur des parenthèses. Vous pouvez ajouter autant d'arguments que vous le souhaitez, il suffit de les séparer par une virgule.


``` py
def saluer_dupont(prenom):
    print(f'Bonjour {prenom} Dupont, ça va ?')

saluer_dupont('Jean')
saluer_dupont('Pierre')
saluer_dupont('Jacques')
```

Ici la fonction `#!python saluer_dupont` capture un argument, une chaîne de caractère, dans une variable que l'on a nommée `#!python prenom`. Lorsque la fonction est appelée, par exemple `#!python saluer_dupont('Jean')`, le paramètre `prenom` prend comme valeur `#!python 'Jean'` et le corps de la fonction est ensuite exécuté. 

!!! note "D'un point de vue sémantique"
    * `prenom` est un **argument** à l'extérieur de la fonction, au moment de son appel. On dit qu'on lui **passe** l'argument.
    
    * `prenom` est un **paramètre** à l'intérieur de la fonction.


On peut passer plusieurs arguments :

``` py
def saluer(prenom, nom):
    print(f'Bonjour {prenom} {nom}, ça va ?')

saluer('Arthur', 'Rouquan')
saluer('Leoš', 'Janáček')
saluer('Cho', 'Chikun')
```

Si vous ne passez qu'un argument, par exemple `#!python saluer('Bob')`, vous aurez droit à une erreur !

### Renvoyer/retourner une valeur

**Renvoyer** une valeur depuis une fonction se fait grâce au mot-clef `#!python return` :

``` py
def double(nombre):
    return nombre * 2

print(double(4))
```

### Syntaxe générale

``` py
def nom_de_la_fonction(argument1, argument2, ...):
    # intructions
    return valeur_renvoyee
```

## Quelques exemples démonstratifs

### Test de parité -- Lisibilité

Pour tester si un nombre est pair, on regarde si le reste de la division de celui-ci par 2 vaut 0. On peut définir une fonction `est_pair` qui nous renvoie `True` si le nombre est pair, `False` sinon :

``` py
def est_pair(nombre):
    return nombre % 2 == 0
```

Ici, on **nomme** explicitement l'intention du code. Ces deux codes sont strictement identiques, mais le dernier est beaucoup plus clair !

``` py
if n % 2 == 0:
    # blabla
```

``` py
if est_pair(n):
    # blabla
```

Qui plus est, il existe une manière plus rapide de tester la parité d'un entier. Sans fonction, s'il faudrait alors modifier chacune des égalités dans le premier cas, dans le second cas il suffirait de modifier juste le corps de la fonction `est_pair`.


### Somme des entiers -- Généricité

Imaginons le programme qui calcule la somme des entiers naturels jusqu'à 1000 :

``` py
s = 0
for i in range(1, 1001):
    s += i
print(s)
```

Transformons-le en une fonction. Un des principes clefs de la programmation est de **généraliser** ses fonctions, de les rendre génériques. Ici, l'objectif est de pouvoir utiliser cette fonction quand on en aura besoin, et éventuellement pour calculer la somme des entiers jusqu'à n'importe quelle valeur $n$, pas nécessairement 1000. Cette valeur $n$ va être le paramètre de la fonction. Et on ne veut plus afficher la somme, mais que cette somme soit renvoyée par la fonction (pour l'affecter à une variable, ou bien pour l'afficher ensuite).

``` py
def somme(n):
    s = 0
    for i in range(1, n + 1):
        s += i
    return s
```

Si l'on exécute :

``` py
>>> somme(42)
903
```

## Quelques subtilités

### Éjecter du code avec `#!python return`

L'emploi du mot-clef `#!python return` provoque une éjection du code : tout ce qui suit cette instruction ne sera pas exécuté.

``` py
def bidon(n):
    if n % 2 == 0:
        print(f'Ce texte est affiché car {n} est pair.')
        return 'Bravo !'
    else:
        return 'Mauvais choix de nombre...'
    print('Ce texte ne sera jamais affiché.')

print(bidon(12))
```

### Respecter l'ordre des arguments

``` py
def repete_lettres(chaine, nombre):
    sortie = ''
    for lettre in chaine:
        sortie += nombre * lettre
    return sortie
```

Il faut alors respecter l'ordre des paramètres lors de l'appel de la fonction :

``` py
>>> repete_lettres('NSI', 3)
'NNNSSSIII'
>>> repete_lettres(3, 'NSI')
Traceback (most recent call last):
File "<pyshell>", line 1, in <module>
File "", line 3, in repete_lettres
    for lettre in chaine:
TypeError: 'int' object is not iterable
```

### La portée des variables

#### Variables locales

Les paramètres d'une fonction, ainsi que les variables déclarées à l'intérieur du corps de la fonction **n'existent que dans le corps de cette fonction**. Il n'est pas possible d'y faire référence depuis une autre instruction, et ce même si la fonction a été appelée.


``` py
def aire_rectangle(longueur, largeur):
    aire = longueur * largeur
    return aire
```

``` py
>>> aire_rectangle(6, 3)
18
>>> longueur
NameError: name 'longueur' is not defined
>>> aire
NameError: name 'aire' is not defined
```

#### Vairables globales

Même si c'est possible, il est fortement recommandé de ne pas utiliser dans le corps d'une fonction des variables définies à l'extérieur de cette fonction. En effet, si plusieurs fonctions agissent sur ces variables, le programme peut aboutir à des valeurs ou des comportements non prévus. On parle alors d'**effet de bord**.

=== "Pas bien"
    ``` py
    a = 5
    def fonction_idiote(n):
        return n + a

    fonction_idiote(1)
    ```

=== "Bien"
    ``` py
    a = 5
    def fonction_idiote(n, m):
        return n + m

    fonction_idiote(1, a)
    ```