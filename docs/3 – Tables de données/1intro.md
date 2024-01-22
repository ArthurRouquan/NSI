# Tables de données

## Introduction et vocabulaire

La façon la plus naturelle et simple de structurer des données est de les organiser sous la forme d'une **table** : bulletins scolaires, extrait de compte bancaire, statistiques sportives etc.

<figure markdown>
| Nom        | Prénom   | Poste             | Taille | Poids |
| ---------- | -------- | ----------------- | ------ | ----- |
| Mbappé     | Kylian   | Attaquant         | 179    | 78    |
| Griezmann  | Antoine  | Attaquant         | 173    | 73    |
| Giroud     | Oliver   | Attaquant         | 192    | 92    |
| Lloris     | Hugo     | Gardien de but    | 188    | 78    |
| Tchouaméni | Aurélien | Milieu de terrain | 185    | 75    |
| Koundé     | Jules    | Défenseur         | 178    | 70    |
<figcaption style="font-style: normal">Exemple de table</figcaption>
</figure>

Le vocabulaire est le suivant :

* Une **table** est un ensemble d'**enregistrements** (lignes).

* Un enregistrement contient les **valeurs** correspondants aux **attributs** (ou **champs**, ou encore **descripteurs**) de la table.

Par exemple, dans la table précédente :

* `Nom`, `Prénom`, `Poste`, `Taille`, `Poids` sont des attributs. On peut noter que chaque champ est défini par un **type** (entier, flottant, chaîne de caractères etc.). 
  
* Chaque ligne de la table est un enregistrement. Il y a 6 enregistrements dans cet table.

* `Mbappé` est une valeur du champ `Nom` pour le premier enregistrement.

## Représentation d'une table en Python

Une question se pose : Comment représenter une telle structure de données en Python ?

### Représentation d'un enregistrement

Il existe deux manières communes de représenter un enregistrement. Puisqu'un tableau ne peux pas contenir des valeurs de différents types, un **p-uplet** (ou tuple) semble être une bonne première approche :

```py
enregistrement = ('Mbappé', 'Kylian', 'Attaquant', 179, 78)
```

Hélas, pour accéder aux valeurs de cet enregistrement, il est nécessaire d'utiliser des indices :

```py
>>> enregistrement[3]
179
```

On préférera alors utiliser un **dictionnaire** qui permet en quelque sorte de "nommer les indices" avec leur champ correspondant :

```py
enregistrement = {
    'nom'    : 'Mbappé',
    'prénom' : 'Kylian',
    'poste'  : 'Attaquant',
    'taille' : 179,
    'poids'  : 78
}
```

Et donc si on veut accéder au champ `Taille` de la table :

```py
>>> enregistrement1['taille']
179
```

Ce qui est bien plus élégant !

### Représentation d'une table

Une table est une collection d'enregistrements, donc on la représenter sous la forme d'une liste d'enregistrements, une **liste de dictionnaires** :

```py
table = [
    {'nom' : 'Mbappé',     'prénom' : 'Kylian',   'poste' : 'Attaquant',         'taille' : 179, 'poids' : 78},
    {'nom' : 'Griezmann',  'prénom' : 'Antoine',  'poste' : 'Attaquant',         'taille' : 173, 'poids' : 73},
    {'nom' : 'Giroud',     'prénom' : 'Oliver',   'poste' : 'Attaquant',         'taille' : 192, 'poids' : 92},
    {'nom' : 'Lloris',     'prénom' : 'Hugo',     'poste' : 'Gardien de but',    'taille' : 188, 'poids' : 78},
    {'nom' : 'Tchouaméni', 'prénom' : 'Aurélien', 'poste' : 'Milieu de terrain', 'taille' : 185, 'poids' : 75},
    {'nom' : 'Koundé',     'prénom' : 'Jules',    'poste' : 'Défenseur',         'taille' : 178, 'poids' : 70}
]
```

Ainsi on peut facilement manipuler cette table :

```py
>>> table[1]
{'nom' : 'Griezmann', 'prénom' : 'Antoine', 'poste' : 'Attaquant', 'taille' : 173, 'poids' : 73 }
>>> table[1]['prénom']
'Antoine'
```

??? question "Question 1 - Manipuler une table sous la forme d'une liste de dictionnaires"
    * Copier la table des joueurs précédent dans un script Python.
        ```py
        table = ...
        ```
    * Afficher le 4ème enregistrement.
        ```py
        print(table[...])
        ```
    * Afficher le nom est la taille de ce joueur.
        ```py
        print(table[...][...], table[...][...])
        ```
    * Parcourir la table pour afficher seulement la taille des joueurs.
        ```py
        for ligne in table:
            print(ligne[...])
        ```
    * Calculer la moyenne de la taille des joueurs.

## Fichiers CSV

<!-- ### Fichier texte tabulé

Comment enregistrer une table dans un fichier ? Il existe deux manières courantes. La première est de séparer les enregistrements par des **sauts à la ligne** et les valeurs par des **tabulations** dans un bête fichier texte :

```
"Mbappé"	"Kylian"	"Attaquant" 179	78
"Griezmann"	"Antoine"	"Attaquant" 173	73
"Giroud"    "Oliver"    "Attaquant" 192 92
```

On ajoute des guillemets autour des valeurs de type chaîne de caractères, car certaines d'entre elles pourraient contenir des sauts à la ligne (`\n`) ou des tabulation (`\ t`) qu'on ne voudrait pas confondre avec ceux structurant le fichier.

### Fichier CSV -->

