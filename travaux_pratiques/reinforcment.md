---
layout : page
title  :  Apprentissage par réinforcement
date   :  2019/05/06  
permalink: /travaux_pratiques/reinforcement/
---

## Table de matière ##
1. [Introduction](#intro)
2. [Itération de la valeur](#valueiteration)
3. [Analyse d'un pont séparateur](#bridgeanalysis)
4. [Stratégies](#policy)
5. [Apprentissage Q](#qlearning)
6. [Pont séparateur revisité](#bridge2)
7. [Apprentissage Q et Pacman](#qlearningPacman)


 






<div class="fig figcenter fighighlight">
  <img src="/assets/reinforcement.png" width="550" height="170"> 
  <div class="figcaption">
   Pacman est maintenant entouré des phantomes. Doit il approcher la nouriture
   ou fuir les fantômes. En situation de doutes, *Q learn*.
  </div>
</div>

## Introduction ##
<a name='intro'></a>

Le but de ce projet est d'implémenter les deux algorithmes d'apprentissage `Value iteration` et `policy iteration`. Pour permettre à un agent débutant d'apprendre toutes les règles et stratégies de `Pacman` et devinir l'ultime Joueur.  


