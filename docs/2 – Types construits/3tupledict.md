# Tuples et Dictionnaires


!!! info "Liens"
    * Lien de la présentation : [:fontawesome-solid-link: PDF de la présentation des deux structures de données](./ressources/tupledict.pdf)
    * Exercices : [:fontawesome-solid-link: Notebook Capytale 49ae-2595433](https://capytale2.ac-paris.fr/web/c/49ae-2595433)
    * Correction : Disponible plus tard !

## Tuple

On retient qu'un tuple (ou p-uplet) est une séquence **continue et ordonnée** d’éléments de types **possiblement différents**. C'est une structure de données **immutables** (qu'on ne peut modifier).

```py
# On construit un tuple avec des parenthèses
eleve = ('Michel', 'Dupont', 17, 175)

# On accède à un élément du tuple par son indice
print(eleve[0]) 

# Erreur ici, on ne peut pas modifier un tuple !
eleve[0] = 'Pierre'

# D'autres opérations classiques
t1 = (12, 34, 56)
t2 = (78, 90)

print(t1 + t2) # affiche (12, 34, 56, 78, 90)
print(t1 * 3) # affiche (12, 34, 56, 12, 34, 56, 12, 34, 56)

# "unpacking a tuple" ou "déballage d'un tuple", marche aussi pour les tableaux !
prenom, nom, age, taille = ('Michel', 'Dupont', 17, 175)
```


## Dictionnaire

Un dictionnaire une structure de données **non-ordonnée** qui permet une 
**association clé–valeur**.


```py
# Construction explicite d'un dictionnaire :
eleve = {
    "prénom": "Michel",
    "nom": "Dupont",
    "âge": 17,
    "taille": 175
}

# On accède à une valeur, grâce à sa clé :
print(eleve["prénom"])

# Modification d'une valeur :
eleve["age"] = 42

# Suppression d'une association :
eleve.pop("taille") # (note : ici, la méthode .pop renvoie la valeur associée à la clé, donc 175)

print(eleve.keys()) # ensemble des clés
print(eleve.values()) # ensemble des valeurs
print(eleve.items()) # ensemble des clés-valeurs

# parcours par clé 
for key in eleve:
    print(key, eleve[key])

# parcours par clé 
for key in eleve.keys():
    print(key, eleve[key])

# parcours par valeurs
for value in eleve.values():
    print(value)

# parcours par clé et valeurs
for key, value in eleve.items():
    print(key, value)
```

