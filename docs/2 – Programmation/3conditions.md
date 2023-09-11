---
header-includes: 
                 \usepackage{xcolor}
                 \definecolor{alizarin}{rgb}{0.82, 0.1, 0.26}
---

# Les conditions

Les structures conditionnelles permettent d'exécuter des blocs de code spécifiques suivant le résultat d'une condition.

## Écrire une condition

### Opérateurs de comparaison et d'appartenance

Ces opérateurs renvoient une valeur **booléenne** : `#!py True` ou `#!py False`.

| Opérateurs de comparaison | Signification       | Exemple           | Résultat         |
| ------------------------- | ------------------- | ----------------- | ---------------- |
| `#!python ==`             | égal à              | `#!python 1 == 1` | `#!python True`  |
| `#!python !=`             | différent de        | `#!python 1 != 1` | `#!python False` |
| `#!python >`              | supérieur à         | `#!python 2 > 0`  | `#!python True`  |
| `#!python >=`             | supérieur ou égal à | `#!python 4 >= 6` | `#!python False` |
| `#!python <`              | inférieur à         | `#!python 5 < 5`  | `#!python False` |
| `#!python <=`             | inférieur ou égal à | `#!python 5 <= 5` | `#!python True`  |


| Opérateur d'appartenance       | Signification                 | Exemple                  | Résultat        |
| ------------------------------ | ----------------------------- | ------------------------ | --------------- |
| `#!python élément in itérable` | `élément` est dans `itérable` | `#!python "t" in "chat"` | `#!python True` |

### Opérateurs logiques

Les opérateurs logiques permettent de **combiner** des conditions. Ils fonctionnent
entre deux booléens.

| Opérateurs logiques | Signification   | Exemple                   | Résultat         |
| ------------------- | --------------- | ------------------------- | ---------------- |
| `#!python not`      | **non** logique | `#!python not True`       | `#!python False` |
| `#!python and`      | **et** logique  | `#!python False and True` | `#!python False` |
| `#!python or`       | **ou** logique  | `#!python False or True`  | `#!python True`  |

Les tables de vérité suivantes caractérisent entièrement ces opérateurs :

=== "Opérateur `#!py not`"
    | `x`                               | `#!py not x`                      |
    | --------------------------------- | --------------------------------- |
    | $\color{#EF5350}{\texttt{False}}$ | $\color{#66BB6A}{\texttt{True}}$  |
    | $\color{#66BB6A}{\texttt{True}}$  | $\color{#EF5350}{\texttt{False}}$ |

=== "Opérateur `#!py and`"
    | `x`                               | `y`                               | `#!py x and y`                    |
    | --------------------------------- | --------------------------------- | --------------------------------- |
    | $\color{#EF5350}{\texttt{False}}$ | $\color{#EF5350}{\texttt{False}}$ | $\color{#EF5350}{\texttt{False}}$ |
    | $\color{#EF5350}{\texttt{False}}$ | $\color{#66BB6A}{\texttt{True}}$  | $\color{#EF5350}{\texttt{False}}$ |
    | $\color{#66BB6A}{\texttt{True}}$  | $\color{#EF5350}{\texttt{False}}$ | $\color{#EF5350}{\texttt{False}}$ |
    | $\color{#66BB6A}{\texttt{True}}$  | $\color{#66BB6A}{\texttt{True}}$  | $\color{#66BB6A}{\texttt{True}}$  |

=== "Opérateur `#!py or`"
    | `x`                               | `y`                               | `#!py x or y`                     |
    | --------------------------------- | --------------------------------- | --------------------------------- |
    | $\color{#EF5350}{\texttt{False}}$ | $\color{#EF5350}{\texttt{False}}$ | $\color{#EF5350}{\texttt{False}}$ |
    | $\color{#EF5350}{\texttt{False}}$ | $\color{#66BB6A}{\texttt{True}}$  | $\color{#66BB6A}{\texttt{True}}$  |
    | $\color{#66BB6A}{\texttt{True}}$  | $\color{#EF5350}{\texttt{False}}$ | $\color{#66BB6A}{\texttt{True}}$  |
    | $\color{#66BB6A}{\texttt{True}}$  | $\color{#66BB6A}{\texttt{True}}$  | $\color{#66BB6A}{\texttt{True}}$  |




## La clause `#!py if`

La clause `#!py if` (si) permet d’exécuter des instructions si une condition est respectée.

```py
if condition:
    instruction1
    instruction2
    ...
```

Si `condition` s'évalue à `#!py True` (vrai), alors la suite d'instructions indentées sera exécutée. Sinon `condition` s'évalue à `#!py False` (faux) et ce bloc sera ignoré.

## La clause `#!py else`

La clause `#!py else` (sinon) permet d’exécuter des instructions si une condition n'est pas respectée (toujours à la suite de `#!py if`).

```py title="Exemple d'utilisation de la clause else"
âge = int(input("Votre âge ? "))
if âge >= 18:
    print("Vous êtes majeur.")
else:
    print("Vous êtes mineur.")
print("Merci au revoir !")
```

## La clause `#!py elif`

En python, `#!py elif` (sinon si) est la contraction de `!py else` et `!py if`, il permet de **chaîner** facilement des conditions.

```py title="Exemple d'utilisation de la clause elif"
âge = int(input("Votre âge ? "))
if âge >= 70:
    print("Vous êtes une personne âgée.")
elif âge >= 18:
    print("Vous êtes un adulte.")
elif âge >= 12:
    print("Vous êtes un adolescent.")
else:
    print("Vous êtes un enfant.")
```