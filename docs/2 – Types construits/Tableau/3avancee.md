# Compléments sur les listes

## Copie de listes

### Un exemple déroutant

```py
>>> listA = [1, 2, 3]
>>> listB = listA
>>> listA.append(7)
>>> listB
[1, 2, 3, 7]
>>> listB.append(8)
>>> listA
[1, 2, 3, 7, 8]
```

Tout se passe comme si les listes `listA` et `listB` étaient devenus des clones «synchronisés» depuis l'affectation `listB = listA`.

<iframe width="800" height="300" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=listA%20%3D%20%5B1,%202,%203%5D%0AlistB%20%3D%20listA%0AlistA.append%287%29%0AlistB.append%288%29%0A&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Les deux variables `listA` et `listB` désginent **la même liste**. Elles ne stockent pas la liste mais une **référence** de celle-ci ! Une variable est une référence vers une adresse en mémoire. Si deux variables font référence à la même adresse, alors elles sont totalement identiques : toute modification de l'une entraîne une modification de l'autre.

### Copier une liste proprement

Trois façons :

```py
>>> listA = [3, 4, 5]
>>> listB = listA.copy() 
>>> listC = list(listA)
>>> listD = listA[:] # slice
```

### Pourquoi une référence ?

Quand vous passez des arguments à une fonction, ils sont **copiés**. Vous ne manipulez pas l'argument en lui-même.

```py
def incremente(x):
    x += 1

a = 1
incremente(a)
print(a)
```

Cet exemple affiche `1`, car `a` n'est pas modifié par la fonction ! Pourtant quand je passe une liste :

```py
def ajoute_1(liste):
    liste.append(1)

t = [1, 2, 3, 4]
ajoute_1(t)
print(t)
```

Ici le programme affiche `[1, 2, 3, 4, 1]` ! La référence est bien copiée, mais elle réfere toujours à la liste en mémoire !
Ainsi, manipuler `t` ou le paramètre `liste` revient à manipuler la même liste.  Une réference correspond à une adresse dans la mémoire, elle est stockée sur 32 ou 64 bits suivant votre machine.

Copier une liste est coûteux, c'est pour cela qu'on préfère les passer **par référence** (Python le fait automatiquement) au lieu de les passer par copie. Lorsque vous manipulez de gros objets (listes, matrices, dictionnaires, ensembles etc.) les variables que vous utilisez sont des références et non pas l'objet en lui-même.

## Les slices

Encore du sucre syntaxique.

```py
tableau[debut:fin:pas]
```