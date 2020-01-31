---
title: Présentation de ML.NET et de son fonctionnement
description: ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion. Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application sans devoir être connecté à un réseau pour utiliser ML.NET. Cet article explique les principes de base du machine learning dans ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: bc157b22201c66bceecf78aaa36b9c653fe6a131
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794577"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a>Présentation de ML.NET et de son fonctionnement

ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion. Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application. Les applications machine learning utilisent des modèles dans les données pour faire des prédictions plutôt que de devoir être programmées explicitement.

Central vers ML.NET est un **modèle**machine learning. Le modèle spécifie les étapes nécessaires à la transformation des données d’entrée en prédiction. Avec ML.NET, vous pouvez effectuer l’apprentissage d’un modèle personnalisé en spécifiant un algorithme, ou vous pouvez importer des modèles TensorFlow et ONNX préformés.

Une fois que vous disposez d’un modèle, vous pouvez l’ajouter à votre application pour effectuer les prédictions.

ML.NET s’exécute sur Windows, Linux et macOS à l’aide de .NET Core ou de Windows à l’aide de .NET Framework. 64 bits est pris en charge sur toutes les plateformes. 32 bits est pris en charge sur Windows, à l’exception des fonctionnalités TensorFlow, LightGBM et ONNX.

Exemples du type de prédictions que vous pouvez effectuer avec ML.NET :

|||
|-|-|
|Classification/Catégorisation|Classer automatiquement les commentaires des clients dans les catégories Positif et Négatif|
|Régression/Prédire les valeurs continues|Prédire les prix des maisons en fonction de la superficie et de l’emplacement|
|Détection d’anomalie|Détecter les transactions bancaires frauduleuses |
|Recommandations|Suggérer d’autres produits aux acheteurs en ligne en fonction de leurs achats précédents|
|Séries chronologiques/données séquentielles|Prévoir les ventes météo/produit|
|Classification des images|Classer les pathologies dans des images médicales|

## <a name="hello-mlnet-world"></a>Hello ML.NET World

Le code dans l’extrait suivant illustre l’application ML.NET la plus simple. Cet exemple crée un modèle de régression linéaire pour prédire les prix de maisons à partir des données de superficie et des prix immobiliers. 

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;

    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }

        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }

        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();

            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));

            // 3. Train model
            var model = pipeline.Fit(trainingData);

            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    }
