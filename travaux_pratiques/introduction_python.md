---
layout : page_stanford
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



[^1]: Votre ligne de commande peut être différent, comme il est possible de la personnaliser.

[^2]: La version récente de python est 3.x, mais nous nous contentons de python 2.7 pour des raisons de compatibilités.
