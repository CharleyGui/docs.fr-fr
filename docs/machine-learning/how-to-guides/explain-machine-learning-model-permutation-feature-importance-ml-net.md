---
title: Expliquer les prédictions de modèle à l’aide de la technique PFI (Permutation Feature Importance)
description: Comprendre l’importance des caractéristiques des modèles avec l’option Permutation Feature Importance dans ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1037a1f1c21ef2c9b9a87a070a7d2003c1e76eb4
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307367"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="9af2d-103">Expliquer les prédictions de modèle à l’aide de la technique PFI (Permutation Feature Importance)</span><span class="sxs-lookup"><span data-stu-id="9af2d-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="9af2d-104">Découvrez comment expliquer les prédictions de modèle Machine Learning ML.NET en comprenant la contribution des caractéristiques aux prédictions à l’aide de la technique PFI (Permutation Feature Importance).</span><span class="sxs-lookup"><span data-stu-id="9af2d-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="9af2d-105">Les modèles Machine Learning sont souvent considérés comme des boîtes noires qui prennent des entrées et génèrent une sortie.</span><span class="sxs-lookup"><span data-stu-id="9af2d-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="9af2d-106">Les interactions ou étapes intermédiaires entre les caractéristiques qui influent sur la sortie sont rarement comprises.</span><span class="sxs-lookup"><span data-stu-id="9af2d-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="9af2d-107">Le machine learning faisant petit à petit son apparition dans les différents aspects de la vie quotidienne, tels que la santé, il est extrêmement important de comprendre pourquoi un modèle Machine Learning prend telle ou telle décision.</span><span class="sxs-lookup"><span data-stu-id="9af2d-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="9af2d-108">Par exemple, si les diagnostics sont effectués par un modèle Machine Learning, les professionnels de la santé doivent pouvoir étudier les facteurs qui ont contribué à l’établissement de ces diagnostics.</span><span class="sxs-lookup"><span data-stu-id="9af2d-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="9af2d-109">La fourniture du bon diagnostic peut s’avérer importante quant à la possibilité pour le patient de jouir ou non d’une récupération rapide.</span><span class="sxs-lookup"><span data-stu-id="9af2d-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="9af2d-110">Ainsi, plus le niveau d’explicabilité d’un modèle est élevé, plus grande est la confiance des professionnels de la santé quand ils acceptent ou rejettent les décisions prises par le modèle.</span><span class="sxs-lookup"><span data-stu-id="9af2d-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="9af2d-111">Différentes techniques sont utilisées pour expliquer les modèles, dont PFI.</span><span class="sxs-lookup"><span data-stu-id="9af2d-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="9af2d-112">PFI est une technique utilisée pour expliquer les modèles de classification et de régression, qui s’inspire du [document *Random Forests* de Leo Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(voir la section 10).</span><span class="sxs-lookup"><span data-stu-id="9af2d-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="9af2d-113">Sur un plan général, elle permute aléatoirement les données à raison d’une caractéristique à la fois pour l’ensemble du jeu de données et calcule la diminution de la métrique de performances d’intérêt.</span><span class="sxs-lookup"><span data-stu-id="9af2d-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="9af2d-114">Plus le changement est élevé, plus la caractéristique concernée est importante.</span><span class="sxs-lookup"><span data-stu-id="9af2d-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="9af2d-115">De plus, les caractéristiques les plus importantes étant ainsi mises en valeur, les générateurs de modèle peuvent se concentrer sur l’utilisation d’une partie des caractéristiques plus significatives qui sont susceptibles de réduire le bruit et la durée de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="9af2d-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="9af2d-116">Charger les données</span><span class="sxs-lookup"><span data-stu-id="9af2d-116">Load the data</span></span>

<span data-ttu-id="9af2d-117">Les caractéristiques dans le jeu de données utilisé pour cet échantillon sont indiquées dans les colonnes 1 à 12.</span><span class="sxs-lookup"><span data-stu-id="9af2d-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="9af2d-118">L’objectif est de prédire `Price`.</span><span class="sxs-lookup"><span data-stu-id="9af2d-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="9af2d-119">Colonne</span><span class="sxs-lookup"><span data-stu-id="9af2d-119">Column</span></span> | <span data-ttu-id="9af2d-120">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="9af2d-120">Feature</span></span> | <span data-ttu-id="9af2d-121">Description</span><span class="sxs-lookup"><span data-stu-id="9af2d-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="9af2d-122">1</span><span class="sxs-lookup"><span data-stu-id="9af2d-122">1</span></span> | <span data-ttu-id="9af2d-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="9af2d-123">CrimeRate</span></span> | <span data-ttu-id="9af2d-124">Taux de criminalité par habitant</span><span class="sxs-lookup"><span data-stu-id="9af2d-124">Per capita crime rate</span></span>
| <span data-ttu-id="9af2d-125">2</span><span class="sxs-lookup"><span data-stu-id="9af2d-125">2</span></span> | <span data-ttu-id="9af2d-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="9af2d-126">ResidentialZones</span></span> | <span data-ttu-id="9af2d-127">Zones résidentielles en ville</span><span class="sxs-lookup"><span data-stu-id="9af2d-127">Residential zones in town</span></span>
| <span data-ttu-id="9af2d-128">3</span><span class="sxs-lookup"><span data-stu-id="9af2d-128">3</span></span> | <span data-ttu-id="9af2d-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="9af2d-129">CommercialZones</span></span> | <span data-ttu-id="9af2d-130">Zones non résidentielles en ville</span><span class="sxs-lookup"><span data-stu-id="9af2d-130">Non-residential zones in town</span></span>
| <span data-ttu-id="9af2d-131">4</span><span class="sxs-lookup"><span data-stu-id="9af2d-131">4</span></span> | <span data-ttu-id="9af2d-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="9af2d-132">NearWater</span></span> | <span data-ttu-id="9af2d-133">Proximité d’une étendue d’eau</span><span class="sxs-lookup"><span data-stu-id="9af2d-133">Proximity to body of water</span></span>
| <span data-ttu-id="9af2d-134">5</span><span class="sxs-lookup"><span data-stu-id="9af2d-134">5</span></span> | <span data-ttu-id="9af2d-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="9af2d-135">ToxicWasteLevels</span></span> | <span data-ttu-id="9af2d-136">Niveaux de toxicité (PPM)</span><span class="sxs-lookup"><span data-stu-id="9af2d-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="9af2d-137">6</span><span class="sxs-lookup"><span data-stu-id="9af2d-137">6</span></span> | <span data-ttu-id="9af2d-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="9af2d-138">AverageRoomNumber</span></span> | <span data-ttu-id="9af2d-139">Nombre moyen de pièces par maison</span><span class="sxs-lookup"><span data-stu-id="9af2d-139">Average number of rooms in house</span></span>
| <span data-ttu-id="9af2d-140">7</span><span class="sxs-lookup"><span data-stu-id="9af2d-140">7</span></span> | <span data-ttu-id="9af2d-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="9af2d-141">HomeAge</span></span> | <span data-ttu-id="9af2d-142">Âge de la maison</span><span class="sxs-lookup"><span data-stu-id="9af2d-142">Age of home</span></span>
| <span data-ttu-id="9af2d-143">8</span><span class="sxs-lookup"><span data-stu-id="9af2d-143">8</span></span> | <span data-ttu-id="9af2d-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="9af2d-144">BusinessCenterDistance</span></span> | <span data-ttu-id="9af2d-145">Distance par rapport aux commerces les plus proches</span><span class="sxs-lookup"><span data-stu-id="9af2d-145">Distance to nearest business district</span></span>
| <span data-ttu-id="9af2d-146">9</span><span class="sxs-lookup"><span data-stu-id="9af2d-146">9</span></span> | <span data-ttu-id="9af2d-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="9af2d-147">HighwayAccess</span></span> | <span data-ttu-id="9af2d-148">Proximité des autoroutes</span><span class="sxs-lookup"><span data-stu-id="9af2d-148">Proximity to highways</span></span>
| <span data-ttu-id="9af2d-149">10</span><span class="sxs-lookup"><span data-stu-id="9af2d-149">10</span></span> | <span data-ttu-id="9af2d-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="9af2d-150">TaxRate</span></span> | <span data-ttu-id="9af2d-151">Montant des taxes foncières</span><span class="sxs-lookup"><span data-stu-id="9af2d-151">Property tax rate</span></span>
| <span data-ttu-id="9af2d-152">11</span><span class="sxs-lookup"><span data-stu-id="9af2d-152">11</span></span> | <span data-ttu-id="9af2d-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="9af2d-153">StudentTeacherRatio</span></span> | <span data-ttu-id="9af2d-154">Rapport entre le nombre d’étudiants et le nombre d’enseignants</span><span class="sxs-lookup"><span data-stu-id="9af2d-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="9af2d-155">12</span><span class="sxs-lookup"><span data-stu-id="9af2d-155">12</span></span> | <span data-ttu-id="9af2d-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="9af2d-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="9af2d-157">Pourcentage de la population vivant au-dessous du seuil de pauvreté</span><span class="sxs-lookup"><span data-stu-id="9af2d-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="9af2d-158">13</span><span class="sxs-lookup"><span data-stu-id="9af2d-158">13</span></span> | <span data-ttu-id="9af2d-159">Price</span><span class="sxs-lookup"><span data-stu-id="9af2d-159">Price</span></span> | <span data-ttu-id="9af2d-160">Prix de la maison</span><span class="sxs-lookup"><span data-stu-id="9af2d-160">Price of the home</span></span>

<span data-ttu-id="9af2d-161">Vous trouverez ci-dessous un échantillon du jeu de données :</span><span class="sxs-lookup"><span data-stu-id="9af2d-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="9af2d-162">Les données de cet échantillon peuvent être modélisées par une classe telle que `HousingPriceData` :</span><span class="sxs-lookup"><span data-stu-id="9af2d-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

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

<span data-ttu-id="9af2d-163">Chargez les données dans un [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9af2d-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="9af2d-164">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="9af2d-164">Train the model</span></span>

<span data-ttu-id="9af2d-165">L’exemple de code ci-dessous illustre le processus d’entraînement d’un modèle de régression linéaire pour prédire le prix des maisons.</span><span class="sxs-lookup"><span data-stu-id="9af2d-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="9af2d-166">Expliquer le modèle avec la technique PFI</span><span class="sxs-lookup"><span data-stu-id="9af2d-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="9af2d-167">Dans ML.NET, utilisez la méthode [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pour votre propre tâche.</span><span class="sxs-lookup"><span data-stu-id="9af2d-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="9af2d-168">Le résultat de l’utilisation de [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) sur le jeu de données d’entraînement est un [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) d’objets [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics).</span><span class="sxs-lookup"><span data-stu-id="9af2d-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="9af2d-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) fournit des statistiques de synthèse comme l’écart type et la moyenne pour plusieurs observations de [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) égales au nombre de permutations spécifiées par le paramètre `permutationCount`.</span><span class="sxs-lookup"><span data-stu-id="9af2d-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="9af2d-170">L’importance, ou, dans ce cas, la baisse moyenne absolue de la métrique du coefficient de détermination calculée par [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions), peut ensuite être classée du plus important au moins important.</span><span class="sxs-lookup"><span data-stu-id="9af2d-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="9af2d-171">L’affichage des valeurs de chacune des caractéristiques dans `featureImportanceMetrics` aboutirait à une sortie similaire à celle ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9af2d-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="9af2d-172">N’oubliez pas que vous devez vous attendre à voir des résultats différents, car ces valeurs varient en fonction des données fournies.</span><span class="sxs-lookup"><span data-stu-id="9af2d-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="9af2d-173">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="9af2d-173">Feature</span></span> | <span data-ttu-id="9af2d-174">Changement du coefficient de détermination</span><span class="sxs-lookup"><span data-stu-id="9af2d-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="9af2d-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="9af2d-175">HighwayAccess</span></span>       |   <span data-ttu-id="9af2d-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="9af2d-176">-0.042731</span></span>
<span data-ttu-id="9af2d-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="9af2d-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="9af2d-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="9af2d-178">-0.012730</span></span>
<span data-ttu-id="9af2d-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="9af2d-179">BusinessCenterDistance</span></span>| <span data-ttu-id="9af2d-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="9af2d-180">-0.010491</span></span>
<span data-ttu-id="9af2d-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="9af2d-181">TaxRate</span></span>             |   <span data-ttu-id="9af2d-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="9af2d-182">-0.008545</span></span>
<span data-ttu-id="9af2d-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="9af2d-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="9af2d-184">0,003949</span><span class="sxs-lookup"><span data-stu-id="9af2d-184">-0.003949</span></span>
<span data-ttu-id="9af2d-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="9af2d-185">CrimeRate</span></span>           |   <span data-ttu-id="9af2d-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="9af2d-186">-0.003665</span></span>
<span data-ttu-id="9af2d-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="9af2d-187">CommercialZones</span></span>     |   <span data-ttu-id="9af2d-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="9af2d-188">0.002749</span></span>
<span data-ttu-id="9af2d-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="9af2d-189">HomeAge</span></span>             |   <span data-ttu-id="9af2d-190">0,002426</span><span class="sxs-lookup"><span data-stu-id="9af2d-190">-0.002426</span></span>
<span data-ttu-id="9af2d-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="9af2d-191">ResidentialZones</span></span>    |   <span data-ttu-id="9af2d-192">0,002319</span><span class="sxs-lookup"><span data-stu-id="9af2d-192">-0.002319</span></span>
<span data-ttu-id="9af2d-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="9af2d-193">NearWater</span></span>           |   <span data-ttu-id="9af2d-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="9af2d-194">0.000203</span></span>
<span data-ttu-id="9af2d-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="9af2d-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="9af2d-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="9af2d-196">0.000031</span></span>
<span data-ttu-id="9af2d-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="9af2d-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="9af2d-198">0,000019</span><span class="sxs-lookup"><span data-stu-id="9af2d-198">-0.000019</span></span>

<span data-ttu-id="9af2d-199">Si nous observons les cinq caractéristiques les plus importantes pour ce jeu de données, nous pouvons constater que le prix d’une maison prédit par ce modèle est tributaire de sa proximité des autoroutes, du rapport nombre d’étudiants/nombre d’enseignants dans les écoles de la zone, de la proximité des principaux bassins d’emploi, du montant des taxes foncières et du nombre moyen de pièces dans la maison.</span><span class="sxs-lookup"><span data-stu-id="9af2d-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
