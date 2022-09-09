# Récapitulatif

## Réprésentation des entiers

* Dans la numération positionnelle, les nombres sont représentés par une suite de symboles, les chiffres.

* La **base** correspond au nombre de chiffres utilisés. On la note explicitement en indice si ambiguïté. 

* Remarque : Pour une base supérieure à 10, il nous faut de nouveaux symboles. On utilise typiquement l'alphabet latin A, B, C, etc. Une autre manière serait aussi d'utiliser tout simplement 10, 11, 12, etc. qu'on sépare par un espace, un point-virgule etc. (typiquement la base 60 pour les secondes et minutes).

* La base 10 dans laquelle on compte usuellement s'appelle la base **décimale**.

* Un nombre dans cette représentation est la somme de ses <span style="color:#ff6188">chiffres</span>
 pondérées par la <span style="color:#71d4e2">base</span> puissance leur <span style="color:#ffd866">rang</span> :

$$
(\textcolor{#ff6188}{176})_\textcolor{#71d4e2}{8} =
\textcolor{#ff6188}{1} \cdot \textcolor{#71d4e2}{8}^\textcolor{#ffd866}{2} +
\textcolor{#ff6188}{7} \cdot \textcolor{#71d4e2}{8}^\textcolor{#ffd866}{1} +
\textcolor{#ff6188}{6} \cdot \textcolor{#71d4e2}{8}^\textcolor{#ffd866}{0} = (126)_{10}
$$

* La plus petite des bases, la base 2, s'appelle la base **binaire**. C'est celle utilisée par les systèmes informatiques pour sa fiabilité (résistance au bruit) et la simplicité de son arithmétique (moins de circuiteries).

* Un chiffre en binaire s'appelle un **bit**.

* 8 bits forme un **octet** (ou byte en anglais).

* Avec $n$ bits on peut distinguer $2^n$ valeurs. Puisque 0 est une valeur, le nombre maximal qu'on puisse exprimer est $2^n - 1$.

---

* Pour convertir rapidement un nombre binaire en base décimale, on additionne simplement les puissances de 2 associées aux bits à 1.

* Pour convertir un nombre en base décimale vers la base binaire, il existe deux algorithmes itératifs :

    * **L'algorithme de soustraction** : on soustrait du nombre la plus grande puissance de 2 possible, et on recommence.

    * **L'algorithme de division** : on effectue les divisions successives du nombre par 2. L'écriture en binaire est donnée par les restes lus de bas en haut.

* L'algorithme de division peut être adapté pour convertir un nombre en base décimal vers n'importe quel base.

* Quand on multiplie (resp. divise) un nombre par 2, sa représentation binaire se voit décalé vers la gauche (resp. droite).

