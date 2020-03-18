---
title: Effectuer des prédictions avec un modèle entraîné
description: Apprenez à effectuer des prédictions à l’aide d’un modèle entraîné
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977046"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="d1e79-103">Effectuer des prédictions avec un modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="d1e79-103">Make predictions with a trained model</span></span>

<span data-ttu-id="d1e79-104">Découvrez comment utiliser un modèle entraîné pour effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="d1e79-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="d1e79-105">Créer des modèles de données</span><span class="sxs-lookup"><span data-stu-id="d1e79-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="d1e79-106">Données d’entrée</span><span class="sxs-lookup"><span data-stu-id="d1e79-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="d1e79-107">Données de sortie</span><span class="sxs-lookup"><span data-stu-id="d1e79-107">Output data</span></span>

<span data-ttu-id="d1e79-108">Comme les noms de colonne d’entrée `Features` et `Label`, ML.NET a des noms par défaut pour les colonnes de valeur prédite produites par un modèle.</span><span class="sxs-lookup"><span data-stu-id="d1e79-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="d1e79-109">Selon la tâche, le nom peut différer.</span><span class="sxs-lookup"><span data-stu-id="d1e79-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="d1e79-110">Parce que l’algorithme utilisé dans cet échantillon est un algorithme de `Score` régression linéaire, le nom par défaut de la colonne de sortie est qui est défini par l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) sur la `PredictedPrice` propriété.</span><span class="sxs-lookup"><span data-stu-id="d1e79-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="d1e79-111">Configurer un pipeline de prédiction</span><span class="sxs-lookup"><span data-stu-id="d1e79-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="d1e79-112">Que vous effectuiez une prédiction unique ou par lot, vous devez charger le pipeline de prédiction dans l’application.</span><span class="sxs-lookup"><span data-stu-id="d1e79-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="d1e79-113">Ce pipeline contient les transformations de prétraitement de données ainsi que le modèle entraîné.</span><span class="sxs-lookup"><span data-stu-id="d1e79-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="d1e79-114">L’extrait de code ci-dessous charge le pipeline de prédiction à partir d’un fichier nommé `model.zip`.</span><span class="sxs-lookup"><span data-stu-id="d1e79-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="d1e79-115">Prédiction unique</span><span class="sxs-lookup"><span data-stu-id="d1e79-115">Single prediction</span></span>

<span data-ttu-id="d1e79-116">Pour faire une seule [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) prédiction, créez un pipeline de prédiction chargé.</span><span class="sxs-lookup"><span data-stu-id="d1e79-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="d1e79-117">Ensuite, utilisez [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) la méthode et passez dans vos données d’entrée comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="d1e79-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="d1e79-118">Notez que [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) l’utilisation de la [`IDataView`](xref:Microsoft.ML.IDataView)méthode ne nécessite pas l’entrée d’être un ).</span><span class="sxs-lookup"><span data-stu-id="d1e79-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="d1e79-119">En effet, elle internalise facilement la manipulation du type de données d’entrée afin que vous puissiez passer un objet du type de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d1e79-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="d1e79-120">De plus, `CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.</span><span class="sxs-lookup"><span data-stu-id="d1e79-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="d1e79-121">Si vous accédez à la propriété `Score` de l’objet `prediction`, vous devez obtenir une valeur similaire à `150079`.</span><span class="sxs-lookup"><span data-stu-id="d1e79-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="d1e79-122">Prévisions multiples</span><span class="sxs-lookup"><span data-stu-id="d1e79-122">Multiple predictions</span></span>

<span data-ttu-id="d1e79-123">Compte tenu des données suivantes, chargez-les en [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="d1e79-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d1e79-124">Dans ce cas, le [`IDataView`](xref:Microsoft.ML.IDataView) `inputData`nom de l’est .</span><span class="sxs-lookup"><span data-stu-id="d1e79-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="d1e79-125">`CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.</span><span class="sxs-lookup"><span data-stu-id="d1e79-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
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

<span data-ttu-id="d1e79-126">Ensuite, utilisez [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) la méthode pour appliquer les transformations de données et générer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="d1e79-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="d1e79-127">Inspectez les valeurs [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) prévues en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="d1e79-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="d1e79-128">Les valeurs prédites dans la colonne des scores doivent se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="d1e79-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="d1e79-129">Observation</span><span class="sxs-lookup"><span data-stu-id="d1e79-129">Observation</span></span> | <span data-ttu-id="d1e79-130">Prédiction</span><span class="sxs-lookup"><span data-stu-id="d1e79-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="d1e79-131">1</span><span class="sxs-lookup"><span data-stu-id="d1e79-131">1</span></span> | <span data-ttu-id="d1e79-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="d1e79-132">144638.2</span></span> |
| <span data-ttu-id="d1e79-133">2</span><span class="sxs-lookup"><span data-stu-id="d1e79-133">2</span></span> | <span data-ttu-id="d1e79-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="d1e79-134">150079.4</span></span> |
| <span data-ttu-id="d1e79-135">3</span><span class="sxs-lookup"><span data-stu-id="d1e79-135">3</span></span> | <span data-ttu-id="d1e79-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="d1e79-136">107789.8</span></span> |
