---
layout : page
date   :  2019/02/21  
permalink: /travaux_pratiques/introduction_python/
---



## Table de matière ##

- [Introduction](#Introduction)
-  [Environnement virtuel](#virtualenv) 
- [Les bases de linux](#linux)
- [Tutorial python](#python)


## Introduction ##
<a name="Introduction"> </a>
L'objectif de ce premier **TP** est de vous préparer pour les projets principaux du cours. Il s'agit principalement d'un `tutorial` pour vous guider à 
installer et préparer un *environnement virtuel* contenant les bibliothèques indispensable pour l'exécution du code. Ensuite, on présentera, en se basant sur des questions simples, l'excellent outil `autograder` qui vous sera d'un aide crucial pour vérifier et valider vos réponses dans les futures **projets**.



## Installation Anaconda ##
<a name="virtualenv"></a>

Nous allons utiliser le language `python` pour les deux projets du cours. La gestion des divers bibliothèques est un peu compliqué. Ainsi, il est recommandé d'installer le gestionnaire de paquetage `anaconda` qui facilite l'installation et la manipulation des modules et environnements python.


Voici le lien pour installer anaconda pour différents systèmes d'exploitation.

[Installation anaconda](https://docs.anaconda.com/anaconda/install/)

On peut vérifier l'installation, en lançant la commande qui devra afficher la version installée.

```shell
conva -V
conda 3.7.0
```

Il faut pas aussi oublier de **mettre à jour** la liste des paquetages:

```shell
conda update conda
```

### Environnement virtuel ###

Aussi, il est fortement recommandé de travailler dans un `environnement virtuel` pour ne pas casser les dépendances avec le système. Alors, nous allons créer  un environnement `AI` qui utilise **python2** [^2].

```shell
conda create -n AI python=2.7 anaconda
```


Une fois que l'installation se termine, on pourra **activer** cet environnement par:

```shell
source activate AI
```

Une fois que vous terminez la manipulation du code de votre projet. On pourra **désactiver** cette version de python.

```shell
source deactivate
```

## Commandes basiques Linux ##
<a name="linux"></a>

Voici quelque commandes *Linux* qui pourront vous aider dans la manipulation des fichiers de votre projet.
<br>

### Manipulation de fichier/dossier ###

Quand vous lancer un **terminal**, vous serez devant une ligne de commande:


```bash
[AI_ensa@cour ~]$
```

Cette ligne de commande montre le *nom d'utilisateur* ainsi que le nom de la *machine* [^1]. Pour créer un **répertoire** nous utilisons la commande `mkdir`. Aussi nous nous déplaçons dans le nouveau dossier avec `cd`.


```bash
[AI_ensa@cour ~]$ mkdir folder
[AI_ensa@cour ~]$ cd folder
[AI_ensa@cour ~/folder]
```


Nous pouvons utiliser les commandes `ls` pour lister le contenu d'un dossier et la commande `touch` pour créer( où changer la date de modification) d'un fichier.

```bash

[AI_ensa@cour ~/folder]$ ls
[AI_ensa@cour ~/folder]$ touch hello_world
[AI_ensa@cour ~/folder]$ ls
hello_world
[AI_ensa@cour ~/folder]$ cd ..
[AI_ensa@cour ~]$
```


Nous allons télécharger les contenu de de projet qui dans [python_basics.zip](ai.berkeley.edu/projects/release/tutorial/v1/001/python_basics.zip). Puis nous allons décompresser son contenu.

```bash
[AI_ensa@cour ~/folder]$ wget ai.berkeley.edu/projects/release/tutorial/v1/001/python_basics.zip
[AI_ensa@cour ~/folder]$ unzip python_basics.zip
[AI_ensa@cour ~/folder]$ cd python_basics
[AI_ensa@cour ~/folder]$ ls
foreach.py  helloWorld.py  listcomp2.py
listcomp.py  quickSort.py  shop.py  shopTest.py
```

Voici aussi quelque commandes qui peuvent vous aider:

* **cp**: copier des fichiers.
* **rm** supprimer des fichiers.
* **mv** déplacer les fichiers.
* **man** afficher le manuel d'aide d'une commande
* **pwd** afficher le nom du dossier courant.
* **Ctrl-c** arrêter le processus en cours.
* **&** ajouter à une commande permet de *détacher* le processus lancé.
* **fg** reprend un programme exécuté en background.

## Tutorial Python
<a name="python"> </a>

Les deux projets de ce cours utiliserons le langage `python`. `Python` est un
langage **interprété**, orienté objet. La section courante servira comme
introduction ( ou rappel) des notions de bases de *python*.

> Je vous encourage à
 suivre le tutoriel en exécutant chaque commande vous même et interpréter le
 résultat.

### Table de matières:
* [Invoquer l'interpréteur Python](#invoquePython)
* [Opérateurs](#operators)
* [Chaines de caractères](#string)
* [Structure de données](#dataSrctures)
* [Scripts](#scripts)
* [Indentation](#indentation)
* [Fonctions](#functions)
* [Objets](#oop)



### Invoquer l'interpréteur Python ###
<a name="invoquePython"> </a>
Le langage **python** peut être exécuté selon deux modes. Le premier comme un
interpréteur simple, ou depuis la ligne de commande pour exécuter un `script`.
Dans un premier temps, nous allons utiliser le premier mode pour une interaction
simple avec le langage.


```python
(AI) ➜  ~ python
Python 2.7.15 |Anaconda, Inc.| (default, May  1 2018, 23:32:55) 
[GCC 7.2.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```


### Operateurs ###
<a name='operators'></a>

**python** peut être utilisé pour évaluer des expressions arithmétiques.  Par
exemple on peut évaluer la somme de deux entiers, le résultat sera affiché après
le `prompt`.

```python
>>> 1+23
24
>>> 4*3
12
>>> 2**4
16
>>> 72%5
2
```

`Python` offre aussi des types **booléens** pour la manipulation des expressions
logiques.

```python
>>> 1 == 32
False
>>> not (1==0)
True
>>> (2==2) and (4==1)
False
>>> (2==2) or (4==1)
True
```

<a name='string'></a>
Comme le langage **Java**, python offre une classe pour le traitement des
chaines de caractères.

```python
>>> A = 'artificial'  #declarer une chaine
>>> A.upper()          # mettre tout en majuscule
'ARTIFICIAL'
>>> B = 'intelligence   '   #remarquer les espace additionnels
'intelligence '
>>> B = B.strip()           # éliminer les espaces
'inteliigence'
>>> C = A+" " +B            #concaténation de chaines
'ARTIFICIAL intelligence'
```

pour une liste détaillée des méthodes, je renvoie à la documentation officielle
  de la classe [string](https://docs.python.org/2/library/string.html)


> Une autre méthode simple pour investir les fonctions d'une classe et la
fonction `dir`.

  1. Utiliser cette méthode sur une chaine de caractères pour lister l'ensemble des
   méthodes offertes par cette classe.

### Structures de données 
<a name='dataSrctures'></a>

Python est équipée par plusieurs **structures de données** utiles qui sont
similaire à ceux offerts par le module `Collections` de Java.

#### Listes

Une `liste` est une collection de données **mutable** hétérogènes. Elle est
définir par l'opérateur **[ ]**.

```python
>>> fruits = ['apple', 'orange', 'pear','banana']
>>> fruits
['apple', 'orange', 'pear','banana']
>>> fruits[0]           # premier élément
'apple'
>>> fruits[:2]         # les deux premiers éléments
['apple', 'orange']
>>> fruits[-2:]         # les deux derniers éléments
>>> fruits.append('kiwi')      #ajouter un element
>>> fruits
['apple', 'orange', 'pear','banana','kiwi']
>>> fruits = fruits + [1,2]
['apple', 'orange', 'pear', 'banana', 'kiwi', 1, 2]
>>> a = fruits.pop()        # extraire le dernier élément
2
>>> fruits[-1]= 'grapefruit'
['apple', 'orange', 'pear', 'banana', 'kiwi','grapefruit']
```


On peut parcourir les liste d'une liste par une boucle for:

```python
for x in fruits:
	print x
```

Les éléments d'une liste peuvent être de n'importe quel type. Par exemple, on pourra définir une liste de fonctions et les appliquer à un nombre.

```python
>>> from math import sin,cos,tan
>>> functions = [sin,cos,tan]      #liste de fonction
>>> x= 3.4 
>>>for f in functions:
		print f(x)
-0.255541102027
-0.966798192579
0.264316900867
```

On pourra aussi définir une liste de liste:

```python
>>> lstofLists = [['a','b','c'],[1,2,3], ['un','deux','trois']
>>> lstofLists[0][-1]
```

>  Exercice: Créer une liste A qui contient les lettres de l'alphabet. Créer ensuite une liste B qui contient les caractères numériques. Calculer une liste Fusion qui combine chaque caractère de A et un chiffre de B.


### Tuples

Les `tuples` offre une structure de données de collections qui sont **immutable** (i.e. On peut pas changer leur contenu). Les tuples sont crées par l'opérateur **( )**


```python
>>> pair = (3,4)
>>> pair[0]
3
>>> x,y = pair
>>> x
3
>>> y
4
>>> pair[1] =6       #erreur les tuples sont immutable
TypeError
```


### Sets


<a name='scripts'></a>

<a name='indentation'></a>
<a name='functions'></a>
<a name='oop'></a>

[^1]: Votre ligne de commande peut être différent, comme il est possible de la personnaliser.

[^2]: La version récente de python est 3.x, mais nous nous contentons de python 2.7 pour des raisons de compatibilités.
