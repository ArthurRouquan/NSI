# Opérations sur les tables

Pour tous ces exercices, on s'appuiera sur [cette table](harrypotter.csv). Pour rappel le code à adapter pour importer un fichier csv :

```py
import csv

file = open('harrypotter.csv', 'r')
table_hp = list(csv.DictReader(file, delimiter=','))
```

## Recherche 

!!!example "Appartient à"
    On souhaite d'abord vérifier qu'une valeur appartient à une table ou non. Pour cela il suffit de parcourir les enregistrements de la table et vérifier que la valeur recherchée est une valeur de l'enregistrement.

    ```py
    def appartient(valeur, table: list) -> bool:
        '''
        Renvoie True si et seulement **si** la valeur apparaît dans les valeurs de la table.
        '''
        for e in table: # e pour enregistrement
            for v in e. ... () : # v pour ...
                if v == ...
                    return ...
        return ...
    ```

    1. Compléter ce code.

    2. Simplifier ce code en utilisant l'opérateur d'appartenance `#!python in`.

    3. Que renvoie `#!python appartient('Harry Potter', table_hp)` ?


!!!example "Appartient à (suivant un champ)"
    Adapter la fonction précédente pour qu'elle prenne en paramètre un champ et qu'elle recherche si la valeur est présente pour le champ précisé. La signature de la fonction :

    ```py
    def appartient(valeur, champ: str, table: list) -> bool:
    ```


!!!example "Recherche"

    On souhaite désormais récupérer certaines données si la valeur recherchée est trouvée.

    Adapter la fonction précédente pour qu'elle renvoie la liste des valeurs correspondant à un second champ (de retour) lorsque la valeur cherchée est trouvée (dans un premier champ de recherche). La signature de la fonction :

    ```py
    def recherche(valeur, champ1: str, champ2: str, table: list) -> list:
    ```

    Un exemple :

    ```py
    >>> recherche('Hufflepuff', 'House', 'Character Name', table_hp)
    ['Cedric Diggory', 'Nymphadora Tonks', 'Susan Bones', 'Pomona Sprout', 'Leanne', 'Justin Finch-Fletchley', 'Zacharias Smith', 'Ernest Macmillan']
    ```

## Agrégation

L'**agrégation** est une fonction qui transforme une liste d'éléments en une unique valeur. Vous connaissez déjà moults fonctions d'aggrégation : **somme** d'une liste, **moyenne** d'une liste, **maximum**/**minimum** d'une liste, **nombre d'éléments** d'une liste etc.


!!!example "Aggrégation avec condition"
    Il est bien utile d'armer une telle fonction avec une **condition**. Par exemple, écrivez la fonction `compte` qui prend en paramètre une valeur, un champ et une table et renvoie le nombre d'occurences de la valeur dans le champ de la table.

    ```py
    >>> compte('Female', 'Gender', table_hp)
    42
    ```

## Sélection

Une **sélection** revient à créer une nouvelle table en extrayant les enregistrements d'une table existante vérifiant une certaine condition. 

Par exemple, on pourrait sélectionner les personnages de Serdaigle (Ravenclaw) :

| Character ID | Character Name     | Species             | Gender | House     | Patronus | Wand (Wood) | Wand (Core)        |
| ------------ | ------------------ | ------------------- | ------ | --------- | -------- | ----------- | ------------------ |
| 25           | Luna Lovegood      | Human               | Female | Ravenclaw | Hare     |             |                    |
| 28           | Gilderoy Lockhart  | Human               | Male   | Ravenclaw |          | Cherry      | Dragon Heartstring |
| 38           | Sybill Trelawney   | Human               | Female | Ravenclaw |          | Hazel       | Unicorn Hair       |
| 39           | Moaning Myrtle     | Ghost               | Female | Ravenclaw |          |             |                    |
| 41           | Quirinus Quirrell  | Human               | Male   | Ravenclaw |          | Alder       | Unicorn Hair       |
| 43           | Garrick Ollivander | Human               | Male   | Ravenclaw |          | Hornbeam    | Dragon Heartstring |
| 54           | Helena Ravenclaw   | Ghost               | Female | Ravenclaw |          |             |                    |
| 55           | Cho Chang          | Human               | Female | Ravenclaw | Swan     |             |                    |
| 59           | Filius Flitwick    | Human (Part-Goblin) | Male   | Ravenclaw |          |             |                    |
| 101          | Padma Patil        | Human               | Female | Ravenclaw |          |             |                    |
| 119          | Michael Corner     | Human               | Male   | Ravenclaw | Squirrel |             |                    |
| 124          | Marcus Belby       | Human               | Male   | Ravenclaw |          |             |                    |

Cela consiste donc à créer une liste en parcourant la table existante et en sélectionnant les enregistrements selon un critère : c'est exactement ainsi qu'on crée une **liste en compréhension avec filtre**.

La table précédente a été obtenu grâce à la ligne de code :

```py
table_serdaigle = [e for e in table_hp if e['House'] == 'Ravenclaw']
```

!!!example "Exercices sur la sélection"
    1. Créer la table des personnages d'espèce "Ghost"
    2. Créer la table des personnages féminins et de Gryffondor.
    3. Créer la table des personnages masculins dont le nombre de lettres de leur nom est pair.
 
## Projection

On peut également avoir à extraire d'une table certaines colonnes, c'est-à-dire seulement des données d'un ou plusieurs champs. On appelle également cette opération **projection**.

Il s'agit donc de créer une nouvelle table (liste) dont les enregistrements sont des dictionnaires qui ne contiennent que les couples champ: valeur des enregistrements de la table initiale pour les champs précisés (sous forme d'une liste par exemple).


!!!example "La projection en code"

    1. Compléter la fonction de projection:

        ```py
        def projection(table: list, liste_champs: list) -> list:
            '''
            Renvoie une table (liste de dictinonaires) des enregistrements de table ne contenant uniquement
            les champs appartenant à liste_champs.
            '''
            table_proj = ...
            for e in ...:
                table_proj.append({c: v for c, v in ... if ... })
            return ...
        ```

    2. Utiliser cette fonction pour créer une table en extrayant les colonnes "Character Name" et "House" de la table d'exemple.