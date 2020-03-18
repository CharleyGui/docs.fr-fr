---
title: Enregistrer et charger des modèles entraînés
description: Découvrez comment enregistrer et charger des modèles entraînés
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977006"
---
# <a name="save-and-load-trained-models"></a>Enregistrer et charger des modèles entraînés

Découvrez comment enregistrer et charger des modèles entraînés dans votre application.

Durant le processus de création de modèle, un modèle se trouve dans la mémoire et est accessible tout au long du cycle de vie de l’application. Toutefois, dès la fin de l’exécution de l’application, le modèle n’est plus accessible s’il n’est pas enregistré localement ou à distance. En général, les modèles sont utilisés après l’entraînement dans d’autres applications à des fins d’inférence ou de réentraînement. C’est pourquoi il est important de stocker le modèle. Enregistrez et chargez les modèles à l’aide de la procédure décrite dans les sections suivantes de ce document quand vous utilisez des pipelines de préparation des données et d’entraînement de modèle semblables à celui détaillé ci-après. Bien que cet exemple utilise un modèle de régression linéaire, le même processus s’applique aux autres algorithmes ML.NET.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
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
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

Étant donné que la plupart des modèles et des pipelines de préparation des données héritent du même ensemble de classes, les signatures des méthodes d’enregistrement et de chargement pour ces composants sont les mêmes. Selon votre cas d’utilisation, vous pouvez combiner le [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) pipeline et le [`ITransformer`](xref:Microsoft.ML.ITransformer) modèle de préparation [`ITransformer`](xref:Microsoft.ML.ITransformer) de données en un seul qui produirait un seul ou les séparer, créant ainsi une séparation pour chacun.

## <a name="save-a-model-locally"></a>Enregistrer un modèle localement

Quand vous enregistrez un modèle, vous avez besoin de deux choses :

1. Le [`ITransformer`](xref:Microsoft.ML.ITransformer) modèle.
2. [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) L’entrée [`ITransformer`](xref:Microsoft.ML.ITransformer)attendue de l’on s’y attend.

Après la formation du [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modèle, utilisez la méthode `model.zip` pour `DataViewSchema` enregistrer le modèle formé à un fichier appelé en utilisant les données d’entrée.

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Charger un modèle stocké localement

Les modèles stockés localement peuvent être utilisés dans d’autres processus ou applications comme `ASP.NET Core` et `Serverless Web Applications`. Consultez les articles de procédure [Utiliser ML.NET dans l’API web](./serve-model-web-api-ml-net.md) et [Déployer une application web serverless ML.NET](./serve-model-serverless-azure-functions-ml-net.md) pour en savoir plus.

Dans une application ou un [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) processus distinct, utilisez la méthode avec le chemin de fichier pour obtenir le modèle formé dans votre application.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Charger un modèle stocké à distance

Pour charger les pipelines et les modèles de préparation [`Stream`](xref:System.IO.Stream) de données stockés [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) dans un endroit éloigné de votre application, utilisez un chemin de fichier au lieu de la méthode.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Utilisation de pipelines de modèle et de préparation des données distincts

> [!NOTE]
> L’utilisation de pipelines d’entraînement de modèle et de préparation des données distincts est facultative. La séparation des pipelines facilite l’inspection des paramètres de modèle appris. Pour les prédictions, il est plus facile d’enregistrer et de charger un seul pipeline qui inclut les opérations de préparation des données et d’entraînement de modèle.

Quand vous utilisez des modèles et des pipelines de préparation des données distincts, le même processus que pour les pipelines uniques s’applique ; la seule différence est qu’à présent les deux pipelines doivent être enregistrés et chargés simultanément.

Soient des pipelines d’entraînement de modèle et de préparation des données distincts :

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Enregistrer le pipeline de préparation des données et le modèle entraîné

Pour enregistrer le pipeline de préparation des données et le modèle entraîné, utilisez les commandes suivantes :

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Charger le pipeline de préparation des données et le modèle entraîné

Dans une application ou un processus distinct, chargez le pipeline de préparation des données et le modèle entraîné simultanément comme suit :

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
