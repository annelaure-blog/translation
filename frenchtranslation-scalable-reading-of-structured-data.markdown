





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

# La lecture évolutive (*scalable reading*), une introduction aux méthodes digitales pour les débutants

La combinaison de lecture distante (*distant reading*) et de lecture attentive (*close reading*) introduites dans cette leçon est entendue comme une introduction aux méthodes digitales pour les étudiants et les chercheurs qui débutent dans l'incorporation du raisonnement computationnel à leur travail. En connectant la lecture distante de grands jeux de données à la lecture attentive de points de données individuels, vous créez un pont entre les méthodes computationnelles et les méthodes de curation manuelles communément employées dans les humanités. De notre expérience, la lecture évolutive (*scalable reading*) - où l'analyse d'un jeu de données entier représente un ensemble de contextes pour la lecture attentive - prévient les difficultés que les personnes débutantes peuvent rencontrer en interrogeant leur matériel qui peut être exploré via le raisonnement computationnel. La manière reproductible de sélectionner chaque cas individuellement pour un examen approfondi éclaire, par exemple, les questions centrales au sein de disciplines comme l'histoire et la sociologie concernant les relations entre un contexte général et un cas d'étude particulier, mais peut aussi être utile à d'autres disciplines des humanités qui travaillent avec des cadres analytiques similaires. 

# La lecture évolutive (*scalable reading*)

Nous avons à l'origine utilisé le processus de travail présenté ci-dessous pour analyser les souvenirs que les enfants états-uniens ont du programme télévisé *Sesame Street* sur Twitter. Nous avons utilisé une combinaison de lecture attentive (*close reading*) et de lecture distante (*distant reading*) pour découvrir comment certains évènements ont généré des discussions sur l'histoire de *Sesame Street*, quels utilisateurs de Twitter dominaient le discours à propos de l'histoire de *Sesame Street*, et quels parties de l'histoire de l'émission étaient mises en exergue. Notre exemple ci-dessous utilise un petit jeu de données en lien avec les tweets concernant *Sesame Street*. Toutefois, le même cadre analytique peut être utilisé pour analyser beaucoup d'autres types de données structurées.
Afin de démontrer l'applicabilité du processus de travail sur d'autres types de données, nous abordons comment ce dernier pourrait être appliqué à des ensembles de données structurées depuis les collections numérisées de la Gallerie Nationale du Danemark. Les données de la Gallerie Nationale sont très différentes des données Twitter utilisées dans l'exemple, mais l'idée d'utiliser la lecture distante pour contextualiser un travail de lecture attentive s'applique aussi bien avec des données Twitter.


The workflow for scalable reading of structured data we suggest below has three steps:

    Chronological exploration of a dataset.
    In the Twitter dataset, we explore how a specific phenomenon gains traction on the platform during a certain period of time. In the case of the National Gallery data, we could have analyzed the timely distribution of their collections e.g. according to acquisition year or when artworks were made.

    Exploring a dataset by creating binary-analytical categories.
    This step suggests using a dataset’s existing metadata categories to create questions of a binary nature, in other words questions which can be answered with a yes/no or true/false logic. We use this creation of a binary-analytical structure as a way to analyze some of the dataset’s overall trends. In the Twitter dataset, we explore the use of hashtags (versus lack of use); the distribution of tweets on verified versus non-verified accounts; and the interaction level of these two types of accounts. In the case of the National Gallery data we could have used the registered meta-data on artwork type, gender and nationality to explore the collection’s representation of Danish versus international artists; paintings versus non-paintings; or artists registered as female and unknown versus artists registered as male, etc.

    Systematic selection of single datapoints for close reading
    This step suggests a systematic and reproducible way of selecting single datapoints for close reading. In the Twitter dataset, we selected for close reading the 20 most commonly liked tweets. In the case of the National Gallery data it could, for instance, be the top 20 most exhibited, borrowed, or annotated items.

Below, the three steps are explained in general terms as well as specifically using our Twitter example.

