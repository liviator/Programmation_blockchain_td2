# Rapport de td Programmation blockchain 

#Introduction

Voici le rapport d'Henry Faure-Geors et Alexandre Bauchet concernant le td2 de programmation BlockChain. Vous trouverez également dans ce git notre programme python permettant d'effectuer les différentes tâches demandées.

#Partie 1 : BIP 39

Afin de genérer une seed correcte, nous avons avant tout utilisé la bibliothèque python secrets, une bibliothèque cryptographicaly strong qui nous a permit de générer un nombre composé de 128 bits aléatoire. Nous avons converti ce nombre en binaire tout en faisant attention à ce que notre fonction ne réduise pas sa taille (en supprimant les 0 tout à gauche par exemple).



