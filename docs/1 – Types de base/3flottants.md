# Représentation approximative des nombres réels

Dans cette partie, nous allons comprendre l'origine de ce bug commun à quasiment tous les langages de programmation :

``` Python
>>> 0.1 + 0.2 == 0.3
False
```

Ce bug ne vient non pas du langage Python mais de la représentation en binaire des nombres réels. En python, un nombre flottant est du type `#!python float`.

## Écriture binaire d'un réel

### Base 2 ▸ Base 10

La décomposition suivante est naturelle en base 10 :

$$
\begin{align*}
(314.15)_{10} &= 300 + 10 + 4 + 0.1 + 0.5 \\
&= 3 \times 10^2 +
1 \times 10^1 +
4 \times 10^0 + 
1 \times 10^{-1} +
5 \times 10^{-2}
\end{align*}
$$

Finalement, rien ne nous empêche d'utiliser les **puissances négatives** de la base ! Un autre exemple en base binaire :

$$
\begin{align*}
    (101.011)_2 &= 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 + 0\times 2^{-1} + 1 \times 2^{-2} + 1 \times 2^{-3} \\
    &= 2^2 + 2^0 + 2^{-2} + 2^{-3} \\
    &= 4 + 1 + 0.25 + 0.125 \\
    &= 5.375
\end{align*}
$$

??? question "Exercices"
    1. Convertir $(1010.1011)_2$ en base décimale.
    2. Est-il vrai que seuls les bits après la virgule contribuent à la partie décimale ?
    3. Que vaut $(0.11111111...)_2$ ?
    4. Si l'écriture d'un nombre réel en base 2 est **finie**, peut-on en dire de même de son écriture en base 10 ? 

??? tip "Une méthode (parfois) plus rapide"
    
    Les puissances de 2 négatives sont difficiles à calculer. Il existe une méthode plus rapide en remarquant par exemple en base 10 que :

    $$
        1745.861 = \frac{1745861}{10^3}
    $$

    De la même manière, en base 2 :

    $$
        (101.011)_2 = \frac{(101011)_2}{2^3}
    $$

    Si on souhaite convertir $(101.011)_2$ en base décimale. On peut alors calculer le nombre binaire sans la virgule puis le diviser par le bonne puissance de 2 :

    $$
        (101011)_2 =  1 + 2 + 8 + 32 = 43 \implies (101.011)_2 = \frac{43}{2^3} = 5.375
    $$

    Aucune puissance de 2 négative n'a été calculée !

### Base 10 ▸ Base 2 

Prenons le nombre $3.6875$, il se décompose en :

* une partie entière $3$
* une partie décimale $0.6875$

??? note "Faire comme avant ?"
    On peut tout à fait appliquer l'algorithme de soustraction étendu aux puissances de 2 négatives afin de déterminer ces bits après la virgule :
    $$
    3.6875 = 2 + 1 + 0.5 + 0.125 + 0.0625
        = (11.1011)_2
    $$
    Cependant, les puissances négatives de 2 sont bien moins triviales.

On a vu précédemment que seuls les bits après la virgule contribue à la partie décimale. Ainsi, on sait déjà que la partie entière en base binaire s'écrira $3 = (11)_2$. Prochaine étape, la partie décimale.

L'algorithme des divisions par 2 successives devient l'**algorithme des multiplications par 2 successives**. On ne s’intéresse qu'à la partie décimale à chaque itération :

