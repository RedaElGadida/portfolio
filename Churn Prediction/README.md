# Prédiction du Churn Client pour une Plateforme de Streaming 📺

## Résumé du Projet

Ce projet analyse le désabonnement (churn) des clients d'une plateforme de streaming. Un modèle de **Random Forest** a été développé pour identifier les abonnés présentant un risque élevé de résiliation, afin de permettre des stratégies de rétention proactives.

## Principaux Résultats

* **Performance du Modèle :** Le modèle a atteint un score **ROC-AUC de 0.74**, démontrant une bonne capacité à prédire le churn.
* **Facteurs de Risque Clés :** Les caractéristiques les plus importantes pour prédire le churn sont l'**ancienneté du compte (`AccountAge`)**, la **durée moyenne de visionnage (`AverageViewingDuration`)** et les **heures de visionnage par semaine (`ViewingHoursPerWeek`)**.

## Méthodologie en Bref

1.  **Préparation des données :** Nettoyage des données, encodage One-Hot des variables catégorielles et standardisation.
2.  **Modélisation :** Entraînement et optimisation d'un classificateur **Random Forest** avec `GridSearchCV`.
3.  **Évaluation :** Mesure de la performance du modèle avec la métrique ROC-AUC.
4.  **Analyse :** Identification des facteurs les plus influents grâce à l'analyse de l'importance des caractéristiques.

## Technologies Utilisées

* Python
* Pandas
* Scikit-learn
* Matplotlib / Seaborn
* Jupyter Notebook

## Comment Lancer le Projet

1.  Clonez ce dépôt.
2.  Installez les bibliothèques nécessaires :
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn jupyter
    ```
3.  Assurez-vous que `train.csv` et `test.csv` sont dans le dossier.
4.  Exécutez le notebook `Churn_Analysis.ipynb`.