# Modèle de Prédiction de Défaut de Paiement 🏦

## Résumé du Projet

Ce projet vise à prédire la probabilité qu'un emprunteur ne rembourse pas son prêt. Un modèle de **Gradient Boosting** a été entraîné pour analyser les informations des emprunteurs et évaluer le risque de défaut, aidant ainsi les institutions financières à minimiser leurs pertes.

## Principaux Résultats

* **Performance du Modèle :** Le modèle a atteint un score **ROC-AUC de 0.758**, montrant une bonne capacité à identifier les prêts à risque.
* **Facteurs de Risque Clés :** Les caractéristiques les plus importantes pour prédire un défaut de paiement sont le **score de crédit (`CreditScore`)**, le **revenu (`Income`)** et le **montant du prêt (`LoanAmount`)**.

## Méthodologie en Bref

1.  **Préparation des données :** Nettoyage des données et transformation des variables catégorielles (One-Hot Encoding).
2.  **Modélisation :** Entraînement et comparaison de plusieurs algorithmes (Random Forest, XGBoost, Gradient Boosting).
3.  **Évaluation :** Le Gradient Boosting a été sélectionné pour sa performance supérieure.
4.  **Analyse :** Identification des facteurs les plus influents grâce à l'analyse de l'importance des caractéristiques.

## Technologies Utilisées

* Python
* Pandas
* Scikit-learn
* XGBoost
* Matplotlib / Seaborn
* Jupyter Notebook

## Comment Lancer le Projet

1.  Clonez ce dépôt.
2.  Installez les bibliothèques nécessaires :
    ```bash
    pip install pandas scikit-learn xgboost matplotlib seaborn jupyter
    ```
3.  Assurez-vous que `train.csv` et `test.csv` sont dans le dossier.
4.  Exécutez le notebook `LoanDefaultPrediction.ipynb`.

---