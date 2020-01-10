---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
ms.date: 01/07/2020
ms.custom: overview
ms.openlocfilehash: ac704b7961a8442a9174cdef5a4cd2a619236a4e
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777397"
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

Un scénario est une description du type de prédiction que vous voulez faire avec vos données. Par exemple :

- prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes
- classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs
- détecter si une transaction bancaire est frauduleuse
- rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Quel est le bon scénario Machine Learning pour moi ?

Dans le générateur de modèles, vous devez sélectionner un scénario. Le type de scénario dépend du type de prédiction que vous essayez d’effectuer.

#### <a name="predict-a-category-when-there-are-only-two-categories"></a>Prédire une catégorie (quand il n’y a que deux catégories)

La classification binaire est utilisée pour catégoriser des données en deux catégories (oui/non ; réussite/échec ; vrai/faux ; positif/négatif).

![Diagramme montrant des exemples de classification binaire incluant la détection des fraudes, l’atténuation des risques et le filtrage d’applications](media/binary-classification-examples.png)

L’analyse des sentiments peut être utilisée pour prédire le sentiment positif ou négatif des commentaires des clients. Il s’agit d’un exemple de la classification binaire Machine Learning tâche.

Si votre scénario nécessite une classification en deux catégories, vous pouvez utiliser ce modèle avec votre propre jeu de données.

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a>Prédire une catégorie (quand il y a trois catégories ou plus)

La classification multiclasse peut être utilisée pour catégoriser des données en trois classes ou plus.

![Exemples de classification multiclasse incluant la classification de documents et de produits, le routage de tickets de support et la hiérarchisation des problèmes des clients](media/multiclass-classification-examples.png)

La classification des problèmes peut être utilisée pour catégoriser des problèmes indiqués dans les commentaires de clients (par exemple sur GitHub) en utilisant le titre du problème et sa description. C’est un exemple de la classification multiclasse Machine Learning tâche.

Vous pouvez utiliser le modèle de classification de problèmes pour votre scénario si vous voulez catégoriser des données en trois catégories ou plus.

#### <a name="predict-a-number"></a>Prédire un nombre

La régression est utilisée pour prédire des nombres.

![Diagramme montrant des exemples de régression, comme la prédiction de prix, les prévisions de ventes et la maintenance prédictive](media/regression-examples.png)

La prédiction des prix peut être utilisée pour prédire le prix d’une maison en fonction de son emplacement, de sa taille et d’autres caractéristiques. Il s’agit d’un exemple de la tâche de régression Machine Learning.

Vous pouvez utiliser le modèle de prédiction des prix pour votre scénario si vous voulez prédire une valeur numérique avec votre propre jeu de données.

#### <a name="classify-images-into-categories"></a>Classer les images en catégories

Ce scénario est un cas particulier de classification multiclasse, où les données d’entrée à classer sont un ensemble d’images.

La classification d’images peut être utilisée pour identifier les images de différentes catégories. Par exemple, différents types de terrain ou d’animaux ou de défauts de fabrication.

Vous pouvez utiliser le modèle de classification d’image pour votre scénario si vous avez un ensemble d’images et que vous souhaitez classer les images en différentes catégories.

#### <a name="custom-scenario"></a>Scénario personnalisé

Le scénario personnalisé vous permet de choisir manuellement votre scénario.

## <a name="data"></a>Données

Une fois que vous avez choisi votre scénario, le générateur de modèles vous demande de fournir un jeu de données. Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario.

![Diagramme montrant les étapes de Model Builder](media/model-builder-steps.png)

Le générateur de modèles prend en charge les jeux de données aux formats. tsv,. csv,. txt, ainsi que le format de base de données SQL. Si vous avez un fichier. txt, les colonnes doivent être séparées par des `,`, `;` ou `/t` et le fichier doit avoir une ligne d’en-tête.

Si le jeu de données est constitué d’images, les types de fichiers pris en charge sont `.jpg` et `.png`.

Pour plus d’informations, consultez [charger des données d’apprentissage dans le générateur de modèles](how-to-guides/load-data-model-builder.md).

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

