---
title: Entraîner et évaluer un modèle
description: Découvrez comment générer des modèles Machine Learning, collecter des mesures et mesurer les performances avec ML.NET. Un modèle Machine Learning identifie les modèles au sein des données d’apprentissage pour élaborer des prédictions à l’aide de nouvelles données.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523856"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="b519d-104">Entraîner et évaluer un modèle</span><span class="sxs-lookup"><span data-stu-id="b519d-104">Train and evaluate a model</span></span>

<span data-ttu-id="b519d-105">Découvrez comment générer des modèles Machine Learning, collecter des mesures et mesurer les performances avec ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b519d-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="b519d-106">Bien que cet exemple entraîne un modèle de régression, les concepts s’appliquent à la majorité des autres algorithmes.</span><span class="sxs-lookup"><span data-stu-id="b519d-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="b519d-107">Fractionner les données à des fins d’entraînement et de test</span><span class="sxs-lookup"><span data-stu-id="b519d-107">Split data for training and testing</span></span>

<span data-ttu-id="b519d-108">L’objectif d’un modèle Machine Learning consiste à identifier des modèles au sein de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="b519d-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="b519d-109">Ces modèles sont utilisés pour effectuer des prédictions à l’aide de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="b519d-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="b519d-110">Les données peuvent être modélisées par une classe comme `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="b519d-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="b519d-111">Compte tenu des données suivantes [`IDataView`](xref:Microsoft.ML.IDataView)qui sont chargées dans un .</span><span class="sxs-lookup"><span data-stu-id="b519d-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="b519d-112">Utilisez [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) la méthode pour diviser les données en ensembles de train et d’essai.</span><span class="sxs-lookup"><span data-stu-id="b519d-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the data into train and test sets.</span></span> <span data-ttu-id="b519d-113">Le résultat sera [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) un objet [`IDataView`](xref:Microsoft.ML.IDataView) qui contient deux membres, l’un pour l’ensemble de train et l’autre pour l’ensemble d’essai.</span><span class="sxs-lookup"><span data-stu-id="b519d-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="b519d-114">Le pourcentage de fractionnement des données est déterminé par le paramètre `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="b519d-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="b519d-115">L’extrait de code ci-dessous réserve 20 % des données d’origine pour le jeu de test.</span><span class="sxs-lookup"><span data-stu-id="b519d-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="b519d-116">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="b519d-116">Prepare the data</span></span>

<span data-ttu-id="b519d-117">Les données doivent être prétraitées avant l’entraînement d’un modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="b519d-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="b519d-118">Vous trouverez plus d’informations sur la préparation des données dans l’[article sur les procédures de préparation des données](prepare-data-ml-net.md) ainsi qu’à la [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="b519d-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="b519d-119">Les algorithmes ML.NET ont des contraintes sur les types de colonnes d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b519d-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="b519d-120">En outre, les valeurs par défaut sont utilisées pour les noms de colonne d’entrée et de sortie quand aucune valeur n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b519d-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="b519d-121">Utilisation de types de colonnes attendus</span><span class="sxs-lookup"><span data-stu-id="b519d-121">Working with expected column types</span></span>

<span data-ttu-id="b519d-122">Les algorithmes de machine learning dans ML.NET attendent un vecteur à virgule flottante de taille connue en tant qu’entrée.</span><span class="sxs-lookup"><span data-stu-id="b519d-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="b519d-123">Appliquez [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) l’attribut à votre modèle de données lorsque toutes les données sont déjà en format numérique et sont destinées à être traitées ensemble (c.-à-pixels d’image).</span><span class="sxs-lookup"><span data-stu-id="b519d-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="b519d-124">Si les données ne sont pas toutes numériques et que vous souhaitez [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) appliquer différentes transformations de données sur chacune des colonnes individuellement, utilisez la méthode après que toutes les colonnes ont été traitées pour combiner toutes les colonnes individuelles en un vecteur de fonctionnalité unique qui est la sortie à une nouvelle colonne.</span><span class="sxs-lookup"><span data-stu-id="b519d-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="b519d-125">L’extrait de code suivant combine les colonnes `Size` et `HistoricalPrices` en un vecteur de caractéristiques unique qui est généré dans une nouvelle colonne appelée `Features`.</span><span class="sxs-lookup"><span data-stu-id="b519d-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="b519d-126">Parce qu’il ya une [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) différence dans `Features` les échelles, est appliqué à la colonne pour normaliser les données.</span><span class="sxs-lookup"><span data-stu-id="b519d-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="b519d-127">Utilisation de noms de colonne par défaut</span><span class="sxs-lookup"><span data-stu-id="b519d-127">Working with default column names</span></span>

