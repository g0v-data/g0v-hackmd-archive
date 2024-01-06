# Représentation des nombres en machine : application du cours
###### tags: `Premieres`
## Base décimale et base binaire
1) Donner la décomposition de l'entier 13<sub>10</sub>.
 13<sub>10</sub>= 10x1+10(puissance0)x3=

:::info
Pour stocker une information, les ordinateurs utilisent des circuits électroniques à deux états : présence ou absence de courant ou de tension électrique. Par convention, on représente ces deux états par les caractères 0 et 1 qui composent la base binaire. La décomposition d'un entier dans la base 2 est donc à effectuer à l'aide de puissances de 2.
:::
2. Donner la décomposition de l'entier 1101<sub>2</sub>.
3. 
4. Convertir 14<sub>10</sub> et 25<sub>10</sub> en binaire.

## Base hexadécimale
### Conversion de la base 16 vers la base 10
On veut convertir un code couleur en hexadécimal #F34DC1 au format RVB.
1) Qu'est-ce que le format RVB ?
2) Quelle base est utilisée dans la représentation des couleurs dans le format RVB. Donner un exemple.
3) Convertir #F34DC1 au format RVB.

### Conversion de la base 10 vers la base 16
On souhaite convertir la couleur codée rgb(241,19,26) en code hexadécimal.Comment doit-on procéder ?
### Conversion de la base 16 vers la base 2 
Convertir les entiers hexadécimaux suivant vers le binaire : 
- F3<sub>16</sub>
- 4D<sub>16</sub>
- C1<sub>16</sub>

### Conversion de la base 2 vers la base 16
Convertir l'entier binaire suivant en base 16 : 1011111101101001111011<sub>2</sub>.
## Integer overflow
:::success
Dans une usine, une machine qui fabrique en moyenne 200 pièces/jour, un compteur stocké sur un octet affiche le nombre de pièces produites. Quand un technicien récupère les pièces fabriquées, il vérifie que le nombre est conforme, puis appuie sur un bouton pour remettre le compteur à zéro. Un jour, le compteur affiche 21 alors que 277 pièces ont été produites. Que s'est-il passé ?
:::
1) Que signifie l'expression « integer overflow » ? Quelle est son équivalent en français ?
2) Représentez 277<sub>10</sub> en binaire. 
3) Représentez 21<sub>10</sub> en binaire et comparez-le au résultat obtenu à la question précédente. Qu'observez-vous ?
4) Proposez une solution au problème rencontré au sein de l'usine.