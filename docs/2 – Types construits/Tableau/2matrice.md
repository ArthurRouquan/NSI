# Tableaux à plusieurs dimensions

## Listes de listes

Nous avons vu qu'une liste pouvait contenir des éléments de tous types : des entiers, des chaines des caractères... et pourquoi pas une liste qui contient des listes ?

On obtient alors un tableau à deux dimensions, qui est semblable au concept mathématique de matrice.


La liste ```tab``` ci-dessous est composée de 3 listes qui elles-mêmes contiennent trois nombres :
```python
tab =  [[3, 5, 2],
        [7, 1, 4], 
        [8, 6, 9]]
```

On accède aux *lignes* du tableau avec un simple crochet:

```python 
>>> tab[1]
[7, 1, 4]
```

Et aux éléments par un double crochet:

```python 
>>> tab[2][1]
6
```

<figure markdown>
  ![Image title](images/tab2.png){ width="300" }
  <figcaption></figcaption>
</figure>

## Parcourir une liste de listes

* Parcours par éléments :
    ```python 
    for ligne in tab:
        for element in ligne:
            print(element)
    ```

* Parcours par indice :
    ```python 
    for i in range(3):
        for j in range(3):
            print(tab[i][j])
    ```