Les tables sont fréquemment enregistrées dans des fichiers au format `.csv` (*comma separated values*). C'est un simple fichier texte où :

* La première ligne définit les attributs.

* Chaque ligne correspond à un enregistrement.

* Les attributs et les valeurs sont séparés par un *délimiteur*, généralement par une **virgule**.

* Les guillemets `"` peuvent être utilisés pour délimiter le contenu d'une châine de caractères.

Par exemple, le début de la table précédente s'écrirait comme :

```csv
Nom,Prénom,Poste,Taille,Poids
Mbappé,Kylian,Attaquant,179,78
Griezmann,Antoine,Attaquant,173,73
Giroud,Oliver,Attaquant,192,92
```

??? question "Question 2 - Un autre exemple de délimiteur"
    * Télécharger  [ce fichier .csv](./pokedex.csv) et l'ouvrir ensuite avec un éditeur de texte (notepad++) pour observer sa construction. Quel est le délimiteur ?

### Charger un fichier CSV avec Python

#### From scratch

Ouvrir un fichier en Python se fait grâce à la fonction `#!python open`. Les méthodes `#!python .read` et `#!py .split` permettent ensuite de récupérer l'ensemble des lignes dans une liste.

!!! warning "Attention !"
    Le ficher `pokedex.csv` doit se trouver dans le même dossier que votre script Python !

```py
>>> fichier = open('pokedex.csv', encoding='UTF-8')
>>> lignes = fichier.read().split('\n')
>>> lignes[0]
'No;Nom;Type;PV;Attaque;Défense;Vitesse;ASpé;DSpé;Talent;Nom US;code'
>>> lignes[6]
'6;Dracaufeu;feu,vol;78;84;78;100;109;85;Brasier,Force Soleil;Charizard;63266'
```
Il va falloir un peu travailler ces chaînes de caractères pour parvenir à des dictionnaires. La méthode `.split` appliquée à une chaîne de caractère permet de la 
scinder suivant un délimiteur donné en paramètre.

```py
>>> "oui bonjour ça va".split(' ')
['oui', 'bonjour', 'ça', 'va']
>>> chaine = "Un peu, trop, de virgules, non?"
>>> chaine.split(',')
['Un peu', ' trop', ' de virgules', ' non?']
```

!!! question "Récupérer les attributs"
    * Dans un nouveau script Python, copier le code suivant :
    ```py
    fichier = open('pokedex.csv', encoding='UTF-8')
    lignes = fichier.read().split('\n')
    attributs = # à compléter
    ```

    * Écrire la code pour récupérer les attributs (les clés de notre futur dictionnaire) sous la forme d'une liste de chaînes de caractères. À la fin de l'exécution de votre code, `attributs` doit être égal à `#!py ['No', 'Nom', 'Type', 'PV', ...]`.

Transformer un enregistrement en un dictionnaire est plus subtil car il nécessaire de convertir certaines valeurs.

```py
>>> lignes[1]
'1;Bulbizarre;plante,poison;45;49;49;45;65;65;Engrais,Chlorophylle;Bulbasaur;77140'
>>> lignes[1].split(';')
['1', 'Bulbizarre', 'plante,poison', '45', '49', '49', '45', '65', '65', 'Engrais,Chlorophylle', 'Bulbasaur', '77140']
```

On peut manuellement convertir certaines valeurs dans son bon type :

```py
vals = lignes[1].split(';')
vals = (int(vals[0]), vals[1], vals[2], int(vals[3]), int(vals[4]), int(vals[5]), int(vals[6]), int(vals[7]), int(vals[8]), vals[9], vals[10], int(vals[11]))
print(vals)
```

Le code affiche :

```py
(1, 'Bulbizarre', 'plante,poison', 45, 49, 49, 45, 65, 65, 'Engrais,Chlorophylle', 'Bulbasaur', 77140)
```

Une fois ce tuple construit, on peut enfin le transformer en un dictionnaire :

```py
enregistrement = {}
for i in range(len(attributs)):
    enregistrement[attributs[i]] = vals[i]
print(enregistrement)
```

!!! question "Récupérer les enregistrements"
    * Adapter ce code pour transformer tous les enregistrements de table en dictionnaires. Structurer votre code avec des fonctions comme `transformer_ligne_en_tuple` et `transformer_tuple_en_dico` !

    * Finalement, à partir des attributs et des enregistrements, construire la liste des dictionnaires représentant la table.

Évidemment ce code ne fonctionnera que pour le fichier csv fourni.

#### Grâce à la bibliothèque `csv`

La bibliothèque `csv` permet de lire et d'écrire des fichiers csv rapidement. Par exemple, la fonction `DictReader` remplace tout notre code précédent :

```py
import csv

fichier = open('pokedex.csv', 'r', encoding='UTF-8')  # 'r' pour read, on veut simplement lire le fichier

table = csv.DictReader(fichier, delimiter=';')

table = list(table) # table est de type 'csv.DictReader', on la convertit ici en une liste de dictionnaires

print(table[0])

fichier.close() # fermeture du fichier
```

Le code affiche :

```py
{'No': '1', 'Nom': 'Bulbizarre', 'Type': 'plante,poison', 'PV': '45', 'Attaque': '49', 'Défense': '49', 'Vitesse': '45', 'ASpé': '65', 'DSpé': '65', 'Talent': 'Engrais,Chlorophylle', 'Nom US': 'Bulbasaur', 'code': '77140'}
```

La conversion des valeurs ne se fait hélas pas automatiquement. 