<span data-ttu-id="b519d-128">Les algorithmes ML.NET utilisent des noms de colonne par défaut quand aucun n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="b519d-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="b519d-129">Tous les entraîneurs ont un paramètre appelé `featureColumnName` pour les entrées de l’algorithme et, le cas échéant, ils ont également un paramètre pour la valeur attendue appelé `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="b519d-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="b519d-130">Par défaut, ces valeurs sont `Features` et `Label` respectivement.</span><span class="sxs-lookup"><span data-stu-id="b519d-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="b519d-131">En utilisant [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) la méthode pendant le pré-traitement pour créer une nouvelle colonne appelée `Features`, il n’est pas nécessaire de `IDataView`spécifier le nom de la colonne de fonctionnalité dans les paramètres de l’algorithme car il existe déjà dans le pré-traité .</span><span class="sxs-lookup"><span data-stu-id="b519d-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="b519d-132">La colonne `CurrentPrice`d’étiquette [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) est, mais puisque l’attribut est utilisé `CurrentPrice` dans `Label` le modèle de données, `labelColumnName` ML.NET renomme la colonne à laquelle supprime la nécessité de fournir le paramètre à l’estimateur de l’algorithme d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="b519d-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="b519d-133">Si vous ne souhaitez pas utiliser les noms de colonne par défaut, passez les noms des colonnes des caractéristiques et des étiquettes en tant que paramètres lors de la définition de l’estimateur de l’algorithme de machine learning, comme illustré dans l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="b519d-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a><span data-ttu-id="b519d-134">Mise en cache de données</span><span class="sxs-lookup"><span data-stu-id="b519d-134">Caching data</span></span>

<span data-ttu-id="b519d-135">Par défaut, lorsque les données sont traitées, elles sont chargées ou diffusées paresseusement, ce qui signifie que les formateurs peuvent charger les données à partir du disque et l’itérer plusieurs fois pendant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="b519d-135">By default, when data is processed, it is lazily loaded or streamed which means that trainers may load the data from disk and iterate over it multiple times during training.</span></span> <span data-ttu-id="b519d-136">Par conséquent, la mise en cache est recommandée pour les ensembles de données qui s’intègrent dans la mémoire afin de réduire le nombre de fois que les données sont chargées à partir du disque.</span><span class="sxs-lookup"><span data-stu-id="b519d-136">Therefore, caching is recommended for datasets that fit into memory to reduce the number of times data is loaded from disk.</span></span> <span data-ttu-id="b519d-137">La mise en cache [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) se [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)fait dans le cadre d’une utilisation .</span><span class="sxs-lookup"><span data-stu-id="b519d-137">Caching is done as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) by using [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A).</span></span>

<span data-ttu-id="b519d-138">Il est recommandé [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) d’utiliser avant tout formateur dans le pipeline.</span><span class="sxs-lookup"><span data-stu-id="b519d-138">It's recommended to use [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before any trainers in the pipeline.</span></span>

<span data-ttu-id="b519d-139">En utilisant [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)ce [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) qui [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) suit, ajoutant avant que le formateur cache les résultats des estimateurs précédents pour une utilisation ultérieure par le formateur.</span><span class="sxs-lookup"><span data-stu-id="b519d-139">Using the following [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601), adding [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) trainer caches the results of the previous estimators for later use by the trainer.</span></span>

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="b519d-140">Entraîner le modèle Machine Learning</span><span class="sxs-lookup"><span data-stu-id="b519d-140">Train the machine learning model</span></span>

