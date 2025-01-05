Bienvenue dans le **Jeu du Nim** ! Ce projet est développé dans le cadre de la SAE1.02 
et implémente une version interactive du jeu du Nim avec différents niveaux de difficulté.

## Utilisation

- Suivez les instructions à l'écran pour configurer le jeu.
- Choisissez parmi les différentes options pour jouer contre l'ordinateur à différents niveaux de difficulté.
- Atteignez le puits représenté par l'emoji 🚩 pour gagner la partie.

  ========================================================================================================================
  ||  Jeu du Nim - SAE 1.02 - Ahmet BASBUNAR - 2024-2025                                                                ||                    
  ||====================================================================================================================||
  || Voici la Liste des fonctions pour le jeu du Nim:                                                                   ||
  ||====================================================================================================================||
  || < Lire_Entier >             - Permet de lire un entier et de le valider entre deux bornes.                         ||
  || < Parametres >              - Permet de lire les paramètres du jeu.                                                ||
  || < Voisines >                - Construit la liste des cases voisines d'une case donnée.                             ||
  || < Hasard >                  - Génère un déplacement au hasard.                                                     ||
  || < Nimber >                  - Calcule le nimber d'une case donnée.                                                 ||
  || < Coup_Joueur >             - Permet au joueur humain de choisir une destination parmi les voisines possibles.     ||
  || < Coup_Ordi_Hasard >        - Permet à l'ordinateur de choisir un coup au hasard.                                  ||
  || < Coup_Ordi_Gagnant >       - Permet à l'ordinateur de jouer un coup gagnant.                                      ||
  || < Affiche_Grille >          - Affiche la grille de jeu avec des bordures.                                          ||
  || < main >                    - Assemble l’ensemble et exécute la partie.                                            ||
  ========================================================================================================================

  ======================================================================================================
  ||  Couleurs ANSI Utilisées dans le jeu du Nim                                                      ||
  ||==================================================================================================||
  || < \033[31m - Rouge >        - Utilisé pour les messages d'erreur                                 ||
  || < \033[32m - Vert >         - Utilisé pour les messages de succès                                ||
  || < \033[33m - Jaune >        - Utilisé pour les messages de prompt                                ||
  || < \033[34m - Bleu >         - Utilisé pour les titres et séparations                             ||
  || < \033[35m - Magenta >      - Utilisé pour les choix du joueur                                   ||
  || < \033[36m - Cyan >         - Utilisé pour les messages spécifiques (créateur, choix du joueur)  ||
  || < \033[0m  - Reset >        - Reset les couleurs au défaut du terminal                           ||
  ======================================================================================================

  ======================
  || symboles :       ||
  ||   -> pion  : ♟   ||
  ||   -> puits : 🚩  ||
  ||   -> fin   : 🔴  ||
  ||   -> case  : -   ||
  ======================
  
  ||||        Prévisualisation :       ||||



  || A. Grille de Jeu (5x5) :            ||

  
          1   2   3   4   5              1   2   3   4   5              1   2   3   4   5
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+
      1 | ♟ | - | - | - | - |        1 | - | - | - | - | - |        1 | - | - | - | - | - |
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+
      2 | - | - | - | - | - |        2 | - | - | - | - | - |        2 | - | - | - | - | - |
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+
      3 | - | - | - | - | - |        3 | - | - | - | - | ♟ |        3 | - | - | - | - | - |
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+
      4 | - | - | - | - | - |        4 | - | - | - | - | - |        4 | - | - | - | - | - |
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+
      5 | - | - | - | - | 🚩|        5 | - | - | - | - | 🚩 |        5 | - | - | - | - | 🔴|
        +---+---+---+---+---+          +---+---+---+---+---+          +---+---+---+---+---+

  || B.   Tableau des Nimbers (5x5) :    ||

          1   2   3   4   5
        +---+---+---+---+---+
      1 | 0 | 1 | 1 | 0 | 1 |
        +---+---+---+---+---+
      2 | 1 | 0 | 1 | 1 | 0 |
        +---+---+---+---+---+
      3 | 1 | 1 | 0 | 1 | 1 |
        +---+---+---+---+---+
      4 | 0 | 1 | 1 | 0 | 1 |
        +---+---+---+---+---+
      5 | 1 | 0 | 1 | 1 | 0 |
        +---+---+---+---+---+

||   - Description :                                                                                       
||     - Chaque case du tableau représente le nimber de la case correspondante dans la grille de jeu.      
||     - Un nimber de `0` indique une position perdante, si le prochaine coup est joué par l'ordinateur.   
||     - Un nimber de `1` indique une position gagnante, si le prochaine coup est joué par le joueur.      

