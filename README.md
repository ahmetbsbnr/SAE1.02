# Jeu du Nim

Bienvenue dans le **Jeu du Nim** ! Ce projet a été développé dans le cadre de la SAE1.02 au **Département Informatique** de l'IUT pour l'année académique **2024-2025**. Il s'agit d'une implémentation interactive du jeu du Nim en langage C, permettant de jouer contre l'ordinateur avec différents niveaux de difficulté.

## Table des Matières

- [Description du Jeu](#description-du-jeu)
- [Paramètres du Jeu](#paramètres-du-jeu)
- [Stratégie Gagnante](#stratégie-gagnante)
- [Fonctionnalités](#fonctionnalités)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Fonctions Principales](#fonctions-principales)
- [Exemple d'Exécution](#exemple-dexécution)
- [Auteurs](#auteurs)
- [Licence](#licence)
- [Dépôt GitHub](#dépôt-github)

## Description du Jeu

Le **Jeu du Nim** oppose deux joueurs autour d'une grille quadrillée composée de `nlig` lignes et de `ncol` colonnes.

- **Début de Partie :** Un pion est placé dans la case de coordonnées `(1, 1)`.
- **Objectif :** À tour de rôle, chaque joueur doit déplacer le pion soit d'une ou deux cases vers la droite, soit d'une ou deux cases vers le bas.
- **Puits :** Le pion termine irrévocablement sa course dans la case `(nlig, ncol)`, appelée **puits**.
- **Gagnant :** Le joueur qui fait tomber le pion dans le puits est déclaré vainqueur.

### Exemple de Grille Initiale et Déplacements Autorisés

         1   2   3   4   5
       +---+---+---+---+---+
    1  | ♟ | - | - | - | - |
       +---+---+---+---+---+
    2  | - | - | - | - | - |
       +---+---+---+---+---+
    3  | - | - | - | - | - |
       +---+---+---+---+---+
    4  | - | - | - | - | - |
       +---+---+---+---+---+
    5  | - | - | - | - | 🚩|
       +---+---+---+---+---+


*Figure 1 – Une configuration initiale et des exemples de déplacements autorisés*

## Paramètres du Jeu

Lors de la configuration d'une partie, le joueur doit saisir les paramètres suivants :

1. **Nombre de Lignes (`nlig`) :** Entre 5 et 30 inclus.
2. **Nombre de Colonnes (`ncol`) :** Entre 5 et 30 inclus.
3. **Niveau de Difficulté (`niveau`) :** De 1 à 4.
    - **Niveau 1 :** Débutant – L'ordinateur joue toujours au hasard.
    - **Niveau 2 :** Moyen – L'ordinateur joue au hasard 2/3 du temps et cherche un coup gagnant 1/3 du temps.
    - **Niveau 3 :** Expert – L'ordinateur joue au hasard 1/3 du temps et cherche un coup gagnant 2/3 du temps.
    - **Niveau 4 :** Virtuose – L'ordinateur joue toujours de manière optimale en cherchant un coup gagnant.
4. **Qui Commence (`next`) :** Choix entre l'ordinateur (1) ou le joueur (2).

### Symboles Utilisés

- **Pion :** ♟
- **Puits :** 🚩
- **Fin de Partie :** 🔴
- **Case Vide :** -

### Couleurs ANSI Utilisées

- `\033[31m` - **Rouge :** Messages d'erreur
- `\033[32m` - **Vert :** Messages de succès
- `\033[33m` - **Jaune :** Messages de prompt
- `\033[34m` - **Bleu :** Titres et séparations
- `\033[35m` - **Magenta :** Choix du joueur
- `\033[36m` - **Cyan :** Messages spécifiques (créateur, choix du joueur)
- `\033[0m`  - **Reset :** Réinitialise les couleurs au défaut du terminal

## Stratégie Gagnante

La stratégie gagnante repose sur le calcul des **nimbers** de chaque case de la grille.

### 1. Les Voisines d’une Case

Une case `c'` est voisine d'une case `c` si un pion placé en `c` peut être déplacé en `c'`. Toute case autre que le puits possède entre 1 et 4 voisines.

### 2. Le Nimber

- **Définition :** Un nimber est un entier associé à chaque case, valant soit `0` soit `1`.
    - **Nimber 0 :** Position perdante
    - **Nimber 1 :** Position gagnante

#### Calcul des Nimbers

1. **Nimber du Puits :** Fixé à `0`.
2. **Autres Cases :** 
    - Si toutes les voisines d'une case ont un nimber égal à `1`, alors le nimber de cette case est `0`.
    - Sinon, le nimber est `1`.

### 3. La Stratégie Gagnante

- **Position Nulle :** Le pion est dans une case de nimber `0`. C'est une position perdante si l'adversaire joue de manière optimale.
- **Position Non Nulle :** Le pion est dans une case de nimber `1`. C'est une position gagnante, car il existe un mouvement vers une position nulle.

**Conséquences :**

1. **Toutes les voisines d’une case de nimber 0 sont de nimber 1.**
2. **Toute case de nimber 1 possède au moins une voisine de nimber 0.**

Pour gagner une partie, un joueur doit donc viser une position nulle dès que possible et s’y maintenir jusqu’à la fin de la partie.

### Exemple

- **Grille 5x5 :** Le joueur qui commence hérite d’une position nulle. Si le second joueur applique la stratégie gagnante, il est sûr de gagner.
- **Grille 5x7 :** Le joueur qui commence hérite d’une position non nulle, assurant sa victoire.

*Figure 2 – Tableau des Nimbers (5x5)*

## Fonctionnalités

- **Modes de Jeu :** Jouez contre l'ordinateur avec quatre niveaux de difficulté.
- **Interface Colorée :** Utilisation de couleurs ANSI et d'emojis pour une meilleure expérience visuelle.
- **Validation des Entrées :** Le programme vérifie la validité des entrées utilisateur pour éviter les erreurs.
- **Stratégie Gagnante :** L'ordinateur peut appliquer une stratégie optimale basée sur les nimbers.

## Installation

### Prérequis

- **Compilateur C :** GCC ou tout autre compilateur compatible.
- **Terminal Supportant ANSI :** Pour afficher les couleurs et les emojis correctement.

### Compilation

Clonez le dépôt GitHub et compilez le programme :

```bash
git clone https://github.com/ahmetbsbnr/SAE1.02.git
cd SAE1.02
gcc -o JeuDeNim JeuDeNim.c
```
