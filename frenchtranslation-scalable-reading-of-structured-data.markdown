---
title: "La lecture évolutive de données structurées"
collection: lecons
layout: lesson
slug: lecture-evolutive-de-donnees-structurees
date: AAAA-MM-JJ
translation_date: AAAA-MM-JJ (champ spécifique aux traductions)
authors:
- Prénom Nom
- Prénom Nom, etc
reviewers:
- Prénom Nom
- Prénom Nom, etc
editors:
- Prénom Nom
translator:
- Prénom Nom (champ spécifique aux traductions)
translation-editor:
- Prénom Nom (champ spécifique aux traductions)
translation-reviewer:
- Prénom Nom (champ spécifique aux traductions)
original: slug to original published lesson (champ spécifique aux traductions)
review-ticket: e.g. https://github.com/programminghistorian/ph-submissions/issues/108
difficulty: voir ci-dessous
activity: UNIQUEMENT UN PARMI: acquiring, transforming, analyzing, presenting, sustaining
topics:
 - sujet un (voir ci-dessous)
 - sujet deux
abstract: |
  voir ci-dessous
avatar_alt: Description de l'image de la leçon
---

# Table des matières

- [Objectifs de la leçon](#Objectifs-de-la-leçon) 
- [Structure de la leçon](#Structure-de-la-leçon)
- [La lecture évolutive, une introduction aux méthodes digitales pour les débutants](#La-lecture-évolutive-,-une-introduction-aux-méthodes-digitales-pour-les-débutants)
- [La lecture évolutive](#La-lecture-évolutive)
- [Données et prérequis](#Données-et-prérequis)
  - [tidyverse](#tidyverse)
  - [lubridate](#lubridate)
  - [jsonlite](#jsonlite)
  - [rtweet](#rtweet)
- [Etape 1.Exploration chronologique du jeu de données](#Etape-1.Exploration-chronologique-du-jeu-de-données)




# Objectifs de la leçon 

Une fois cette leçon complétée, les lecteurs seront en mesure de :
 * configurer un processus de travail où la lecture exploratoire distante est utilisée en tant que contexte pour guider la sélection de points de données en vue d'une lecture attentive
 * faire appel aux analyses exploratoires pour identifier des schémas au sein de données structurées
 * appliquer et combiner des filtres de base et ajuster les fonctions dans R (si vous n'avez pas ou peu de connaissances de R, nous recommandons de consulter la leçon ["Les bases de R avec des données tabulaires"](https://programminghistorian.org/en/lessons/r-basics-with-tabular-data))


# Structure de la leçon

Dans cette leçon, nous introduisons un processus de travail pour une lecture évolutive (*scalable reading*) de données structurées - une combinaison d'interprétation rigoureuse de points de données individuels et d'analyse statistique du jeu de données entier. 
Cette leçon est structurée en deux cheminements parallèles :
* un cheminement général qui suggère une façon de travailler analytiquement avec des données structurées où la lecture distante d'un grand jeu de données est 
utilisée comme contexte pour une lecture attentive de points de données distincts ;
* un cheminement basé sur un exemple dans lequel nous utilisons des fonctions simples du language de programmation R pour analyser des données Twitter.
En combinant ces deux cheminements, nous montrons comment la lecture extensible peut être employée pour analyser une large variété de données structurées.
Notre processus de travail évolutif suggéré inclus deux types de lectures distantes qui peuvent aider à explorer et analyser les caractéristiques globales de grands jeux de données (chronologiquement et en relation avec des structures binaires), en plus de permettre l'utilisation de la lecture distante pour sélectionner des points de données individuels pour une lecture attentive (*close reading*) de manière systématique et reproductible.

# La lecture évolutive, une introduction aux méthodes digitales pour les débutants

La combinaison de lecture distante (*distant reading*) et de lecture attentive (*close reading*) introduites dans cette leçon est entendue comme une introduction aux méthodes digitales pour les étudiants et les chercheurs qui débutent dans l'incorporation du raisonnement computationnel à leur travail. En connectant la lecture distante de grands jeux de données à la lecture attentive de points de données individuels, vous créez un pont entre les méthodes computationnelles et les méthodes de curation manuelles communément employées dans les humanités. De notre expérience, la lecture évolutive (*scalable reading*) - où l'analyse d'un jeu de données entier représente un ensemble de contextes pour la lecture attentive - prévient les difficultés que les personnes débutantes peuvent rencontrer en interrogeant leur matériel qui peut être exploré via le raisonnement computationnel. La manière reproductible de sélectionner chaque cas individuellement pour un examen approfondi éclaire, par exemple, les questions centrales au sein de disciplines comme l'histoire et la sociologie concernant les relations entre un contexte général et un cas d'étude particulier, mais peut aussi être utile à d'autres disciplines des humanités qui travaillent avec des cadres analytiques similaires. 

# La lecture évolutive

Nous avons utilisé à l'origine le processus de travail présenté ci-dessous pour analyser les souvenirs que les enfants états-uniens ont du programme télévisé *Sesame Street* sur Twitter. Nous avons utilisé une combinaison de lecture attentive (*close reading*) et de lecture distante (*distant reading*) pour découvrir comment certains évènements ont généré des discussions sur l'histoire de *Sesame Street*, quels utilisateurs de Twitter dominaient le discours à propos de l'histoire de *Sesame Street*, et quels parties de l'histoire de l'émission étaient mises en exergue. Notre exemple ci-dessous utilise un petit jeu de données en lien avec les tweets concernant *Sesame Street*. Toutefois, le même cadre analytique peut être utilisé pour analyser de nombreux autres types de données structurées.
Afin de démontrer l'applicabilité du processus de travail sur d'autres types de données, nous abordons comment ce dernier pourrait être appliqué à des ensembles de données structurées depuis les collections numérisées de la Galerie Nationale du Danemark. Les données de la Galerie Nationale sont très différentes des données Twitter utilisées dans l'exemple, mais l'idée d'utiliser la lecture distante pour contextualiser un travail de lecture attentive s'applique aussi bien avec des données Twitter.

Le processus de travail pour la lecture évolutive de données structurées que nous proposons ci-dessous se présente en trois étapes :

1. **L'exploration chronologique du jeu de données** : Dans le jeu de données Twitter, nous explorons comment un phénomène spécifique génère de l'intérêt sur la plateforme durant une certaine période de temps. Dans le cas des données de la Galerie Nationale, nous aurions pu analyser la distribution temporelle de leurs collections, c'est-à-dire classer les données par année d'acquisition ou par année de création des oeuvres.
2. **Explorer un jeu de données en créant des catégories analytiques binaires** : Cette étape suggère l'utilisation de catégories existantes de métadonnées pour créer des questions de nature binaire, soit des questions qui appellent une réponse de type oui/non ou vrai/faux. Nous utilisons la création d'une structure analytique binaire comme moyen d'étudier les tendances générales d'un jeu de données. Dans le jeu de données Twitter, nous explorons l'usage des hashtags (versus leur non usage); la distribution des tweets via des comptes vérifiés versus des comptes non vérifiés, et le niveau d'interaction pour ces deux types de comptes. Dans le cas de la Galerie Nationale, nous aurions pu utiliser les métadonnées sur le type d'oeuvre d'art, le genre et la nationalité pour explorer la représentation des artistes Danois versus les autres nationalités d'artistes; les peintures versus les autres types d'oeuvres; ou encore les artistes par genre, etc.
3. **Sélection systématique de points de données uniques pour la lecture attentive** : Cette étape suggère une manière systématique et reproductible de sélection de points de données uniques pour la lecture attentive. Dans le jeu de données Twitter, nous avons sélectionné pour la lecture attentive les 20 tweets les plus likés. Dans le cas de la Galerie Nationale, nous aurions pu choisir par exemple les 20 oeuvres les plus exposées, empruntées ou annotées.

Ci-dessous, les trois étapes sont expliquées en des termes généraux mais aussi plus spécifiquement à partir de l'exemple des données Twitter.

# Données et prérequis

Si vous souhaitez reproduire l'analyse que nous présentons ci-dessous, en utilisant pas seulement le cadre conceptuel de travail mais aussi le code, nous partons du principe que vous avez déjà à disposition un jeu de données contenant des données Twitter au format JSON. Si ce n'est pas le cas, vous pouvez vous en acquérir un par les méthodes suivantes :

1. Utiliser l'une des APIs de Twitter, c'est-à-dire leur API dite "Essentielle" (*Essential*) que nous avons utilisé pour récupérer le jeu de données utilisé dans l'exemple (pour en savoir plus sur les APIs, vous pouvez consulter [cette section de la leçon sur l'introduire et peupler un site web avec des données API](https://programminghistorian.org/en/lessons/introduction-to-populating-a-website-with-api-data#what-is-application-programming-interface-api)(en anglais). Ce lien vous mènera [aux options API de Twitter](https://developer.twitter.com/en/docs/twitter-api/getting-started/about-twitter-api). Vous pouvez utiliser le paquet 'rtweet' , avec vos propres identifiants Twitter pour accéder à l'API Twitter via R, comme décrit ci-dessous.
2. Utiliser notre [guide pour débutants sur les données Twitter](https://programminghistorian.org/en/lessons/beginners-guide-to-twitter-data) par Programming Historian. Choisissez plutôt un export en JSON au lieu du CSV.

Dans R, vous travaillez avec des paquets (*packages*), chacun ajoutant des fonctionnalités aux fonctions de base de R. Les paquets sont souvent créés de manière communautaire et rendus disponibles à la réutilisation. En recourant aux paquets, nous vous tenez sur les épaules d'autres codeurs. Dans cet exemple, les paquets que nous allons utiliser sont les suivants : rtweet, tidyverse, libridate et jsonlite. Pour installer ces paquets dans R, consultez [cette section de la leçon sur le traitement de texte basique dans R](https://programminghistorian.org/en/lessons/basic-text-processing-in-r#package-set-up) (en anglais). Pour utiliser les paquets dans R, il faut les charger via la fonction `library()` comme ci-dessous :

    library(rtweet)
    library(tidyverse)
    library(lubridate)
    library(jsonlite)
     
Afin de pouvoir suivre les exemples de code, assurez-vous d'avoir installé et chargé les paquets R suivants :

## tidyverse
Le paquet "tidyverse" est un paquet parapluie qui charge plusieurs librairies toutes utiles lorsqu'il s'agit de travailler avec des données. Pour plus d'informations et savoir comment utiliser tidyverse, voir [https://www.tidyverse.org](https://www.tidyverse.org) <sup>[1](#Références)</sup>.

## lubridate
Le paquet "lubridate" est utilisé pour manipuler différents formats de dates dans R, ainsi qu'effectuer des opérations sur ces dates. Le paquet a été créé par le même groupe que celui derrière "tidyverse" mais ne fait pas partie de ce dernier. <sup>[2](#Références)</sup>

## jsonlite
Le paquet "jsonlite" permet de manipuler le format Javascript Object Notation (json), format utilisé pour échanger des données sur internet. Pour plus d'informations sur le paquet jsonlite, voir : [https://cran.r-project.org/web/packages/jsonlite/index.html3](https://cran.r-project.org/web/packages/jsonlite/index.html3) <sub>[3](#Références)</sub>

Si vous êtes déjà en possession d'un fichier json contenant vos données twitter, vous pouvez utiliser la fonction `fromJSON` dans le paquet "jsonlite" pour importer les données dans votre environnement R.

## rtweet
Le paquet "rtweet" est une implémentation d'appels destinés à collecter et à organiser des données Twitter via l'API REST et l'API stream de Twitter, qui se trouve à l'adresse suivante : [https://developer.twitter.com/en/docs](https://developer.twitter.com/en/docs) <sub>[4](#Références)</sub>

Si vous avez déjà acquis des données Twitter et que vous souhaitez suivre les exemples de code à suivre étape par étape, vous pouvez utiliser votre compte twitter et la fonction `search_tweets()` du paquet 'rtweet', pour importer vos données twitter dans votre environnement R. Cette opération va retourner jusqu'à 18 000 tweets datant des 10 derniers jours. Les données vont être structurées en tableau de données (*dataframe*). Tout comme une feuille de calcul, un tableau de données organise vos données en un tableau à deux dimensions avec des lignes et des colonnes. En copiant le code ci-dessous, vous serez capable de générer un tableau de données basé sur une recherche textuelle libre du terme "sesamestreet" pour suivre notre exemple. Le paramètre q représente votre requête. C'est à cette place qu'il faut taper le contenu qui vous intéresse. Le paramètre n indique le nombre de tweets à retourner.

    sesamestreet_data <- search_tweets(q = "sesamestreet", n = 18000)

# Etape 1. Exploration chronologique du jeu de données

Explorer les dimensions chronologiques d'un jeu de données peut faciliter la première analyse globale de vos données. Dans le cas où vous étudiez l'évolution d'un phénomène au cours du temps (comme notre intérêt autour des évènements précis ayant déclenché des discussions sur Sesame Street), comprendre comment ce phénomène a généré de l'attention et/ou comment cet intérêt diminue peut être révélateur de son importance. Cela peut constituer la première étape de compréhension de la manière dont les données collectées se rapportent au phénomène au cours du temps. L'intérêt pour la dispersion temporelle peut aussi se raporter non pas à un évènement mais plutôt à la distribution totale d'un jeu de données sur la base d'un ensemble de catégories.
Par exemple, dans le cas où vous travaillez avec les données de la Galerie Nationale, il peut s'avérer utile d'explorer la distribution de ses collections en fonction des différentes périodes d'histoire de l'art afin d'établir quelles périodes sont les mieux représentées dans le jeu de données de la Galerie Nationale. Connaître la dispersion temporelle de l'ensemble du jeu de données aide à contextualiser les points de données individuels sélectionnés pour une lecture attentive à l'étape 3 en cela qu'elle donne une idée de la relation spécifique entre le point de donnée et la chronologie du jeu de données entier, en comparaison de tous les autres points de données.

## Exemple d'une dispersion temporelle d'un jeu de donnée : les données Twitter

Dans cet exemple, vous allez découvrir à quel point Sesame Street est discuté sur Twitter pendant une certaine période de temps. Vous allez aussi voir combien de tweets utilisent le hashtag officiel "#sesamestreet" durant cette période.

___

In the following, you begin with some data processing before moving on to the actual visualisation. What you are asking the data here is a two-piece question:

    First of you want to know the dispersion of the tweets over time.
    Second, you want to know how many of these contain a the hashtag “#sesamestreet”.

Especially the last question needs some data wranglig before it is possible to answer it.


# Références

(1)  Hadley Wickham, Mara Averick, Jennifer Bryan, Winston Chang, Lucy D’Agostino McGowan, Romain François, Garrett Grolemund, Alex Hayes, Lionel Henry, Jim Hester, Max Kuhn, Thomas Lin Pedersen, Evan Miller, Stephan Milton Bache, Kirill Müller, Jeroen Ooms, David Robinson, Dana Paige Seidel, Vitalie Spinu, Kohske Takahashi, Davis Vaughan, Claus Wilke, Kara Woo, and Hiroaki Yutani (2019). “Welcome to the tidyverse.” Journal of Open Source Software, 4(43), 1686, 1-6. doi: [10.21105/joss.01686](https://joss.theoj.org/papers/10.21105/joss.01686)<br/>
(2) Garrett Grolemund and Hadley Wickham (2011). “Dates and Times Made Easy with lubricate", Journal of Statistical Software, 40(3), 1-25. [www.jstatsoft.org/v40/i03/](www.jstatsoft.org/v40/i03/)<br/>
(3) Ooms, Jeroen (2014). “The jsonlite Package: A Practical and Consistent Mapping Between JSON Data and R Objects.”, [arxiv.org/abs/1403.2805](https://arxiv.org/abs/1403.2805)<br/>
(4) Kearney, (2019). "rtweet: Collecting and analyzing Twitter data". Journal of Open Source Software, 4(42), 1829, [https://doi.org/10.21105/joss.01829](https://doi.org/10.21105/joss.01829)<br/>




