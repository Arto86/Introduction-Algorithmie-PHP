# **1** Représentation interne des instructions et des données


## Base 2 et 10


1. **Base 10**

Pour convertir le binaire en valeur décimal il faut utiliser les puissances de 2.

La plus petite valeur est la plus à droite on l'appelle **bit de poids faible**.
La plus grande valeur est la plus à gauche on l'appelle **bit de poids fort**.

Valeur décimal 1234 :
` 1*10³ + 2*10² + 3*10¹ + 4*10⁰ = 1000 + 200 + 30 + 4 = 1234 `


2. **Base 2**

En **décimal** même principe avec les puissances de 10.

Valeur binaire 11 :
` 1*2¹ + 1*2⁰ = 2 + 1 = 3 `

> Une notation en **indice** (nombres en retrait en bas comme tel : $11_{(2)}=3_{(10)}$ ) est souvent utilisé pour indiquer les conversions


3. **Format 8 bits**

Exemple de valeur binaire codé sur 8 bits :
` 2⁷ + 2⁶ + 2⁵ + 2⁴ + 2³ + 2² + 2¹ + 2⁰ = 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255 `

> Donc : $11111111_{(2)}=255_{(10)}$

Il y a 256 valeurs possibles dans 8 bits, de 0 à 255.
Nous pouvons aussi l'écrire de cette manière **2<sup>n</sup>**. <sup>n</sup> étant le nombre de bits contenus dans la valeur binaire.

> Il faut bien noter que la valeur **maximale** convertie en décimal est 2<sup>n</sup>-1


4. **Conversion d'un décimal ($\neq$ base 10) à la base 2**

- On divise successivement par 2, ensuite, avec les restes alignez les 0 et les 1 en partant du dernier reste obtenu vers le premier :
    - 183/2=91, reste 1;
    - 91/2=45, reste 1;
    - 45/2=22, reste 1;
    - 22/2=11, reste 0;
    - 11/2=5, reste 1;
    - 5/2=2, reste 1;
    - 2/2=1, reste 0;
    - 1/2=0, reste 1;

En partant du dernier résultat : 10110111

> Depuis les années 2000 les ordinateurs peuvent manipuler des nombres sur 64 bits = 2<sup>64</sup> = 18 446 744 073 709 551 616 soit plus de 18 milliards de milliards.

> L'idée d'utiliser 2 valeurs pour encoder d'autre valeurs remonte à **Francis Bacon** (1623).  Le "bilitère" composé de 2 lettres groupés par cinq : AAAAA = A, AAAAB = B, BABBB = Z. L'alphabet latin contenait 24 lettres (i = j et u = v).


## Les octets et les mots

1 octet = 8 bits (2⁸ = 256 valeurs).

> Pendant longtemps 256 valeurs suffisait à représenter les chiffres, lettres et symboles des alphabets occidentaux.

Avec les progrès informatiques certains microprocesseurs peuvent manipuler des valeurs atteignant jusqu'à 128 bits (16 octets) et plus. Ces valeurs devenant de plus en plus difficiles à décrire et à représenter, on parle maintenant de **mot** mémoire.

> Le bit est l'unité de mesure de l'information (0 ou 1), tandis que le mot (word en anglais) est l'unité de travail du CPU (processeur). On peut le voir comme **la taille de la main** du CPU.

Certains CPU font une différence entre divers types de mots (Par exemple les 68000 de Motorola utilisent des mots de 16 bits, et des mots longs (long word) de 32 bits).

!! Suivant le type de CPU l'ordre des mots est différent de l'ordre "logique". Par exemple sur un microprocesseur x86 en mode réel (16 bits), où, 1 mot = 16 bits = 2 octets, la valeur décimale 38457 (1001011000111001<sub>(2)</sub>), pour être stockés prend 2 octets ( Puisque > à 255 (1 octet) et < à 65 535 (2 octets) ) l'octet de poids faible (8 premiers bits), sera placé dans la première case mémoire et l'octet de poids fort ira à la case suivante (Idem pour 32 et 64 bits).

| **Case mémoire 1** | **Case mémoire 2** |
| :--- | :--- |
| 00111001 | 10010110 |


## L'hexadécimal

Si on reprend l'exemple d'une valeur de 64 bits en binaire il faut **64** 0 ou 1 pour la décrire. En décimal il en faut **20**. Ça prend de la place et c'est difficile à manipuler. C'est pour cela que l'on utilise en informatique une base hexadécimal<sub>(16)</sub> (de 0 à 9 puis de A(10) à F(15)).

- Donc:
    - 1 caractère hexadécimal (de 0 à F) représente exactement 4 bits (car 2⁴ = 16).
    - Pour 64 bits, on fait donc le calcul : 64/4 = 16.

| Décimal | Hexadécimal | Binaire |
| :--- | :--- | :--- |
| 0 | **0** | `0000` |
| 1 | **1** | `0001` |
| 2 | **2** | `0010` |
| 3 | **3** | `0011` |
| 4 | **4** | `0100` |
| 5 | **5** | `0101` |
| 6 | **6** | `0110` |
| 7 | **7** | `0111` |
| 8 | **8** | `1000` |
| 9 | **9** | `1001` |
| 10 | **A** | `1010` |
| 11 | **B** | `1011` |
| 12 | **C** | `1100` |
| 13 | **D** | `1101` |
| 14 | **E** | `1110` |
| 15 | **F** | `1111` |

> On utilise 0x en préfixe devant un hexadécimal pour ne pas confondre 10<sub>(10)</sub> et 10<sub>(16)</sub>. Exemple : 0x10 = 16.

### Conversion Décimal ↔ Hexadécimal

- **10 → 16 :** Diviser le nombre par 16 successivement et noter les restes de bas en haut (10=A, 11=B, etc.).
- **16 → 10 :** Multiplier chaque chiffre par $16^{position}$ (en partant de 0 à droite) et additionner les résultats.
- **Exemple 8C :** $(8 \times 16^1) + (12 \times 16^0) = 128 + 12 = 140$.

> À savoir, sur différentes machines et systèmes d'exploitations il est possible de voir différentes base que les trois vus.

# **2** L'algorithmique

## Programmer c'est un art

On peut voir la programmation comme de la cuisine. À moins d'avoir la science innée des mélanges (Ou d'avoir pratiqué pendant longtemps), vous aurez beau avoir les meilleurs instruments de cuisine/ordinateurs ou les meilleurs ingrédients/langages de programmation, sans recette/technique le résultat ne sera jamais délicieux/optimisé.

**DÉFINITION** : Un **algorithme** est une suite d'instructions qui quand elles sont exécutées correctement aboutissent au résultat attendu.

` ### **DÉFINITION** : Un **algorithme** est une suite d'instructions qui quand elles sont exécutées correctement aboutissent au résultat attendu. `