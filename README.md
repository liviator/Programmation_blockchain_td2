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

En ce qui concerne la deuxième partie. Nous avons tout d'abord utilisé la fonction pbkdf2_hmac de la bibliothèque hashlib avec comme mode de chiffrement le SHA-512 pendant 2048 ittération en utilisant comme salt "mnemonic" afin de générer la root seed depuis notre liste de 12 mots.

Nous avons ensuite encore utilisé le SHA 512 afin de générer la master private key ainsi que le master chain code.
Nous n'avons malheureusement pas réussi à générer de public key à partir d'une private key. Nous avons donc utilisé notre private key comme remplacement de la public key. Un axe d'amélioration de notre programme serait ainsi de determiner cette public key.
Pour la génération des clé children. Nous avons utilisé le SHA-512 avec comme input notre private key, notre chain code ainsi qu'un index sur 32bit. 
Nous avons également fais une déclinaison de cette fonction qui utilise également un entier correspondant la dérivation de l'enfant. Ainsi, par recursivité, nous arrivons à obtenir un enfant à un index précis dérrivant lui même d'un enfant à cet index etc 


# Temps passé sur le projet: Ensemble : 10H Séparé : environ 4-5h chacun

Nous avons eu du mal à trouver certaines informations très importante et nous aurions aimé avoir une doc peut être un plus concise 
