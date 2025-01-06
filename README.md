Jeu du Nim
Bienvenue dans le Jeu du Nim ! Ce projet a été développé dans le cadre de la SAE1.02 au Département Informatique de l'IUT pour l'année académique 2024-2025. Il s'agit d'une implémentation interactive du jeu du Nim en langage C, permettant de jouer contre l'ordinateur avec différents niveaux de difficulté.

Table des Matières
Description du Jeu
Fonctionnalités
Paramètres du Jeu
Stratégie Gagnante
Installation
Utilisation
Fonctions Principales
Exemple d'Exécution
Auteurs
Licence
Description du Jeu
Le Jeu du Nim oppose deux joueurs autour d'une grille quadrillée composée de nlig lignes et de ncol colonnes.

Début de Partie : Un pion est placé dans la case de coordonnées (1, 1).
Objectif : À tour de rôle, chaque joueur doit déplacer le pion soit d'une ou deux cases vers la droite, soit d'une ou deux cases vers le bas.
Puits : Le pion termine irrévocablement sa course dans la case (nlig, ncol), appelée puits.
Gagnant : Le joueur qui fait tomber le pion dans le puits est déclaré vainqueur.
Ce jeu appartient à la famille des jeux de Nim, caractérisés par la possibilité de déterminer une stratégie gagnante.

Fonctionnalités
Modes de Jeu : Jouez contre l'ordinateur avec quatre niveaux de difficulté.
Interface Colorée : Utilisation de couleurs ANSI et d'emojis pour une meilleure expérience visuelle.
Validation des Entrées : Le programme vérifie la validité des entrées utilisateur pour éviter les erreurs.
Stratégie Gagnante : L'ordinateur peut appliquer une stratégie optimale basée sur les nimbers.
Paramètres du Jeu
Lors de la configuration d'une partie, le joueur doit saisir les paramètres suivants :

Nombre de Lignes (nlig) : Entre 5 et 30 inclus.
Nombre de Colonnes (ncol) : Entre 5 et 30 inclus.
Niveau de Difficulté (niveau) : De 1 à 4.
Niveau 1 : Débutant – L'ordinateur joue toujours au hasard.
Niveau 2 : Moyen – L'ordinateur joue au hasard 2/3 du temps et cherche un coup gagnant 1/3 du temps.
Niveau 3 : Expert – L'ordinateur joue au hasard 1/3 du temps et cherche un coup gagnant 2/3 du temps.
Niveau 4 : Virtuose – L'ordinateur joue toujours de manière optimale en cherchant un coup gagnant.
Qui Commence (next) : Choix entre l'ordinateur (1) ou le joueur (2).
Stratégie Gagnante
La stratégie gagnante repose sur le calcul des nimbers de chaque case de la grille.

Voisines d'une Case
Une case c' est voisine d'une case c si un pion placé en c peut être déplacé en c' selon les règles du jeu.

Calcul des Nimbers
Nimber du Puits : Fixé à 0.
Autres Cases :
Si toutes les voisines d'une case ont un nimber égal à 1, alors le nimber de cette case est 0.
Sinon, le nimber est 1.
Position Nulle
Position Nulle : Le pion est dans une case de nimber 0. C'est une position perdante si l'adversaire joue de manière optimale.
Position Non Nulle : Le pion est dans une case de nimber 1. C'est une position gagnante, car il existe un mouvement vers une position nulle.
Installation
Prérequis
Compilateur C : GCC ou tout autre compilateur compatible.
Terminal Supportant ANSI : Pour afficher les couleurs et les emojis correctement.
Compilation
Clonez le dépôt GitHub et compilez le programme :

bash
Copier le code
git clone https://github.com/ahmetbsbnr/SAE1.02.git
cd SAE1.02
gcc -o jeu_nim jeu_nim.c
Utilisation
Exécutez le programme compilé :

bash
Copier le code
./jeu_nim
Suivez les instructions à l'écran pour configurer et jouer une partie.

Fonctions Principales
Voici la liste des fonctions principales implémentées dans ce projet :

Lire_Entier : Lit un entier et le valide entre deux bornes.
Parametres : Lit les paramètres du jeu.
Voisines : Construit la liste des cases voisines d'une case donnée.
Hasard : Génère un déplacement aléatoire.
Nimber : Calcule le nimber d'une case donnée.
Coup_Joueur : Permet au joueur humain de choisir une destination parmi les voisines possibles.
Coup_Ordi_Hasard : Permet à l'ordinateur de choisir un coup aléatoire.
Coup_Ordi_Gagnant : Permet à l'ordinateur de jouer un coup gagnant.
Affiche_Grille : Affiche la grille de jeu avec des bordures.
main : Assemble l’ensemble et exécute la partie.
Exemple d'Exécution
plaintext
Copier le code
==================================================================
================== Bienvenue dans le jeu du Nim ! ==================
==================================================================
================== Créateur : Ahmet BASBUNAR ======================
==================================================================
=> Le but est d'atteindre le puits de la grille
=> en choisissant des cases voisines, et avec une certaine stratégie
==================================================================
==> Veuillez saisir les Paramètres du jeu :
==================================================================
==> Entrez le nombre de lignes ( entre 5 et 30 )   : 5
==================================================================
==> Entrez le nombre de colonnes ( entre 5 et 30 )  : 5
==================================================================
==> Choisissez un niveau de 1 à 4 : 2
==================================================================
---------------------- Qui commence le jeu ? ---------------------
==================================================================
==> Qui commence le jeu ? L’ordinateur (1) ou le joueur (2) : 2
==================================================================
==================================================================
====================== La partie COMMENCE ! ======================
==================================================================
   1   2   3   4   5
   +---+---+---+---+---+
 1 | ♟ | - | - | - | - |
   +---+---+---+---+---+
 2 | - | - | - | - | - |
   +---+---+---+---+---+
 3 | - | - | - | - | - |
   +---+---+---+---+---+
 4 | - | - | - | - | - |
   +---+---+---+---+---+
 5 | - | - | - | - | 🚩 |
   +---+---+---+---+---+

A toi de jouer !
Choisir la destination :
1:(1,2)
---------
2:(1,3)
---------
3:(2,1)
---------
4:(3,1)
---> 3

   1   2   3   4   5
   +---+---+---+---+---+
 1 | - | - | - | - | - |
   +---+---+---+---+---+
 2 | O | - | - | - | - |
   +---+---+---+---+---+
 3 | - | - | - | - | - |
   +---+---+---+---+---+
 4 | - | - | - | - | - |
   +---+---+---+---+---+
 5 | - | - | - | - | 🚩 |
   +---+---+---+---+---+

L’ordinateur déplace le pion en (2,3)

... [Suite de la partie]
Auteurs
Ahmet BASBUNAR
Licence
Ce projet est sous licence MIT.
