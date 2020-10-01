*Ceci est un guide C++, qui permet de voir toutes les nouvelles fonctionnalités possibles par rapport au langage C, et ce jusqu'à la norme C++20 (2020), si possible.*

*Dérnière mise à jour, le 29/09/20.*

---
Sommaire :
---------
- [C++](#C++)
    1. [Les fichiers et les extensions](#les-fichiers-et-les-extensions)
    1. [La compilation](#la-compilation)
    1. [Les commentaires](#les-commentaires)
    1. [Les *libraries*](#les-libraries)
    1. [L'affichage](#l'affichage)
        - [Les caractères](#les-caractères)
            - [L'affichage des char](#l'affichage-des-char)
            - [L'affichage des wchar](#l'affichage-des-wchar)
        - [Les nombres](#les-nombres)
            - [Les formats d'affichage des nombres](#les-formats-d'affichage-des-nombres)
            - [L'affichage d'un booléen](#l'affichage-d'un-booléen)
            - [L'affichage après la virgule d'un nombre décimal](#l'affichage-après-la-virgule-d'un-nombre)
            - [L'affichage du signe d'un nombre](#l'affichage-du-signe-d'un-nombre)
            - [L'affichage en majuscule](#l'affichage-en-majuscule)
        - [Le sens de remplissage des espaces vides](#le-sens-de-remplissage-des-espaces-vides)
        - [L'affichage par <iomanip>](#l'affichage-par-<iomanip>)
            - [Remplissage d'espaces vides](#remplissage-d'espaces-vides)
            - [Remplissage de caractères](#remplissage-de-caractères)
            - [L'affichage d'une variable](#l'affichage-d'une-variable)
    1. [Les variables et les constantes](#les-variables-et-les-constantes)
        - [La déclaration et l'initialisation](#la-déclaration-et-l'initialisation)
        - [Les constantes](#les-constantes)
        - [Le typage dynamique](#le-typage-dynamique)
        - [Forcer/Renforcer le typage](#forcer/renforcer-le-typage)
        - [Les casts](#les-casts)
        - [La library <limits>](#la-library-<limits>)
    1. [Saisie utilisateur](#saisie-utilisateur)
---

# C++

Le langage C++ est un langage de programmation procédurale et orienté objet. C'est un langage plutôt bas niveau. Il est utilisé dans tous les secteurs où la performance est importante. En effet, c'est un langage puissant et rapide !

## Les fichiers et les extensions
---
Les programmes C++ sont écrits de la même manière que les programmes en C, cependant ces fichiers C++ peuvent avoir différentes extentions dont les plus courantes sont `.cpp`, `.cc`, `.cxx` ou encore `.C` (en majuscule ≠ `.c`) pour les fichiers sources et `.h`, `.hh`, `.hxx`, `.hpp` pour les fichiers *header* **de déclaration et de définition**. Il existe aussi les extensions `.inc`, `.inl` beaucoup moins utilisés pour les fichiers *header* **d'implémentation**, ils contiennent généralement des fonctions *inline*.

>Rappel :
>   Les fichiers *header* se structure de la forme suivante pour **éviter les inclusions multiples** :
>   ```c++
>   #ifndef NOM_DU_FICHIER_H
>   #define NOM_DU_FICHIER_H
>   /* les déclarations */
>   #endif
>   ```

## La compilation
---
Les programmes en C++ peuvent être compilés avec des compilateurs différents. Les compilateurs les plus courants sont **g++** et **clang++**. Un programme en C++ ce compile de la même manière qu'un programme écrit en langage C.

## Les commentaires
---
Les commentaires sont exactements les mêmes que pour le langage C.

```c++
// ligne de commentaire
```

```c++
/*
*  bloc de commentaire
*/
```

## Les *libraries*
---
Tout comme le langage C, le C++ utilise des *libraries* standard pour utiliser des fonctions. Etant donné que le C++ est basé sur le langage C, il inclut presque toutes les *libraries* du langage C. Mais le C++ a aussi ses propres *libraries* standard.

La *library* standard de base (à mettre absolument) est :

 * `<iostream>`
    
    L'équivalent de la library standard `<stdio.h>` en langage C. Comme son nom l'indique, elle gère les **inputs/outputs**. En incluant cette en-tête, nous allons en réalité en inclure beaucoup d'autres dans un but pratique (`<ios>`, `<iosfwd>`, `<istream>`, `<ostream>`, `<streambuf>`).


## L'affichage
---
L' affichage se fait par le biais du **flux de sortie** à l'aide d'une classe std. Un type d'affichage serait par exemple :

```c++
std::cout << "Mon Affichage" << std::endl
```
 * `cout`
 	***'c'*** pour caractère/char. ***'out'*** pour sortie. `std::cout` indique donc qu'il affiche un message sur l'écran.

 * `<<`
    Dans cette exemple, il s'agit d'un opérateur de **flux** et plus prècisement d'un **opérateur d'insertion**.
    
 * `std::endl`
 	***'endl'*** pour fin de ligne ou *"endline"*. Retourne à la ligne et **vide la mémoire tampon (flush).**

L'utilisation de plusieurs `std::cout` n'utilise qu'un seul objet *cout*. Le *cout* est donc toujours le même, cela ne créera pas deux *cout* différents !

### Les caractères :
---
#### L'affichage des `char` :

Les autres flux de sortie pour les caractères sont :

 * `cerr`
 	Représente la **sortie standard d'erreur**.

 * `clog`
 	Pour *"character logging"*. Représente la **sortie standard des log** **(informations contenues dans un fichier externe pour l'analyse des erreurs d'un programme)**.

#### L'affichage des `wchar` :

Pour gérer les caractères spéciaux (`wchar`), des flux de sortie spécifiques existent :
	
 * `wcout`

 * `wcerr`

 * `wclog`

 Leurs fonctions sont identiques dans leurs utilisations que pour celles des `char`.

### Les nombres :
---
#### Les formats d'affichage des nombres :

Il est possible de modifier sur le flux de sortie standard (`cout`) le format d'affichage des nombres qui seront affichés par la suite. Les formats d'affichage sont les suivants :

 * `std::hex`
 	Format hexadécimal.

 * `std::oct`
 	Format octal.

 * `std::dec`
 	Format décimal.

 * `std::defaultfloat`
 	Format flottant.

 * `std::scientific`
 	Format scientifique.

 * `std::fixed`
 	Format fixe.

#### L'affichage d'un booléen :

Il est possible d'afficher/masquer la valeur d'un type booléen :

 * `std::boolalpha`
 	Affiche le type booléen.

 * `std::noboolalpha`
 	Masque le type booléen.

#### L'affiche après la virgule d'un nombre décimal :

Il est possible d'afficher/masquer les valeurs après la virgule d'un nombre de type décimal :

 * `std::showpoint`
 	Affiche les valeurs après la virgule.

 * `std::noshowpoint`
 	Masque les valeurs après la virgule.

#### L'affichage du signe d'un nombre :

Il est possible d'afficher/masquer le signe d'un nombre arithmétique :

 * `std::showpos`
 	Affiche le signe.

 * `std::noshowpos`
 	Masque le signe.

#### L'affichage en majuscule :

Il est possible d'afficher/masquer l'affichage scientifique ou héxadécimal en majuscule :

 * `std::uppercase`
 	Affiche en majuscule

 * `std::nouppercase`
 	Affiche en minuscule

### Le sens de remplissage des espaces vides :
---
Il est possible de modifier le sens de remplissage des espaces vide lors de l'affichage :

 * `std::right`
 	Remplit les espaces à droite.

 * `std::left`
 	Remplit les espaces à gauche.

 * `std::internal`
 	Remplit les espace en les insérants à l'intérieur.

### L'affichage par `<iomanip>` :
---
`<iomanip>` est une library très importante qui fournie des **manipulateurs de paramètres**.

#### Remplissage d'espaces vides :

Il est possible de remplir des espaces vides lors de l'affichage :

 * `std::setw(n)`
 	Remplit n espace vide.

#### Remplissage de caractères :

Il est possible de remplir des caractères lors de l'affichage :

 * `std::setfill('c')`
 	Remplit n caractère *'c'*. L'utilisation est lié a `setw()`. Exemple d'utilisation :

```c++
// Remplit 10 '-' à l'écran suivit du nom 'Dylan'
std::cout << std::setfill('-') << std::setw(10) << "Dylan" << std::endl;
```

#### L'affichage d'une variable :

Les variables peuvent être directement affichées via `std::cout`. Cela est beaucoup plus rapide que d'afficher avec un `printf` et `%d`, `%f`, `%c`, etc, ...

Exemple :

```c++
// Affiche 255 à l'écran
maVariable = 255;
std::cout << maVariable << std::endl;
```

## Les variables et les constantes
---
Il est recommandé en C++ de **déclarer et initialiser les variables au moment de leur première utilisation** et non au tout début du programme, comme c'est le cas en C.

Les types de variables sont les même qu'en C. Cependant leurs déclarations change en C++.

### La déclaration et l'initialisation :
---
Il est toujours possible de faire la déclaration et l'initialisation en *"Camel case"* (convention standard d'écriture C). 

Exemple :

```c++
int camelCase = 22;
```

Il existe la déclaration et l'initialisation en 'syntaxe parenthèse' :

```c++
int camleCase(22);
```

Et enfin, il existe en C++ une nouvelle syntaxe qui n'existe pas en C, la 'syntaxe crochet' :

```c++
int camleCase{22};
```

Il est recommandé en C++ d'utiliser la **dernière syntaxe** qui est la plus moderne et la **plus optimale** pour le compilateur.

### Les constantes :
---
Les constantes se déclarent et s'initialisent de la même manière qu'en langage C. A savoir commme ceci :

```c++
// TOUJOURS EN MAJUSCULE
const int CONST = 5;
```

Il existe en C++ une nouvelle constante qui s'utilise de la même manière que `const` :

```c++
constexpr int CONST = 5;
```
* `constexpr` se traduit par "constante d'expression". Il s'agit d'un type de constante particulière.

### Le typage dynamique :
---
Le langage C++ prend en charge la **déclaration de type dynamique** (à l'image de Python) avec l'attribut `auto`. 

Exemple :

```c++
auto data = 12;
/*
* Le compilateur va déduire automatiquement le type de la variable.
* Dans ce cas si, la variable sera de type entier.
*/
```

Pour connaitre le type déduit, il existe une fonction qui **déduit le type d'une variable passé en paramètre**. Il s'agit de la fonction `decltype()`.
Exemple :

```c++
decltype(auto) data = 12;
/*
* decltype va déduire que data est de type int (normalement).
*/
```

La fonction `decltype` peut également **donner le type déduit de la variable à une autre variable** de la manière suivante :

```c++
int oldData = 12;
decltype(oldData) newData{0};
/*
* Ici la fonction decltype déduit que oldData est de type int,
* il donne ensuite le type entier à la variable newData
* qui sera initialisé à 0.
*/
```

### Forcer/Renforcer le typage :
---
Pour être encore plus précis concerant le *typage* d'une variable, il est possible en C++ d'ajouter un "suffixe" à la valeur de cette variable.

Les suffixes sont :

 * `u`, `U` pour `unsigned`.

```c++
usigned int data = 10u;		usigned int data = 10U;
```

 * `l` ou `L` pour `long int` ou `long double`.

```c++
long data = 7842963469l;	double data = 835265263824527L;
```

 * `ll`, `LL` pour `long long int`.

```c++
long long data = 8352675890065263824527LL;
long long data = 8352675890065263824527ll;
```
 * `f`, `F` pour `float`.

 ```c++
float data = 32.0f;		float data = 32.0F;
 ```
 Il faut **obligatoirement indiquer la virgule concernant le float**.

### Les *casts*
---
Le *casting* classique se fait de la même manière qu'en C, à savoir :

```c++
float data = 32.2;
data = (int)data;   // on cast en int
```

ou alors :

```c++
float data = 32.2;
data = int(data);
```
Le *cast* est un outil dangereux qu'il faut éviter d'utiliser le plus possible pour éviter la perte d'information (surtout si vous ne savez pas ce que vous faite !). Mais le C++ ajoute la possibilité de faire un ***cast* static activé à la compilation** :

```c++
const auto data = static_cast<int>{10}
```

Il est possible de faire du *cast* sur une donnée constante et ne plus la rendre constante l'espace d'un moment. On peut aussi *'caster'* des pointeurs (***cast* dynamique**).

### La library `<limits>`
---
Il est possible de savoir la valeur maximum que l'on peut stocker dans un type. Exemple :

```c++
// Affiche la valeur 2 147 483 64
std::cout << std::numeric_limits<int>::max() << std::endl;
```

 * `numeric_limits`
	C'est une classe qui fournit des informations sur les propriétés des types arithmétiques. Elle possède de nombreuses méthodes.

 * `max()`
	C'est une des méthodes de la classe `numeric_limits`. Elle renvoie la valeur maximale que peut prendre le type placé en paramètre.

D'autres exemples de méthodes sont :
 
 * `min()`
 	Pour connaitre le valeur minimale que peut prendre le type placé en paramètre.

 * `is_signed()`
 	Pour savoir si le type est signé.

 * `is_integral()`
 	Pour savoir si le type est un intégral.

 * `is_const()`
 	Pour savoir si le type est constant.

## Saisie utilisateur
---
L' affichage se fait par le biais du **flux d'entrée** toujours à l'aide de la classe `std` mais avec l'objet `cin` cette fois. Un type de saisie utilisateur serait par exemple :

```c++
int n{0};

std::cout << "Entrez un nombre : " << std::endl;
std::cin >> n;
std::cout << "Vous avez entré : " << n << std::endl;
/*
* On demande à l'utilisateur d'entrer un nombre  	> exemple : 64
* On stock sa valeur dans la variable n 			> n = 64
* On affiche la valeur du nombre que l'on a stocké 	> Vous avez entré : 64
*/
```

Veuillez noter qu'ici, on a vidé le *buffer*/tampon avec `std::endl`. Ce qui veux dire, que si l'on voudrait faire une nouvelle lecture avec `std::cin`, le programme demandera la saisie d'une nouvelle information, puisqu'il n'y a plus rien à lire dans le *buffer* !

Maintenant si l'utilisateur entre plusieurs nombres :

```c++
int n{0};

std::cout << "Entrez un nombre : " << std::endl;
std::cin >> n;
std::cout << "Vous avez entré : " << n << std::endl;
/*
* On demande à l'utilisateur d'entrer un nombre 	> exemple : 56 78 14
* On stock la valeur dans la variable n 			> n = 56
* On affiche la valeur du nombre que l'on a stocké	> Vous avez entré : 56
*/
```

Pourquoi n vaut 56 et pas 56 78 14 ? Où sont passé les deux autres nombres 78 et 14 ?

Au départ, notre programme attend une entrée au clavier donné par l'utilisateur. Celui-ci étant maladroit, il entre 56 78 et 14. Seulement, notre lecture s'arrête lorsqu'elle arrive à une fin de chaîne, à un retour chariot ou à un espace blanc. Nous allons donc stocker 56 dans le *buffer*. Ensuite, nous allons extraire ce qui stocké dans ce *buffer* avec `<<` et le vider complétement avec `std::endl`. n prendra alors la valeur 56 et notre *buffer* sera vide.

Maintenant, imaginons que l'on répète le `std::cin >> n` une nouvelle fois avec l'exemple prècédent. Que ce passerait-il ? Le programme attendrait-il une nouvelle information au clavier ? Ou n prendrait-il directement la valeur 78 ?

Et bien, n prendrait directement la valeur 78.
En effet, à la fin de notre exemple n vaut 56 et notre *buffer* est vide. Mais il reste toujours des informations en entrée. Une fois notre *buffer* vidé par `std::endl`, si l'on fait `std::cin >> n`, le *buffer* contiendra 78 (uniquement !). On affiche ensuite cette valeur à l'écran et on revide le *buffer* avec `std::endl`.
Si l'on rèpete cette action une troisième fois. n prendra la valeur 14. Ce n'est donc seulement qu'à la quatrième fois que le programme attendra une nouvelle entrée par l'utilisateur.

### Les méthodes de `cin`
---
Tout comme `cout`, `cin` est un objet qui possède de nombreuses méthodes. Parmis elles, l'on peut citer :

 * `clear()`
    Cette méthode permet à `cin` de retourner à un état de départ (son état d'origine) qu'elle que soit son état actuelle. `cin` sera prêt à être utilisé.

 * `ignore()`
    Elle qui ignore les caractères. Elle peut également prendre en paramètre le nombre de caractère à ignorer et un **"délimiteur"** qui stoppera la méthode.
```c++
// ignore les 50 premiers caractères jusqu'à rencontrer un espace
std::cin.ignore(50, " ");
```

 * `getline(<flux>, <string>, <delimiter>)`
    Récupère une chaîne de caractère jusqu'à arriver à un `'\n'`. Elle prend en paramettre un flux (ici `std::cin`), une chaîne de caractère de type `string` dans laquelle on stockera la ligne, et éventuellement un délimiteur. Sans délimiteur la méthode s'arrête au premier `'\n'`.
```c++
std::string name{};
std::cout << "Entrez votre nom :" << std::endl;
std::getline(std::cin, name)
std::cout << "Votre nom est " << name << std::endl
/*
* De cette manière, si l'utilisateur entre un nom composé
* ou son nom et prénom "Dylan HARAL"
* name contiendra "Dylan HARAL" et pas "Dylan".
*/
```

#### Les états de `cin`
---
L'objet `cin` peut avoir plusieurs **états** qui le définissent à un instant donné. Ces états peuvent être vérifiés par des méthodes. Ces méthodes retournent toutes un booléen. Ces méthodes sont :

 * `good()`
    Retourne *true* si le flux est valide. *false* dans le cas contraire.
 * `bad()`
    Retourne *true* s'il y a une erreur sur le flux (exemple : une erreur de saisie). *false* dans le cas contraire.
 * `fail()`
    Retourne *true* s'il y a une erreur de flux ou que la dernière opération effectuée avec `cin` à échoué. *false* dans le cas contraire.

> Note : inutile de tester avec `fail()` si `bad()` retourne *true*.
    
|           |      good()     |      bad()      |         fail()        |
| :-------- | :-------------: | :-------------: |   -----------------:  |
| good()    |      true       |      false      |         false         |
| bad()     |      true       |       true      |   false **OR** true   |
| fail()    |      true       |       true      |          true         |