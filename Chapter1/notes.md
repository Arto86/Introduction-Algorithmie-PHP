# **Chapitre 1**


## Base 2 et 10


1. Base 10

Pour convertir le binaire en valeur décimal il faut utiliser les puissances de 2.

La plus petite valeur est la plus à droite on l'appelle **bit de poids faible**.
La plus grande valeur est la plus à gauche on l'appelle **bit de poids fort**.

Valeur décimal 1234 :
` 1*10³ + 2*10² + 3*10¹ + 4*10⁰ = 1000 + 200 + 30 + 4 = 1234 `


2. Base 2

En **décimal** même principe avec les puissances de 10.

Valeur binaire 11 :
` 1*2¹ + 1*2⁰ = 2 + 1 = 3 `

> Une notation en **indice** (nombres en retrait en bas comme tel : $11_{(2)}=3_{(10)}$ ) est souvent utilisé pour indiquer les conversions


3. Format 8 bits

Exemple de valeur binaire codé sur 8 bits :
` 2⁷ + 2⁶ + 2⁵ + 2⁴ + 2³ + 2² + 2¹ + 2⁰ = 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255 `

> Donc : $11111111_{(2)}=255_{(10)}$

Il y a 256 valeurs possibles dans 8 bits, de 0 à 255.
Nous pouvons aussi l'écrire de cette manière **2<sup>n</sup>**. <sup>n</sup> étant le nombre de bits contenus dans la valeur binaire.

> Il faut bien noter que la valeur **maximale** convertie en décimal est 2<sup>n</sup>-1


4. Conversion d'un décimal ($\neq$ base 10) à la base 2

- On divise successivement par 2, ensuite, avec les restes alignez les 0 et les 1 en partant du dernier reste obtenu vers le premier :
    - 183/2=91, reste 1;
    - 91/2=45, reste 1;
    - 45/2=22, reste 1;
    - 22/2=11, reste 0;
    - 11/2=5, reste 1;
    - 5/2=2, reste 1;
    - 2/2=1, reste 0;
    - On prend en compte le dernier résultat (forcément 1)

En partant du dernier résultat : 10110111