$$
\begin{align*}
0.6875 \times 2 &= \textcolor{#ff6188}{1}.\textcolor{#71d4e2}{375} \\
0.\textcolor{#71d4e2}{375}  \times 2 &= \textcolor{#ff6188}{0}.\textcolor{#69ba76}{75} \\
0.\textcolor{#69ba76}{75}   \times 2 &= \textcolor{#ff6188}{1}.\textcolor{#ffd866}{5} \\
0.\textcolor{#ffd866}{5}    \times 2 &= \textcolor{#ff6188}{1}.0
\end{align*}
$$

Ainsi, on a $0.6875 = (0.\textcolor{#ff6188}{1011})_2$ et donc avec la partie entière : $3.6875 = (11.1011)_2$. Pouvez-vous expliquer pourquoi ça fonctionne ?

??? question "Exercices"
    
    1. Donner l'écriture binaire de $20.875$.

    2. Donner l'écriture binaire de $0.1$.

    3. En déduire celle de $0.2$.

    4. Expliquer alors le comportement étrange de ce code :
        ``` Python
        >>> 0.1 + 0.2 == 0.3
        False
        ```

??? warning "Écritures binaires infinies"
    Un nombre réel ayant une écriture décimale **finie** peut avoir une écriture binaire **infinie** ! Or la mémoire d'un ordinateur est finie. Certains nombres ne peuvent donc pas être représentés correctement en machine, c'est une impossibilité théorique.


## Précautions d'usage

Puisqu'un nombre admettant une écriture binaire infinie ne peut pas être parfaitement représenté, le nombre manipulé sur la machine est donc une **valeur approchée**. Ainsi, il faut garder en tête que les calculs sont potentiellement faux, ou du moins **imprécis**, lorsque des flottants interviennent.


??? Warning "On ne teste JAMAIS l'égalité entre deux flottants"

    ``` python
    >>> a = 0.1
    >>> b = 0.3 - 0.2
    >>> if a == b:
            print("a et b sont égaux")
        else:
            print("a et b sont différents")

    a et b sont différents
    >>> 
    ```
    Le calcul `#!python 0.3 - 0.2` est imprécis et donnera une autre valeur approchée que `#!python 0.1`. L'opérateur d'égalité `#!python ==` vérifie en fait une égalité *bit par bit*. On préfère alors tester si deux nombres sont suffisamment proches, c'est-à-dire s'il existe un faible écart entre-eux. On teste alors si la différence en valeur absolue est inférieure à une précision donnée (suffisamment petite) :

    ``` python
    >>> a = 0.1
    >>> b = 0.3 - 0.2
    >>> epsilon = 10 ** (-12)
    >>> if abs(a - b) < epsilon:
            print("a et b sont égaux")
        else:
            print("a et b sont différents")

    a et b sont égaux
    >>>
    ```

??? Warning "La cumulation d'imprécisions"
    Effectuer des calculs imprécis avec les flottants génèrent des **imprécisions** qui vont se **cumuler**.

    Lors de la guerre du Golfe, en 1991, les américains disposaient de systèmes d'antimissiles Patriot pour intercepter les missiles Scud irakiens. Les Patriot disposaient d'une horloge interne émettant un signal tous les $0.1$ secondes, dès leur mise sous tension. Une durée écoulée est donc : $0.1 \times$ le nombre de « tics ».

    Sur ces systèmes, les nombres sont codés en virgule fixe sur 24 bits : c'est tout simplement une troncature de l'écriture binaire.

    Or $0.1 = 0.00011001100110011001100 ~|~ 1100 \ldots$

    L'erreur commise est donc d'environ $0.000000000000000000000001100 \approx 9.54 \cdot 10^{-8}$.

    Sur 100 heures de surveillance cela entraîne donc un décalage d'horloge interne de $9.54 \cdot 10^{-8} \cdot 10 \cdot 100 \cdot 3600 = 0.34$ seconde... ce qui correspond à une distance de plus de 500 mètres à la vitesse d'un missile Scud (1676 m/s).

    Ainsi un Patriot est passé à plus de 500 mètres d'un Scud le 25 février 1991 qui s'est abattu sur la caserne de Dhahran et a causé ainsi la mort de 28 personnes et 98 bléssés. Une fameuse frappe chirurgicale américaine.

## Représentation en machine d'un réel

### Virgule fixe

Sur certains systèmes informatiques, on utilise un codage à virgule fixe : on spécifie un nombre fixe de bits après la virgule. Par exemple, le mot binaire $\texttt{10110001}$ peut signifier $(10110.001)_2$ si on le code avec 3 bits après la virgule.

??? question "Exercices"
    1. Soit le mot binaire $\texttt{10011111}$. Donner sa valeur en base décimale si on le code avec 4 bits après la virgule.

    2. De même pour 3 bits, 2 bits et 1 bit après sa virgule.

    3. Soit $n$ le nombre de bits après la virgule, quelle est la distance entre les valeurs représentées par deux mots binaires successifs ?

    4. Et les nombres réels négatifs dans ce codage ?

### Virgule flottante : Norme IEEE 754 (Hors-Programme)

On a vu que le code à virgule fixe a un inconvénient notable : l’erreur relative commise sur le codage des nombres peut devenir très grande lorsque les nombres sont petits. D'où la nécessité d'un codage plus flexible. Pour justement s'adapter à tous les ordres de grandeur de nombres, l'idée est de coder les nombres réels dans une écriture scientifique :

$$
\pm \underbrace{1, \ldots}_{\text{mantisse } m} \times 2^e
$$

Nous avons trois informations à retenir :

* Le **signe** $\pm$.

* la **mantisse** $m$, les chiffres significatifs.

* l'**exposant** $e$. 

Deux formats les plus courants, standardisés par l'organisation IEEE :

* 32 bits : 1 bit pour le signe, 8 bits pour pour l'exposant, 23 bits pour la mantisse. Aussi appelé **simple précision**.

* 64 bits : 1 bit pour le signe, 11 bits pour l'exposant, 52 bits pour la mantisse. Aussi appelé **double précision**.

Les deux formats utilisent la même méthode pour stocker et représenter les nombres réels, on se place alors dans cas d'un flottant 32 bits sans perte de généralité.

![](./ressources/ieee.png)


#### Le signe

Un bit 1 indique un nombre négatif et un bit 0 indique un nombre positif.

#### L'exposant

L'exposant $e$ est un entier relatif entre $-127$ et $128$ codé sur un octet. Il est représenté par un entier positif $E = e + 127$ appelé l'**exposant biaisé**.

| Exposant $e$ | Exposant biaisé $E$ | Représentation binaire de $E$ |
| :----------: | :-----------------: | :---------------------------: |
|     -10      |         117         |      $\texttt{01110101}$      |
|      0       |         127         |      $\texttt{01111111}$      |
|      5       |         132         |      $\texttt{10000100}$      |
|     108      |         235         |      $\texttt{11101011}$      |

Ce décalage est donc une représentation des entiers relatifs sans utiliser de bit de signe.

#### La mantisse

Avant toute chose, la mantisse doit être **normalisée**. C'est le même processus de normalisation qu'en base décimale. Par exemple, $1234.567$ est normalisé comme $1.234567 \cdot 10^3$ de telle manière qu'il n'y a plus qu'un seul chiffre devant la virgule.

De la même manière, $(1101.101)_2$ est normalisé comme $(1.0101101)_2 \cdot 2^3$ en décalant la virgule 3 fois vers la gauche. Quelques exemples :


| Nombre       | Normalisé   | Exposant |
| ------------ | ----------- | -------- |
| $1101.101$   | $1.101101$  | $3$      |
| $0.00101$    | $1.01$      | $-3$     |
| $1.0001$     | $1.0001$    | $0$      |
| $10000011.0$ | $1.0000011$ | $7$      |

Vous avez peut-être remarqué que dans une mantisse normalisée, le chiffre $1$ apparaît toujours à gauche de la virgule. En fait, le $\texttt{1}$ initial est omis du stockage réel de la mantisse car non-nécessaire.

#### Conclusion

Combinons maintenant le signe, l'exposant et la mantisse normalisée pour représenter un nombre réel sur 32 bits. Par exemple, on souhaite coder $-13.625$ suivant la norme IEE 754 :

$$
\begin{align*}
-13.625 &= (-1101.101)_{\small 2} \\ 
        &= (-1.101101)_{\small 2} \times 2^3 \\
\end{align*}
\rule{0pt}{4ex}
$$

* Le nombre est négatif donc le bit de signe est à $\texttt{1}$
* L'exposant biaisé $E = e + 127 = 3 + 127 = 130 = (10000010)_2$ donc $\texttt{10000010}$
* La mantisse sera codée $\texttt{10110100000000000000000}$

Somme toute, le nombre $-13.625$ suivant la norme IEE 754 est codé en machine comme :
$$
\texttt{11000001010110100000000000000000}
$$

#### Cas particuliers

Il existe quelques valeurs spéciales dans ce codage IEEE 754 en simple précision. Suivant les valeurs de l’exposant biaisé $E$ (notez que le décalage vaut $2^{b-1} - 1$ où $b$  est le nombre de bits utilisés pour coder l’exposant) et de la mantisse, le nombre final peut appartenir à l'une ou l'autre des catégories suivantes :


| Type                                  | Exposant biaisé $E$ | Mantisse   |
| ------------------------------------- | ------------------- | ---------- |
| Zéros                                 | $0$                 | $0$        |
| Nombres dénormalisés                  | $0$                 | $\neq 0$   |
| Nombres normalisés                    | $1$ à $254$         | Quelconque |
| Infinis                               | $255$               | 0          |
| Nombres indéfinis (Not A Number, NaN) | $255$               | $\neq 0$   |

Un nombre dénormalisé s'écrit sous la forme $\pm \cdot 0,m \cdot 2^{-126}$.

#### Exercices

!!! question "Exercice 1"
    Donner la représentation IEEE 754 du nombre $3.6875$ en simple précision.

!!! question "Exercice 2"
    Quel nombre s'écrit en virgule flottante simple précision : `11000101000000101100001101000000` ?

!!! question "Exercice 3"
    On imagine un codage en virgule flottante sur simplement 6 bits, avec 1 bit pour le signe, 3 bits pour l'exposant et 2 pour la mantisse. On a donc $E = e + 3$.

    1. Déterminer les nombres indéfinis.
    
    2. Déterminer l'écriture de  $+\infty$ et $-\infty$.

    3. Placer sur une droite graduée les nombres normalisés positifs.

    4. Placer sur une autre droite graduée les nombres dénormalisés positifs.