<span data-ttu-id="b519d-141">Une fois que les données [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) sont prétrass transformées, utilisez la méthode pour former le modèle d’apprentissage automatique avec l’algorithme [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) de régression.</span><span class="sxs-lookup"><span data-stu-id="b519d-141">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="b519d-142">Extraire les paramètres de modèle</span><span class="sxs-lookup"><span data-stu-id="b519d-142">Extract model parameters</span></span>

<span data-ttu-id="b519d-143">Une fois que le modèle [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) a été formé, extraire les savants pour l’inspection ou le recyclage.</span><span class="sxs-lookup"><span data-stu-id="b519d-143">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or retraining.</span></span> <span data-ttu-id="b519d-144">Les [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) fournir le biais et les coefficients appris ou les poids du modèle formé.</span><span class="sxs-lookup"><span data-stu-id="b519d-144">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="b519d-145">D’autres modèles ont des paramètres qui sont spécifiques de leurs tâches.</span><span class="sxs-lookup"><span data-stu-id="b519d-145">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="b519d-146">Par exemple, l’[algorithme k-moyennes](xref:Microsoft.ML.Trainers.KMeansTrainer) place les données dans un cluster basé sur des centroïdes et [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contient une propriété qui stocke ces centroïdes appris.</span><span class="sxs-lookup"><span data-stu-id="b519d-146">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="b519d-147">Pour en savoir plus, visitez la `ModelParameters` [ `Microsoft.ML.Trainers` documentation API](xref:Microsoft.ML.Trainers) et recherchez des cours qui contiennent en leur nom.</span><span class="sxs-lookup"><span data-stu-id="b519d-147">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="b519d-148">Évaluer la qualité du modèle</span><span class="sxs-lookup"><span data-stu-id="b519d-148">Evaluate model quality</span></span>

<span data-ttu-id="b519d-149">Pour choisir plus facilement le modèle le plus performant, il est essentiel d’évaluer ses performances sur des données de test.</span><span class="sxs-lookup"><span data-stu-id="b519d-149">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="b519d-150">Utilisez [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) la méthode, pour mesurer diverses mesures pour le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="b519d-150">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="b519d-151">La méthode `Evaluate` produit différentes métriques en fonction de la tâche de machine learning qui a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="b519d-151">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="b519d-152">Pour plus de détails, visitez la `Metrics` [ `Microsoft.ML.Data` documentation API](xref:Microsoft.ML.Data) et recherchez les cours qui contiennent en leur nom.</span><span class="sxs-lookup"><span data-stu-id="b519d-152">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

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

<span data-ttu-id="b519d-153">Dans l’exemple de code précédent :</span><span class="sxs-lookup"><span data-stu-id="b519d-153">In the previous code sample:</span></span>

1. <span data-ttu-id="b519d-154">Le jeu de données de test est prétraité à l’aide de transformations de préparation de données préalablement définies.</span><span class="sxs-lookup"><span data-stu-id="b519d-154">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="b519d-155">Le modèle Machine Learning entraîné est utilisé pour effectuer des prédictions sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="b519d-155">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="b519d-156">Dans la méthode `Evaluate`, les valeurs de la colonne `CurrentPrice` du jeu de données de test sont comparées à la colonne `Score` des prédictions qui viennent d’être générées pour calculer les métriques du modèle de régression, dont l’une, le coefficient de détermination, est stockée dans la variable `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="b519d-156">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="b519d-157">Dans ce petit exemple, le coefficient de détermination est un nombre qui n’appartient pas à la plage 0-1 en raison de la taille limitée des données.</span><span class="sxs-lookup"><span data-stu-id="b519d-157">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="b519d-158">Dans un scénario réel, vous devez vous attendre à une valeur comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="b519d-158">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
