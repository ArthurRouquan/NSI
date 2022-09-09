# Représentation approximative des nombres réels

Dans cette partie, nous allons comprendre l'origine de ce bug commun à quasiment tous les langages de programmation :

``` Python
>>> 0.1 + 0.2 == 0.3
False
```

Ce bug ne vient non pas du langage Python mais de la représentation en binaire des nombres à virgule, les nombres **flottants**. En python, un nombre flottant est du type `#!python float`.

## Écriture binaire

Rien ne nous empêche d'utiliser les puissances négatives de la base ! Par exemple, la décomposition suivante est naturelle en base 10 :

$$
(314.15)_{10} =
3 \times 10^2 +
1 \times 10^1 +
4 \times 10^0 + 
1 \times 10^{-1} +
5 \times 10^{-2}
$$

!!! summary "Base 2 → Base 10"
    La méthode ne change pas, la difficulté ici réside dans le calcul des puissances de 2 négatives.

    ![](./images/float.png)

    !!! example "Exemple"
        Que vaut $(101.011)_2$ en décimal ?

        $$
        \begin{align*}
            (101.011)_2 &= 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 + 0\times 2^{-1} + 1 \times 2^{-2} +1 \times 2^{-2} \\
            &= 4 + 1 + 0.25 + 0.125 \\
            &= 5.375
        \end{align*}
        $$

    !!! note "Remarque 1"
        Puisque seules les puissances négatives de 2 sont des nombres à virgule en base 10, seuls les bits après la virgule contribue à la partie décimale ! Que vaudrait le nombre binaire $(0.1111111...)_2$ ?



    !!! note "Remarque 2"
        Si l'écriture en base 2 est **finie**, alors l'écriture en base 10 est également finie (car les puissances de 2 négatives sont des nombres finis en base décimale).

!!! summary "Base 10 → Base 2"
    Prenons le nombre $3.6875$, il se décompose en une partie entière $3$ et une partie décimale $0.6875$. On a vu précedemment que la partie décimale sera representée par des bits après la virgule. Ainsi on sait déjà que la partie entière en base binaire s'écrira $3 = (11)_2$.

    * On peut tout à fait appliquer l'algorithme de soustraction étendu aux puissances de 2 négatives afin de déterminer ces bits après la virgule :

    $$
    3.6875 = 2 + 1 + 0.5 + 0.125 + 0.0625
           = (11.1011)_2
    $$

    C'est tout de suite légèrement moins évident.

    * L'algorithme des divisions par 2 successives devient l'**algorithme des multiplications par 2 successives**. On ne s'interesse qu'à la partie décimale :

    

    $$
    \begin{align*}
    0.6875 \times 2 &= \textcolor{#ff6188}{1}.\textcolor{#71d4e2}{375} \\
    0.\textcolor{#71d4e2}{375}  \times 2 &= \textcolor{#ff6188}{0}.\textcolor{#69ba76}{75} \\
    0.\textcolor{#69ba76}{75}   \times 2 &= \textcolor{#ff6188}{1}.\textcolor{#ffd866}{5} \\
    0.\textcolor{#ffd866}{5}    \times 2 &= \textcolor{#ff6188}{1}.0
    \end{align*}
    $$

    Ainsi, on a $0.6875 = (0.\textcolor{#ff6188}{1011})_2$ et donc avec la partie entière : $3.6875 = (11.1011)_2$. Pouvez-vous expliquer pourquoi ça fonctionne ?

!!! Exemple "Exercices"
    
    1. Donner l'écriture binaire de $20.875$.

    2. Donner l'écriture binaire de $0.1$.

    3. En déduire celle de $0.2$.



!!! note "Remarque"
    Toutes les puissances négatives de 2 finissent par un 5 dans la partie décimale. 