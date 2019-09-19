---
title: Effectuer des prédictions avec un modèle entraîné
description: Apprenez à effectuer des prédictions à l’aide d’un modèle entraîné
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33e0cb74342ca3e82ff5f108453d63e022d63d20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118010"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="44c10-103">Effectuer des prédictions avec un modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="44c10-103">Make predictions with a trained model</span></span>

<span data-ttu-id="44c10-104">Découvrez comment utiliser un modèle entraîné pour effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="44c10-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="44c10-105">Créer des modèles de données</span><span class="sxs-lookup"><span data-stu-id="44c10-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="44c10-106">Données d’entrée</span><span class="sxs-lookup"><span data-stu-id="44c10-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="44c10-107">Données de sortie</span><span class="sxs-lookup"><span data-stu-id="44c10-107">Output data</span></span>

<span data-ttu-id="44c10-108">Comme les noms de colonne d’entrée `Features` et `Label`, ML.NET a des noms par défaut pour les colonnes de valeur prédite produites par un modèle.</span><span class="sxs-lookup"><span data-stu-id="44c10-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="44c10-109">Selon la tâche, le nom peut différer.</span><span class="sxs-lookup"><span data-stu-id="44c10-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="44c10-110">L’algorithme utilisé dans cet exemple étant un algorithme de régression linéaire, le nom par défaut de la colonne de sortie est `Score`, défini par l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) sur la propriété `PredictedPrice`.</span><span class="sxs-lookup"><span data-stu-id="44c10-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="44c10-111">Configurer un pipeline de prédiction</span><span class="sxs-lookup"><span data-stu-id="44c10-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="44c10-112">Que vous effectuiez une prédiction unique ou par lot, vous devez charger le pipeline de prédiction dans l’application.</span><span class="sxs-lookup"><span data-stu-id="44c10-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="44c10-113">Ce pipeline contient les transformations de prétraitement de données ainsi que le modèle entraîné.</span><span class="sxs-lookup"><span data-stu-id="44c10-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="44c10-114">L’extrait de code ci-dessous charge le pipeline de prédiction à partir d’un fichier nommé `model.zip`.</span><span class="sxs-lookup"><span data-stu-id="44c10-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="44c10-115">Prédiction unique</span><span class="sxs-lookup"><span data-stu-id="44c10-115">Single prediction</span></span>

<span data-ttu-id="44c10-116">Pour effectuer une prédiction unique, créez un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) en utilisant le pipeline de prédiction chargé.</span><span class="sxs-lookup"><span data-stu-id="44c10-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="44c10-117">Ensuite, utilisez la méthode [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) pour transmettre vos données d’entrée en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="44c10-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="44c10-118">Notez que l’utilisation de la méthode [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) ne requiert pas que l’entrée soit un [`IDataView`](xref:Microsoft.ML.IDataView)).</span><span class="sxs-lookup"><span data-stu-id="44c10-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="44c10-119">En effet, elle internalise facilement la manipulation du type de données d’entrée afin que vous puissiez passer un objet du type de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="44c10-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="44c10-120">De plus, `CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.</span><span class="sxs-lookup"><span data-stu-id="44c10-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

<span data-ttu-id="44c10-121">Si vous accédez à la propriété `Score` de l’objet `prediction`, vous devez obtenir une valeur similaire à `150079`.</span><span class="sxs-lookup"><span data-stu-id="44c10-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="44c10-122">Prédictions multiples</span><span class="sxs-lookup"><span data-stu-id="44c10-122">Multiple predictions</span></span>

<span data-ttu-id="44c10-123">Soient les données suivantes. Chargez-les dans un [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="44c10-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="44c10-124">Dans ce cas, le nom de notre [`IDataView`](xref:Microsoft.ML.IDataView) est `inputData`.</span><span class="sxs-lookup"><span data-stu-id="44c10-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="44c10-125">`CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.</span><span class="sxs-lookup"><span data-stu-id="44c10-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

<span data-ttu-id="44c10-126">Ensuite, utilisez la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pour appliquer les transformations de données et générer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="44c10-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="44c10-127">Inspectez les valeurs prédites à l’aide de la méthode [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*).</span><span class="sxs-lookup"><span data-stu-id="44c10-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="44c10-128">Les valeurs prédites dans la colonne des scores doivent se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="44c10-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="44c10-129">Observation</span><span class="sxs-lookup"><span data-stu-id="44c10-129">Observation</span></span> | <span data-ttu-id="44c10-130">Prédiction</span><span class="sxs-lookup"><span data-stu-id="44c10-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="44c10-131">1</span><span class="sxs-lookup"><span data-stu-id="44c10-131">1</span></span> | <span data-ttu-id="44c10-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="44c10-132">144638.2</span></span> |
| <span data-ttu-id="44c10-133">2</span><span class="sxs-lookup"><span data-stu-id="44c10-133">2</span></span> | <span data-ttu-id="44c10-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="44c10-134">150079.4</span></span> |
| <span data-ttu-id="44c10-135">3</span><span class="sxs-lookup"><span data-stu-id="44c10-135">3</span></span> | <span data-ttu-id="44c10-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="44c10-136">107789.8</span></span> |
