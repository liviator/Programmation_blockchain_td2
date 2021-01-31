# Rapport de td Programmation blockchain 

# Introduction

Voici le rapport d'Henry Faure-Geors et Alexandre Bauchet concernant le td2 de programmation BlockChain. Vous trouverez également dans ce git notre programme python permettant d'effectuer les différentes tâches demandées.

# Partie 1 : BIP 39

Afin de genérer une seed correcte, nous avons avant tout utilisé la bibliothèque python secrets, une bibliothèque cryptographicaly strong qui nous a permit de générer un nombre composé de 128 bits aléatoire. Nous avons converti ce nombre en binaire tout en faisant attention à ce que notre fonction ne réduise pas sa taille (en supprimant les 0 tout à gauche par exemple).

Nous avons ensuite changé le type de ce nombre afin de l'utiliser dans l'algorithme SHA-256 ( de la bibliothèque python Hashlib ).
Une fois le hash récupéré, nous avons fusionné notre entropie ainsi que les 4 premiers bits du hash (checksum) afin d'obtenir une séquence de 132 bit qu'on a divisé en 12 segments.

Enfin, chaque séquence nous a permit d'obtenir un mot (la séquence convertie en décimal nous donnait un nombre inférieur a 2048 et nous avions plus qu'à aller chercher le mot situé à la xième ligne sur la BIP english word list).

Nous avons donc ainsi obtenu une liste de 12 mots qui correspondait à notre seed.

Afin de vérifier sa conformité, nous avons d'une part utilisé le site https://iancoleman.io/bip39/, mais nous avons également fais une fonction qui, avec une série de 12 mots donnés, nous permettait de retrouver l'entropy et de vérifier si le checksum était correcte


# Partie 2 : BIP 43/44



