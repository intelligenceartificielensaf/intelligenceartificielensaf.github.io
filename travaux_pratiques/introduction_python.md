---
layout : page
date   :  2019/02/21  
permalink: /travaux_pratiques/introduction_python/
---



## Table de matière

- [Introduction](#Introduction)
-  [Environnement virtuel](#virtualenv) 
- [Les bases de linux](#linux)
- [Tutorial python](#python)
- [Autograder](#autograder)
- [Question 1: Addition ](#question1)
- [Question 2: Acheter un ordre](#buyFruits)
- [Question 3: Meilleur magasin](#bestShop)





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


Nous allons télécharger les contenu de de projet qui dans [python_basics.zip](https://github.com/intelligenceartificielensaf/intelligenceartificielensaf.github.io/blob/master/travaux_pratiques/python_basics.zip). Puis nous allons décompresser son contenu.

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

Un `set` (ensemble) est une structure de données pour réprésenter une liste non
ordonnée sans des répétitions.

```python
>>>formes = ['cercle','carre', 'triangle', 'cercle'] #liste contenant des répetition.
>>>Ensemble = set(formes)   # créer un ensemble de cette liste
 {'carre', 'cercle', 'triangle'}
>>> Ensemble.add('Polygone')
>>>Ensemble
{'carre', 'cercle', 'polygon', 'triangle'}
>>> Ensemble.add(cercle)  # dexiste déja donc rien ne change
{'carre', 'cercle', 'polygon', 'triangle'}
>>> 'cercle' in Ensemble   #test d'appartenance
True
```


On peut appliquer les opérations mathématique *ensemblistes* (Unition,
Intersection, Soustraction)

```python
>>>Ensemble = set(['cercle','carre', 'triangle', 'cercle'])
>>>favoris  = set(['cercle','triangle'])
>>>Ensemble-favoris   #A - B (elements dans A et non dans B)
{'carre'}
>>>Ensemble & favoris  #intesection 
{'cercle','triangle'}
>>> Ensemble | favoris # Union
{'cercle','triangle','carre'}
```
> Faites attention, les éléments d'un ensemble ne sont par ordonés. (.i.e. Il
> faut pas assumer qu'il vont apparaitre dans le même ordre.

### Dictionnaires
Un dictionnaire ou *hash-map* est une structure de données qui permet un accès
rapide à une collection indexé par un ensemble de **clés**. La clé doit être un
objet *immutable*  pour permettre une identification unique des valeurs.


```python
>>>Scientists = {'knuth': 42.0, 'turing': 56.0, 'nash': 92.0}
>>>Scientists['knuth']   #accéder une valeur par sa clé
42.0
>>> Scientists['turing'] = 87       #changer la valeur
>>> del Scientists['turing']        #détruire l'entrée
>>> Scientists.keys()           #afficher les clés
['knuth', 'nash']
>>> Scientists.values()       #afficher les valeurs
[42.0, 92.0]

>>> Scientists.items()       # list of tuple [(key,val),....]
```

> Exercice: Supposons qu'on veut envoyer un message par un code simple où
> chaque lettre est codée par un entier qui représente sa position (i.e A=1,
> B=2,....)
> 1. Créer un dictionnaire pour codes cettres
> 2. Afficher le code du message 'artificialintelligence'

<a name='scripts'></a>
Maintenant que vous avez accumulé les notions de bases de la syntaxe **python**.
On peut écrire des programmes simples pour démontrer les capacités du langage

Changer le contenu du fichier `foreach.py` dans votre projet:
```python
# This is what a comment looks like 
fruits = ['apples','oranges','pears','bananas']
for fruit in fruits:
    print fruit + ' for sale'

fruitPrices = {'apples': 2.00, 'oranges': 1.50, 'pears': 1.75}
for fruit, price in fruitPrices.items():
    if price < 2.00:
        print '%s cost %f a pound' % (fruit, price)
    else:
        print fruit + ' are too expensive!'
```

Pour exécuter alors ce fichier, lancer la commande suivante:

```python
python foreach.py
```

Investiguer le contenu du fichier `listcomp.py` qui démontre la puissance des
[lists  comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)

```python
nums = [1,2,3,4,5,6]
oddNums = [x for x in nums if x % 2 == 1]
print oddNums
oddNumsPlusOne = [x+1 for x in nums if x % 2 ==1]
print oddNumsPlusOne
```
> Executer ce script, puis générer une liste comprhension qui garde 
> que les chaines ayant une longeur supérieure ou
> égale à 5. Les chaines sauvegardées doivent être en lettre **miniscules**.
> la solution est dans `listcomp2.py`


### Fonctions
<a name='functions'></a>

Similaire à tous les langages de programmation, python vous permet de définir
vos propres **fonctions**.


```python
fruitPrices = {'apples':2.00, 'oranges': 1.50, 'pears': 1.75}

def buyFruit(fruit, numPounds):
    if fruit not in fruitPrices:
        print "Sorry we don't have %s" % (fruit)
    else:
        cost = fruitPrices[fruit] * numPounds
        print "That'll be %f please" % (cost)

# Main Function
if __name__ == '__main__':        
    buyFruit('apples',2.4)
    buyFruit('coconuts',2) 
```

> Classique (exercice avancé ***) Ecire la fonction quicksort avec une
> comprehension. Vous trouverez la solution dans `quickSort.py`

#### Programmation Orienté Objet
<a name='oop'></a>

La majorité des questions des projet va vous demander de changer le contenu d'un
fonction ou méthodes d'un objet.  Ainsi, dans cette section, nous présonterons
une introduction simple à la programmation *orienté object* par python.

```python
class Rectangle:
  def __init__(self,width):
    """
    Constructeur par une longueur
    """
    self.width = width

  def get_width(self):
    """
    Renvoir la longueur du rectangle
    """
    return self.width
  
  def  get_surface(self):
    return self.width**2

  def __str__(self):
    return "Carre [width=%d]" %self.width
```


Cette classe définit un `Rectangle` avec un constcuteur, deux **getters** et une
méthode pour convertir en **string**.

#### Utiliser les objets:

```python
>>> A =Rectangle(4)
>>> A.get_width
4
>>> A.get_surface()
16
>>> print A
Carre [width=4]
```

[^1]: Votre ligne de commande peut être différent, comme il est possible de la personnaliser.

## Autograder
<a name='autograder'></a>

Les deux projet de  ce cours contient un outil appelé `autograder` qui permet la
notation automatique de votre solution. Ainsi vous pouvez essayer plusieurs
solutions et l'autograder va vous renvoier un feed-back de votre solution. Les
commentaires de ce dernier, vous seront d'une grande utilisté pour détecter vos
erreurs ou de de confirmer la exactitude de vos réponses.

Dans section, on va se familiariser avec cet outil et lister les méthodes pour intéragir avec ce dernier.

Vous devez télécharcher le contenu du projet [tutorial](http://ai.berkeley.edu/projects/release/tutorial/v1/001/tutorial.zip)

Ainsi dans votre project, executé la commande:

```python
python autograder.py
Question q1
===========

*** FAIL: test_cases/q1/addition1.test
*** 	add(a,b) must return the sum of a and b
*** 	student result: "0"
*** 	correct result: "2"
*** FAIL: test_cases/q1/addition2.test
*** 	add(a,b) must return the sum of a and b
*** 	student result: "0"
*** 	correct result: "5"
*** FAIL: test_cases/q1/addition3.test
*** 	add(a,b) must return the sum of a and b
*** 	student result: "0"
*** 	correct result: "7.9"
*** Tests failed.

### Question q1: 0/1 ###
```
On peut voir l'**autograder**  evalue votre solution sur différent cas et vous
renvoie votre note indiquant si vous avez passé le test ou non.


## Question 1 : Addition
<a name='question1'></a>

Ouvrez le fichier `addition.py` et examiner la définition de la méthode **add**


```python
"""
Run python autograder.py
"""

def add(a, b):
    "Renvoie la somme de a et b"
    "*** Votre code ***"
    return 0
```

Changer le contenu de la fonction pour calculer la bonne solution. Une fois
terminé, exécuter la commande pour vérifier votre solution:


```python
python autograder.py -q q1
```

Vous devez vous assurer que vous avez passé la solution

## Question 2: Acheter des Fruits
<a name='buyFruits'></a>

Implémenter la fonction *buyLotsOfFruit(orderList)* dans le fichier `buyLotsOfFruit.py`. Cette fonction prend comme argument une liste de couples **(fruit, pound)** et renvoie le prix de cette liste.

> S'il y as un fruit dans la liste qui ne figure pas dans la  liste de fruits
> offerts par le magasin, la fonction doit afficher un message d'erreur et
> renvoie  la valeur **None**.


> Il ne faut, dans aucun cas, changer la variable **fruitPrices**.


Pour vérifier votre réponse, exécuter le code suivant.

```python
python autograder.py -q q2 --mute
```

### Question 3: acheter avec meilleur prix
<a name='bestShop'></a>

Remplir la fonction **shopSmart(orders, shops)** dans le fichier `shopSmart.py`.
Cette fonction prend, comme argument, une liste *orders* comme fruits à acheter avec leur
poids. Elle prend aussi une liste de magasins *shops* où on peut acheter ces
fruits. Cette fonction doit renvoie le **magasin** avec le coût minimal de notre
ordre.

Vérifier votre réponse avec

```python
python autograder.py -q q3  --mute
```


> Félicitions, vous avez terminé avec succès ce premier TP. Vous êtes
maintenant prêt, pour entrer dans le fabuleux monde de **PACMAN**.
----

[^2]: La version récente de python est 3.x, mais nous nous contentons de python 2.7 pour des raisons de compatibilités.

