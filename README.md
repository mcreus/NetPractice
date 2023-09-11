NETPRACTICE


11111111 11111111 11111111 11111111 (MASQUE RESEAU REPRESENTE EN BITS)







----------------------------------------------------------------------------------------------------
                 |        |             |            |           |        |       |        |       |
bits             |   1    |      2      |     3      |      4    |   5    |   6   |    7   |    8  |
                 |        |             |            |           |        |       |        |       |
-----------------|---------------------------------------------------------------------------------|
                 |        |             |            |           |        |       |        |       |
puissances de 2  |   7    |      6      |     5      |      4    |   3    |   2   |    1   |    0  |
                 |        |             |            |           |        |       |        |       |
-----------------|---------------------------------------------------------------------------------|
                 |        |             |            |           |        |       |        |       |
res. puissances  |  128   |      64     |     32     |      16   |   8    |   4   |    2   |    1  |
                 |        |             |            |           |        |       |        |       |
-----------------|---------------------------------------------------------------------------------|
                 |        |             |            |           |        |       |        |       |
add. totaux      |  128   |      192    |     224    |     240   |  248   |   252 |   254  |   255 |
                 |        |             |            |           |        |       |        |       |
---------------------------------------------------------------------------------------------------|
                 |        |             |            |           |        |       |        |       |
 Plages IP dispo |  127   |      63     |     31     |     15    |   7    |   3   |   1    |    0  |
                 |        |             |            |           |        |       |        |       |
----------------------------------------------------------------------------------------------------




Un petit aide memoire que j'ai utilise pendant mon projet pour l'adresse IP :

- J'ai, tout d'abord represente le masque reseau a 255.255.255.255 soit 11111111.11111111.11111111.111111111

- ce qui correspond a 4 fois 8 bits a 1, cela va servir par la suite pour attribuer les plages IP des reseaux.

- Ensuite j'ai effectue un tableau avec les huit bits et leur position

- A chaque fois que l'on aura un 1 on effectuera la puissance et on l'additionnera avec les autres 1 des 8 bits

- Il va ensuite falloir utiliser les puissances en base 2 mais le plus grand (2^7) est en premiere position et on redescend jusqu'a 2^0, le plus petit, en dernier.

- les trois dernieres lignes du tableau servent a calculer le nombre d'adresses IP disponibles pour un reseau :
      - La premiere est le resultat de chaque puissances.
      - La deuxieme est l'addition de chacune, c'est ce qui permettra de connaitre le nombre.

EXEMPLE :
    - Pour un masque a 255.255.255.252, il restera 3 adresses IP attribuables (255 - 252 = 3).

-!!!!!! Petite particularite, on ne peut pas attribuer la premiere adresse IP qui sera l'adresse reseau et on ne pourra pas attribuer la derniere qui est l'adresse de diffusion
  qui servira a envoyer un message a toutes les machines du reseau simultanement. !!!!!!!!

En exemple, si un masque reseau est 255.255.255.0, il y aura 255 adresses IP possibles, cependant l'adresse IP terminant par 0 est automatiquement attribuee a l'adresse
reseau et l'IP se terminant par 255 sera celle de l'adresse de diffusion. ON POURRA DONC ATTRIBUER DES IP SE TERMINANT PAR 1 A 254.

-Attention par contre a ce que les differends reseaux ne se chevauchent pas!!!


MASQUES RESEAU :
- Ils peuvent etre representes par les anciennes notations soit 255.255.255.255
- Soit par les notations CIDR (/8, /16, /24, /32)


  voici les equivalences des notations CIDR :
  - /0 -> 0.0.0.0
  - /1 -> 128.0.0.0
  - /2 -> 192.0.0.0
  - /3 -> 224.0.0.0
  - /4 -> 240.0.0.0
  - /5 -> 248.0.0.0
  - /6 -> 252.0.0.0
  - /7 -> 254.0.0.0
  - /8 -> 255.0.0.0
 
  - /9 -> 255.128.0.0
  - /10 -> 255.192.0.0
  - /11 -> 255.224.0.0
  - /12 -> 255.240.0.0
  - /13 -> 255.248.0.0
  - /14 -> 255.252.0.0
  - /15 -> 255.254.0.0
  - /16 -> 255.255.0.0
 
  - /17 -> 255.255.128.0
  - /18 -> 255.255.192.0
  - /19 -> 255.255.224.0
  - /20 -> 255.255.240.0
  - /21 -> 255.255.248.0
  - /22 -> 255.255.252.0
  - /23 -> 255.255.254.0
  - /24 -> 255.255.255.0
 
  - /25 -> 255.255.255.128
  - /26 -> 255.255.255.192
  - /27 -> 255.255.255.224
  - /28 -> 255.255.255.240
  - /29 -> 255.255.255.248
  - /30 -> 255.255.255.252
  - /31 -> 255.255.255.254
  - /32 -> 255.255.255.255
