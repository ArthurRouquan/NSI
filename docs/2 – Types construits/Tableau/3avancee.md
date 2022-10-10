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



## Les slices
