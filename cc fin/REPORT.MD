# Bank Marketing Dataset

## Description
Le jeu de données est lié aux campagnes de marketing direct (appels téléphoniques) d'une institution bancaire portugaise. L'objectif est de prédire si un client souscrira un dépôt à terme (variable cible : y).

## Caractéristiques
- **Type de données** : Multivariées
- **Domaine** : Business
- **Tâche associée** : Classification
- **Type de variables** : Catégorielles, Entières
- **Nombre d'instances** : 45 211
- **Nombre de features** : 16

## Informations supplémentaires
- Les campagnes de marketing étaient basées sur des appels téléphoniques.
- Plusieurs contacts peuvent être nécessaires pour un même client.
- Le but est de prédire si le produit est souscrit ("yes") ou non ("no").
- Quatre ensembles de données existent, variant par taille et nombre de variables (de 17 à 20).
- Aucune valeur manquante dans le jeu de données.
- Les variables incluent : âge, type de travail, statut marital, éducation, défaut de crédit, solde moyen annuel, prêts (logement et personnel), type de contact, jour et mois du dernier contact, durée du dernier contact, nombre de contacts pendant la campagne, entre autres.
- Sortie (cible) : souscription (oui/non) à un dépôt à terme.

## Variables clés

| Nom de variable  | Type       | Description                             |
|------------------|------------|---------------------------------------|
| age              | Entier     | Âge du client                         |
| job              | Catégoriel | Type d'emploi                         |
| marital          | Catégoriel | État civil                           |
| education        | Catégoriel | Niveau d'éducation                   |
| default          | Binaire    | Crédit en défaut ?                   |
| balance          | Entier     | Solde moyen annuel (en euros)        |
| housing          | Binaire    | Prêt logement ?                     |
| loan             | Binaire    | Prêt personnel ?                    |
| contact          | Catégoriel | Type de communication (cellular, téléphone) |
| day              | Entier     | Jour du dernier contact              |
| month            | Catégoriel | Mois du dernier contact              |
| duration         | Entier     | Durée du dernier contact (secondes)  |
| campaign         | Entier     | Nombre de contacts dans cette campagne|
| pdays            | Entier     | Jours depuis dernier contact précédant|
| previous         | Entier     | Nombre de contacts avant cette campagne|
| poutcome         | Catégoriel | Résultat de la campagne précédente   |
| y (target)       | Binaire    | Souscription dépôt ? (yes/no)        |

## Publications de référence
- Moro, S., Cortez, P., & Rita, P. (2014). *Bank Marketing*. Decision Support Systems.  
DOI : [10.24432/C5K306](https://doi.org/10.24432/C5K306)

## Licence
Creative Commons Attribution 4.0 International (CC BY 4.0) — libre partage et adaptation sous condition de citation.

"""
# Installer les packages nécessaires
!pip install pandas matplotlib seaborn --quiet

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import requests, zipfile
from io import BytesIO

# Télécharger et extraire le dataset
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/00222/bank-additional.zip"
response = requests.get(url)
with zipfile.ZipFile(BytesIO(response.content)) as zf:
    zf.extract('bank-additional/bank-additional-full.csv')

# Charger les données
df = pd.read_csv('bank-additional/bank-additional-full.csv', sep=';')

# Aperçu des données
print("Dimensions du dataset :", df.shape)
print(df.info())
print(df.head())

# Analyse univariée - variables numériques
num_cols = df.select_dtypes(include=['int64', 'float64']).columns
df[num_cols].hist(bins=20, figsize=(14, 10), layout=(4,4))
plt.suptitle('Distribution des variables numériques')
plt.show()

# Analyse univariée - variables catégorielles avec taux de souscription
cat_cols = df.select_dtypes(include=['object']).columns.drop('y')
for col in cat_cols:
    plt.figure(figsize=(10,5))
    sns.countplot(data=df, x=col, hue='y', palette='Set2')
    plt.title(f'Distribution de {col} par souscription')
    plt.xticks(rotation=45)
    plt.show()

# Analyse bivariée - corrélation entre variables numériques
plt.figure(figsize=(12,8))
sns.heatmap(df[num_cols].corr(), annot=True, cmap='coolwarm')
plt.title('Matrice de corrélation des variables numériques')
plt.show()

# Analyse de l'impact de la durée de l'appel sur la souscription
plt.figure(figsize=(10,5))
sns.boxplot(x='y', y='duration', data=df)
plt.title("Durée de l'appel selon souscription")
plt.show()

# Sauvegarder le résumé statistique dans un fichier CSV (optionnel)
df.describe().to_csv('resume_statistique_bank_data.csv')

print("Analyse exploratoire terminée. Vous pouvez télécharger 'resume_statistique_bank_data.csv' pour un résumé numérique.")


---

Les données sont disponibles via le dépôt UCI Machine Learning Repository.

