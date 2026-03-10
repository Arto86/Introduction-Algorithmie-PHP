# **Chapitre 2**

## Les variables

### Les nombres dans une variable

Une variable est contenu dans une case mémoire (8 bits = 1 octet = 256 valeurs différents).

**Nombre réel (1.7) != Nombre entier (2)**

Un **entier** : nombre sans virgule, négatif ou positif.

Un **réels** : nombre à virgule, positif ou négatif.

#### Variable signée

Comment faire dans le cas d'un nombre **négatif** ? Le premier bit est réservé au signe et nous passons donc de 0 à 255, à, -128 à 127. Nous appelons ça une variable **signée**.

Pour de plus grandes valeurs il est possible d'allouer plusieurs cases mémoires à une variable afin de stocker de plus grande valeurs.

> 16 bits = -32768 à 32767, 32 bits = -2 147 483 648 à 2 147 483 647.

#### Variable avec nombre réels

Les nombres réels sont plus lents à manipuler que les autres et leur codage binaire est radicalement différents que les nombres entiers.

- Pour visualiser concrètement sur 32 bits :
    - Pour un entier : 1 bit de signe + 31 bits de valeur pure.
    - Pour un réel : 1 bit de signe + 8 bits d'exposant (qui place la virgule) + 23 bits de mantisse (les chiffres significatifs).

> Les entiers sont traduits directement en base 2, tandis que les nombres réels sont découpés comme une notation scientifique (norme IEEE 754) avec un signe, un exposant et une mantisse.

Tableaux des plages possibles en fonction des types numériques :
| Taille en mémoire | Type courant (C/Java) | Signé / Non signé | Valeur minimale | Valeur maximale |
| :--- | :--- | :--- | :--- | :--- |
| **8 bits** (1 octet) | `int8` / `byte` / `char` | Signé | -128 | 127 |
| **8 bits** (1 octet) | `uint8` / `unsigned char` | Non signé | 0 | 255 |
| **16 bits** (2 octets)| `int16` / `short` | Signé | -32 768 | 32 767 |
| **16 bits** (2 octets)| `uint16` / `unsigned short`| Non signé | 0 | 65 535 |
| **32 bits** (4 octets)| `int32` / `int` | Signé | -2 147 483 648 | 2 147 483 647 |
| **32 bits** (4 octets)| `uint32` / `unsigned int` | Non signé | 0 | 4 294 967 295 |
| **64 bits** (8 octets)| `int64` / `long` | Signé | -9 223 372 036 854 775 808 | 9 223 372 036 854 775 807 |
| **64 bits** (8 octets)| `uint64` / `unsigned long` | Non signé | 0 | 18 446 744 073 709 551 615 |
| **32 bits** | `float` (virgule flottante)| Signé | ~ -3.4 × 10³⁸ | ~ 3.4 × 10³⁸ |
| **64 bits** | `double` (virgule flottante)| Signé | ~ -1.7 × 10³⁰⁸ | ~ 1.7 × 10³⁰⁸ |


#### Caractères

Dans la grande majorité des cas tous les caractères nécessaires logent dans un octet. Donc pour une phrase de 50 caractères est égale à 50 octets.

> Se référer à table ASCII mais aussi les normes comme ISO UTF-8 et d'autre.

## Les opérateurs arithmétiques

- "+" : addition,
- "-" : soustraction,
- "*" / x : multiplication,
- "/" : division,
- "%" / "mod" : modulo,
- "DIV" : division entière.

> Modulo est le reste d'une division entière (9/2 = 4 reste 1 donc 9%2 = 1).
> DIV à le même principe que modulo mais à l'envers (9/2 = 4 reste 1 donc 9 DIV 2 = 3).

*Une partie de ce chapitre concerne les opérations du second degré et la calculation du delta. Ce sur quoi je ne vais pas m'attarder pour le moment.*

En PHP des fonctions mathématiques sont intégrées. Comme "**sqrt**" (racine carrée).

Mais aussi des opérateurs arithmétiques unaires :
- "++x" : Incrémente x de 1.
- "x++" : Idem mais après l'utilisation en cours.
- "--x" : Décrémente x de 1.
- "x--" : Idem mais après l'utilisation en cours.

Mise en contexte :
```php
<?php
$x = 1;

for ($i = 3; $i > 0; $i--){
    echo ++$x;
    echo $x++;
    echo $x;
}
?>
```
Ce code retourne le résultat suivant :
- 1er tour :
    - 2 ($x passe de 1 à 2, puis on l'affiche)
    - 2 (On affiche $x tel quel (qui vaut 2), ensuite, $x passe à 3.)
    - 3 (On affiche la valeur actuelle de $x, qui est maintenant de 3.)
- 2ème tour :
    - 4
    - 4
    - 5
- 3ème tour :
    - 6
    - 6
    - 7

## Les opérateurs booléens

Un **opérateur booléen** est un outil de logique (comme ET, OU, NON) qui permet de relier ou d'inverser plusieurs conditions entre elles pour déterminer si une situation finale est strictement Vraie ou Fausse.

**Pourquoi a-t-on besoin de ces opérateurs binaires ?**
Ces opérateurs sont indispensables car ils constituent le langage fondamental des processeurs, leur permettant de combiner des états électriques basiques (0 et 1) afin de prendre des décisions logiques complexes.

### Table de vérité : ET (AND)

| A | B | A ET B |
| :---: | :---: | :---: |
| Faux (0) | Faux (0) | Faux (0) |
| Faux (0) | Vrai (1) | Faux (0) |
| Vrai (1) | Faux (0) | Faux (0) |
| Vrai (1) | Vrai (1) | Vrai (1) |

---

### Table de vérité : OU (OR)

| A | B | A OU B |
| :---: | :---: | :---: |
| Faux (0) | Faux (0) | Faux (0) |
| Faux (0) | Vrai (1) | Vrai (1) |
| Vrai (1) | Faux (0) | Vrai (1) |
| Vrai (1) | Vrai (1) | Vrai (1) |

---

### Table de vérité : NON (NOT)

| A | NON A |
| :---: | :---: |
| Faux (0) | Vrai (1) |
| Vrai (1) | Faux (0) |