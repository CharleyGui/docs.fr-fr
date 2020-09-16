---
title: Réentraîner un modèle
description: Découvrez comment réentraîner un modèle dans ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 50f35e3511acc344339b1e150b47d7ce6de94254
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679558"
---
# <a name="re-train-a-model"></a>Réentraîner un modèle

Apprenez à réentraîner un modèle Machine Learning dans ML.NET.

Le monde et les données qui l’entourent changent à un rythme constant. Ainsi, les modèles doivent également subir des changements et des mises à jour. ML.NET fournit des fonctionnalités à l’aide desquelles vous pouvez réentraîner les modèles à partir de paramètres de modèle appris. Ainsi, en vous appuyant en permanence sur l’expérience acquise, vous n’avez pas besoin de repartir de zéro à chaque fois.

Les algorithmes suivants sont réentraînables dans ML.NET :

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Charger un modèle préentraîné

Tout d’abord, chargez le modèle préentraîné dans votre application. Pour en savoir plus sur le chargement des pipelines et des modèles d’apprentissage, consultez [enregistrer et charger un modèle formé](save-load-machine-learning-models-ml-net.md).

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

## <a name="extract-pre-trained-model-parameters"></a>Extraire les paramètres du modèle préentraîné

Une fois le modèle chargé, extrayez les paramètres du modèle appris en accédant à la [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase%601.Model%2A) propriété du modèle pré-formé. Le modèle pré-formé a été formé à l’aide du modèle de régression linéaire [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) qui crée une [`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) sortie [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) . Ces paramètres de modèle de régression linéaire contiennent le biais appris et les pondérations ou les coefficients du modèle. Ces valeurs sont utilisées comme point de départ pour le nouveau modèle réentraîné.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Réentraîner le modèle

Le processus de réentraînement d’un modèle ressemble beaucoup au processus d’entraînement d’un modèle. La seule différence est que la [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer%602.Fit%2A) méthode en plus des données prend également comme entrée les paramètres du modèle appris d’origine et les utilise comme point de départ dans le processus de nouvelle formation.

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

## <a name="compare-model-parameters"></a>Comparer les paramètres de modèle

Comment savoir si un réentraînement a eu lieu ? Une façon consisterait à déterminer si les paramètres du modèle réentraîné sont différents de ceux du modèle d’origine. L’exemple de code ci-dessous compare les pondérations du modèle d’origine à ceux du modèle réentraîné et les envoie à la console.

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

Le tableau ci-dessous montre à quoi peut ressembler la sortie.

|Original | Réentraîné | Différence |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
