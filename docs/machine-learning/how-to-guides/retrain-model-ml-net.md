---
title: Réentraîner un modèle
description: Découvrez comment réentraîner un modèle dans ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976963"
---
# <a name="re-train-a-model"></a><span data-ttu-id="2d4d9-103">Réentraîner un modèle</span><span class="sxs-lookup"><span data-stu-id="2d4d9-103">Re-train a model</span></span>

<span data-ttu-id="2d4d9-104">Apprenez à réentraîner un modèle Machine Learning dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="2d4d9-105">Le monde et les données qui l’entourent changent à un rythme constant.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="2d4d9-106">Ainsi, les modèles doivent également subir des changements et des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="2d4d9-107">ML.NET fournit des fonctionnalités à l’aide desquelles vous pouvez réentraîner les modèles à partir de paramètres de modèle appris. Ainsi, en vous appuyant en permanence sur l’expérience acquise, vous n’avez pas besoin de repartir de zéro à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="2d4d9-108">Les algorithmes suivants sont réentraînables dans ML.NET :</span><span class="sxs-lookup"><span data-stu-id="2d4d9-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="2d4d9-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="2d4d9-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="2d4d9-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="2d4d9-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="2d4d9-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="2d4d9-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="2d4d9-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="2d4d9-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="2d4d9-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="2d4d9-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="2d4d9-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="2d4d9-119">Charger un modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="2d4d9-119">Load pre-trained model</span></span>

<span data-ttu-id="2d4d9-120">Tout d’abord, chargez le modèle préentraîné dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="2d4d9-121">Pour en savoir plus sur le chargement des pipelines et des modèles d’apprentissage, consultez [enregistrer et charger un modèle formé](save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="2d4d9-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="2d4d9-122">Extraire les paramètres du modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="2d4d9-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="2d4d9-123">Une fois le modèle chargé, extrayez les paramètres de modèle appris en accédant à la propriété [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) du modèle préentraîné.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="2d4d9-124">Le modèle préentraîné a été entraîné à l’aide du modèle de régression linéaire [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) qui crée un [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) générant des [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="2d4d9-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="2d4d9-125">Ces paramètres de modèle de régression linéaire contiennent le biais appris et les pondérations ou les coefficients du modèle.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="2d4d9-126">Ces valeurs sont utilisées comme point de départ pour le nouveau modèle réentraîné.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="2d4d9-127">Réentraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="2d4d9-127">Re-train model</span></span>

<span data-ttu-id="2d4d9-128">Le processus de réentraînement d’un modèle ressemble beaucoup au processus d’entraînement d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="2d4d9-129">La seule différence est la suivante : la méthode [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*), en plus des données, prend en entrée les paramètres de modèle appris d’origine et les utilise comme point de départ dans le processus de réentraînement.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
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

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel =
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a><span data-ttu-id="2d4d9-130">Comparer les paramètres de modèle</span><span class="sxs-lookup"><span data-stu-id="2d4d9-130">Compare model parameters</span></span>

<span data-ttu-id="2d4d9-131">Comment savoir si un réentraînement a eu lieu ?</span><span class="sxs-lookup"><span data-stu-id="2d4d9-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="2d4d9-132">Une façon consisterait à déterminer si les paramètres du modèle réentraîné sont différents de ceux du modèle d’origine.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="2d4d9-133">L’exemple de code ci-dessous compare les pondérations du modèle d’origine à ceux du modèle réentraîné et les envoie à la console.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs =
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

<span data-ttu-id="2d4d9-134">Le tableau ci-dessous montre à quoi peut ressembler la sortie.</span><span class="sxs-lookup"><span data-stu-id="2d4d9-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="2d4d9-135">D'origine</span><span class="sxs-lookup"><span data-stu-id="2d4d9-135">Original</span></span> | <span data-ttu-id="2d4d9-136">Réentraîné</span><span class="sxs-lookup"><span data-stu-id="2d4d9-136">Retrained</span></span> | <span data-ttu-id="2d4d9-137">Différence</span><span class="sxs-lookup"><span data-stu-id="2d4d9-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="2d4d9-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="2d4d9-138">33039.86</span></span> | <span data-ttu-id="2d4d9-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="2d4d9-139">56293.76</span></span> | <span data-ttu-id="2d4d9-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="2d4d9-140">-23253.9</span></span> |
| <span data-ttu-id="2d4d9-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="2d4d9-141">29099.14</span></span> | <span data-ttu-id="2d4d9-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="2d4d9-142">49586.03</span></span> | <span data-ttu-id="2d4d9-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="2d4d9-143">-20486.89</span></span> |
| <span data-ttu-id="2d4d9-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="2d4d9-144">28938.38</span></span> | <span data-ttu-id="2d4d9-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="2d4d9-145">48609.23</span></span> | <span data-ttu-id="2d4d9-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="2d4d9-146">-19670.85</span></span> |
| <span data-ttu-id="2d4d9-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="2d4d9-147">30484.02</span></span> | <span data-ttu-id="2d4d9-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="2d4d9-148">53745.43</span></span> | <span data-ttu-id="2d4d9-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="2d4d9-149">-23261.41</span></span> |
