---
layout : page
title  :  Exploration
date   :  2019/03/19  
permalink: /travaux_pratiques/recherche/
---


## Table de matière ##

- [Introduction](#intro)
- [Bienvenue](#welcome)
- [Q1: Depth First Search](#DFS1)
- [Q2: Breadth-First-Search](#BFS)
- [Q3: Uniform Cost Search](#UCS)
- [Q4: A star](#astar)
- [Q5: Problème 4 coins: Représentation](#corners)
- [Q6: Problème 4 coins: Heuristique](#linkLabel)
- [Q7: Manger toute la nouriture: Heuristique](#alldots)






<div class="fig figcenter fighighlight">
  <img src="/assets/maze.png" width="300" height="300"> 
  <div class="figcaption">
   Exploration de pacman pour trouver atteindre son objectif final.
  </div>
</div>


## Introduction ##
<a name='intro'></a>

Dans ce projet, Votre **agent** **Pacman** doit trouver les chemins dans un
environnement `labyrinthe`. L'objectif diffère selon chaque tache. Mais en
général vous devez soit atteindre un **point défini**, soit collecter tous les **points**. L'essentiel de ce projet, est d'implémenter les algorithmes d'`exploration` d'une manière **abstraite** puis les appliquer a chaque tache en variant juste l'état **final**.

> Idem au projet  d'initiation à python, le dossier fourni propose un
`autograder.py` pour obtenir un *feedback* instantané de vos réponse.
```python
python autograder.py 
```


Le dossier de ce projet consiste en différent programmes python. Vous devez
lire est **comprendre** certains fichier **clé** pour pouvoir répondre au
questions. Vous pouvez ignorer certains fichiers (pratiquement destinés à la
préparation de votre environnement).

> **Le lien du dossier est le suivant : [search.zip](https://github.com/intelligenceartificielensaf/intelligenceartificielensaf.github.io/blob/master/travaux_pratiques/search.zip)**


### Fichiers de programmation ###

- `search.py`: L'emplacement principal de tous les algorithmes de recherche.
- `searchAgents.py` : Fichiers des agents d'exploration.


### Fichiers à lire  ###

- `pacman.py`: L'environnement principal du jeu  **pacman**, il décrit aussi
    l'ensemble des états.

- `game.py` : Toute la logique derrière l'environnement pacman. Il comporte
    plusieurs classes comme : 
    * AgentState
    * Agent
    * Direction
    * Grid
- `util.py`:  Implémentation des **structures de données** que vous pouvez
    utiliser.


> Vous pouvez ignorer le reste des fichiers et surtout ne les pas modifier.


## Bienvenue dans le monde de pacman ##
<a name='welcome'></a>

Vérifier l'état de votre projet en lançant la commande:
```python
python paman.py
```

qui vous permet de jouer à *pacman* avec des entrées clavier.


L'agent le plus simple qu'on peut implémenter dans `searchAgents.py` est un
agent appelé *GoWestAgent* qui part toujours vers l'ouest. Remarquez qu'il peut
gagner dans certains situations:

```python
python pacman.py --layout testMaze --pacman GoWestAgent
```


Mais il n'aura aucune chance, si la situation nécessite de tourner:

```python
python pacman.py --layout tinyMaze --pacman GoWestAgent
```


> A la fin de projet, votre agent pacman pourra résoudre n'importe quel
labyrinthe

## Question 1: (3 points) : Trouver un point de nouriture fixé par (DFS) ##
<a name='DFS1'></a>

Dans le fichier `searchAgents.py`, vous trouverez une *implémentation complète*
d'un `SearchAgent`, qui peut planifier un chemin dans le monde de pacman et
exécuter *étape par étape* le chemin fourni. Cependant, l'algorithme qui
implémente n'est pas encore implémenté ( *c'est votre tache*).

Avant de se lancer à votre implémentation, vérifier que votre agent peut naviguer correctement dans un
labyrinthe simple par la commande:

```python
python pacman.py -l tinyMaze -p SearchAgent -a fn=tinyMazeSearch
```

Cette commande utilise un fonctionnement *prédéfini* dans la fonction
`tinyMazeSearch`.

Une fois que cette commande est fonctionnelle, vous pouvez écrire votre
algorithme de recherche pour aider pacman à attendre son but.

> Rappeler vous, que dans la recherche en arbre, un noeud contient toutes les
> informations (chemin) pour attendre ce noeud depuis le noeud initial.


**Question**: Implémenter l'algorithme *Depth First Search*(DFS) dans le fichier
`search.py`. L'algorithme doit être implémenté dans la fonction
`depthFirstSearch`.


**Notes importantes**

<div class="notyet"> Toutes les fonctions que vous développez doivent retourner une liste d' _actions_
qui permet à l'agent d'attendre l'objectif à partir du point initial. Ces
actions doivent être des déplacements légales.
</div>


<div class="notyet">
Vous ne pouvez pas utiliser vos propres structures de données. Utilisez plutôt
ceux délivrés dans le fichier `util.py`. Car ces classes donnent des
informations nécessaires pour l'autograder.
</div>

<div class="kw"> Indice</div> Tous les algorithmes de recherche sont similaires
et diffèrent seulement dans les détails de gestion de la **frontière**. Ainsi,
concentrez vous a implémenter correctement `DFS` et le reste tombera comme des
pommes.


Votre code doit facilement trouver une solution aux problèmes:

```python
python pacman.py -l tinyMaze -p SearchAgent
python pacman.py -l mediumMaze -p SearchAgent
python pacman.py -l bigMaze -z .5 -p SearchAgent
```

Enfin pour **évaluer** votre réponse exécuter la commande:

```python
python autograder.py -q q1
```


## Question 2 (3points): Breadth First Search ##
<a name='BFS'></a>


Implémenter l'algorithme *breadth-first-search*(BFS) dans la fonction
`breadthFirstSearch` dans le fichier `search.py`. Puis tester votre code, par

```python
python pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
python pacman.py -l bigMaze -p SearchAgent -a fn=bfs -z .5
```

> Est ce que le coût de BFS est inférieur à celui de DFS? Si ce n'est pas le
cas il faut revoir l'implémentation.


Vérifier votre réponse avec l'autograder avec:

```python
python autograder.py -q q2
```


<div class="kw"> Implémentation abstraite</div>
L'un des avantage d'une implémentation abstraite (générale) est que vous pouvez
appliquer votre algorithme indépendamment du détails du problème. Comme preuve,
on pourra utiliser votre algorithme pour résoudre le problème classique *8
puzzle*

```python
python eightpuzzle.py
```
## Question 3 (3 points): Variant la fonction coût ##
<a name='UCS'></a>

Tandis que *BFS* trouve le chemin le plus court en terme de pas. Il se peut que
le meilleur chemin soit différents si on inclut d'autre facteurs:

* place dangereuse ( proche d'un fantôme) 
* pullule de puissance: ( donne une invincibilité)

Implémenter alors, la fonction *uniform cost* dans la fonction
`uniformCostSearch`.  Je vous encourage à jeter et comprendre les structures de
données figurant le fichier `utils.py` puisque vous aurez besoin de l'une de ces
structures pour implémenter *UCS*.

Tester votre implémentation par:

```python
python pacman.py -l mediumMaze -p SearchAgent -a fn=ucs
python pacman.py -l mediumDottedMaze -p StayEastSearchAgent
python pacman.py -l mediumScaryMaze -p StayWestSearchAgent
```


Puis vérifier votre réponse par:

```python
python autograder -q q3
```

## Question 4 (3points) : Exploration A*  ##
<a name='astar'></a>

Implémenter l'exploration en _A*_ dans la fonction `aStarSearch` dans le fichier
`search.py`. Cette fonction prend une *heuristique* comme argument.

<div class="kw" Information> </div>
Une heuristique est une fonction à **deux** arguments:
1. Un état (State) de l'espace de recherche.
2. Le problème entier

Jeter un coup deuil sur la fonction `nullHeuristic` pour un exemple trivial
d'une  telle fonction.


Tester votre  code avec:

```python
python pacman.py -l bigMaze -z .5 -p SearchAgent -a fn=astar,
heuristic=manhatttanHeuristic
```
> Apprécier l'efficiacité de A* contre UCS


Vérifier votre votre solution avec:

```python
python autograder -q q4
```


## Question 5 (3 points): Trouver tous les coins ##
<a name='corners'></a>

Pour montrer la supériorité de A*, nous allons considérer un problème plus
*complexe*.

Le problème de **coins d'un labyrinthe** consiste naviguer l'agent a ce qu'il
touche les 4 **coins* du labyrinthe (même si le coin ne contient pas une
nourriture).

Votre tache est de définir **l'environnement** *CornersProblem* dans le fichier
`searchAgent`. Vous devez choisir une représentation pour coder juste les
*élements nécessaires* pour détecter si l'agent à atteint son but ou non.

Tester votre implémentation par les deux commandes:

```python
python pacman.py -l tinyCorners -p SearchAgent -a fn=bfs,prob=CornersProblem
python pacman.py -l mediumCorners -p SearchAgent -a fn=bfs,prob=CornersProblem
```


<div class="kw"> Indice </div>

Vous aurez seulement besoin de stocker la position de départ de l'agent et la
position des 4 coins.


Finalement tester votre réponse par:

```python
python autograder -q q5
```

## Question 6 (3 points) Heuristique du problèmes des 4 points ##
<a name='linkLabel'></a>

Implémenter une *heuristique* **consistante**  pour le problème des *quatre
coins* dans la fonction `cornersHeuristic`.

Tester votre implémentation avec:

```python
python pacman.py -l mediumCorners -p AStarCornersAgent -z 0.5
```


<div class="notyet">
Heuristique non triviale:
</div>



Votre heuristique doit être non triviale pour recevoir une note complète. Votre
heuristique est jugé selon le nombre de nœuds développés.


 <table style="width:50%">
 <tr>
    <th>Nombre de noeuds développés</th>
    <th>Note</th>
    </tr>
    <tr>
    <td> Plus que 2000</td>
    <td>0/3</td>
    </tr>
    <tr>
    <tr>
    <td> Moins que 2000</td>
    <td>1/3</td>
    </tr>
    <td> Moins que 1600</td>
    <td>2/3</td>
    </tr>
    </tr>
    <td> Moins que 1200</td>
    <td>3/3</td>
    </tr>
</table>


## Question 7 (4 points) : Manger toute la nouriture ##
<a name='alldots'></a>


Maintenant on peut résoudre un problème plus  difficile, *prendre toute la
nouriture* par un déplacement optimal. Le problème est déjà formulé dans la
classe `FoodSearchProblem` dans le fichier `searchAgents.py`. Pour le problème
actuel, l'agent ne prend pas en considération les fantômes et les pullules de
puissance.

Tester ce problème avec l'heuristique nulle par:

```python
python pacman.py -l testSearch -p AStarFoodSearchAgent
```


Votre tache maintenant est de définir une heuristique pour aider A* a compléter
son exploration d'un manière efficace. La fonction est appelée
`foodHeuristic.py` dans le fichier `searchAgent.py`.

Essayer votre agent avec le problème:

```python
python pacman.py -l trickySearch -p AStarFoodSearchAgent
```

Finalement tester votre implémentation avec:

```python
python autograder.py -q q7
```


