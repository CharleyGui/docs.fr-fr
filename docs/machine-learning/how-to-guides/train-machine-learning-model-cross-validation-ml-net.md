---
title: Entraîner un modèle Machine Learning avec la validation croisée
description: Découvrez comment utiliser la validation croisée pour générer des modèles Machine Learning plus robustes dans ML.NET. La validation croisée est une technique d’entraînement et d’évaluation de modèle qui fractionne les données en plusieurs partitions sur lesquelles elle entraîne plusieurs algorithmes.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: c68c2b61054f59f03b4743ec30a694e94086ebab
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397656"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Entraîner un modèle Machine Learning avec la validation croisée

Découvrez comment utiliser la validation croisée pour entraîner des modèles Machine Learning plus robustes dans ML.NET. 

La validation croisée est une technique d’entraînement et d’évaluation de modèle qui fractionne les données en plusieurs partitions sur lesquelles elle entraîne plusieurs algorithmes. Cette technique améliore la robustesse du modèle en réservant des données à partir du processus d’entraînement. Outre améliorer les performances sur les observations invisibles, dans les environnements limités en données, cette technique peut être un outil efficace pour entraîner des modèles avec un jeu de données plus petit.

## <a name="the-data-and-data-model"></a>Données et modèle de données

Soient les données d’un fichier présentant la mise en forme suivante :

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Les données peuvent être modélisées par une classe telle que `HousingData` :

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

Chargez les données dans un [`IDataView`](xref:Microsoft.ML.IDataView).

## <a name="prepare-the-data"></a>Préparer les données

Prétraitez les données avant de les utiliser pour générer le modèle Machine Learning. Dans cet échantillon, les colonnes `Size` et `HistoricalPrices` sont combinées en un vecteur de caractéristiques unique, qui est généré dans une colonne nommée `Features` à l’aide de la méthode [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*). En plus d’obtenir les données dans le format attendu par les algorithmes ML.NET, la concaténation des colonnes optimise les opérations suivantes dans le pipeline en appliquant l’opération une fois pour la colonne concaténée au lieu de le faire pour chacune des colonnes. 

Une fois les colonnes combinées en un vecteur unique, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) est appliqué à la colonne `Features` pour obtenir `Size` et `HistoricalPrices` dans la même plage comprise entre 0 et 1. 

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator = 
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a>Entraîner le modèle avec la validation croisée

Une fois les données prétraitées, vous pouvez entraîner le modèle. Tout d’abord, sélectionnez l’algorithme qui convient le mieux pour la tâche de machine learning à effectuer. La valeur prédite étant une valeur numériquement continue, la tâche est la régression. Un des algorithmes de régression implémentés par ML.NET est l’algorithme [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer). Pour entraîner le modèle avec la validation croisée, utilisez la méthode [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*). 

> [!NOTE]
> Bien que cet échantillon utilise un modèle de régression linéaire, CrossValidate s’applique à toutes les autres tâches de machine learning dans ML.NET, à l’exception de la détection d’anomalie.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) effectue les opérations suivantes :

1. Elle partitionne les données en un nombre de partitions égal à la valeur spécifiée dans le paramètre `numberOfFolds`. Le résultat de chaque partition est un objet [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).
1. Un modèle est entraîné sur chacune des partitions à l’aide de l’estimateur d’algorithme de machine learning spécifié sur le jeu de données d’entraînement.
1. Les performances de chaque modèle sont évaluées à l’aide de la méthode [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) sur le jeu de données de test. 
1. Pour chacun des modèles, le modèle ainsi que ses métriques sont retournés.

Le résultat stocké dans `cvResults` est une collection d’objets [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601). Cet objet inclut le modèle entraîné ainsi que les métriques, qui sont respectivement accessibles à partir des propriétés [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) et [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics). Dans cet échantillon, la propriété `Model` est de type [`ITransformer`](xref:Microsoft.ML.ITransformer), tandis que la propriété `Metrics` est de type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="evaluate-the-model"></a>Évaluer le modèle

Les métriques des différents modèles entraînés sont accessibles via la propriété `Metrics` de l’objet [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) concerné. En l’occurrence, la [métrique du coefficient de détermination](https://en.wikipedia.org/wiki/Coefficient_of_determination) est accessible et stockée dans la variable `rSquared`. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Si vous inspectez le contenu de la variable `rSquared`, la sortie doit comporter cinq valeurs comprises entre 0 et 1, où plus une valeur est proche de 1, meilleure est la qualité. À l’aide de métriques telles que le coefficient de détermination, sélectionnez les modèles du plus au moins performant. Ensuite, sélectionnez le meilleur modèle avec lequel faire des prédictions ou effectuer des opérations supplémentaires.

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
