





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

Nous avons utilisé à l'origine le processus de travail présenté ci-dessous pour analyser les souvenirs que les enfants états-uniens ont du programme télévisé *Sesame Street* sur Twitter. Nous avons utilisé une combinaison de lecture attentive (*close reading*) et de lecture distante (*distant reading*) pour découvrir comment certains évènements ont généré des discussions sur l'histoire de *Sesame Street*, quels utilisateurs de Twitter dominaient le discours à propos de l'histoire de *Sesame Street*, et quels parties de l'histoire de l'émission étaient mises en exergue. Notre exemple ci-dessous utilise un petit jeu de données en lien avec les tweets concernant *Sesame Street*. Toutefois, le même cadre analytique peut être utilisé pour analyser de nombreux autres types de données structurées.
Afin de démontrer l'applicabilité du processus de travail sur d'autres types de données, nous abordons comment ce dernier pourrait être appliqué à des ensembles de données structurées depuis les collections numérisées de la Galerie Nationale du Danemark. Les données de la Galerie Nationale sont très différentes des données Twitter utilisées dans l'exemple, mais l'idée d'utiliser la lecture distante pour contextualiser un travail de lecture attentive s'applique aussi bien avec des données Twitter.

Le processus de travail pour la lecture évolutive de données structurées que nous proposons ci-dessous se présente en trois étapes :

1. **L'exploration chronologique du jeu de données** : Dans le jeu de données Twitter, nous explorons comment un phénomène spécifique génère de l'intérêt sur la plateforme durant une certaine période de temps. Dans le cas des données de la Galerie Nationale, nous aurions pu analyser la distribution temporelle de leurs collections, c'est-à-dire classer les données par année d'acquisition ou par année de création des oeuvres.
2. **Explorer un jeu de données en créant des catégories analytiques binaires** : Cette étape suggère l'utilisation de catégories existantes de métadonnées pour créer des questions de nature binaire, soit des questions qui appellent une réponse de type oui/non ou vrai/faux. Nous utilisons la création d'une structure analytique binaire comme moyen d'étudier les tendances générales d'un jeu de données. Dans le jeu de données Twitter, nous explorons l'usage des hashtags (versus leur non usage); la distribution des tweets via des comptes vérifiés versus des comptes non vérifiés, et le niveau d'interaction pour ces deux types de comptes. Dans le cas de la Galerie Nationale, nous aurions pu utiliser les métadonnées sur le type d'oeuvre d'art, le genre et la nationalité pour explorer la représentation des artistes Danois versus les autres nationalités d'artistes; les peintures versus les autres types d'oeuvres; ou encore les artistes par genre, etc.
3. **Sélection systématique de points de données uniques pour la lecture attentive** : 

     

    Systematic selection of single datapoints for close reading
    This step suggests a systematic and reproducible way of selecting single datapoints for close reading. In the Twitter dataset, we selected for close reading the 20 most commonly liked tweets. In the case of the National Gallery data it could, for instance, be the top 20 most exhibited, borrowed, or annotated items.

Below, the three steps are explained in general terms as well as specifically using our Twitter example.