```

## <a name="code-workflow"></a>Workflow du code

Le diagramme suivant représente la structure du code de l’application ainsi que le processus itératif de développement du modèle :

- Collecter et charger des données d’entraînement dans un objet **IDataView**
- Spécifier un pipeline d’opérations pour extraire des caractéristiques et appliquer un algorithme de machine learning
- Entraîner un modèle en appelant **Fit()** sur le pipeline
- Évaluer le modèle et effectuer des itérations pour l’améliorer
- Enregistrer le modèle au format binaire pour l’utiliser dans une application
- Recharger le modèle dans un objet **ITransformer**
- Effectuer des prédictions en appelant **CreatePredictionEngine.Predict()**

![Workflow du développement d’application ML.NET, avec les composants pour la génération des données, le développement du pipeline, l’entraînement du modèle, l’évaluation du modèle et l’utilisation du modèle](./media/mldotnet-annotated-workflow.png)

Revoyons maintenant tous ces concepts un peu plus en détail.

## <a name="machine-learning-model"></a>Modèle Machine Learning

Un modèle ML.NET est un objet qui contient des transformations à effectuer sur vos données d’entrée pour produire la sortie prédite.

### <a name="basic"></a>Basic

Le modèle de base, le plus simple, est la régression linéaire à deux dimensions, où une quantité continue est proportionnelle à une autre, comme dans l’exemple des prix de maisons ci-dessus.

![Modèle de régression linéaire avec des paramètres de biais et de poids](./media/linear-regression-model.svg)

Le modèle est simple : $Price = b + Size * w$. Les paramètres $b$ et $w$ sont estimés en ajustant une ligne sur un ensemble de paires de valeurs (size, price). Les données utilisées pour rechercher les paramètres du modèle sont appelées **données d’entraînement**. Les entrées d’un modèle Machine Learning sont des **caractéristiques**. Dans cet exemple, $Size$ est la seule caractéristique. Les valeurs certifiées vraies utilisées pour entraîner un modèle Machine Learning sont appelées des **étiquettes**. Ici, les étiquettes sont les valeurs $Price$ contenues dans le jeu de données d’entraînement.

### <a name="more-complex"></a>Plus complexe

Un modèle plus complexe classe les transactions financières dans différentes catégories en fonction du texte de description de la transaction.

Chaque description de transaction est décomposée en un ensemble de caractéristiques, après suppression des mots et caractères redondants, et comptage des combinaisons de mots et caractères. L’ensemble des caractéristiques est ensuite utilisé pour entraîner un modèle linéaire basé sur l’ensemble des catégories trouvées dans les données d’entraînement. Plus une nouvelle description se rapproche d’une des descriptions figurant dans le jeu de données d’entraînement, plus elle a de chance d’être attribuée à la même catégorie.

![Modèle de classification de texte](./media/text-classification-model.svg)

Le modèle de prix des maisons et le modèle de classification de texte sont tous les deux des modèles de type **linéaire**. Selon la nature de vos données et le problème à résoudre, vous pouvez également utiliser des modèles d’**arbre de décision**, des modèles **additifs généralisés** et d’autres modèles. Pour plus d’informations sur les modèles, consultez [Tâches](./resources/tasks.md).

## <a name="data-preparation"></a>Préparation des données

Dans la plupart des cas, les données dont vous disposez ne peuvent pas être utilisées directement pour entraîner un modèle Machine Learning. Les données brutes doivent être préparées ou prétraitées avant de pouvoir être utilisées pour rechercher les paramètres de votre modèle. Par exemple, vous devrez peut-être convertir vos données de valeurs de chaîne en une représentation numérique, supprimer des informations redondantes dans vos données d’entrée, réduire ou développer les dimensions de vos données d’entrée, ou encore normaliser ou redimensionner vos données.

Les [tutoriels ML.NET](./tutorials/index.md) vous montrent différents pipelines de traitement des données (pour les données texte, d’image, numériques et de série chronologique) qui sont utilisés dans le cadre de tâches de machine learning spécifiques.

[La préparation de vos données](./how-to-guides/prepare-data-ml-net.md) vous montre comment appliquer la préparation des données plus généralement.

Vous trouverez toutes les [transformations disponibles](./resources/transforms.md) en annexe, dans la section des ressources.

## <a name="model-evaluation"></a>Évaluation du modèle

Une fois que vous avez entraîné votre modèle, comment savoir si ses prédictions futures seront correctes ? Avec ML.NET, vous pouvez évaluer votre modèle par rapport à de nouvelles données de test.

Chaque type de tâche de machine learning présente des métriques qui permettent d’évaluer l’exactitude et la précision du modèle par rapport au jeu de données de test.

Dans notre exemple de prix des maisons, nous avons utilisé la tâche de **régression**. Pour évaluer le modèle, ajoutez le code suivant à l’exemple de code initial.

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);

        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

Les métriques d’évaluation indiquent une erreur relativement faible, et une forte corrélation entre la sortie prédite et la sortie du test. C’était facile ! En réalité, vous aurez davantage de réglages à faire pour parvenir à des métriques de modèle satisfaisantes.

## <a name="mlnet-architecture"></a>Architecture de ML.NET

Dans cette section, nous allons examiner les modèles architecturaux de ML.NET. Si vous êtes un développeur .NET expérimenté, certains de ces modèles vous sont déjà familiers, et d’autres moins. Ne perdez pas le fil pendant ces explications !

Au démarrage de toute application ML.NET, il y a un objet <xref:Microsoft.ML.MLContext>. Cet objet singleton contient des **catalogues**. Un catalogue est une fabrique pour les composants de chargement et d’enregistrement des données, des transformations, des entraîneurs et de l’utilisation du modèle. Chaque objet catalogue a des méthodes permettant de créer les différents types de composants :

|||||
|-|-|-|-|
|Enregistrement et chargement des données||<xref:Microsoft.ML.DataOperationsCatalog>||
|Préparation des données||<xref:Microsoft.ML.TransformsCatalog>||
|Algorithmes d’entraînement|Classification binaire|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||Classification multiclasse|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||Détection d’anomalie|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||Clustering|<xref:Microsoft.ML.ClusteringCatalog>||
||Prévision|<xref:Microsoft.ML.ForecastingCatalog>||
||Classement|<xref:Microsoft.ML.RankingCatalog>||
||Régression|<xref:Microsoft.ML.RegressionCatalog>||
||Recommandation|<xref:Microsoft.ML.RecommendationCatalog>|Ajouter le package NuGet `Microsoft.ML.Recommender`|
||TimeSeries|<xref:Microsoft.ML.TimeSeriesCatalog>|Ajouter le package NuGet `Microsoft.ML.TimeSeries`|
|Utilisation du modèle ||<xref:Microsoft.ML.ModelOperationsCatalog>||

Vous pouvez accéder aux méthodes de création dans chacune des catégories ci-dessus. Dans Visual Studio, les catalogues s’affichent via IntelliSense.

   ![IntelliSense pour les entraîneurs de régression](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a>Créer le pipeline

Chaque catalogue contient un ensemble de méthodes d’extension. Examinons de quelle manière les méthodes d’extension sont utilisées pour créer un pipeline d’entraînement.

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

Dans l’extrait de code, `Concatenate` et `Sdca` sont deux méthodes figurant dans le catalogue. Chaque méthode crée un objet [IEstimator](xref:Microsoft.ML.IEstimator%601) qui est ajouté au pipeline.

À ce stade, les objets sont seulement créés. Ils ne sont pas exécutés.

### <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Une fois que les objets dans le pipeline ont été créés, les données peuvent être utilisées pour entraîner le modèle.

```csharp
    var model = pipeline.Fit(trainingData);
