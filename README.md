# Effet de la taille des classes sur les résultats scolaires (Analyse économétrique (CASchools))

## Objectif

Ce projet examine la relation entre la taille des classes mesurée par le ratio élèves/enseignant et les résultats scolaires des élèves, à partir de données réelles sur 420 districts scolaires en Californie. L'analyse s'inscrit dans une démarche de microéconométrie appliquée : identifier un effet causal tout en tenant compte des biais statistiques classiques (variable omise, hétéroscédasticité).

## Question de recherche

Quel est l’effet de la taille des classes sur les résultats scolaires  ?

## Données

**Source** : [CASchools (package AER)](https://vincentarelbundock.github.io/Rdatasets/csv/AER/CASchools.csv), issu du manuel *Introduction to Econometrics* de Stock & Watson.

**Unité d'observation** : district scolaire (n = 420)

**Variables clés** :
- `score` :moyenne des scores en lecture et en mathématiques (variable expliquée)
- `student_teacher_ratio` : nombre d'élèves par enseignant (variable explicative principale)
- `lunch` : % d'élèves bénéficiant de la cantine à tarif réduit (mesure de pauvreté)
- `english` : % d'élèves apprenant l'anglais comme langue seconde
- `income` : revenu moyen du district

## Méthodologie

1. Import, nettoyage et exploration des données
2. Analyse descriptive et visualisation 
3. Construction des variables `score` et `student_teacher_ratio`
4. Estimation de trois modèles de régression MCO en ajout progressif de contrôles :
   - Modèle 1 : `score ~ student_teacher_ratio`
   - Modèle 2 : `score ~ student_teacher_ratio + lunch`
   - Modèle 3 : `score ~ student_teacher_ratio + lunch + english`
5. Comparaison des modèles et discussion du biais de variable omise
6. Discussion critique sur la portée causale des résultats

## Principaux résultats

coefficient_teacher_ratio et R² ajusté
Modèle 1 (-2,28 ; 0,049)
Modèle 2 (-1,12 ; 0,766)
Modèle 3 (-1 ; 0,773)

L'effet du ratio élèves/enseignant sur le score reste négatif et statistiquement significatif dans les trois modèles, mais sa magnitude diminue fortement une fois les variables `lunch` et `english` contrôlées ce qui met en évidence un biais de variable omise dans le modèle simple. La variable `lunch` (pauvreté) s'avère être le contrôle le plus déterminant.

## Limites

L'effet estimé ne peut pas être interprété comme pleinement causal : des facteurs non observés (qualité des enseignants, implication des familles, ressources pédagogiques) pourraient encore biaiser l'estimation. Une approche par variable instrumentale permettrait d'aller plus loin sur l'identification causale.

## Outils utilisés


- Jupyter Notebook ((pandas, statsmodels, matplotlib)

## Auteur

LAWSON Théodora : Projet réalisé dans le cadre d'une remise à niveau en économétrie
