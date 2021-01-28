---
layout: post
title: Algorithme de Dijkstra (Problème du plus court chemin)
---

Salut! Bienvenu sur ce nouvel article, aujourd'hui nous allons explorer l'un des problèmes les plus courants en théorie des graphes: le problème du ***plus court chemin***(PCC).

Avez-vous déjà voulu vous déplacer d'un point **A** à un point **B** et vous vous êtes demandé quel est le plus court chemin à emprunter? Il existe plusieurs algorithmes en théorie des graphes pour résoudre ce problème parmi lesquels: l'algorithme de **DIJKSTRA**.


### Principe de l'algorithme de DIJKSTRA

En réalité l'algorithme prend en entrée un graphe(orienté ou non) dont-il calcule à partir d'un sommet donné, les distances minimales vers tous les autres sommets du graphe.
En fait il s'agit de construire progressivement un sous-graphe dont les sommets sont classés par ordre croissant en fonction de leurs distance minimale par rapport au sommet d'origine (Je sais que ça peut sembler un peu flou pour l'instant mais ne vous inquiétez pas, tout deviendra plus clair au fur et à mesure).

Au départ on initialise les distances de tous les sommets par rapport au sommet de départ à l'infini, sauf celle du sommet de départ qui est initialisée à 0.

Au cours de chaque itération, on choisit en dehors du sous-graphe un sommet de distance minimale et on l'ajoute au sous-graphe. Ensuite, on met à jour les distances des sommets voisins de celui ajouté. La mise à jour s'opère comme suit : la nouvelle distance du sommet voisin est le minimum entre la distance existante et celle obtenue en ajoutant le poids de l'arc entre sommet voisin et sommet ajouté à la distance du sommet ajouté.

On continue ainsi jusqu'à épuisement des sommets (ou jusqu'à sélection du sommet d'arrivée).

###### Bon trêve de mondanités, passons à la pratique.

Dans l'exemple du graphe ci-dessous, on va rechercher le chemin le plus court menant de **A** à **E**.

![graphe]({{ site.baseurl }}/images/Dijkstra/graphe.png)

Après observation du graphe, vous avez dû remarquer que c'est le chemin A-->C-->E. Appliquons l'algorithme de Dijkstra pour vérifier cela.

###### <u>Initialisation:</u>

On construit un tableau ayant pour colonnes chacun des sommets du graphe. On ajoute à gauche une colonne qui recensera les sommets choisis à chaque étape (les éléments de cette colonne constituerons les sommets du sous-graphe dont on parlait plus haut).

Puisqu'on part du sommet A, on initialisera sa colonne avec 0 et celles des autres colonnes avec infini.

|   | A | B | C | D |
|---|---|---|---|---|
|   |   |   |   |   |
|   |   |   |   |   |
|   |   |   |   |   |