# Types, valeurs et variables

## :fontawesome-solid-shapes: Types et valeurs

### Définition et exemples

Les **valeurs** manipulées par un programme sont caractérisées par leur **type**.

| Type             | Terme anglais | Signification                | Exemples de valeur                            |
| ---------------- | ------------- | ---------------------------- | --------------------------------------------- |
| `#!python int  ` | integer       | Nombre entier                | `#!python 45` `#!python -255` `#!python 1998` |
| `#!python float` | float         | Nombre décimal (ou flottant) | `#!python 3.1412` `#!python -1.14152`         |
| `#!python str  ` | string        | Chaîne de caractères (texte) | `#!python "Bonjour"` `#!python "42"`          |
| `#!python bool ` | boolean       | Booléen                      | `#!python True` `#!python False`              |

### Conversion entre types

Pour convertir une valeur vers un autre type, si cela a du sens, on utilise les fonctions `#!python int`,
`#!python float`, `#!python str` ou `#!python bool` :

```py
>>> int(17.6)  # float ► int
17
>>> int("42")  # str   ► int
42
>>> str(3.14)  # float ► str
"3.14"
```

### Opérateurs arithmétiques

#### Entre deux valeurs arithmétiques (`#!python int` ou `#!python float`)

| Opérateur Arithmétique | Signification                              | Exemple              | Résultat        |
| ---------------------- | ------------------------------------------ | -------------------- | --------------- |
| `#!python +`           | Addition                                   | `#!python 10 + 3`    | `#!python 13`   |
| `#!python -`           | Soustraction                               | `#!python 42 - 10.5` | `#!python 31.5` |
| `#!python *`           | Multiplication                             | `#!python 7 * 8`     | `#!python 56`   |
| `#!python /`           | Division                                   | `#!python 13 / 5`    | `#!python 2.6`  |
| `#!python //`          | Division entière                           | `#!python 13 // 5`   | `#!python 2`    |
| `#!python %`           | Reste dans la division entière (ou modulo) | `#!python 13 % 5`    | `#!python 3`    |
| `#!python **`          | Puissance                                  | `#!python 4 ** 3`    | `#!python 64`   |

Les calculs suivent la priorité usuelle des opérateurs.

```py title="Syntaxe abrégée"
x += 10  # équivalent à x = x + 10
x *= 2   # équivalent à x = x * 2
x //= 2  # équivalent à x = x // 2
# etc.
```


#### Entre d'autres types

Les opérateurs arithmétiques ont un sens différent suivant le type de valeurs manipulées.
Par exemple, on peut utiliser des chaînes de caractères :

```py
>>> "Oui" + "Non"  # concaténation
'OuiNon'
>>> "Oui" * 3
'OuiOuiOui'
```

C'est tout l'intérêt d'avoir différents types, la machine les traite différemment.

## :fontawesome-solid-box: Variables

### Affectation et substitution 

Une variable permet de **stocker** une valeur (de n’importe quel type) et est identifiée par un **nom**. Lors de l’évaluation d’une expression, le nom d’une variable est **substitué** par sa valeur.

```py
>>> toto = 42  # affection
>>> toto = 56  # une nouvelle affectation écrase l'ancienne valeur
>>> toto + 3   # substitution
45
```

Lorsqu’on affecte une valeur pour la première fois à une nouvelle variable, on parle d’**initialisation**. Le symbole `=` est l'opérateur d'affectation, il n'a pas la même signification qu'en mathématiques.


### Utilité

* Les expressions avec des variables sont générales, elles sont valides peu importe le contenu des variables. 

    ```py title="Modifier les notes ne change pas le calcul de la moyenne"
    maths    = 11
    français = 13
    anglais  = 14
    moyenne  = (maths + français + anglais) / 3
    print("Moyenne générale :")
    print(moyenne)
    ```

* Certaines valeurs ne sont pas connus à l’avance, typiquement une entrée clavier de l’utilisateur.

    ```py title="Le prénom de l'utilisateur n'est pas connu à l'avance"
    prénom = input()
    print("Bonjour", prénom)
    ```

* Une variable permet de stocker des résultats intermédiaires et de les réutiliser ultérieurement, une ou plusieurs fois.

* Bien nommer ces variables rend le code plus lisible et compréhensible.

## :fontawesome-solid-display: :fontawesome-solid-keyboard: Sortie / Entrée

* La fonction `#!py print` permet d'**afficher** une ou plusieurs valeurs.

    ```py
    prénom = "Arthur"
    âge = 27
    print(prénom, "a exactement ", âge, "ans")
    ```

* La fonction `#!py input` récupère une **saisie utilisateur** au clavier. Elle renvoie une chaîne de caractères.

    ```py
    saisie = input("Rayon ?")  # input renvoie une chaîne de caractères
    rayon = float(saisie) # conversion vers un nombre décimal
    aire = 3.14 * rayon * rayon
    print("Aire du disque: ", rayon)
    ```