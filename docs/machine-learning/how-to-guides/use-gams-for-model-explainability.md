---
title: Interpréter les modèles ML.NET avec des modèles additifs généralisés
description: Utilisez des modèles additifs généralisés et des fonctions de forme pour l’interprétation du modèle dans ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 29eac7a609ada57283a7c5b55b935e30709930dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243126"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="9d195-103">Utilisez des modèles additifs généralisés et des fonctions de forme pour l’interprétation du modèle dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="9d195-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="9d195-104">Lorsque vous créez des modèles Machine Learning, se contenter de faire des prédictions n’est souvent pas suffisant.</span><span class="sxs-lookup"><span data-stu-id="9d195-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="9d195-105">Les développeurs Machine Learning, les décideurs et les personnes affectées par les modèles doivent souvent comprendre comment les modèles Machine Learning prennent les décisions et connaître les fonctionnalités qui affectent leurs performances.</span><span class="sxs-lookup"><span data-stu-id="9d195-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="9d195-106">**Les modèles additifs généralisés (GAM)** sont utilisés en interne chez Microsoft pour l’interprétabilité des modèles afin d’aider les développeurs d’apprentissage automatique à créer des modèles de grande capacité qui peuvent être facilement interprétés par d’autres.</span><span class="sxs-lookup"><span data-stu-id="9d195-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="9d195-107">Les GAM constituent une catégorie de **modèles interprétables** représentant des modèles linéaires où les termes sont des fonctions non linéaires appelées « fonctions de forme » d’une variable unique.</span><span class="sxs-lookup"><span data-stu-id="9d195-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="9d195-108">En tant que modèles linéaires, ils sont interprétés facilement, mais comme les modèles apprennent les fonctions de fonctionnalités au lieu d’une pondération unique, ils peuvent modéliser des relations plus complexes qu’un simple modèle linéaire.</span><span class="sxs-lookup"><span data-stu-id="9d195-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="9d195-109">La prédiction GAM qui en résulte comporte un terme intercept qui représente la prédiction moyenne sur le jeu d’apprentissage ainsi que des fonctions de forme qui représentent l’écart par rapport à la prédiction moyenne.</span><span class="sxs-lookup"><span data-stu-id="9d195-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="9d195-110">Les fonctions de forme peuvent être inspectées à l’œil nu pour voir la réponse du modèle à différentes valeurs d’une fonctionnalité, puis visualisées comme dans le graphique suivant créé à la fin de l’exemple de code.</span><span class="sxs-lookup"><span data-stu-id="9d195-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="9d195-111">Le formateur GAM dans ML.NET est implémenté à l’aide d’arborescences étroites avec augmentation du gradient (par exemple des souches) afin d’apprendre les fonctions de forme non paramétriques, et il repose sur la méthode décrite dans l’article [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) rédigé par Lou, Caruana et Gehrke.</span><span class="sxs-lookup"><span data-stu-id="9d195-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Graphique de fonction de forme de modèles additifs généralisés](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="9d195-113">Pour un exemple de la façon de former un modèle GAM et d’inspecter et d’interpréter les résultats, voir [l’échantillon de formateur de classification binaire](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span><span class="sxs-lookup"><span data-stu-id="9d195-113">For an example of how to train a GAM model and inspect and interpret the results, see the [binary classification trainer sample](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span></span>
