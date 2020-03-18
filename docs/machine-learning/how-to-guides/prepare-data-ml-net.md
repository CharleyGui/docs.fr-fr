---
title: Préparer des données pour la génération d’un modèle
description: Découvrez comment utiliser des transformations dans ML.NET pour manipuler et préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452985"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="fb2d3-103">Préparer des données pour la génération d’un modèle</span><span class="sxs-lookup"><span data-stu-id="fb2d3-103">Prepare data for building a model</span></span>

<span data-ttu-id="fb2d3-104">Découvrez comment utiliser ML.NET pour préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="fb2d3-105">Les données sont souvent dans un format incorrect et disséminées.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="fb2d3-106">ML.NET algorithmes d’apprentissage automatique s’attendent à ce que l’entrée ou les fonctionnalités se trouve dans un seul vecteur numérique.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="fb2d3-107">De même, la valeur de prévoir (l’étiquette), surtout lorsqu’il s’agit de données catégoriques, doit être codée.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="fb2d3-108">Ainsi, un des objectifs de la préparation des données consiste à obtenir les données dans le format attendu par les algorithmes ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="fb2d3-109">Filtrer les données</span><span class="sxs-lookup"><span data-stu-id="fb2d3-109">Filter data</span></span>

<span data-ttu-id="fb2d3-110">Parfois, toutes les données d’un jeu de données ne sont pas appropriées pour l’analyse.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="fb2d3-111">Une approche pour supprimer les données non pertinentes consiste à effectuer un filtrage.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="fb2d3-112">Le [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contient un ensemble d’opérations [`IDataView`](xref:Microsoft.ML.IDataView) de filtre qui prennent dans un contenant toutes les données et de retourner un [IDataView](xref:Microsoft.ML.IDataView) contenant uniquement les points de données d’intérêt.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="fb2d3-113">Il est important de noter que parce [`IEstimator`](xref:Microsoft.ML.IEstimator%601) [`ITransformer`](xref:Microsoft.ML.ITransformer) que les [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)opérations de filtre ne sont [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) pas un ou comme ceux dans le , ils ne peuvent pas être inclus dans un pipeline ou de préparation de données.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="fb2d3-114">Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="fb2d3-115">Pour filtrer les données en fonction [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) de la valeur d’une colonne, utilisez la méthode.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="fb2d3-116">L’exemple ci-dessus prend les lignes dans le jeu de données ayant un prix entre 200 000 et 1 000 000.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="fb2d3-117">L’application de ce filtre retourne uniquement les deux dernières lignes dans les données et exclut la première ligne, car son prix, 1 00 000, n’appartient pas à la plage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="fb2d3-118">Remplacer des valeurs manquantes</span><span class="sxs-lookup"><span data-stu-id="fb2d3-118">Replace missing values</span></span>

<span data-ttu-id="fb2d3-119">Les valeurs manquantes sont courantes dans les jeux de données.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="fb2d3-120">Pour traiter les valeurs manquantes, une approche consiste à les remplacer par la valeur par défaut du type donné éventuel ou par une autre valeur significative telle que la valeur moyenne dans les données.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="fb2d3-121">Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

<span data-ttu-id="fb2d3-122">Notez que le dernier élément dans notre liste a une valeur manquante pour `Price`.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="fb2d3-123">Pour remplacer les valeurs `Price` manquantes [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) dans la colonne, utilisez la méthode pour combler cette valeur manquante.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb2d3-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)ne fonctionne qu’avec des données numériques.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="fb2d3-125">ML.NET prend en charge divers [modes de remplacement](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="fb2d3-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="fb2d3-126">L’échantillon ci-dessus utilise le `Mean` mode de remplacement, qui remplit la valeur manquante avec la valeur moyenne de cette colonne.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="fb2d3-127">Le remplacement se traduit par le remplissage de la propriété `Price` pour le dernier élément dans les données avec la valeur 200 000, soit la moyenne de 100 000 et 300 000.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="fb2d3-128">Utiliser des normaliseurs</span><span class="sxs-lookup"><span data-stu-id="fb2d3-128">Use normalizers</span></span>

<span data-ttu-id="fb2d3-129">[La normalisation](https://en.wikipedia.org/wiki/Feature_scaling) est une technique de pré-traitement des données utilisée pour mettre à l’échelle les fonctionnalités pour être dans la même plage, généralement entre 0 et 1, de sorte qu’ils peuvent être traités avec plus de précision par un algorithme d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="fb2d3-130">Par exemple, les fourchettes d’âge et de revenu varient considérablement selon l’âge généralement de 0 à 100 ans et le revenu étant généralement de l’ordre de zéro à des milliers.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="fb2d3-131">Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de normalisation.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="fb2d3-132">Normalisation min-max</span><span class="sxs-lookup"><span data-stu-id="fb2d3-132">Min-Max normalization</span></span>

<span data-ttu-id="fb2d3-133">Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

<span data-ttu-id="fb2d3-134">La normalisation peut être appliquée aux colonnes avec des valeurs numériques uniques, ainsi qu’aux vecteurs.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="fb2d3-135">Normalisez les `Price` données de la colonne à [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) l’aide d’une normalisation min-max avec la méthode.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="fb2d3-136">Les valeurs `[200000,100000]` de prix `[ 1, 0.5 ]` d’origine sont converties en utilisant la `MinMax` formule de normalisation qui génère des valeurs de production de l’ordre de 0-1.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="fb2d3-137">Quantification</span><span class="sxs-lookup"><span data-stu-id="fb2d3-137">Binning</span></span>

<span data-ttu-id="fb2d3-138">La [quantification](https://en.wikipedia.org/wiki/Data_binning) convertit des valeurs continues en une représentation discrète de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="fb2d3-139">Par exemple, supposons qu’une de vos caractéristiques est l’âge.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="fb2d3-140">Au lieu d’utiliser la valeur de l’âge réel, la quantification crée des plages pour cette valeur.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="fb2d3-141">0-18 pourrait être une cellule, de même que 19-35, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="fb2d3-142">Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="fb2d3-143">Normalisez les données en [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) bacs à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="fb2d3-144">Le paramètre `maximumBinCount` vous permet de spécifier le nombre de cellules nécessaires pour classifier vos données.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="fb2d3-145">Dans cet exemple, les données sont placées dans deux cellules.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="fb2d3-146">La quantification crée des bornes de cellule de `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="fb2d3-147">Ainsi, les cellules obtenues sont `[0,1,1]`, car la première observation est comprise entre 0 et 200 000, et les autres sont supérieures à 200 000 mais inférieures à l’infini.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="fb2d3-148">Utiliser des données de catégorie</span><span class="sxs-lookup"><span data-stu-id="fb2d3-148">Work with categorical data</span></span>

<span data-ttu-id="fb2d3-149">L’un des types de données les plus courants est celui des données catégoriques.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="fb2d3-150">Les données catégories ont un nombre limité de catégories.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="fb2d3-151">Par exemple, les États des États-Unis, ou une liste des types d’animaux trouvés dans un ensemble d’images.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="fb2d3-152">Que les données catégoriques soient des caractéristiques ou des étiquettes, elles doivent être cartographiées sur une valeur numérique afin qu’elles puissent être utilisées pour générer un modèle d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="fb2d3-153">Il existe un certain nombre de façons de travailler avec des données catégoriques dans ML.NET, en fonction du problème que vous résolvez.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="fb2d3-154">Cartographie de la valeur clé</span><span class="sxs-lookup"><span data-stu-id="fb2d3-154">Key value mapping</span></span>

<span data-ttu-id="fb2d3-155">Dans ML.NET, une clé est une valeur integer qui représente une catégorie.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="fb2d3-156">La cartographie des valeurs clés est le plus souvent utilisée pour cartographier les étiquettes de chaîne en valeurs integer uniques pour la formation, puis revenir à leurs valeurs de chaîne lorsque le modèle est utilisé pour faire une prédiction.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="fb2d3-157">Les transformations utilisées pour effectuer la cartographie de valeur clé sont [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) et [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="fb2d3-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="fb2d3-158">`MapValueToKey`ajoute un dictionnaire de cartes dans `MapKeyToValue` le modèle, de sorte que peut effectuer la transformation inverse lors de la prise d’une prédiction.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="fb2d3-159">Un codage chaud</span><span class="sxs-lookup"><span data-stu-id="fb2d3-159">One hot encoding</span></span>

<span data-ttu-id="fb2d3-160">Un codage chaud prend un ensemble fini de valeurs et les cartographie `1` sur les entiers dont la représentation binaire a une valeur unique dans des positions uniques dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="fb2d3-161">Un codage chaud peut être le meilleur choix s’il n’y a pas de commande implicite des données catégoriques.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="fb2d3-162">Le tableau suivant montre un exemple avec des codes postaux comme valeurs brutes.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="fb2d3-163">Valeur brute</span><span class="sxs-lookup"><span data-stu-id="fb2d3-163">Raw value</span></span>|<span data-ttu-id="fb2d3-164">Une valeur codée chaude</span><span class="sxs-lookup"><span data-stu-id="fb2d3-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="fb2d3-165">98052</span><span class="sxs-lookup"><span data-stu-id="fb2d3-165">98052</span></span>|<span data-ttu-id="fb2d3-166">00...01</span><span class="sxs-lookup"><span data-stu-id="fb2d3-166">00...01</span></span>|
|<span data-ttu-id="fb2d3-167">98100</span><span class="sxs-lookup"><span data-stu-id="fb2d3-167">98100</span></span>|<span data-ttu-id="fb2d3-168">00...10</span><span class="sxs-lookup"><span data-stu-id="fb2d3-168">00...10</span></span>|
|<span data-ttu-id="fb2d3-169">...</span><span class="sxs-lookup"><span data-stu-id="fb2d3-169">...</span></span>|<span data-ttu-id="fb2d3-170">...</span><span class="sxs-lookup"><span data-stu-id="fb2d3-170">...</span></span>|
|<span data-ttu-id="fb2d3-171">98109</span><span class="sxs-lookup"><span data-stu-id="fb2d3-171">98109</span></span>|<span data-ttu-id="fb2d3-172">10...00</span><span class="sxs-lookup"><span data-stu-id="fb2d3-172">10...00</span></span>|

<span data-ttu-id="fb2d3-173">La transformation pour convertir les données catégoriques en [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)numéros codés à un seul chaud est .</span><span class="sxs-lookup"><span data-stu-id="fb2d3-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="fb2d3-174">Hashing</span><span class="sxs-lookup"><span data-stu-id="fb2d3-174">Hashing</span></span>

<span data-ttu-id="fb2d3-175">Le hachage est une autre façon de convertir les données catégoriques en nombres.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="fb2d3-176">Une fonction de hachage cartographie les données d’une taille arbitraire (une chaîne de texte par exemple) sur un nombre à portée fixe.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="fb2d3-177">Le hachage peut être un moyen rapide et efficace pour l’espace de vectoriser les caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="fb2d3-178">Un exemple notable de hachage dans l’apprentissage automatique est le filtrage des spams par courriel où, au lieu de maintenir un dictionnaire de mots connus, chaque mot dans l’e-mail est haché et ajouté à un vecteur de fonctionnalités grande.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="fb2d3-179">L’utilisation du hachage de cette façon évite le problème du contournement malveillant de filtrage de spam par l’utilisation de mots qui ne sont pas dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="fb2d3-180">ML.NET fournit la transformation [de Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) pour effectuer le hachage sur le texte, les dates et les données numériques.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="fb2d3-181">Comme la cartographie des clés de valeur, les sorties de la transformation du hachage sont des types clés.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="fb2d3-182">Utiliser des données texte</span><span class="sxs-lookup"><span data-stu-id="fb2d3-182">Work with text data</span></span>

<span data-ttu-id="fb2d3-183">Comme les données catégoriques, les données textuelles doivent être transformées en caractéristiques numériques avant de les utiliser pour construire un modèle d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="fb2d3-184">Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de texte.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="fb2d3-185">Utilisation de données comme les données [`IDataView`](xref:Microsoft.ML.IDataView)ci-dessous qui ont été chargées dans un :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

<span data-ttu-id="fb2d3-186">ML.NET fournit la [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformation qui prend la valeur de chaîne d’un texte et crée un ensemble de fonctionnalités à partir du texte, en appliquant une série de transformations individuelles.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="fb2d3-187">La transformation qui en résulte `Description` convertit les valeurs de texte dans la colonne en un vecteur numérique qui ressemble à la sortie ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="fb2d3-188">Les transformations qui `FeaturizeText` composent peuvent également être appliquées individuellement pour un contrôle plus fin du grain sur la génération de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="fb2d3-189">`textEstimator`contient un sous-ensemble d’opérations effectuées par la [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) méthode.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="fb2d3-190">L’avantage d’un pipeline plus complexe est qu’il procure une visibilité et un contrôle des transformations appliquées aux données.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="fb2d3-191">Si, par exemple, nous utilisons la première entrée, voici une description détaillée des résultats produits par les étapes de transformation définies par `textEstimator` :</span><span class="sxs-lookup"><span data-stu-id="fb2d3-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="fb2d3-192">**Texte original: C’est un bon produit**</span><span class="sxs-lookup"><span data-stu-id="fb2d3-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="fb2d3-193">Transformer</span><span class="sxs-lookup"><span data-stu-id="fb2d3-193">Transform</span></span> | <span data-ttu-id="fb2d3-194">Description</span><span class="sxs-lookup"><span data-stu-id="fb2d3-194">Description</span></span> | <span data-ttu-id="fb2d3-195">Résultats</span><span class="sxs-lookup"><span data-stu-id="fb2d3-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="fb2d3-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="fb2d3-196">1. NormalizeText</span></span> | <span data-ttu-id="fb2d3-197">Convertit toutes les lettres en minuscules par défaut</span><span class="sxs-lookup"><span data-stu-id="fb2d3-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="fb2d3-198">this is a good product</span><span class="sxs-lookup"><span data-stu-id="fb2d3-198">this is a good product</span></span>
|<span data-ttu-id="fb2d3-199">2. Mots symboliques</span><span class="sxs-lookup"><span data-stu-id="fb2d3-199">2. TokenizeWords</span></span> | <span data-ttu-id="fb2d3-200">Fractionne la chaîne en mots individuels</span><span class="sxs-lookup"><span data-stu-id="fb2d3-200">Splits string into individual words</span></span> | <span data-ttu-id="fb2d3-201">["this","is","a","good","product"]</span><span class="sxs-lookup"><span data-stu-id="fb2d3-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="fb2d3-202">3. SupprimerDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="fb2d3-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="fb2d3-203">Supprime les mots vides comme *is* et *a*.</span><span class="sxs-lookup"><span data-stu-id="fb2d3-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="fb2d3-204">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="fb2d3-204">["good","product"]</span></span>
|<span data-ttu-id="fb2d3-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="fb2d3-205">4. MapValueToKey</span></span> | <span data-ttu-id="fb2d3-206">Mappe les valeurs sur des clés (catégories) en fonction des données d’entrée</span><span class="sxs-lookup"><span data-stu-id="fb2d3-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="fb2d3-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="fb2d3-207">[1,2]</span></span>
|<span data-ttu-id="fb2d3-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="fb2d3-208">5. ProduceNGrams</span></span> | <span data-ttu-id="fb2d3-209">Transforme le texte en une séquence de mots consécutifs</span><span class="sxs-lookup"><span data-stu-id="fb2d3-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="fb2d3-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="fb2d3-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="fb2d3-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="fb2d3-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="fb2d3-212">Applique une mise à l’échelle aux entrées d’après leur norme IP</span><span class="sxs-lookup"><span data-stu-id="fb2d3-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="fb2d3-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="fb2d3-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
