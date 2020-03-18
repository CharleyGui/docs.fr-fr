---
title: Interpréter ML.NET modèles avec Permutation Feature Importance
description: Comprendre l’importance des caractéristiques des modèles avec l’option Permutation Feature Importance dans ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092614"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="04052-103">Interpréter les prédictions des modèles à l’aide de Permutation Feature Importance</span><span class="sxs-lookup"><span data-stu-id="04052-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="04052-104">À l’aide de Permutation Feature Importance (PFI), apprenez à interpréter ML.NET prédictions des modèles d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="04052-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="04052-105">PFI donne la contribution relative que chaque fonctionnalité apporte à une prédiction.</span><span class="sxs-lookup"><span data-stu-id="04052-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="04052-106">Les modèles Machine Learning sont souvent considérés comme des boîtes noires qui prennent des entrées et génèrent une sortie.</span><span class="sxs-lookup"><span data-stu-id="04052-106">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="04052-107">Les interactions ou étapes intermédiaires entre les caractéristiques qui influent sur la sortie sont rarement comprises.</span><span class="sxs-lookup"><span data-stu-id="04052-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="04052-108">Le machine learning faisant petit à petit son apparition dans les différents aspects de la vie quotidienne, tels que la santé, il est extrêmement important de comprendre pourquoi un modèle Machine Learning prend telle ou telle décision.</span><span class="sxs-lookup"><span data-stu-id="04052-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="04052-109">Par exemple, si les diagnostics sont effectués par un modèle Machine Learning, les professionnels de la santé doivent pouvoir étudier les facteurs qui ont contribué à l’établissement de ces diagnostics.</span><span class="sxs-lookup"><span data-stu-id="04052-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="04052-110">La fourniture du bon diagnostic peut s’avérer importante quant à la possibilité pour le patient de jouir ou non d’une récupération rapide.</span><span class="sxs-lookup"><span data-stu-id="04052-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="04052-111">Ainsi, plus le niveau d’explicabilité d’un modèle est élevé, plus grande est la confiance des professionnels de la santé quand ils acceptent ou rejettent les décisions prises par le modèle.</span><span class="sxs-lookup"><span data-stu-id="04052-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="04052-112">Différentes techniques sont utilisées pour expliquer les modèles, dont PFI.</span><span class="sxs-lookup"><span data-stu-id="04052-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="04052-113">PFI est une technique utilisée pour expliquer les modèles de classification et de régression qui [s’inspire du papier *Random Forests* de Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (voir la section 10).</span><span class="sxs-lookup"><span data-stu-id="04052-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="04052-114">À un niveau élevé, il fonctionne en permutant aléatoirement les données d’une fonctionnalité à la fois pour l’ensemble du jeu de données et en calculant dans quelle mesure la métrique de performance utile diminue.</span><span class="sxs-lookup"><span data-stu-id="04052-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="04052-115">Plus la modification est importante, et plus la fonctionnalité l’est également.</span><span class="sxs-lookup"><span data-stu-id="04052-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="04052-116">De plus, les caractéristiques les plus importantes étant ainsi mises en valeur, les générateurs de modèle peuvent se concentrer sur l’utilisation d’une partie des caractéristiques plus significatives qui sont susceptibles de réduire le bruit et la durée de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="04052-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="04052-117">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="04052-117">Load the data</span></span>

<span data-ttu-id="04052-118">Les caractéristiques dans le jeu de données utilisé pour cet échantillon sont indiquées dans les colonnes 1 à 12.</span><span class="sxs-lookup"><span data-stu-id="04052-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="04052-119">L’objectif est de prédire `Price`.</span><span class="sxs-lookup"><span data-stu-id="04052-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="04052-120">Colonne</span><span class="sxs-lookup"><span data-stu-id="04052-120">Column</span></span> | <span data-ttu-id="04052-121">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="04052-121">Feature</span></span> | <span data-ttu-id="04052-122">Description</span><span class="sxs-lookup"><span data-stu-id="04052-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="04052-123">1</span><span class="sxs-lookup"><span data-stu-id="04052-123">1</span></span> | <span data-ttu-id="04052-124">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="04052-124">CrimeRate</span></span> | <span data-ttu-id="04052-125">Taux de criminalité par habitant</span><span class="sxs-lookup"><span data-stu-id="04052-125">Per capita crime rate</span></span>
| <span data-ttu-id="04052-126">2</span><span class="sxs-lookup"><span data-stu-id="04052-126">2</span></span> | <span data-ttu-id="04052-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="04052-127">ResidentialZones</span></span> | <span data-ttu-id="04052-128">Zones résidentielles en ville</span><span class="sxs-lookup"><span data-stu-id="04052-128">Residential zones in town</span></span>
| <span data-ttu-id="04052-129">3</span><span class="sxs-lookup"><span data-stu-id="04052-129">3</span></span> | <span data-ttu-id="04052-130">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="04052-130">CommercialZones</span></span> | <span data-ttu-id="04052-131">Zones non résidentielles en ville</span><span class="sxs-lookup"><span data-stu-id="04052-131">Non-residential zones in town</span></span>
| <span data-ttu-id="04052-132">4</span><span class="sxs-lookup"><span data-stu-id="04052-132">4</span></span> | <span data-ttu-id="04052-133">NearWater</span><span class="sxs-lookup"><span data-stu-id="04052-133">NearWater</span></span> | <span data-ttu-id="04052-134">Proximité d’une étendue d’eau</span><span class="sxs-lookup"><span data-stu-id="04052-134">Proximity to body of water</span></span>
| <span data-ttu-id="04052-135">5</span><span class="sxs-lookup"><span data-stu-id="04052-135">5</span></span> | <span data-ttu-id="04052-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="04052-136">ToxicWasteLevels</span></span> | <span data-ttu-id="04052-137">Niveaux de toxicité (PPM)</span><span class="sxs-lookup"><span data-stu-id="04052-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="04052-138">6</span><span class="sxs-lookup"><span data-stu-id="04052-138">6</span></span> | <span data-ttu-id="04052-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="04052-139">AverageRoomNumber</span></span> | <span data-ttu-id="04052-140">Nombre moyen de pièces par maison</span><span class="sxs-lookup"><span data-stu-id="04052-140">Average number of rooms in house</span></span>
| <span data-ttu-id="04052-141">7</span><span class="sxs-lookup"><span data-stu-id="04052-141">7</span></span> | <span data-ttu-id="04052-142">HomeAge</span><span class="sxs-lookup"><span data-stu-id="04052-142">HomeAge</span></span> | <span data-ttu-id="04052-143">Âge de la maison</span><span class="sxs-lookup"><span data-stu-id="04052-143">Age of home</span></span>
| <span data-ttu-id="04052-144">8</span><span class="sxs-lookup"><span data-stu-id="04052-144">8</span></span> | <span data-ttu-id="04052-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="04052-145">BusinessCenterDistance</span></span> | <span data-ttu-id="04052-146">Distance par rapport aux commerces les plus proches</span><span class="sxs-lookup"><span data-stu-id="04052-146">Distance to nearest business district</span></span>
| <span data-ttu-id="04052-147">9</span><span class="sxs-lookup"><span data-stu-id="04052-147">9</span></span> | <span data-ttu-id="04052-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="04052-148">HighwayAccess</span></span> | <span data-ttu-id="04052-149">Proximité des autoroutes</span><span class="sxs-lookup"><span data-stu-id="04052-149">Proximity to highways</span></span>
| <span data-ttu-id="04052-150">10</span><span class="sxs-lookup"><span data-stu-id="04052-150">10</span></span> | <span data-ttu-id="04052-151">TaxRate</span><span class="sxs-lookup"><span data-stu-id="04052-151">TaxRate</span></span> | <span data-ttu-id="04052-152">Montant des taxes foncières</span><span class="sxs-lookup"><span data-stu-id="04052-152">Property tax rate</span></span>
| <span data-ttu-id="04052-153">11</span><span class="sxs-lookup"><span data-stu-id="04052-153">11</span></span> | <span data-ttu-id="04052-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="04052-154">StudentTeacherRatio</span></span> | <span data-ttu-id="04052-155">Rapport entre le nombre d’étudiants et le nombre d’enseignants</span><span class="sxs-lookup"><span data-stu-id="04052-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="04052-156">12</span><span class="sxs-lookup"><span data-stu-id="04052-156">12</span></span> | <span data-ttu-id="04052-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="04052-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="04052-158">Pourcentage de la population vivant au-dessous du seuil de pauvreté</span><span class="sxs-lookup"><span data-stu-id="04052-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="04052-159">13</span><span class="sxs-lookup"><span data-stu-id="04052-159">13</span></span> | <span data-ttu-id="04052-160">Price</span><span class="sxs-lookup"><span data-stu-id="04052-160">Price</span></span> | <span data-ttu-id="04052-161">Prix de la maison</span><span class="sxs-lookup"><span data-stu-id="04052-161">Price of the home</span></span>

<span data-ttu-id="04052-162">Vous trouverez ci-dessous un échantillon du jeu de données :</span><span class="sxs-lookup"><span data-stu-id="04052-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="04052-163">Les données de cet échantillon peuvent être `HousingPriceData` modélisés par une classe comme et chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="04052-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="04052-164">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="04052-164">Train the model</span></span>

<span data-ttu-id="04052-165">L’exemple de code ci-dessous illustre le processus d’entraînement d’un modèle de régression linéaire pour prédire le prix des maisons.</span><span class="sxs-lookup"><span data-stu-id="04052-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="04052-166">Expliquer le modèle avec la technique PFI</span><span class="sxs-lookup"><span data-stu-id="04052-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="04052-167">Dans ML.NET utilisez la [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) méthode pour votre tâche respective.</span><span class="sxs-lookup"><span data-stu-id="04052-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="04052-168">Le résultat [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) de l’utilisation sur [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) le jeu de données de formation est un des objets.</span><span class="sxs-lookup"><span data-stu-id="04052-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="04052-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)fournit des statistiques sommaires comme l’écart [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) moyen et standard pour les observations `permutationCount` multiples égales au nombre de permutations spécifiées par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="04052-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="04052-170">L’importance, ou dans ce cas, la diminution moyenne [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) absolue de la métrique R-carré calculée par peut alors être commandée de plus important à moins important.</span><span class="sxs-lookup"><span data-stu-id="04052-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="04052-171">L’affichage des valeurs de chacune des caractéristiques dans `featureImportanceMetrics` aboutirait à une sortie similaire à celle ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="04052-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="04052-172">N’oubliez pas que vous devez vous attendre à voir des résultats différents, car ces valeurs varient en fonction des données fournies.</span><span class="sxs-lookup"><span data-stu-id="04052-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="04052-173">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="04052-173">Feature</span></span> | <span data-ttu-id="04052-174">Changement du coefficient de détermination</span><span class="sxs-lookup"><span data-stu-id="04052-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="04052-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="04052-175">HighwayAccess</span></span>       |   <span data-ttu-id="04052-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="04052-176">-0.042731</span></span>
<span data-ttu-id="04052-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="04052-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="04052-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="04052-178">-0.012730</span></span>
<span data-ttu-id="04052-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="04052-179">BusinessCenterDistance</span></span>| <span data-ttu-id="04052-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="04052-180">-0.010491</span></span>
<span data-ttu-id="04052-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="04052-181">TaxRate</span></span>             |   <span data-ttu-id="04052-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="04052-182">-0.008545</span></span>
<span data-ttu-id="04052-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="04052-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="04052-184">0,003949</span><span class="sxs-lookup"><span data-stu-id="04052-184">-0.003949</span></span>
<span data-ttu-id="04052-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="04052-185">CrimeRate</span></span>           |   <span data-ttu-id="04052-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="04052-186">-0.003665</span></span>
<span data-ttu-id="04052-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="04052-187">CommercialZones</span></span>     |   <span data-ttu-id="04052-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="04052-188">0.002749</span></span>
<span data-ttu-id="04052-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="04052-189">HomeAge</span></span>             |   <span data-ttu-id="04052-190">0,002426</span><span class="sxs-lookup"><span data-stu-id="04052-190">-0.002426</span></span>
<span data-ttu-id="04052-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="04052-191">ResidentialZones</span></span>    |   <span data-ttu-id="04052-192">0,002319</span><span class="sxs-lookup"><span data-stu-id="04052-192">-0.002319</span></span>
<span data-ttu-id="04052-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="04052-193">NearWater</span></span>           |   <span data-ttu-id="04052-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="04052-194">0.000203</span></span>
<span data-ttu-id="04052-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="04052-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="04052-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="04052-196">0.000031</span></span>
<span data-ttu-id="04052-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="04052-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="04052-198">0,000019</span><span class="sxs-lookup"><span data-stu-id="04052-198">-0.000019</span></span>

<span data-ttu-id="04052-199">Si nous observons les cinq caractéristiques les plus importantes pour ce jeu de données, nous pouvons constater que le prix d’une maison prédit par ce modèle est tributaire de sa proximité des autoroutes, du rapport nombre d’étudiants/nombre d’enseignants dans les écoles de la zone, de la proximité des principaux bassins d’emploi, du montant des taxes foncières et du nombre moyen de pièces dans la maison.</span><span class="sxs-lookup"><span data-stu-id="04052-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