```

L’appel de `Fit()` déclenche l’utilisation des données d’entraînement d’entrée pour estimer les paramètres du modèle. C'est ce que l'on appelle l'apprentissage du modèle. Souvenez-vous, le modèle de régression linéaire vu plus haut avait deux paramètres de modèle : le **biais** et le **poids**. Après l’appel de `Fit()`, les valeurs des paramètres sont connues. La plupart des modèles ont beaucoup plus de paramètres que cela.

Vous pouvez en savoir plus sur l’apprentissage du modèle dans [la manière d’effectuer l’apprentissage de votre modèle](./how-to-guides/train-machine-learning-model-ml-net.md).

L’objet modèle obtenu implémente l’interface <xref:Microsoft.ML.ITransformer>. Autrement dit, le modèle transforme les données d’entrée en prédictions.

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a>Utiliser le modèle

Vous pouvez transformer les données d’entrée en prédictions soit en bloc, soit entrée par entrée. Dans l’exemple des prix de maisons, nous avons fait les deux : en bloc pour l’évaluation du modèle et entrée par entrée pour effectuer une nouvelle prédiction. Examinons le cas des prédictions uniques.

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

La méthode `CreatePredictionEngine()` a une classe d’entrée et une classe de sortie. Les noms de champs et/ou les attributs de code déterminent les noms des colonnes de données utilisées durant l’entraînement du modèle et la prédiction de données. Pour savoir [comment effectuer une prédiction unique](./how-to-guides/single-predict-model-ml-net.md), consultez la section des guides pratiques.

### <a name="data-models-and-schema"></a>Schéma et modèles de données

Les objets [DataView](xref:Microsoft.ML.IDataView) sont au cœur du pipeline de machine learning de ML.NET.

Chaque transformation dans le pipeline a deux schémas : un schéma d’entrée (noms de données, types et tailles que la transformation s’attend à voir dans son entrée) et un schéma de sortie (noms de données, types et tailles générés suite à l’exécution de la transformation). Le document suivant explique de façon détaillée l’[interface IDataView et son système de type](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).

Si le schéma de sortie d’une transformation dans le pipeline ne correspond pas au schéma d’entrée de la transformation suivante, ML.NET lève une exception.

Un objet vue de données contient des colonnes et des lignes. Chaque colonne a un nom, un type et une longueur. Par exemple, les colonnes d’entrée dans l’exemple de prix de la maison sont la **taille** et le **prix**. Ils sont tous deux de type et sont des quantités scalaires plutôt que des vecteurs.

   ![Exemple d’objet vue de données dans ML.NET avec les données de prédiction des prix de maisons](./media/ml-net-dataview.png)

Tous les algorithmes ML.NET recherchent une colonne d’entrée de type vecteur. Par défaut, cette colonne vecteur est appelée **Features** (Caractéristiques). C’est pourquoi nous avons concaténé la colonne **Size** dans une nouvelle colonne appelée **Features** dans notre exemple de prix de maisons.

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

Tous les algorithmes créent également des colonnes après avoir effectué une prédiction. Les noms fixes de ces nouvelles colonnes dépendent du type d’algorithme de machine learning. Pour la tâche de régression, l’une des nouvelles colonnes s’appelle **Score**. C’est pourquoi nous avons attribué ce nom à nos données de prix.

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

Pour plus d’informations sur les colonnes de sortie des différentes tâches de machine learning, consultez le guide [Tâches de machine learning](resources/tasks.md).

Gardez à l’esprit que les objets DataView sont évalués **tardivement**. Les objets vue de données sont uniquement chargés et traités pendant l’entraînement et l’évaluation du modèle, et durant la prédiction de données. Lors des phases d’écriture et de test de votre application ML.NET, vous pouvez utiliser le débogueur Visual Studio pour avoir un aperçu d’un objet vue de données en appelant la méthode [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*).

```csharp
    var debug = testPriceDataView.Preview();
```

Vous pouvez voir la variable `debug` dans le débogueur et examiner son contenu. N’utilisez pas la méthode Preview dans le code de production, car elle dégrade considérablement les performances.

### <a name="model-deployment"></a>Déploiement du modèle

Dans les applications réelles, votre code d’entraînement et d’évaluation du modèle sera séparé de votre code de prédiction. En fait, ces deux activités sont souvent effectuées par des équipes distinctes. L’équipe de développement du modèle peut enregistrer le modèle pour une utilisation dans l’application de prédiction.

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a>Étapes suivantes :

* Découvrez comment créer des applications à l’aide de différentes tâches de Machine Learning avec des jeux de données plus réalistes dans les [didacticiels](./tutorials/index.md).

* En savoir plus sur des rubriques spécifiques plus en détail dans les [guides de procédures](./how-to-guides/index.md).

* Si vous êtes super, vous pouvez vous plonger directement dans la [documentation de référence](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)sur les API.
