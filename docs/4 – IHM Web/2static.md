# Page statique : HTML & CSS

Concentrons-nous sur le scénario le plus simple, où le serveur envoie une page **statique**, c'est-à-dire identique pour tous les clients et qui ne présente aucune interactivité. Une telle page ne nécessite qu'un fichier HTML et optionnellement un fichier CSS.

<figure markdown>
![](rsc/img/client-serveur-STATIC.png){ width=75%, .center }
</figure markdown>

## :material-language-html5: Les bases de l'HTML

### Un langage de balisage

L'HTML n'est pas un langage de programmation, mais **un langage de balisage** utilisé pour **structurer le contenu** des pages Web.

Un fichier HTML est composé d'une série d'**éléments** avec lesquels vous pouvez encadrer (ou **baliser**) différentes parties du contenu pour les faire apparaître ou agir d'une certaine manière. Des balises encadrantes peuvent transformer une petite partie de contenu en un lien vers une autre page sur le Web, mettre des mots en italique, etc. Par exemple :

<figure markdown>
| Code HTML                                              | Rendu                   |
| ------------------------------------------------------ | ----------------------- |
| `#!html T'as les cramptés ?`                           | T'as les cramptés ?     |
| `#!html T'as les <strong>cramptés</strong> ?` | T'as les **cramptés** ? |
</figure markdown>

!!! idea "Tester les exemples"
    Pour tester un code HTML, il existe deux manières courantes. Soit simplement copier-coller le code HTML dans un fichier `ma_page.html` puis l'ouvrir avec un navigateur web. Soit utiliser un site web de type « *sandbox* » comme [Playcode.io](https://playcode.io/1480073) : cette dernière méthode est plus confortable pour tester rapidement et partager facilement des bouts de code.

#### Anatomie d'un élément HTML

<figure markdown>
![](rsc/img/balise.png)
</figure markdown>

#### Imbrication des éléments

Les éléments peuvent être imbriqués :

```html
<p>T'as les <strong>cramptés</strong> ?</p>
```

!!! question
    Quelles sont les erreurs dans l'extrait de code HTML suivant ?

    ```html
    </balise1>
        <balise2>
        <balise1>
    </balise2>
    ```

#### Éléments bloc vs en ligne

Les éléments de niveau **bloc** forment un bloc visible sur une page, tandis que les éléments en **ligne** ne fait pas apparaître une nouvelle ligne.

```html
<em>Alice</em><em>Bob</em><em>Charlie</em>

<p>— T'as les cramptés ?</p><p>— Quoi ?</p><p>— Quoicoubet !</p>
```

!!! question
    L'élément `#!html <p>` fait partie de quelle catégorie ? De même pour `#!html <em>` ?


### Une première page web structurée

Voici une page web complète et minimale :

```html
<!DOCTYPE html> <!-- (1)! -->
<html lang=fr> <!-- (2)! -->
    <head> <!-- (3)! -->                                      
        <meta charset="utf-8"> 
        <title>Je suis le titre de l'onglet</title>
    </head>

    <body> <!-- (4)! --> 
        <h1>Ma magnifique page web 🌈</h1> <!-- (5)! --> 
        <p> <!-- (6)! --> 
            Un texte très <strong>intéressant</strong>. 
        </p>
        <a href="http://www.lyceecivray.net">Un super site !</a> <!-- (7)! --> 
        <!-- Un commentaire... -->
    </body>
</html>
```

1. Déclare quelle **version** du langage HTML utiliser.
2.  * l’élément `#!html <html>` est l’élément **racine** du document. Tous les autres éléments du document en seront des descendants. 
    * `lang` est ce qu'on appelle un **attribut**. Les éléments HTML peuvent recevoir des attributs, c'est-à-dire des informations supplémentaires.
3. `#!html <head>` fournit des informations et des **métadonnées** sur le document HTML lui-même. Il ne représente pas le contenu visible de la page.
4. `#!html <body>` est l'élement qui contient le **contenu visible** de la page.
5. `#!html <h1>` représente un **titre** (*header* en anglais). Il existe différents sous-niveaux de titre par ordre décroissant d'importance : `#!html <h1>`, `#!html <h2>`, `#!html <h3>` etc.
6. `#!html <p>` représente un **paragraphe**.
7. `#!html <a>` représente une **ancre** qui permet de définir **un lien hypertexte** absolu ou relatif.

!!! question
    Répondre à l'aide de recherches sur le web :

    1. Quelle est la balise permettant d'**insérer une image** dans une page web ? Combien d'attributs obligatoires et non-obligatoires comporte-t-elle?
    2. Quelles sont les balises pour insérer des listes ordonnées et non-ordonnées ?
    3. Les tabulations sont-elles nécessaires dans le code HTML ?
    4. Réaliser une petite page web qui présente votre album de musique préféré (titre, pochette, description, liste des titres, un lien vers le site du groupe etc.). [Exemple de page.](rsc/html/justice.html) Un autre projet serait de réaliser une page web présentant la biographie d'une personnalité.

!!! note "On retient"
    On retient que le ficher HTML décrit de manière structuré le contenu d'une page web grâce à un système de balises.

## :material-language-css3: Styliser sa page avec du CSS

Soyons honnête, le site web crée précédemment est objectivement laid. Le langage CSS (*Cascading Style Sheets*, feuilles de style en cascade) permet de **mettre en forme**, styliser, une page web comme changer la fonte de caractères ou la couleur d'un titre, centrer une image, agencer différents éléments sous la forme d'une grille etc.

On peut incorporer du CSS directement dans le fichier HTML en spécifiant l'attribut `style` :

```html
<h1 style="color: red;">Ma magnifique page web 🌈</h1>
<p style="text-align: center;">
    Un texte très <strong>intéressant</strong>.
</p>
```

Toutefois, ceci est une **mauvaise pratique**, il est préférable de spécifier le style d'une page web dans un fichier CSS séparé du code HTML. Imaginez devoir spécifier le style de chaque élément de l'ensemble des pages web d'un site... et un jour devoir changer la couleur des titres 🙀

### Lié un style CSS à un code HTML

Dans un fichier nommé `mon_style.css` :

```css title="mon_style.css"
body
{
    font-family: sans-serif;
}

h1
{
    color: red;
}
```

Ce fichier CSS peut être ensuite spécifié dans le code HTML au sein de la balise `#!html <head>` :

```html
<link href="mon_style.css" rel="stylesheet" type="text/css" />
```