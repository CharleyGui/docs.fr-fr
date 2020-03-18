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
# <a name="save-and-load-trained-models"></a><span data-ttu-id="e0a6f-103">Enregistrer et charger des modèles entraînés</span><span class="sxs-lookup"><span data-stu-id="e0a6f-103">Save and load trained models</span></span>

<span data-ttu-id="e0a6f-104">Découvrez comment enregistrer et charger des modèles entraînés dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="e0a6f-105">Durant le processus de création de modèle, un modèle se trouve dans la mémoire et est accessible tout au long du cycle de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="e0a6f-106">Toutefois, dès la fin de l’exécution de l’application, le modèle n’est plus accessible s’il n’est pas enregistré localement ou à distance.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="e0a6f-107">En général, les modèles sont utilisés après l’entraînement dans d’autres applications à des fins d’inférence ou de réentraînement.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="e0a6f-108">C’est pourquoi il est important de stocker le modèle.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="e0a6f-109">Enregistrez et chargez les modèles à l’aide de la procédure décrite dans les sections suivantes de ce document quand vous utilisez des pipelines de préparation des données et d’entraînement de modèle semblables à celui détaillé ci-après.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="e0a6f-110">Bien que cet exemple utilise un modèle de régression linéaire, le même processus s’applique aux autres algorithmes ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="e0a6f-111">Étant donné que la plupart des modèles et des pipelines de préparation des données héritent du même ensemble de classes, les signatures des méthodes d’enregistrement et de chargement pour ces composants sont les mêmes.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="e0a6f-112">Selon votre cas d’utilisation, vous pouvez combiner le [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) pipeline et le [`ITransformer`](xref:Microsoft.ML.ITransformer) modèle de préparation [`ITransformer`](xref:Microsoft.ML.ITransformer) de données en un seul qui produirait un seul ou les séparer, créant ainsi une séparation pour chacun.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="e0a6f-113">Enregistrer un modèle localement</span><span class="sxs-lookup"><span data-stu-id="e0a6f-113">Save a model locally</span></span>

<span data-ttu-id="e0a6f-114">Quand vous enregistrez un modèle, vous avez besoin de deux choses :</span><span class="sxs-lookup"><span data-stu-id="e0a6f-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="e0a6f-115">Le [`ITransformer`](xref:Microsoft.ML.ITransformer) modèle.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="e0a6f-116">[`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) L’entrée [`ITransformer`](xref:Microsoft.ML.ITransformer)attendue de l’on s’y attend.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="e0a6f-117">Après la formation du [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modèle, utilisez la méthode `model.zip` pour `DataViewSchema` enregistrer le modèle formé à un fichier appelé en utilisant les données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="e0a6f-118">Charger un modèle stocké localement</span><span class="sxs-lookup"><span data-stu-id="e0a6f-118">Load a model stored locally</span></span>

<span data-ttu-id="e0a6f-119">Les modèles stockés localement peuvent être utilisés dans d’autres processus ou applications comme `ASP.NET Core` et `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="e0a6f-120">Consultez les articles de procédure [Utiliser ML.NET dans l’API web](./serve-model-web-api-ml-net.md) et [Déployer une application web serverless ML.NET](./serve-model-serverless-azure-functions-ml-net.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="e0a6f-121">Dans une application ou un [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) processus distinct, utilisez la méthode avec le chemin de fichier pour obtenir le modèle formé dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="e0a6f-122">Charger un modèle stocké à distance</span><span class="sxs-lookup"><span data-stu-id="e0a6f-122">Load a model stored remotely</span></span>

<span data-ttu-id="e0a6f-123">Pour charger les pipelines et les modèles de préparation [`Stream`](xref:System.IO.Stream) de données stockés [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) dans un endroit éloigné de votre application, utilisez un chemin de fichier au lieu de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="e0a6f-124">Utilisation de pipelines de modèle et de préparation des données distincts</span><span class="sxs-lookup"><span data-stu-id="e0a6f-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="e0a6f-125">L’utilisation de pipelines d’entraînement de modèle et de préparation des données distincts est facultative.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="e0a6f-126">La séparation des pipelines facilite l’inspection des paramètres de modèle appris.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="e0a6f-127">Pour les prédictions, il est plus facile d’enregistrer et de charger un seul pipeline qui inclut les opérations de préparation des données et d’entraînement de modèle.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="e0a6f-128">Quand vous utilisez des modèles et des pipelines de préparation des données distincts, le même processus que pour les pipelines uniques s’applique ; la seule différence est qu’à présent les deux pipelines doivent être enregistrés et chargés simultanément.</span><span class="sxs-lookup"><span data-stu-id="e0a6f-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="e0a6f-129">Soient des pipelines d’entraînement de modèle et de préparation des données distincts :</span><span class="sxs-lookup"><span data-stu-id="e0a6f-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="e0a6f-130">Enregistrer le pipeline de préparation des données et le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="e0a6f-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="e0a6f-131">Pour enregistrer le pipeline de préparation des données et le modèle entraîné, utilisez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0a6f-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="e0a6f-132">Charger le pipeline de préparation des données et le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="e0a6f-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="e0a6f-133">Dans une application ou un processus distinct, chargez le pipeline de préparation des données et le modèle entraîné simultanément comme suit :</span><span class="sxs-lookup"><span data-stu-id="e0a6f-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
