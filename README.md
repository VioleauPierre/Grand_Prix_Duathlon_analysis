# Grand_Prix_Duathlon_analysis

## Introduction : 
Le Duathlon est l’enchainement d’une portion de course à pied avec une portion de vélo avant de terminer par une nouvelle portion de course à pied. Le format le plus courant sur les Grand Prix de duathlons est le suivant :

5km course à pied / 20km vélo / 2.5km course à pied

Le Championnat de France des clubs de Duathlon se compose de 3 divisions, que ce soit pour le championnat féminin ou masculin. Les équipes des divisions 1 et 2 s’affrontent sur un championnat composé de 5 étapes en D1 et 4 étapes en D2. La D3 se déroule sur un format ¼ final, ½ finale et finale ou seules les meilleures équipes de chaque
manche se qualifie pour la suivante. A la fin de la saison les 3 premières équipes de la finale D3 accèdent à la D2, les 3 premières équipes de la D2 accèdent à la D1 et enfin les 3 dernières équipes en D1 et D2 sont relégués dans la division inférieure. Chaque club peut engager jusqu’à 5 athlètes par étape. Le classement est réalisé au cumul des places des 3 premiers athlètes de chaque équipe. A l’issue de chaque étape, un classement club est établi. A l’issue des 5 étapes, Les clubs féminins et masculins en tête du classement général de la D1 sont déclarés Champions de France. Le Championnat de France et particulièrement la D1 est l'endroit où évolue les meilleurs duathlètes du monde, et il ne faut pas s'étonner que chaque année le podium des championnats d'Europe et des Mondiaux, soit garni d'athlètes issus de ses rangs. Comme tout championnat, les grands prix de duathlon ont beaucoup évolué avec le temps, le but de cette étude est de déterminé quelles sont les évolutions sur la période 2018 - 2023 et les marqueurs de performance en fonction du championnat (D1, D2, Féminin, Masculin).
 
## Methodologie :
Les données des années 2023 et 2022 ont été récupéré par webscraping sur Prolivesport, pour les autres antérieur à 2022, les données proviennent directement de l’onglet résultat sur le site de la FFTRI. Les données venant du site de la FFTRI, on subit un traitement manuel pour homogénéiser le format, les colonnes et conserver uniquement les
informations pertinentes.

	La suite de la préparation des jeux de données a été réalisé dans un notebook en python. Pour chaque étape on retrouve un premier dataframe dit « scratch » qui regroupe le classement et les temps intermédiaire pour chaque course de l’étape (D1F, D1H, D2F, D2H) et un second dataframe dit « class_etape » qui regroupe le classement par
 équipe et le temps des 3 athlètes classant chaque équipe. Plusieurs fonctions ont été développé spécialement pour l’analyse, tout d’abord les données de chaque étape sont nettoyées et enrichies avec l’ajout d’un delta temps entre le meilleur temps pour chaque partie de la course et chaque athlète. Le delta est disponible en (s) et en (s/km)
 pour comparer différent format de course. Un score est calculé pour chaque athlète, la formule du calcul est la suivante :
 
Score = Meilleur temps portion de course / Temps de l’athlète sur la portion * 10000 

	L’étape suivante consiste à regrouper les différentes étapes d’une année au sein d’un même dataframe avant ensuite de regrouper toutes les années ensemble et de retirer les colonnes sans informations importantes ou alors celle n’étant disponible que pour certaine année. Les deux dataframes (« scratch » et « class_etape ») sont ensuite
sauvegardés au format csv pour pouvoir être utiliser ultérieurement lors de l’analyse et la visualisation des données.

	Pour l’analyse des données, le choix a été fait de représenter les deltas de temps à l’aide de diagramme en boîte pour faciliter l’observation et une l’interprétation des données. Il y a donc une figure par partie de course et sur chaque figure un diagramme par année (ex :cf figure 1).  Il y a aussi une figure pour représenter le delta de temps du 3ème athlète de chaque équipe par rapport au meilleur temps. Grâce au score précédemment calculé, il est possible d’étudier la corrélation entre les différentes parties de la course entre elle et avec le score total. Cette corrélation est représentée via une matrice de corrélation (ex :cf figure 2), les valeurs sont obtenues par calcul du coefficient de corrélation de Pearson. Enfin, la dernière visualisation proposée est la dynamique de course (ex : cf figure 4 et 5). Cette figure représente l’évolution des écarts entre tous les membres du top 30 final et le meilleur temps à plusieurs stades de la course : fin de cap 1, fin du vélo et à l’arrivé. Cela permet d’étudier comment chaque athlète du top 30 a évolué sur une course donnée. Il y a une figure par course. Ce rapport contiendra uniquement quelques exemples de dynamique de course, l’intégralité des graphiques est disponible dans le notebook ici 


