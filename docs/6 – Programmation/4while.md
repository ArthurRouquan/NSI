# La boucle while

Lorsqu'on souhaite répéter une série d'instructions plusieurs fois d'affilé, les boucles sont l'outil adpaté. Il en existe deux types en Python, la boucle bornée `for` (pour) et la boucle non-bornée `while` (tant que). Sa syntaxe est la suivante :

``` py
while condition_est_vraie:
    instruction1
    instruction2
    instruction3
    ...
```
Tant que la condition est vraie, alors le bloc indenté est exécutée. La condition est vérifiée en entrée de la boucle, les instructions peuvent être donc totalement ignorées. La condition est réévaluée à la fin du bloc d'instructions indenté.

## Un premier exemple

> Combien de fois doit-on plier une feuille de papier pour que son épaisseur dépasse la hauteur de la Tour Eiffel (324 m) ?

On suppose une feuille de papier classique, d'épaisseur de 0.1 mm. Plier la feuille en deux revient à multiplier son épaisseur par deux.

``` py
epaisseur = 0.0001
nombre_pliages = 0

while epaisseur < 324:
    epaisseur = 2 * epaisseur
    nombre_pliages += 1

print("Il faut", nombre_pliages, "pliages.")
```