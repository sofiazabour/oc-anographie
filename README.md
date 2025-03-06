# océanographie
# Rapport d'exploration des données CalCOFI

## 1. Familiarisation avec les données

Les données utilisées dans ce projet proviennent de l'étude CalCOFI (California Cooperative Oceanic Fisheries Investigations). Le fichier **bottle.csv** contient des mesures océanographiques effectuées à différentes profondeurs et localisations.

### Description des données

Les principaux champs de données pertinents pour l'étude sont :

- **T\_degC** : Température de l'eau en degrés Celsius (variable cible).
- **Salnty** : Salinité de l'eau.
- **Depthm** : Profondeur en mètres.
- **O2ml\_L** : Concentration d'oxygène dissous.
- **Chlorophyll (Chl)** : Concentration de chlorophylle.

Des colonnes inutiles comme **Depth\_ID** et **Sta\_ID** ont été supprimées, et les valeurs manquantes ont été remplacées par des zéros.

## 2. Exploration des données

### Nettoyage des données

- Suppression des colonnes avec trop de valeurs manquantes.
- Remplacement des valeurs manquantes par 0.0.

### Analyse exploratoire

- Visualisation des distributions des variables.
- Matrice de corrélation montrant une forte corrélation négative entre la température et la profondeur.

#### Observations

- La température diminue avec la profondeur.
- La salinité montre une corrélation modérée avec la température.

## 3. Ingénierie des descripteurs et Modélisation

### Modèles Utilisés

- Régression Linéaire
- KNN (K-Nearest Neighbors)
- Forêt Aléatoire

### Validation Croisée

Chaque modèle a été évalué à l'aide d'une validation croisée à 5 plis.

## 4. Évaluation

Les métriques d'évaluation utilisées sont :

- MSE (Mean Square Error)
- MAE (Mean Absolute Error)
- R² (Coefficient de détermination)

| Modèle              | MSE      | MAE     | R²    |
| ------------------- | -------- | ------- | ----- |
| Régression Linéaire | 3.22e-07 | 0.00012 | 0.999 |
| KNN                 | 4.11     | 1.24    | 0.78  |
| Forêt Aléatoire     | 0.0004   | 0.0011  | 0.999 |

## 5. Interprétation des résultats

Les résultats montrent que la Forêt Aléatoire donne les meilleures performances, grâce à sa capacité à modéliser des relations non linéaires complexes.

### Implications

- La profondeur reste le facteur prédominant pour la prédiction de la température.
- Les modèles non linéaires offrent des résultats plus précis.

## Conclusion

L'étude a permis de prédire la température de l'eau avec une précision satisfaisante. La Forêt Aléatoire s'est révélée être la méthode la plus performante.

## Références

- Dataset CalCOFI : [https://www.calcofi.org/](https://www.calcofi.org/)
- Documentation pandas : [https://pandas.pydata.org/](https://pandas.pydata.org/)
- Scikit-learn : [https://scikit-learn.org/](https://scikit-learn.org/)

