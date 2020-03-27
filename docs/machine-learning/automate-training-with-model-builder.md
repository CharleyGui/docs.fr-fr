---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344770"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Qu’est-ce que Model Builder et comment fonctionne-t-il ?

Model Builder ML.NET est une extension graphique intuitive de Visual Studio, qui permet de générer, d’entraîner et de déployer des modèles Machine Learning personnalisés.

Model Builder utilise le Machine Learning automatisé (AutoML) pour explorer différents algorithmes et paramètres de machine learning afin de vous aider à trouver le modèle qui convient le mieux à votre scénario.

Vous n’avez pas besoin d’une expertise en machine learning pour utiliser Model Builder. Vous avez seulement besoin de quelques données et d’un problème à résoudre. Model Builder génère le code pour ajouter le modèle à votre application .NET.

![Animation de l’interface utilisateur de l’extension Model Builder de Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="scenario"></a>Scénario

Vous pouvez soumettre de nombreux scénarios différents à Model Builder pour générer un modèle Machine Learning pour votre application.

Un scénario est une description du type de prédiction que vous voulez faire avec vos données. Par exemple :

- prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes
- classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs
- détecter si une transaction bancaire est frauduleuse
- rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Quel est le bon scénario Machine Learning pour moi ?

Dans Model Builder, vous devez sélectionner un scénario. Le type de scénario dépend du type de prédiction que vous essayez de faire.

#### <a name="text-classification"></a>Classification de texte

La classification est utilisée pour classer les données en catégories.

![Diagramme montrant des exemples de classification binaire incluant la détection des fraudes, l’atténuation des risques et le filtrage d’applications](media/binary-classification-examples.png)

![Exemples de classification multiclasse incluant la classification de documents et de produits, le routage de tickets de support et la hiérarchisation des problèmes des clients](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a>Prévision de la valeur

La régression est utilisée pour prédire des nombres.

![Diagramme montrant des exemples de régression, comme la prédiction de prix, les prévisions de ventes et la maintenance prédictive](media/regression-examples.png)

#### <a name="image-classification"></a>Classification d’image

La classification des images peut être utilisée pour identifier les images de différentes catégories. Par exemple, différents types de terrain ou d’animaux ou de défauts de fabrication.

Vous pouvez utiliser le scénario de classification d’image si vous avez un ensemble d’images, et que vous souhaitez classer les images en différentes catégories.

#### <a name="recommendation"></a>Recommandation

Le scénario de recommandation prévoit une liste d’éléments suggérés pour un utilisateur particulier, en fonction de la similitude de leurs goûts et de leurs aversions pour les autres utilisateurs.

Vous pouvez utiliser le scénario de recommandation lorsque vous avez un ensemble d’utilisateurs et un ensemble de «produits», tels que des articles à acheter, des films, des livres ou des émissions de télévision, ainsi qu’un ensemble de utilisateurs "évaluations" de ces produits.

## <a name="environment"></a>Environnement

Vous pouvez former votre modèle d’apprentissage automatique localement sur votre machine ou dans le cloud sur Azure.

Lorsque vous vous entraînez localement, vous travaillez dans les contraintes de vos ressources informatiques (processeur, mémoire et disque). Lorsque vous vous entraînez dans le cloud, vous pouvez intensifier vos ressources pour répondre aux exigences de votre scénario, en particulier pour les grands jeux de données.

La formation locale est soutenue pour tous les scénarios.

La formation Azure est soutenue pour la classification d’images.

## <a name="data"></a>Données

Une fois que vous avez choisi votre scénario, Model Builder vous demande de fournir un jeu de données. Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario.

![Diagramme montrant les étapes de Model Builder](media/model-builder-steps.png)

Modèle Builder prend en charge les ensembles de données dans les formats .tsv, .csv, .txt, ainsi que le format de base de données SQL. Si vous avez un fichier .txt, `,` `;` les `/t` colonnes doivent être séparées avec, ou et le fichier doit avoir une rangée d’en-tête.

Si le jeu de données est composé d’images, les types de fichiers pris en charge sont `.jpg` et `.png`.

Pour plus d’informations, voir [les données de formation de charge dans Model Builder](how-to-guides/load-data-model-builder.md).

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

|Scénario|Exemple|Données|Étiquette|Fonctionnalités|
|-|-|-|-|-|
|classification ;|Prédire les anomalies de vente|[Données de ventes de produits](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ventes de produits|Month|
||Prédire le sentiment des commentaires sur les sites Web|[Données de commentaires de site web](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)|Commentaire, Année|
||Prédire les transactions frauduleuses par carte de crédit|[Données de carte de crédit](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 en cas de fraude, sinon 0)|Quantité, V1-V28 (caractéristiques anonymisées)|
||Prédire le type de problème dans un référentiel GitHub|[Données de problèmes GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Domaine|Titre, Description|
|Prévision de la valeur|Prédire le prix du billet de taxi|[Données de courses de taxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Fare|Heure, distance du trajet|
|Classification d’image|Prédire la catégorie d’un problème|[images de fleurs](http://download.tensorflow.org/example_images/flower_photos.tgz)|Le type de fleur: marguerite, pissenlit, roses, tournesols, tulipes|Les données d’image elles-mêmes|
|Recommandation|Prédire les films que quelqu’un aimera|[notes de film](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|Utilisateurs, Films|Évaluations|

## <a name="train"></a>Former

Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.

### <a name="what-is-training"></a>Qu’est-ce que l’entraînement ?

L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario. Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant. Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.

Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.

### <a name="how-long-should-i-train-for"></a>Combien de temps doit durer l’entraînement ?

Model Builder utilise AutoML pour explorer plusieurs modèles pour vous trouver le modèle le plus performant.

Des périodes de formation plus longues permettent à AutoML d’explorer plus de modèles avec un plus large éventail de réglages.

Le tableau ci-dessous résume le temps moyen pris pour obtenir de bonnes performances pour une suite d’exemples de jeux de données, sur une machine locale.

|Taille de dataset|Temps moyen de formation|
|------------|---------------------|
|0 - 10 Mo|10 s|
|10 - 100 Mo|10 min|
|100 - 500 Mo|30 min|
|500 - 1 Go|60 min|
|1 Go|Plus de 3 heures|

Ces chiffres sont un guide seulement. La durée exacte de la formation dépend des faits :

- le nombre de fonctionnalités (colonnes) utilisées comme entrée au modèle
- le type de colonnes
- la tâche ML
- le processeur, le disque et les performances de mémoire de la machine utilisée pour la formation

## <a name="evaluate"></a>Évaluer

L’évaluation est le processus de mesure de la qualité de votre modèle. Modèle Builder utilise le modèle formé pour faire des prédictions avec de nouvelles données de test, puis mesure la qualité des prédictions sont.

Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test. Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle.

### <a name="how-do-i-understand-my-model-performance"></a>Comment puis-je comprendre la performance de mon modèle ?

Un scénario est adapté à une tâche d’apprentissage automatique. Chaque tâche ML a son propre ensemble de mesures d’évaluation.

#### <a name="value-prediction"></a>Prévision de la valeur

La mesure par défaut pour les problèmes de prédiction de valeur est RSquared, la valeur des gammes RSquared entre 0 et 1. 1 est la meilleure valeur possible ou en d’autres termes plus la valeur de RSquared à 1 mieux votre modèle est performant.

D’autres mesures signalées telles que la perte absolue, la perte au carré et la perte de RMS sont des mesures supplémentaires, qui peuvent être utilisées pour comprendre comment votre modèle fonctionne et le compare à d’autres modèles de prédiction de valeur.

#### <a name="classification-2-categories"></a>Classification (2 catégories)

La mesure par défaut pour les problèmes de classification est l’exactitude. L’exactitude définit la proportion de prédictions correctes que votre modèle fait sur le jeu de données de test. Plus il est proche de 100% ou 1,0, mieux c’est.

D’autres mesures signalées comme l’AUC (zone sous la courbe), qui mesure le taux positif réel par rapport au taux de faux positifs devraient être supérieurs à 0,50 pour que les modèles soient acceptables.

Des mesures supplémentaires comme le score F1 peuvent être utilisées pour contrôler l’équilibre entre précision et rappel.

#### <a name="classification-3-categories"></a>Classification (3 catégories et plus)

La mesure par défaut pour la classification multi-classes est Micro Accuracy. Plus la Micro Accuracy est proche à 100% ou 1,0, mieux c’est.

Une autre mesure importante pour la classification multi-classe est macro-précision, semblable à Micro-précision le plus proche de 1.0 le mieux il est. Une bonne façon de penser à ces deux types de précision est:

- Micro-précision : À quelle fréquence un billet entrant est-il classé à la bonne équipe ?
- Macro-précision : Pour une équipe moyenne, à quelle fréquence un billet entrant est-il correct pour son équipe ?

### <a name="more-information-on-evaluation-metrics"></a>Plus d’informations sur les mesures d’évaluation

Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).

## <a name="improve"></a>Améliorer

Si le score de performances de votre modèle n’est pas aussi bon que souhaité, vous pouvez :

- Entraîner sur une période de temps plus longue. Avec plus de temps, le moteur d’apprentissage automatique automatisé expérimente avec plus d’algorithmes et de paramètres.

- Ajouter des données. Parfois, la quantité de données n’est pas suffisante pour entraîner un modèle Machine Learning de haute qualité.

- Équilibrer vos données. Pour les tâches de classification, vérifiez que le jeu d’entraînement est équilibré entre les différentes catégories. Par exemple, si vous avez quatre classes pour 100 exemples d’entraînement et que les deux premières classes (étiquette1 et étiquette2) sont utilisées pour 90 enregistrements, mais que les deux autres (étiquette3 et étiquette4) sont utilisées seulement sur les 10 enregistrements restants, l’absence de données équilibrées peut faire que votre modèle aura du mal à prédire correctement étiquette3 ou étiquette4.

## <a name="code"></a>Code

Après la phase d’évaluation, Model Builder génère un fichier de modèle et du code que vous pouvez utiliser pour ajouter le modèle à votre application. Les modèles ML.NET sont enregistrés sous la forme d’un fichier zip. Le code pour charger et utiliser votre modèle est ajouté en tant que nouveau projet dans votre solution. Model Builder ajoute également un exemple d’application console que vous pouvez exécuter pour voir votre modèle en action.

En outre, Model Builder produit le code qui a généré le modèle, ce qui vous permet de comprendre les étapes utilisées pour cette génération. Vous pouvez également utiliser le code de l’entraînement du modèle pour réentraîner votre modèle avec de nouvelles données.

## <a name="whats-next"></a>Quelle est l’étape suivante ?

[Installer](how-to-guides/install-model-builder.md) l’extension Visual Studio Model Builder

Essayer [le scénario de prédiction des prix ou un autre scénario de régression](tutorials/predict-prices-with-model-builder.md)