|Scénario|Tâche ML|Données|Ajouter des contrôles|Fonctionnalités|
|-|-|-|-|-|
|Prédiction des prix|régression|[Données de courses de taxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifs|Heure, distance du trajet|
|Détection d’anomalie|classification binaire ;|[Données de ventes de produits](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ventes de produits|Mois|
|Analyse d'opinions|classification binaire ;|[Données de commentaires de site web](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)|Commentaire, Année|
|Détection des fraudes|classification binaire ;|[Données de carte de crédit](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 en cas de fraude, sinon 0)|Quantité, V1-V28 (caractéristiques anonymisées)|
|Classification de texte|classification multiclasse.|[Données de problèmes GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Zone|Titre, Description|
|Classification d’images|classification multiclasse.|[Images de fleurs](http://download.tensorflow.org/example_images/flower_photos.tgz)|Type de fleur : marguerites, dandelion, roses, tournesols, tulipes|Données d’image elles-mêmes|

## <a name="train"></a>Former

Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.

### <a name="what-is-training"></a>Qu’est-ce que l’entraînement ?

L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario. Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant. Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.

Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.

### <a name="how-long-should-i-train-for"></a>Combien de temps doit durer l’entraînement ?

Le générateur de modèles utilise AutoML pour explorer plusieurs modèles afin de trouver le meilleur modèle d’exécution.

Des périodes de formation plus longues permettent à AutoML d’explorer plus de modèles avec un plus grand nombre de paramètres.

Le tableau ci-dessous résume la durée moyenne nécessaire pour obtenir de bonnes performances pour une suite d’exemples de jeux de données, sur un ordinateur local.

|Taille du jeu de données|Temps moyen de formation|
|------------|---------------------|
|0-10 MO|10 s|
|10-100 MO|10 min|
|100-500 MO|30 min|
|500-1 GO|60 min|
|1 GO +|plus de 3 heures|

Ces chiffres sont un guide uniquement. La longueur exacte de l’apprentissage dépend des éléments suivants :

- nombre de fonctionnalités (colonnes) utilisées comme entrée pour le modèle
- type de colonne
- tâche ML
- performances du processeur, du disque et de la mémoire de l’ordinateur utilisé pour l’apprentissage

## <a name="evaluate"></a>Évaluer

L’évaluation est le processus qui consiste à mesurer la qualité de votre modèle. Le générateur de modèles utilise le modèle formé pour faire des prédictions avec de nouvelles données de test, puis mesure la qualité des prédictions.

Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test. Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle. 

### <a name="how-do-i-understand-my-model-performance"></a>Comment faire comprenez les performances de mon modèle ?

Un scénario est mappé à une tâche de Machine Learning. Chaque tâche ML possède son propre ensemble de mesures d’évaluation.

#### <a name="regression-for-example-price-prediction"></a>Régression (par exemple, prédiction de prix)

La mesure par défaut pour les problèmes de régression est RSquared, la valeur de RSquared est comprise entre 0 et 1. 1 est la meilleure valeur possible, ou en d’autres termes, plus la valeur de RSquared est proche de 1, plus votre modèle est performant.

D’autres métriques signalées telles que la perte absolue, la perte au carré et la perte RMS sont des métriques supplémentaires, qui peuvent être utilisées pour comprendre comment votre modèle s’exécute et le comparer à d’autres modèles de régression.

#### <a name="binary-classification-for-example-sentiment-analysis"></a>Classification binaire (par exemple, Analyse des sentiments)

La mesure par défaut pour les problèmes de classification est la précision. La précision définit la proportion de prédictions correctes que votre modèle effectue sur le jeu de données de test. Plus la valeur est proche de 100% ou 1,0, mieux c’est.

D’autres mesures signalées telles que AUC (zone sous la courbe), qui mesurent le taux réel positif par rapport au taux de faux positifs, doivent être supérieures à 0,50 pour que les modèles soient acceptables.

Des métriques supplémentaires comme le score F1 peuvent être utilisées pour contrôler l’équilibre entre précision et rappel.

#### <a name="multi-class-classification-for-example-issue-classification-image-classification"></a>Classification multiclasse (par exemple, classification des problèmes, classification des images)

La mesure par défaut de la classification multiclasse est micro-précision. Plus la micro-précision est proche de 100% ou 1,0, mieux c’est.

Une autre mesure importante pour la classification multiclasse est la précision des macros, similaire à la microprécision, plus proche de 1,0. Un bon moyen de réfléchir à ces deux types de précision est :

- Microprécision : à quelle fréquence un ticket entrant est-il classé à l’équipe appropriée ?
- Précision des macros : pour une équipe moyenne, à quelle fréquence un ticket entrant est-il correct pour son équipe ?

### <a name="more-information-on-evaluation-metrics"></a>Plus d’informations sur les métriques d’évaluation

Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).

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
