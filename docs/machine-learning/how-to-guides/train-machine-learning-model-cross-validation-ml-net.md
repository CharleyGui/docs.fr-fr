---
title: Entraîner et évaluer un modèle Machine Learning avec la validation croisée
description: Découvrez comment entraîner et évaluer un modèle Machine Learning avec la validation croisée
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: a15dfbfcd563cf9df9c25779a5854a9f556523d1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065562"
---
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="68709-103">Entraîner et évaluer un modèle Machine Learning avec la validation croisée</span><span class="sxs-lookup"><span data-stu-id="68709-103">Train and evaluate a machine learning model using cross validation</span></span>

<span data-ttu-id="68709-104">Découvrez comment utiliser la validation croisée pour générer des modèles Machine Learning plus robustes dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="68709-104">Learn how to use cross validation to build more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="68709-105">La validation croisée est une technique d’entraînement et d’évaluation de modèle qui fractionne les données en plusieurs partitions sur lesquelles elle entraîne plusieurs algorithmes.</span><span class="sxs-lookup"><span data-stu-id="68709-105">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="68709-106">Cette technique améliore la robustesse du modèle en réservant des données à partir du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="68709-106">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="68709-107">Outre améliorer les performances sur les observations invisibles, dans les environnements limités en données, cette technique peut être un outil efficace pour entraîner des modèles avec un jeu de données plus petit.</span><span class="sxs-lookup"><span data-stu-id="68709-107">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="68709-108">Données et modèle de données</span><span class="sxs-lookup"><span data-stu-id="68709-108">The data and data model</span></span>

<span data-ttu-id="68709-109">Soient les données d’un fichier présentant la mise en forme suivante :</span><span class="sxs-lookup"><span data-stu-id="68709-109">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="68709-110">Les données peuvent être modélisées par une classe telle que `HousingData` :</span><span class="sxs-lookup"><span data-stu-id="68709-110">The data can be modeled by a class like `HousingData`:</span></span>

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

<span data-ttu-id="68709-111">Chargez les données dans un [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="68709-111">Load the data in into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="68709-112">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="68709-112">Prepare the data</span></span>

<span data-ttu-id="68709-113">Prétraitez les données avant de les utiliser pour générer le modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="68709-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="68709-114">Dans cet échantillon, les colonnes `Size` et `HistoricalPrices` sont combinées en un vecteur de caractéristiques unique, qui est généré dans une colonne nommée `Features` à l’aide de la méthode [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*).</span><span class="sxs-lookup"><span data-stu-id="68709-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="68709-115">En plus d’obtenir les données dans le format attendu par les algorithmes ML.NET, la concaténation des colonnes optimise les opérations suivantes dans le pipeline en appliquant l’opération une fois pour la colonne concaténée au lieu de le faire pour chacune des colonnes.</span><span class="sxs-lookup"><span data-stu-id="68709-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="68709-116">Une fois les colonnes combinées en un vecteur unique, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) est appliqué à la colonne `Features` pour obtenir `Size` et `HistoricalPrices` dans la même plage comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="68709-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="68709-117">Entraîner le modèle avec la validation croisée</span><span class="sxs-lookup"><span data-stu-id="68709-117">Train model with cross validation</span></span>

<span data-ttu-id="68709-118">Une fois les données prétraitées, vous pouvez entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="68709-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="68709-119">Tout d’abord, sélectionnez l’algorithme qui convient le mieux pour la tâche de machine learning à effectuer.</span><span class="sxs-lookup"><span data-stu-id="68709-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="68709-120">La valeur prédite étant une valeur numériquement continue, la tâche est la régression.</span><span class="sxs-lookup"><span data-stu-id="68709-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="68709-121">Un des algorithmes de régression implémentés par ML.NET est l’algorithme [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer).</span><span class="sxs-lookup"><span data-stu-id="68709-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="68709-122">Pour entraîner le modèle avec la validation croisée, utilisez la méthode [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*).</span><span class="sxs-lookup"><span data-stu-id="68709-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="68709-123">Bien que cet échantillon utilise un modèle de régression linéaire, CrossValidate s’applique à toutes les autres tâches de machine learning dans ML.NET, à l’exception de la détection d’anomalie.</span><span class="sxs-lookup"><span data-stu-id="68709-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="68709-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="68709-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="68709-125">Elle partitionne les données en un nombre de partitions égal à la valeur spécifiée dans le paramètre `numberOfFolds`.</span><span class="sxs-lookup"><span data-stu-id="68709-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="68709-126">Le résultat de chaque partition est un objet [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).</span><span class="sxs-lookup"><span data-stu-id="68709-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="68709-127">Un modèle est entraîné sur chacune des partitions à l’aide de l’estimateur d’algorithme de machine learning spécifié sur le jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="68709-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="68709-128">Les performances de chaque modèle sont évaluées à l’aide de la méthode [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) sur le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="68709-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="68709-129">Pour chacun des modèles, le modèle ainsi que ses métriques sont retournés.</span><span class="sxs-lookup"><span data-stu-id="68709-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="68709-130">Le résultat stocké dans `cvResults` est une collection d’objets [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1).</span><span class="sxs-lookup"><span data-stu-id="68709-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1) objects.</span></span> <span data-ttu-id="68709-131">Cet objet inclut le modèle entraîné ainsi que les métriques, qui sont respectivement accessibles à partir des propriétés [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) et [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics).</span><span class="sxs-lookup"><span data-stu-id="68709-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics) properties respectively.</span></span> <span data-ttu-id="68709-132">Dans cet échantillon, la propriété `Model` est de type [`ITransformer`](xref:Microsoft.ML.ITransformer), tandis que la propriété `Metrics` est de type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="68709-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="extract-metrics"></a><span data-ttu-id="68709-133">Extraire les métriques</span><span class="sxs-lookup"><span data-stu-id="68709-133">Extract metrics</span></span>

<span data-ttu-id="68709-134">Les métriques des différents modèles entraînés sont accessibles via la propriété `Metrics` de l’objet [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) concerné.</span><span class="sxs-lookup"><span data-stu-id="68709-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="68709-135">En l’occurrence, la [métrique du coefficient de détermination](https://en.wikipedia.org/wiki/Coefficient_of_determination) est accessible et stockée dans la variable `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="68709-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="68709-136">Si vous inspectez le contenu de la variable `rSquared`, la sortie doit comporter cinq valeurs comprises entre 0 et 1, où plus une valeur est proche de 1, meilleure est la qualité.</span><span class="sxs-lookup"><span data-stu-id="68709-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span>

## <a name="select-the-best-performing-model"></a><span data-ttu-id="68709-137">Sélectionner le modèle le plus performant</span><span class="sxs-lookup"><span data-stu-id="68709-137">Select the best performing model</span></span>

<span data-ttu-id="68709-138">À l’aide de métriques telles que le coefficient de détermination, sélectionnez les modèles du plus au moins performant.</span><span class="sxs-lookup"><span data-stu-id="68709-138">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="68709-139">Ensuite, sélectionnez le meilleur modèle avec lequel faire des prédictions ou effectuer des opérations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="68709-139">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
