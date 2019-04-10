---
layout : page
title  :  Exploration Multi-agents
date   :  2019/04/09  
permalink: /travaux_pratiques/multiagent/
---

## Table de matière ##
1. [Introduction](#intro)
2. [Multi-Agent Pacman](#multiagentpacman)
3. [Agent de reflèxe](#reflexagent)
4. [MiniMax](#minimax)
5. [Elagage Alpha-Beta](#alphabeta)
6. [ExpectiMax](#expectimax)
7. [Fonction d'évaluation](#evalFunction)

 






<div class="fig figcenter fighighlight">
  <img src="/assets/pacman_multi_agent.png" width="550" height="170"> 
  <div class="figcaption">
   Pacman est maintenant entouré des phantomes. Heureusement il vient
   d'ajouter MiniMax et ExpectiMax a son arsenal.
  </div>
</div>

## Introduction ##
<a name='intro'></a>

Le but de ce projet est de concevoir un agent pour le jeu de `Pacman` contenant
des agent adverses (**Fantômes**). Vous devez implémenter  la recherche *MiniMax* et *ExpectiMax* avec différents *fonctions d'évaluations*.


Le code comporte des simples modifications de votre premier projet. Mais il est
recommandé de commencer par copie fraiche du dossier fourni plutôt que de
continuer sur l'ancien projet.


> Le lien du dossier est le suivant : [multiagent.zip](https://github.com/intelligenceartificielensaf/intelligenceartificielensaf.github.io/blob/master/travaux_pratiques/multiagent.zip)

Comme dans le premier projet, vous disposez d'un *autograder* pour vérifier vos
réponses. Ce dernier peut être invoqué pour vérifier toutes  les questions par:

```python
python autograder.py
```
Ou pour vérifier une seule question, par exemple si on veut vérifier juste la
question **1**:

```python
python autograder -q q1
```


### Fichiers de programmation ###

* `multiAgents.py` : Emplacement de vos agents de recherche.
* `pacman.py` : Le fichier principal du jeu Pacman. Ce fichier décrit le type
    **GameState**, que vous allez utiliser à plusieurs reprises.
* `game.py`: Toute la logique derrière la dynamique du monde de Pacman. Ce
    fichier décrit plusieurs type come:
  * AgentState
  * Agent
  * Direction
  * Grid
* `util.py` : Structure de données utiles pour vos algorithmes de recherche.

## Multi-Agent Pacman ##
<a name='multiagentpacman'></a>

Pour commencer, testez votre dossier en lançant une version classique du jeu:

```python
python pacman.py
```

Ensuite, lancer le jeu avec un agent *réflexe* qui figure dans la classe
`ReflexAgent`.

```python
python pacman.py -p ReflexAgent
```
On peut remarquer qu'il joue pauvrement même dans un simple labyrinthe.

Vous êtes invités à examiner le code de cet agent pour comprendre la
**structure** du jeu et son **fonctionnement**  interne.

## Question 1 (4 points): Agent de réflexe ##
<a name='reflexagent'></a>

Améliorer votre agent de réflexe dans `multiAgents.py` pour jouer mieux jouer. Le code montre plusieurs *exemples* des méthodes utiles pour **extraire** des informations du monde du jeu `GameState`. Votre agent doit considérer non seulement la position de la **nourriture** mais aussi celle des **fantômes** pour passer le test. Vous devez gagner *facilement* dans le test *testClassic*.


```python
python pacman.py -p ReflexAgent -l testClassic
```

Essayer ensuite votre agent dans le labyrinthe classique `mediumClassic` avec un
ou deux fantômes.


```python
python pacman.py -p ReflexAgent -k 1 
python pacman.py -p ReflexAgent -k 2
```


Pour accélérer la vitesse d'animation ajouter l'option `--frameTime 0`.


> Interpréter le comportement de votre agent selon la fonction d'évaluation
> considérée.


<div class="notyet">
Note: Comme caractéristiques de votre fonction d'évaluation, considérer
l'**inverse** de valeurs importantes comme (distance à la nourriture).
</div>

<div class="notyet">
Note: Votre fonction d'évaluation agit sur une pair **(État, Action)**. A la fin du
projet, vous allez écrire des fonctions qui évaluent seulement un **État**.
</div>

Finalement évaluer votre code par:

```python
python autograder.py -q q1
```

Pour exécuter votre code *sans graphique* ajouter l'option `--no-graphics` .

## Question 2 ( 5 points): Minimax ##
<a name='minimax'></a>

Maintenant vous allez implémenté la stratégie **MiniMax** de recherche en *adversité* fournie dans la classe `MinimaxAgent` dans le fichier `multiAgents.py`. Votre agent doit fonctionner quelque soit le nombre de **fantômes** (agent adverses). Ainsi, vous devez écrire un algorithme modifié (qui généralise le concept des agent minimiseurs).


<div class="notyet">
En particulier, Votre arbre de recherche doit considérer plusieurs couches de
minimisation (Une pour chaque fantôme) et une seule pour l'agent max.
</div>

  Le nombre de pli (*profendeur*) est stocké dans le champ `self.depth`. Les
  feuilles de l'arbre doivent être évaluées en utilisant la fonction
  `self.evaluationFunction`.


<div class="notyet">
Un pli de l'arbre consiste d'une action de tous les agents du jeu (pacman et les
fantômes). Ainsi  pour une profondeur 2, pacman et les fantômes doivent exécuter
deux actions.
</div>


Vérifier votre réponse par:

```python
python autograder.py -q q2
```
### Indices et Observations ###

* L'implémentation correcte de minimax peut mener pacman à **perdre** quelque
    parties. Ceci ne constitue pas un problème tant que le **comportement** de
    l'agent est correct.
* La fonction d'*évaluation* pour ce test est déjà implémentée dans
    (`self.evaluationFunction`). Ne la changer pas.
* Voici quelque valeurs de références pour le labyrinthe classique `{1:9, 2: 8,
    3:7, 4:-492}`. Comparer ces valeurs avec votre implémentation en lançant
    le code:

```python
python pacman.py -p MinimaxAgent -l minimaxClassic -a depth=4
```
* Pacman porte toujours l'indice **0** et les agent de déplacent selon l'ordre
    de leur indices.
* Quand pacman estime qu'il peut pas éviter  la mort. Il va essayer de terminer
    le jeu le plus tôt possible pour éviter la pénalité de déplacement.

```python
python pacman.py -p MinimaxAgent -l trappedClassic -a depth=3
```
## Question 3 (5 points): Elagage Alpha-Beta ##
<a name='alphabeta'></a>

Le but de cette question est d'implémenter une l'exploration avec élagage
*alpha-beta*. La classe associée a cet agent est `AlphaBetaAgent`. La version que vous devez implémenter sera différente que
celle de la lecture, puisqu'elle doit prendre en considération l'existence de
**plusieurs** agents minimiseurs.

<div class="fig figcenter fighighlight">
  <img src="/assets/alpha-beta-on-inequality.png" width="550" height="300"> 
  <div class="figcaption">
  Implémentation Alpha-Beta pour l'agent min et Max.
  </div>
</div>
Tester votre implémentation sur un simple labyrinthe.

```python
python pacman.py -p AlphaBetaAgent -a depth=3 -l smallClassic
```



<div class="notyet">
Comme présenté dans le cours les valeurs de Alpha-Beta doivent être similaires
à ceux de MiniMax. Ainsi vous devez obtenir `{1:9, 2: 8,
    3:7, 4:-492}` pour le labyrinthe classique.
</div>

```python
python pacman.py -p ExpectimaxAgent -l minimaxClassic -a depth=4
```
Finalement pour valider votre question:

```python
python autograder.py  -q q3
```
## Question 4 (5 points): ExpectiMax ##
<a name='expectimax'></a>

MiniMax et Alpha-beta offrent des solutions optimales en assumant que
l'adversaire va choisir son action **optimale**. Cependant, c'est pas le cas de
tous les adversaires. Ainsi, pour introduire le facteur aléatoire d'un
adversaire, on vous demande d'implémenter l'exploration *expectimax* dans la
classe `ExpectimaxAgent`.

Vérifier votre code par:

```python
python autograder.py -q q4
```

**Assurer vous  quand vous calculer des moyennes que vous utiliser  des réels**.

```python
1/2 = 0
1.0/2 = 0.5
```

Pour voir votre agent en action, lancez:

```python
python pacman.py -p ExpectimaxAgent -l minimaxClassic -a depth=3
```

Vous devez témoigner un agent plus *courageux* autour des fantômes. Aussi
  essayer votre code dans le labyrinthe avec un agent *condamné* à l'échec.

```python

python pacman.py -p MinimaxAgent -l trappedClassic -a depth=3 -q -n 10

python pacman.py -p ExpectimaxAgent -l trappedClassic -a depth=3 -q -n 10
```

Vous devez constaté que  votre agent gagne en moyenne la **moitié** des
parties!!



## Question 5 ( 6 points): Fonction d'évaluation ##
<a name='evalFunction'></a>

L'objectif de cette question est d'**améliorer** la fonction d'évaluation de
pacman. Cette dernière, doit  évaluer des états et non pas des actions comme
l'agent de *reflèxe*. Le code de cette fonction doit ête ajouté à
`betterEvaluationFunction`.  Vous pouvez utiliser tous les outils à votre
disposition, mêmes les algorithmes de recherches développés dans le premier
projet.


Vérifier votre code  par


```python
python autograder.py -q q5
```

### Indices et Obserations ###

* Comme pour la fonction d'agent de reflèxe, vous avisés d'utiliser l'*inverse*
    des caractéristiques (comme la distance à la nouriture).
* Similaire au réseaux de neuronnes, il est recommandé de considérer une
    **combinaison linéaire** des caractéristiques choisies. 


