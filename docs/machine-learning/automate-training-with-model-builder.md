---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
author: natke
ms.date: 06/26/2019
ms.custom: overview
ms.openlocfilehash: 6f5bbe3c389e3ca42550a48ef3e6edbc963ac2e9
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410587"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a>Qu’est-ce que Model Builder et comment fonctionne-t-il ?

Model Builder ML.NET est une extension graphique de Visual Studio facile à comprendre, qui permet de générer, d’entraîner et de déployer des modèles Machine Learning personnalisés. 

Model Builder utilise le Machine Learning automatisé (AutoML) pour explorer différents algorithmes et paramètres de machine learning afin de vous aider à trouver le modèle qui convient le mieux à votre scénario.

Vous n’avez pas besoin d’une expertise en machine learning pour utiliser Model Builder. Vous avez seulement besoin de quelques données et d’un problème à résoudre. Model Builder génère le code pour ajouter le modèle à votre application .NET.

![Animation de l’interface utilisateur de l’extension Model Builder de Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> Model Builder est actuellement en préversion.

## <a name="scenarios"></a>Scénarios

Vous pouvez soumettre de nombreux scénarios différents à Model Builder pour générer un modèle Machine Learning pour votre application.

Un scénario est une description du type de prédiction que vous voulez faire sur vos données. Par exemple :
- prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes
- classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs
- détecter si une transaction bancaire est frauduleuse
- rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise

Dans Model Builder, vous devez mapper votre scénario à une [tâche ML.NET](resources/tasks.md). Vous pouvez utiliser Model Builder pour la **régression** (prédiction de nombres) et pour la **classification** (prédiction de catégories).

### <a name="which-machine-learning-scenario-is-right-for-me"></a>Quel est le bon scénario Machine Learning pour moi ?

Model Builder est fourni avec des modèles pour l’analyse des sentiments, la classification des problèmes, la prédiction des prix et des scénarios personnalisés. Ces modèles peuvent être utilisés comme point de départ pour votre scénario ML.NET spécifique.

#### <a name="sentiment-analysis-binary-classification"></a>Analyse des sentiments (classification binaire)

L’analyse des sentiments peut être utilisée pour prédire le sentiment positif ou négatif des commentaires des clients. C’est un exemple de tâche de classification binaire.

La classification binaire est utilisée pour catégoriser des données en deux classes (oui/non ; réussite/échec ; vrai/faux ; positif/négatif). Elle peut être utilisée pour répondre à des questions comme celles-ci :

- Cet e-mail est-il un courrier indésirable ? (détection des courriers indésirables)
- Quels candidats sont éligibles à l’adhésion ? (filtrage des candidatures)
- Quels comptes sont susceptibles de ne pas payer leurs factures à temps ? (atténuation des risques)
- Cette transaction de carte de crédit est-elle frauduleuse ? (détection des fraudes)

Si votre scénario nécessite une classification en deux catégories, vous pouvez utiliser ce modèle avec votre propre jeu de données.
 
#### <a name="issue-classification-multiclass-classification"></a>Classification des problèmes (classification multiclasse)

La classification des problèmes peut être utilisée pour catégoriser des problèmes indiqués dans les commentaires de clients (par exemple sur GitHub) en utilisant le titre du problème et sa description. C’est un exemple de tâche de classification multiclasse.

La classification multiclasse peut être utilisée pour catégoriser des données en trois classes ou plus. Elle peut être utilisée pour répondre à des questions comme celles-ci :

- À quel service dois-je diriger un ticket de support ? (routage de tickets de support)
- Quelle est la priorité du problème d’un client ? (définition des priorités des problèmes des clients)
- À quelle catégorie un produit appartient-il ? (classification de produits)
- Quel est le type d’un document ? (classification de document/e-mail)

Vous pouvez utiliser le modèle de classification de problèmes pour votre scénario si vous voulez catégoriser des données en trois catégories ou plus.

#### <a name="price-prediction-regression"></a>Prédiction des prix (régression)

La prédiction des prix peut être utilisée pour prédire le prix d’une maison en fonction de son emplacement, de sa taille et d’autres caractéristiques. C’est un exemple de tâche de régression.

La régression est utilisée pour prédire des nombres. Elle peut être utilisée pour répondre à des questions comme celles-ci :

- À quel prix se vendra une maison ? (prédiction des prix)
- Au bout de combien de temps une pièce mécanique va-t-elle nécessiter de la maintenance ? (maintenance prédictive)
- Quel est le taux d’humidité dans ce sèche-linge ? (surveillance des machines)
- Quel sera le total des ventes annuelles pour cette région ? (prévision des ventes)

Vous pouvez utiliser le modèle de prédiction des prix pour votre scénario si vous voulez prédire une valeur numérique avec votre propre jeu de données.

#### <a name="custom-scenario-choose-your-task"></a>Scénario personnalisé (choisir votre tâche)

Le scénario personnalisé vous permet de choisir votre propre tâche. Choisissez le scénario le plus pertinent pour votre problème.

Le scénario personnalisé vous permet de choisir votre propre tâche Machine Learning. Dans les modèles précédents, la tâche Machine Learning était déterminée pour le scénario : classification binaire, classification multiclasse ou régression. Dans ce modèle, vous pouvez choisir la tâche ML que vous voulez utiliser sur vos données.

## <a name="data"></a>Données

Une fois que vous avez mappé votre scénario à une tâche, Model Builder vous demande de fournir un jeu de données. Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario. Vous devez également choisir le résultat que vous voulez prédire.

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

### <a name="data-formats"></a>Formats de données

Model Builder est soumis aux limitations suivantes sur les données :

- Les données doivent être stockées dans un fichier (.csv ou .tsv, avec une ligne d’en-tête), ou dans une base de données SQL Server.
- Une limite de 1 Go sur le jeu de données d’entraînement
- Le serveur SQL Server a une limite de 100 000 lignes pour l’entraînement
- Les données du serveur SQL Server sont copiées du serveur vers votre machine locale avant l’entraînement

### <a name="example-datasets"></a>Exemples de jeux de données

Si vous n’avez pas encore vos propres données, essayez un de ces jeux de données :

|Scénario|Tâche ML|Données|Etiquette|Fonctionnalités|
|-|-|-|-|-|
|Prédiction des prix|régression ;|[Données de courses de taxi](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|Tarifs|Heure, distance du trajet|
|Détection d’anomalie|classification binaire ;|[Données de ventes de produits](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|Ventes de produits|Mois|
|analyse de sentiments|classification binaire ;|[Données de commentaires de site web](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_SentimentAnalysis/SentimentAnalysis/Data/wikiDetoxAnnotated40kRows.tsv)|Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)|Commentaire, Année|
|Détection des fraudes|classification binaire ;|[Données de carte de crédit](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|Classe (1 en cas de fraude, sinon 0)|Quantité, V1-V28 (caractéristiques anonymisées)|
|Classification de texte|classification multiclasse.|[Données de problèmes GitHub](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|Domaine|Titre, Description|

## <a name="train"></a>Former

Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.

### <a name="what-is-training"></a>Qu’est-ce que l’entraînement ?

L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario. Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant. Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.

Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.

### <a name="how-long-should-i-train-for"></a>Combien de temps doit durer l’entraînement ?

Vous pouvez fournir une durée d’entraînement. En règle générale, un entraînement qui dure plus longtemps produit un modèle plus précis. Plus la taille du jeu de données d’entraînement augmente, plus la durée de l’entraînement doit être allongée. Le tableau suivant donne des indications sur la durée de l’entraînement pour des jeux de données d’une taille croissante.

Taille du jeu de données  | Type du jeu de données       | Avg. Durée de l’entraînement
------------- | ------------------ | --------------
0 - 10 Mo     | Numérique et texte   | 10 s
10 - 100 Mo   | Numérique et texte   | 10 min 
100 - 500 Mo  | Numérique et texte   | 30 min 
500 - 1 Go    | Numérique et texte   | 60 min 
\+ de 1 Go         | Numérique et texte   | \+ de 3 heures 

La durée exacte de l’entraînement dépend également des éléments suivants :

- le type des colonnes, c’est-à-dire texte ou numérique
- le type de tâche Machine Learning (régression ou classification)
- le nombre de lignes utilisées pour l’entraînement
- le nombre de colonnes de caractéristique utilisées pour l’entraînement

Model Builder a été testé à grande échelle avec un jeu de données de 1 To, mais la création d’un modèle de haute qualité pour un jeu de données de cette taille peut prendre jusqu’à quatre jours !

## <a name="evaluate"></a>Évaluer

L’évaluation est le processus consistant à utiliser le modèle entraîné pour faire des prédictions avec de nouvelles données de test, puis à mesurer la qualité des prédictions.

Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test. Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle.  Les métriques utilisées pour l’évaluation dépendent de la tâche ML. Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).  

### <a name="sentiment-analysis-binary-classification"></a>Analyse des sentiments (classification binaire)

La métrique par défaut pour les problèmes de classification binaire est la **précision**. La précision définit la proportion de prédictions correctes faites par votre modèle sur le jeu de données de test . **Plus elle est proche de 100 %, plus elle est bonne**.

D’autres métriques sont produites, comme AUC (Aire sous la courbe), qui mesure le taux de vrais positifs par rapport au taux de faux positifs, et qui doit être supérieure à 0,50 pour que les modèles soient acceptables. 

Vous pouvez utiliser des métriques supplémentaires comme le score F1 pour contrôler l’équilibre entre la précision (taux de prédictions correctes par rapport au nombre total de prédictions de cette classe) et le rappel (proportion de prédictions correctes pour le nombre total de membres réels de cette classe).

### <a name="issue-classification-multiclass-classification"></a>Classification des problèmes (classification multiclasse)

La métrique par défaut pour les problèmes de classification multiclasse est la **microprécision**. **Plus elle est proche de 100 %, plus elle est bonne**.

Pour les problèmes où les données sont catégorisées en plusieurs classes, il existe deux types de précision :

- Microprécision : la fraction de prédictions correctes parmi toutes les instances. Dans le scénario de classification des problèmes, la microprécision est la proportion de problèmes entrants qui sont affectés à la catégorie correcte. 
- Macroprécision : la précision moyenne au niveau de la classe. Dans le scénario de classification des problèmes, la précision est mesurée pour chaque catégorie, puis les précisions des catégories sont moyennées. Pour cette métrique, toutes les classes reçoivent une pondération égale. Pour les jeux de données parfaitement équilibrés (où il y a un nombre égal d’exemples de chaque catégorie), la microprécision et la macroprécision sont identiques.


### <a name="price-prediction-regression"></a>Prédiction des prix (régression)

La métrique par défaut pour les problèmes de régression est **RSquared**. 1 est la meilleure valeur possible. Plus RSquared est proche de 1, meilleur est votre modèle.

D’autres métriques produites, comme l’erreur absolue, l’erreur quadratique et l’erreur quadratique moyenne (RMS), peuvent être utilisées pour comprendre votre modèle et pour le comparer à d’autres modèles de régression. 

## <a name="improve"></a>Améliorer

Si le score de performances de votre modèle n’est pas aussi bon que souhaité, vous pouvez :

* Entraîner sur une période de temps plus longue. Avec plus de temps, le moteur Machine Learning automatisé va essayer plus d’algorithmes et de paramètres.

* Ajouter des données. Parfois, la quantité de données n’est pas suffisante pour entraîner un modèle Machine Learning de haute qualité. 

* Équilibrer vos données. Pour les tâches de classification, vérifiez que le jeu d’entraînement est équilibré entre les différentes catégories. Par exemple, si vous avez quatre classes pour 100 exemples d’entraînement et que les deux premières classes (étiquette1 et étiquette2) sont utilisées pour 90 enregistrements, mais que les deux autres (étiquette3 et étiquette4) sont utilisées seulement sur les 10 enregistrements restants, l’absence de données équilibrées peut faire que votre modèle aura du mal à prédire correctement étiquette3 ou étiquette4.

## <a name="code"></a>Code

Après la phase d’évaluation, Model Builder génère un fichier de modèle et du code que vous pouvez utiliser pour ajouter le modèle à votre application. Les modèles ML.NET sont enregistrés sous la forme d’un fichier zip. Le code pour charger et utiliser votre modèle est ajouté en tant que nouveau projet dans votre solution. Model Builder ajoute également un exemple d’application console que vous pouvez exécuter pour voir votre modèle en action.

En outre, Model Builder produit le code qui a généré le modèle, ce qui vous permet de comprendre les étapes utilisées pour cette génération. Vous pouvez également utiliser le code de l’entraînement du modèle pour réentraîner votre modèle avec de nouvelles données.

## <a name="whats-next"></a>Étapes suivantes

Essayer [le scénario de prédiction des prix ou un autre scénario de régression](tutorials/predict-prices-with-model-builder.md)
