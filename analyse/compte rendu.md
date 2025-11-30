# Analyse des Données du Football Mondial ⚽

## Introduction

Ce document présente une analyse exploratoire des données (EDA) réalisée sur un ensemble de données concernant les résultats de matchs de football internationaux et les marqueurs de buts mondiaux. L'objectif principal de cette analyse est d'identifier les tendances historiques, la distribution des résultats, et les performances des équipes nationales à travers le temps.

L'analyse a été effectuée à l'aide de librairies Python courantes telles que **Pandas** et **NumPy** pour la manipulation des données, et **Matplotlib** et **Seaborn** pour la visualisation.

## Développement : Exploration et Analyse des Données

### 1. Préparation des données

Le jeu de données principal (contenant les résultats des matchs) comporte **48 673 entrées** et 9 colonnes. Aucune valeur manquante n'a été détectée dans les colonnes clés.

Plusieurs caractéristiques ont été dérivées pour enrichir l'analyse :
* `total_goals` : Le nombre total de buts marqués dans le match.
* `goal_diff` : La différence de buts (domicile - extérieur).
* `match_result` : Le résultat du match, classé en `Home Win` (Victoire à Domicile), `Away Win` (Victoire à l'Extérieur) ou `Draw` (Match Nul).

### 2. Tendances Historiques

L'étude des données a révélé des tendances notables :

* **Fréquence des matchs :** Le nombre de matchs joués annuellement a considérablement augmenté au fil du temps, marquant une croissance particulièrement forte à partir du début du 20e siècle et après la Seconde Guerre mondiale.
* **Moyenne de buts :** La moyenne de buts par match, qui a atteint des sommets au début du 20e siècle, s'est stabilisée au cours des dernières décennies, tournant autour de 2,5 à 3 buts par match.

### 3. Résultats et Performances

L'analyse des résultats des matchs historiques révèle une prépondérance des victoires à domicile :

* **Distribution des résultats :** Les **victoires à domicile** (`Home Win`) sont de loin le résultat le plus fréquent, suivies par les **matchs nuls** (`Draw`), qui sont légèrement plus fréquents que les **victoires à l'extérieur** (`Away Win`).
* **Scores fréquents :** Les scores les plus courants dans l'histoire sont **1-1**, **1-0** et **2-1**. La majorité des matchs se terminent avec un faible nombre de buts (2 ou 3 au total).
* **Équipes dominantes :** Des équipes historiques comme le **Brésil**, l'**Uruguay**, l'**Argentine** et l'**Angleterre** font partie des 20 équipes ayant joué le plus de matchs. Le **Brésil** se distingue également comme l'équipe ayant marqué le plus grand nombre total de buts.
* **Corrélation :** Une forte corrélation positive est observée entre le score à domicile, le score à l'extérieur et le nombre total de buts.

## Conclusion

L'analyse des données du football mondial confirme une augmentation marquée du nombre de matchs joués au fil des ans, reflétant la croissance du sport. Elle met en évidence un **avantage clair pour l'équipe jouant à domicile** et une tendance aux **scores relativement bas**. Historiquement, le **Brésil** se positionne comme l'équipe la plus prolifique en termes de buts marqués.

