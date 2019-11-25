---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971527"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Qu’est-ce que Model Builder et comment fonctionne-t-il ?

Model Builder ML.NET est une extension graphique intuitive de Visual Studio, qui permet de générer, d’entraîner et de déployer des modèles Machine Learning personnalisés.

Model Builder utilise le Machine Learning automatisé (AutoML) pour explorer différents algorithmes et paramètres de machine learning afin de vous aider à trouver le modèle qui convient le mieux à votre scénario.

Vous n’avez pas besoin d’une expertise en machine learning pour utiliser Model Builder. Vous avez seulement besoin de quelques données et d’un problème à résoudre. Model Builder génère le code pour ajouter le modèle à votre application .NET.

![Animation de l’interface utilisateur de l’extension Model Builder de Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="scenarios"></a>Scénarios

Vous pouvez soumettre de nombreux scénarios différents à Model Builder pour générer un modèle Machine Learning pour votre application.

Un scénario est une description du type de prédiction que vous voulez faire avec vos données. Exemple :

- prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes
- classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs
- détecter si une transaction bancaire est frauduleuse
- rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise

## <a name="choose-a-model-type"></a>Choisir un type de modèle

Dans Model Builder, vous devez sélectionner un type de modèle Machine Learning. Le type de modèle dépend du type de prédiction que vous essayez de faire.

Pour les scénarios qui prédisent un nombre, le type de modèle Machine Learning est appelé `regression`.

Pour les scénarios qui prédisent une catégorie, le type de modèle est `classification`. Il existe deux types de classification :

- où il n’y a que 2 catégories : `binary classification`.
- où il y a 3 catégories ou plus : `multiclass classification`.

### <a name="which-model-type-is-right-for-me"></a>Quel est le type de modèle qui me convient ?

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Prédire une catégorie (quand il n’y a que deux catégories)

La classification binaire est utilisée pour catégoriser des données en deux catégories (oui/non ; réussite/échec ; vrai/faux ; positif/négatif).

![Diagramme montrant des exemples de classification binaire incluant la détection des fraudes, l’atténuation des risques et le filtrage d’applications](media/binary-classification-examples.png)

L’analyse des sentiments peut être utilisée pour prédire le sentiment positif ou négatif des commentaires des clients. C’est un exemple de type de modèle de classification binaire.

Si votre scénario nécessite une classification en deux catégories, vous pouvez utiliser ce modèle avec votre propre jeu de données.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Prédire une catégorie (quand il y a trois catégories ou plus)

La classification multiclasse peut être utilisée pour catégoriser des données en trois classes ou plus.

![Exemples de classification multiclasse incluant la classification de documents et de produits, le routage de tickets de support et la hiérarchisation des problèmes des clients](media/multiclass-classification-examples.png)

La classification des problèmes peut être utilisée pour catégoriser des problèmes indiqués dans les commentaires de clients (par exemple sur GitHub) en utilisant le titre du problème et sa description. C’est un exemple de type de modèle de classification multiclasse.

Vous pouvez utiliser le modèle de classification de problèmes pour votre scénario si vous voulez catégoriser des données en trois catégories ou plus.

#### <a name="predict-a-number"></a>Prédire un nombre

La régression est utilisée pour prédire des nombres.

![Diagramme montrant des exemples de régression, comme la prédiction de prix, les prévisions de ventes et la maintenance prédictive](media/regression-examples.png)

La prédiction des prix peut être utilisée pour prédire le prix d’une maison en fonction de son emplacement, de sa taille et d’autres caractéristiques. C’est un exemple de type de modèle de régression.

Vous pouvez utiliser le modèle de prédiction des prix pour votre scénario si vous voulez prédire une valeur numérique avec votre propre jeu de données.

#### <a name="custom-scenario-choose-your-model-type"></a>Scénario personnalisé (choisir votre type de modèle)

Le scénario personnalisé vous permet de choisir manuellement votre type de modèle.

## <a name="data"></a>Données

Une fois que vous avez choisi votre type de modèle, Model Builder vous demande de fournir un jeu de données. Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario.

![Diagramme montrant les étapes de Model Builder](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a>Choisir le résultat à prédire (étiquette)

Un jeu de données est une table de lignes d’exemples et de colonnes d’attributs pour l’entraînement. Chaque ligne a :

- une **étiquette** (l’attribut que vous voulez prédire)
- des **caractéristiques** (des attributs qui sont utilisés comme entrées pour prédire l’étiquette).

Pour le scénario de prédiction de prix d’une maison, les caractéristiques peuvent être :

- la superficie de la maison
- le nombre de chambres et de salles de bain
- le code postal

L’étiquette est l’historique des prix des maisons pour cette ligne de valeurs correspondant à la superficie, aux chambres et aux salles de bain, et au code postal.

![Tableau montrant des lignes et des colonnes de données sur les prix de maisons avec des caractéristiques consistant en une taille, un nombre de pièces, un code postal et une étiquette de prix](media/model-builder-data.png)

### <a name="example-datasets"></a>Exemples de jeux de données

Si vous n’avez pas encore vos propres données, essayez un de ces jeux de données :

|Scénario|Type de modèle|Données|Etiquette|Fonctionnalités|
|-|-|-|-|-|
|Prédiction des prix|régression|[Données de courses de taxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifs|Heure, distance du trajet|
|Détection d’anomalie|classification binaire|[Données de ventes de produits](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ventes de produits|Mois|
|Analyse des sentiments|classification binaire|[Données de commentaires de site web](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)|Commentaire, Année|
|Détection des fraudes|classification binaire|[Données de carte de crédit](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 en cas de fraude, sinon 0)|Quantité, V1-V28 (caractéristiques anonymisées)|
|Classification de texte|classification multiclasse|[Données de problèmes GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Zone|Titre, Description|

## <a name="train"></a>Recyclage

Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.

### <a name="what-is-training"></a>Qu’est-ce que l’entraînement ?

L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario. Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant. Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.

Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.

## <a name="evaluate"></a>Évaluer

L’évaluation est le processus consistant à utiliser le modèle entraîné pour faire des prédictions avec de nouvelles données de test, puis à mesurer la qualité des prédictions.

Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test. Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle. Model Builder utilise des métriques pour mesurer la qualité du modèle. Les métriques spécifiques utilisées dépendent du type de modèle. Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).

## <a name="improve"></a>Améliorer

Si le score de performances de votre modèle n’est pas aussi bon que souhaité, vous pouvez :

- Entraîner sur une période de temps plus longue. Avec plus de temps, le moteur Machine Learning automatisé va essayer plus d’algorithmes et de paramètres.

- Ajouter des données. Parfois, la quantité de données n’est pas suffisante pour entraîner un modèle Machine Learning de haute qualité.

- Équilibrer vos données. Pour les tâches de classification, vérifiez que le jeu d’entraînement est équilibré entre les différentes catégories. Par exemple, si vous avez quatre classes pour 100 exemples d’entraînement et que les deux premières classes (étiquette1 et étiquette2) sont utilisées pour 90 enregistrements, mais que les deux autres (étiquette3 et étiquette4) sont utilisées seulement sur les 10 enregistrements restants, l’absence de données équilibrées peut faire que votre modèle aura du mal à prédire correctement étiquette3 ou étiquette4.

## <a name="code"></a>Code

Après la phase d’évaluation, Model Builder génère un fichier de modèle et du code que vous pouvez utiliser pour ajouter le modèle à votre application. Les modèles ML.NET sont enregistrés sous la forme d’un fichier zip. Le code pour charger et utiliser votre modèle est ajouté en tant que nouveau projet dans votre solution. Model Builder ajoute également un exemple d’application console que vous pouvez exécuter pour voir votre modèle en action.

En outre, Model Builder produit le code qui a généré le modèle, ce qui vous permet de comprendre les étapes utilisées pour cette génération. Vous pouvez également utiliser le code de l’entraînement du modèle pour réentraîner votre modèle avec de nouvelles données.

## <a name="whats-next"></a>Étapes suivantes

[Installer](how-to-guides/install-model-builder.md) l’extension Visual Studio Model Builder

Essayer [le scénario de prédiction des prix ou un autre scénario de régression](tutorials/predict-prices-with-model-builder.md)
