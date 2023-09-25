# Les boucles

Une boucle est une structure de contrôle de flot qui permet de répéter un bloc de code.

!!! info "Lien Capytale"
    [:fontawesome-solid-link: Notebook Capytale d7ca-1776728](https://capytale2.ac-paris.fr/web/c/d7ca-1776728) regroupant l'ensemble des exercices introductifs. La correction sera disponible plus tard.

## Boucle non-bornée `#!py while`

Lorsque le nombre de répétitions n'est pas connu à l'avance, la boucle `#!py while` (tant que en anglais) permet de répéter un bloc d'instructions tant qu'une condition est vérifiée (parfois appelée la condition d'arrêt).

```py title="Syntaxe de la boucle while"
while condition:
    instruction1
    instruction2
    ...
```

Tant que `condition` est évaluée à `True`, alors  le bloc indenté est exécutée. La condition est vérifiée en entrée de la boucle, les instructions peuvent être donc totalement ignorées. La condition est réévaluée à la fin du bloc d'instructions indenté.

```py title="Programme"
i = 1
while i < 10:
    print('i a pour valeur', i)
    i *= 2  # Syntaxe abrégée pour x = x * 2
print('Fin', i)  # i vaut 16 à la fin de la boucle !
```
``` title="Sortie"
i a pour valeur 1
i a pour valeur 2
i a pour valeur 4
i a pour valeur 8
Fin 16
```

## Boucle bornée `#!py for`

Si le nombre d'itérations est connue à l'avance, on préférera utiliser dans ce cas la boucle `#!py for` (pour en anglais). Cette boucle permet de parcourir un itérable.

### Itérable

Un itérable désigne un objet qui est décomposable en une suite d'éléments individuels. Quelques exemples concrets :

* La chaîne de caractère `#!py 'chat'` est un itérable car on peut le décomposer comme une suite de caractères : `#!py 'c'`, `#!py 'h'`, `#!py 'a'` et `#!py 't'`.

* Le tableau `#!py [4, 3, 17]` est aussi un itérable car on peut le décomposer comme une suite de nombres : `#!py 4`, `#!py 3` et `#!py 17`.

* En revanche, le nombre `#!python 42` n'est pas un itérable car il ne peut être décomposé.

### Syntaxe et exemples

La boucle `#!py for` permet de parcourir un itérable pour manipuler séparément ces éléments individuels.

```py title="Syntaxe de la boucle for"
for i in itérable:
    instruction1
    instruction2
    ...
```

On dit la variable d'itération `variable` parcourt `itérable`, elle va capturer chaque élément de l'itérable à chaque tour de boucle.

=== "Chaîne de caractères"
    ```py title="Programme"
    for caractère in 'chat':
        print(caractère)
    ```
    ``` title="Sortie"
    c
    h
    a
    t
    ```
=== "Tableau d'entiers"
    ```py title="Programme"
    for valeur in [1, 5, 17]:
        print(valeur)
    ```
    ``` title="Sortie"
    1
    5
    17
    ```
=== "Range"
    ```py title="Programme"
    for i in range(5):
        print(i)
    ```
    ``` title="Sortie"
    0
    1
    2
    3
    4
    ```

=== "Sans utilisation de la variable d'itération"
    ```py title="Programme"
    for jenesersarien in [1, 5, 17]:
        print('OK')
    ```
    ``` title="Sortie"
    OK
    OK
    OK
    ```


### Précisions sur `#!python range`

Il est fréquent d'énumérer une suite de nombres entiers consécutifs. Avec une boucle `#!python while` :

``` py
i = 0
while i < 10:
    print(i)
    i += 1
```

Avec la boucle `#!python for`, on arrive au même résultat en itérant un tableau :

``` py
for i in [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]:
    print(i)
```

En plus d'être extrêmement pénible à écrire, ce code est peu générique. Heureusement, `#!python range` (intervalle en anglais) permet de générer facilement une suite d'entiers consécutifs :

``` py
for i in range(10):
    print(i)
```

`#!python range(start, stop, step)` génère une suite d'entiers consécutifs en partant de `#!python start` (inclus) jusqu'à `#!python stop` (exclus), en incrémentant de `#!python step` (*pas* en anglais).

* `#!python start` est facultatif et vaut 0 par défaut.

* `#!python step` est facultatif et vaut 1 par défaut. Mais si on veut préciser `#!python step`, alors il faut donner aussi `#!python start`, même si sa valeur est 0.

??? info "Un générateur"
    On peut convertir un objet de type `#!python range` vers un tableau (`#!python list`) :

    ``` py
    >>> range(10)
    range(0, 10)
    >>> list(range(5))
    [0, 1, 2, 3, 4]
    >>> list(range(1, 20 , 3))
    [1, 4, 7, 10, 13, 16, 19]
    ```

    `#!python range` va en fait générer ces valeurs à la volée, on évite ainsi de stocker tout un tableau en mémoire. On parle aussi du concept plus général de **lazy evaluation** en anglais, ou évaluation paresseuse : on ne génère le nombre qu'à la demande de celui-ci.