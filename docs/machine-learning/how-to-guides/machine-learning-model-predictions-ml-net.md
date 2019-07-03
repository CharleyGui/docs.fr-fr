---
title: Effectuer des prédictions avec un modèle entraîné
description: Apprenez à effectuer des prédictions à l’aide d’un modèle entraîné
ms.date: 06/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: ef2b22ff220d1fce1ec43f26c7d51f7e551e038d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307398"
---
# <a name="make-predictions-with-a-trained-model"></a>Effectuer des prédictions avec un modèle entraîné

Découvrez comment utiliser un modèle entraîné pour effectuer des prédictions.

## <a name="create-data-models"></a>Créer des modèles de données

### <a name="input-data"></a>Données d’entrée

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

### <a name="output-data"></a>Données de sortie

Comme les noms de colonne d’entrée `Features` et `Label`, ML.NET a des noms par défaut pour les colonnes de valeur prédite produites par un modèle. Selon la tâche, le nom peut différer.

L’algorithme utilisé dans cet exemple étant un algorithme de régression linéaire, le nom par défaut de la colonne de sortie est `Score`, défini par l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) sur la propriété `PredictedPrice`.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

Le modèle de données `HousingPrediction` hérite de `HousingData` pour faciliter la visualisation des données d’entrée d’origine ainsi que de la sortie générée par le modèle.  

## <a name="set-up-a-prediction-pipeline"></a>Configurer un pipeline de prédiction

Que vous effectuiez une prédiction unique ou par lot, vous devez charger le pipeline de prédiction dans l’application. Ce pipeline contient les transformations de prétraitement de données ainsi que le modèle entraîné. L’extrait de code ci-dessous charge le pipeline de prédiction à partir d’un fichier nommé `model.zip`.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Prédiction unique

Pour effectuer une prédiction unique, créez un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) en utilisant le pipeline de prédiction chargé.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Ensuite, utilisez la méthode [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) pour transmettre vos données d’entrée en tant que paramètre. Notez que l’utilisation de la méthode [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) ne requiert pas que l’entrée soit un [`IDataView`](xref:Microsoft.ML.IDataView)). En effet, elle internalise facilement la manipulation du type de données d’entrée afin que vous puissiez passer un objet du type de données d’entrée. De plus, `CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.

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

Si vous accédez à la propriété `Score` de l’objet `prediction`, vous devez obtenir une valeur similaire à `150079`.

## <a name="batch-prediction"></a>Prédiction par lot

Soient les données suivantes. Chargez-les dans un [`IDataView`](xref:Microsoft.ML.IDataView). Dans ce cas, le nom de notre [`IDataView`](xref:Microsoft.ML.IDataView) est `inputData`. `CurrentPrice` étant la cible ou l’étiquette que vous tentez de prédire à l’aide de nouvelles données, aucune valeur correspondante n’est censée exister pour le moment.

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

Ensuite, utilisez la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pour appliquer les transformations de données et générer des prédictions.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Inspectez les valeurs prédites à l’aide de la méthode [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*).

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Les valeurs prédites dans la colonne des scores doivent se présenter comme suit :

| Observation | Prédiction |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
