---
title: Interpréter les modèles ML.NET avec l’importance des fonctionnalités de permutation
description: Comprendre l’importance des caractéristiques des modèles avec l’option Permutation Feature Importance dans ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092614"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>Interpréter les prédictions de modèle à l’aide de la fonctionnalité de permutation

À l’aide de permutation Feature importance (PFI), Découvrez comment interpréter les prédictions de modèle de Machine Learning ML.NET. PFI donne la contribution relative de chaque fonctionnalité à une prédiction.

Les modèles Machine Learning sont souvent considérés comme des boîtes noires qui prennent des entrées et génèrent une sortie. Les interactions ou étapes intermédiaires entre les caractéristiques qui influent sur la sortie sont rarement comprises. Le machine learning faisant petit à petit son apparition dans les différents aspects de la vie quotidienne, tels que la santé, il est extrêmement important de comprendre pourquoi un modèle Machine Learning prend telle ou telle décision. Par exemple, si les diagnostics sont effectués par un modèle Machine Learning, les professionnels de la santé doivent pouvoir étudier les facteurs qui ont contribué à l’établissement de ces diagnostics. La fourniture du bon diagnostic peut s’avérer importante quant à la possibilité pour le patient de jouir ou non d’une récupération rapide. Ainsi, plus le niveau d’explicabilité d’un modèle est élevé, plus grande est la confiance des professionnels de la santé quand ils acceptent ou rejettent les décisions prises par le modèle.

Différentes techniques sont utilisées pour expliquer les modèles, dont PFI. PFI est une technique utilisée pour expliquer les modèles de classification et de régression inspirés par le [papier de *forêts aléatoires* de Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (voir la section 10). À un niveau élevé, il fonctionne en permutant aléatoirement les données d’une fonctionnalité à la fois pour l’ensemble du jeu de données et en calculant dans quelle mesure la métrique de performance utile diminue. Plus la modification est importante, et plus la fonctionnalité l’est également.

De plus, les caractéristiques les plus importantes étant ainsi mises en valeur, les générateurs de modèle peuvent se concentrer sur l’utilisation d’une partie des caractéristiques plus significatives qui sont susceptibles de réduire le bruit et la durée de l’entraînement.

## <a name="load-the-data"></a>Chargement des données

Les caractéristiques dans le jeu de données utilisé pour cet échantillon sont indiquées dans les colonnes 1 à 12. L’objectif est de prédire `Price`.

| Colonne | Fonctionnalité | Description
| --- | --- | --- |
| 1 | CrimeRate | Taux de criminalité par habitant
| 2 | ResidentialZones | Zones résidentielles en ville
| 3 | CommercialZones | Zones non résidentielles en ville
| 4 | NearWater | Proximité d’une étendue d’eau
| 5 | ToxicWasteLevels | Niveaux de toxicité (PPM)
| 6 | AverageRoomNumber | Nombre moyen de pièces par maison
| 7 | HomeAge | Âge de la maison
| 8 | BusinessCenterDistance | Distance par rapport aux commerces les plus proches
| 9 | HighwayAccess | Proximité des autoroutes
| 10 | TaxRate | Montant des taxes foncières
| 11 | StudentTeacherRatio | Rapport entre le nombre d’étudiants et le nombre d’enseignants
| 12 | PercentPopulationBelowPoverty | Pourcentage de la population vivant au-dessous du seuil de pauvreté
| 13 | Price | Prix de la maison

Vous trouverez ci-dessous un échantillon du jeu de données :

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Les données de cet exemple peuvent être modélisées par une classe comme `HousingPriceData` et chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

L’exemple de code ci-dessous illustre le processus d’entraînement d’un modèle de régression linéaire pour prédire le prix des maisons.

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames =
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Expliquer le modèle avec la technique PFI

Dans ML.NET, utilisez la méthode [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pour votre propre tâche.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Le résultat de l’utilisation de [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) sur le jeu de données d’entraînement est un [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) d’objets [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics). [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) fournit des statistiques de synthèse comme l’écart type et la moyenne pour plusieurs observations de [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) égales au nombre de permutations spécifiées par le paramètre `permutationCount`.

L’importance, ou, dans ce cas, la baisse moyenne absolue de la métrique du coefficient de détermination calculée par [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions), peut ensuite être classée du plus important au moins important.

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

L’affichage des valeurs de chacune des caractéristiques dans `featureImportanceMetrics` aboutirait à une sortie similaire à celle ci-dessous. N’oubliez pas que vous devez vous attendre à voir des résultats différents, car ces valeurs varient en fonction des données fournies.

| Fonctionnalité | Changement du coefficient de détermination |
|:--|:--:|
HighwayAccess       |   -0,042731
StudentTeacherRatio |   -0,012730
BusinessCenterDistance| -0,010491
TaxRate             |   -0,008545
AverageRoomNumber   |   0,003949
CrimeRate           |   -0,003665
CommercialZones     |   0,002749
HomeAge             |   0,002426
ResidentialZones    |   0,002319
NearWater           |   0,000203
PercentPopulationLivingBelowPoverty|    0,000031
ToxicWasteLevels    |   0,000019

Si nous observons les cinq caractéristiques les plus importantes pour ce jeu de données, nous pouvons constater que le prix d’une maison prédit par ce modèle est tributaire de sa proximité des autoroutes, du rapport nombre d’étudiants/nombre d’enseignants dans les écoles de la zone, de la proximité des principaux bassins d’emploi, du montant des taxes foncières et du nombre moyen de pièces dans la maison.
