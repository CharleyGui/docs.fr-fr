---
title: Entraîner et évaluer un modèle
description: Découvrez comment générer des modèles Machine Learning, collecter des mesures et mesurer les performances avec ML.NET. Un modèle Machine Learning identifie les modèles au sein des données d’apprentissage pour élaborer des prédictions à l’aide de nouvelles données.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976758"
---
# <a name="train-and-evaluate-a-model"></a>Entraîner et évaluer un modèle

Découvrez comment générer des modèles Machine Learning, collecter des mesures et mesurer les performances avec ML.NET. Bien que cet exemple entraîne un modèle de régression, les concepts s’appliquent à la majorité des autres algorithmes.

## <a name="split-data-for-training-and-testing"></a>Fractionner les données à des fins d’entraînement et de test

L’objectif d’un modèle Machine Learning consiste à identifier des modèles au sein de données d’entraînement. Ces modèles sont utilisés pour effectuer des prédictions à l’aide de nouvelles données.

Les données peuvent être modélisées par une classe comme `HousingData`.

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

Prenons un exemple avec les données suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

Utilisez la méthode [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) pour fractionner les données en jeux d’entraînement et de test. Le résultat est un objet [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) qui contient deux membres [`IDataView`](xref:Microsoft.ML.IDataView) : un pour le jeu d’entraînement, l’autre pour le jeu de test. Le pourcentage de fractionnement des données est déterminé par le paramètre `testFraction`. L’extrait de code ci-dessous réserve 20 % des données d’origine pour le jeu de test.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Préparer les données

Les données doivent être prétraitées avant l’entraînement d’un modèle Machine Learning. Vous trouverez plus d’informations sur la préparation des données dans l’[article sur les procédures de préparation des données](prepare-data-ml-net.md) ainsi qu’à la [`transforms page`](../resources/transforms.md).

Les algorithmes ML.NET ont des contraintes sur les types de colonnes d’entrée. En outre, les valeurs par défaut sont utilisées pour les noms de colonne d’entrée et de sortie quand aucune valeur n’est spécifiée.

### <a name="working-with-expected-column-types"></a>Utilisation de types de colonnes attendus

Les algorithmes de machine learning dans ML.NET attendent un vecteur à virgule flottante de taille connue en tant qu’entrée. Appliquez l’attribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) à votre modèle de données quand toutes les données sont déjà au format numérique et sont destinées à être traitées ensemble (par exemple, les pixels d’une image).

Si les données ne sont pas toutes numériques et que vous souhaitez appliquer différentes transformations de données sur chacune des colonnes individuellement, utilisez la méthode [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) une fois que toutes les colonnes ont été traitées pour combiner toutes les colonnes individuelles en un vecteur de caractéristiques unique qui est généré dans une nouvelle colonne.

L’extrait de code suivant combine les colonnes `Size` et `HistoricalPrices` en un vecteur de caractéristiques unique qui est généré dans une nouvelle colonne appelée `Features`. Les échelles étant différentes, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) est appliqué à la colonne `Features` pour normaliser les données.

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a>Utilisation de noms de colonne par défaut

Les algorithmes ML.NET utilisent des noms de colonne par défaut quand aucun n’est spécifié. Tous les entraîneurs ont un paramètre appelé `featureColumnName` pour les entrées de l’algorithme et, le cas échéant, ils ont également un paramètre pour la valeur attendue appelé `labelColumnName`. Par défaut, ces valeurs sont `Features` et `Label` respectivement.

La méthode [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) ayant été utilisée pendant le prétraitement pour créer une colonne appelée `Features`, il est inutile de spécifier le nom de la colonne des caractéristiques dans les paramètres de l’algorithme dans la mesure où il existe déjà dans le `IDataView` prétraité. La colonne des étiquettes est `CurrentPrice`, mais comme l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) est utilisé dans le modèle de données, ML.NET renomme la colonne `CurrentPrice` en `Label` ; ainsi, il n’est pas nécessaire de fournir le paramètre `labelColumnName` à l’estimateur de l’algorithme de machine learning.

Si vous ne souhaitez pas utiliser les noms de colonne par défaut, passez les noms des colonnes des caractéristiques et des étiquettes en tant que paramètres lors de la définition de l’estimateur de l’algorithme de machine learning, comme illustré dans l’extrait de code suivant :

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Entraîner le modèle Machine Learning

Une fois les données prétraitées, utilisez la méthode [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) pour entraîner le modèle Machine Learning avec l’algorithme de régression [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Extraire les paramètres de modèle

Une fois le modèle entraîné, extrayez les [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) appris à des fins d’inspection ou de réentraînement. Les [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) fournissent les coefficients de biais et appris ou les pondérations du modèle entraîné.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> D’autres modèles ont des paramètres qui sont spécifiques de leurs tâches. Par exemple, l’[algorithme k-moyennes](xref:Microsoft.ML.Trainers.KMeansTrainer) place les données dans un cluster basé sur des centroïdes et [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contient une propriété qui stocke ces centroïdes appris. Pour en savoir plus, consultez la [documentation de l’API `Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) et recherchez les classes dont le nom contient `ModelParameters`.

## <a name="evaluate-model-quality"></a>Évaluer la qualité du modèle

Pour choisir plus facilement le modèle le plus performant, il est essentiel d’évaluer ses performances sur des données de test. Utilisez la méthode [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) afin de mesurer diverses métriques pour le modèle entraîné.

> [!NOTE]
> La méthode `Evaluate` produit différentes métriques en fonction de la tâche de machine learning qui a été effectuée. Pour plus d’informations, consultez la [documentation de l’API `Microsoft.ML.Data`](xref:Microsoft.ML.Data) et recherchez les classes dont le nom contient `Metrics`.

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

Dans l’exemple de code précédent :

1. Le jeu de données de test est prétraité à l’aide de transformations de préparation de données préalablement définies.
2. Le modèle Machine Learning entraîné est utilisé pour effectuer des prédictions sur les données de test.
3. Dans la méthode `Evaluate`, les valeurs de la colonne `CurrentPrice` du jeu de données de test sont comparées à la colonne `Score` des prédictions qui viennent d’être générées pour calculer les métriques du modèle de régression, dont l’une, le coefficient de détermination, est stockée dans la variable `rSquared`.

> [!NOTE]
> Dans ce petit exemple, le coefficient de détermination est un nombre qui n’appartient pas à la plage 0-1 en raison de la taille limitée des données. Dans un scénario réel, vous devez vous attendre à une valeur comprise entre 0 et 1.
