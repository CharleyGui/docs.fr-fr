---
title: Préparer des données pour la génération d’un modèle
description: Découvrez comment utiliser des transformations dans ML.NET pour manipuler et préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452985"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="952e8-103">Préparer des données pour la génération d’un modèle</span><span class="sxs-lookup"><span data-stu-id="952e8-103">Prepare data for building a model</span></span>

<span data-ttu-id="952e8-104">Découvrez comment utiliser ML.NET pour préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.</span><span class="sxs-lookup"><span data-stu-id="952e8-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="952e8-105">Les données sont souvent dans un format incorrect et disséminées.</span><span class="sxs-lookup"><span data-stu-id="952e8-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="952e8-106">Les algorithmes Machine Learning ML.NET attendent que les entrées ou les fonctionnalités soient dans un vecteur numérique unique.</span><span class="sxs-lookup"><span data-stu-id="952e8-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="952e8-107">De même, la valeur à prédire (étiquette), en particulier lorsqu’il s’agit de données catégoriques, doit être encodée.</span><span class="sxs-lookup"><span data-stu-id="952e8-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="952e8-108">Ainsi, un des objectifs de la préparation des données consiste à obtenir les données dans le format attendu par les algorithmes ML.NET.</span><span class="sxs-lookup"><span data-stu-id="952e8-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="952e8-109">Filtrer les données</span><span class="sxs-lookup"><span data-stu-id="952e8-109">Filter data</span></span>

<span data-ttu-id="952e8-110">Parfois, toutes les données d’un jeu de données ne sont pas appropriées pour l’analyse.</span><span class="sxs-lookup"><span data-stu-id="952e8-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="952e8-111">Une approche pour supprimer les données non pertinentes consiste à effectuer un filtrage.</span><span class="sxs-lookup"><span data-stu-id="952e8-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="952e8-112">Le [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) comporte un ensemble d’opérations de filtre qui acceptent un [`IDataView`](xref:Microsoft.ML.IDataView) contenant toutes les données et retournent un [IDataView](xref:Microsoft.ML.IDataView) contenant uniquement les points de données d’intérêt.</span><span class="sxs-lookup"><span data-stu-id="952e8-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="952e8-113">Il est important de noter que les opérations de filtre, qui ne sont pas un [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) comme dans le [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), ne peuvent pas être incluses dans le cadre d’un pipeline de préparation des données [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601).</span><span class="sxs-lookup"><span data-stu-id="952e8-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="952e8-114">Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:</span><span class="sxs-lookup"><span data-stu-id="952e8-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="952e8-115">Pour filtrer les données en fonction de la valeur d’une colonne, utilisez la méthode [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="952e8-116">L’exemple ci-dessus prend les lignes dans le jeu de données ayant un prix entre 200 000 et 1 000 000.</span><span class="sxs-lookup"><span data-stu-id="952e8-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="952e8-117">L’application de ce filtre retourne uniquement les deux dernières lignes dans les données et exclut la première ligne, car son prix, 1 00 000, n’appartient pas à la plage spécifiée.</span><span class="sxs-lookup"><span data-stu-id="952e8-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="952e8-118">Remplacer des valeurs manquantes</span><span class="sxs-lookup"><span data-stu-id="952e8-118">Replace missing values</span></span>

<span data-ttu-id="952e8-119">Les valeurs manquantes sont courantes dans les jeux de données.</span><span class="sxs-lookup"><span data-stu-id="952e8-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="952e8-120">Pour traiter les valeurs manquantes, une approche consiste à les remplacer par la valeur par défaut du type donné éventuel ou par une autre valeur significative telle que la valeur moyenne dans les données.</span><span class="sxs-lookup"><span data-stu-id="952e8-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="952e8-121">Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:</span><span class="sxs-lookup"><span data-stu-id="952e8-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="952e8-122">Notez que le dernier élément dans notre liste a une valeur manquante pour `Price`.</span><span class="sxs-lookup"><span data-stu-id="952e8-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="952e8-123">Pour remplacer la valeur manquante dans la colonne `Price`, utilisez la méthode [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) afin de remplir cette valeur manquante.</span><span class="sxs-lookup"><span data-stu-id="952e8-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="952e8-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) fonctionne uniquement avec des données numériques.</span><span class="sxs-lookup"><span data-stu-id="952e8-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="952e8-125">ML.NET prend en charge divers [modes de remplacement](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span><span class="sxs-lookup"><span data-stu-id="952e8-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="952e8-126">L’exemple ci-dessus utilise le mode de remplacement `Mean`, qui remplit la valeur manquante avec la valeur moyenne de cette colonne.</span><span class="sxs-lookup"><span data-stu-id="952e8-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="952e8-127">Le remplacement se traduit par le remplissage de la propriété `Price` pour le dernier élément dans les données avec la valeur 200 000, soit la moyenne de 100 000 et 300 000.</span><span class="sxs-lookup"><span data-stu-id="952e8-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="952e8-128">Utiliser des normaliseurs</span><span class="sxs-lookup"><span data-stu-id="952e8-128">Use normalizers</span></span>

<span data-ttu-id="952e8-129">La [normalisation](https://en.wikipedia.org/wiki/Feature_scaling) est une technique de prétraitement des données utilisée pour mettre à l’échelle des fonctionnalités qui se trouvent dans la même plage, généralement entre 0 et 1, afin qu’elles puissent être traitées de façon plus précise par un algorithme machine learning.</span><span class="sxs-lookup"><span data-stu-id="952e8-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="952e8-130">Par exemple, les plages de l’âge et du revenu varient considérablement avec l’âge généralement dans la plage de 0-100 et le revenu est généralement compris entre zéro et des milliers.</span><span class="sxs-lookup"><span data-stu-id="952e8-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="952e8-131">Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de normalisation.</span><span class="sxs-lookup"><span data-stu-id="952e8-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="952e8-132">Normalisation min-max</span><span class="sxs-lookup"><span data-stu-id="952e8-132">Min-Max normalization</span></span>

<span data-ttu-id="952e8-133">Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:</span><span class="sxs-lookup"><span data-stu-id="952e8-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="952e8-134">La normalisation peut être appliquée aux colonnes avec des valeurs numériques uniques, ainsi qu’aux vecteurs.</span><span class="sxs-lookup"><span data-stu-id="952e8-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="952e8-135">Normalisez les données dans la colonne `Price` à l’aide de la normalisation min-max avec la méthode [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="952e8-136">Les valeurs de prix d’origine `[200000,100000]` sont converties en `[ 1, 0.5 ]` à l’aide de la formule de normalisation `MinMax` qui génère des valeurs de sortie dans la plage 0-1.</span><span class="sxs-lookup"><span data-stu-id="952e8-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="952e8-137">Quantification</span><span class="sxs-lookup"><span data-stu-id="952e8-137">Binning</span></span>

<span data-ttu-id="952e8-138">La [quantification](https://en.wikipedia.org/wiki/Data_binning) convertit des valeurs continues en une représentation discrète de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="952e8-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="952e8-139">Par exemple, supposons qu’une de vos caractéristiques est l’âge.</span><span class="sxs-lookup"><span data-stu-id="952e8-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="952e8-140">Au lieu d’utiliser la valeur de l’âge réel, la quantification crée des plages pour cette valeur.</span><span class="sxs-lookup"><span data-stu-id="952e8-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="952e8-141">0-18 pourrait être une cellule, de même que 19-35, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="952e8-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="952e8-142">Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:</span><span class="sxs-lookup"><span data-stu-id="952e8-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

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

<span data-ttu-id="952e8-143">Normalisez les données en cellules à l’aide de la méthode [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="952e8-144">Le paramètre `maximumBinCount` vous permet de spécifier le nombre de cellules nécessaires pour classifier vos données.</span><span class="sxs-lookup"><span data-stu-id="952e8-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="952e8-145">Dans cet exemple, les données sont placées dans deux cellules.</span><span class="sxs-lookup"><span data-stu-id="952e8-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="952e8-146">La quantification crée des bornes de cellule de `[0,200000,Infinity]`.</span><span class="sxs-lookup"><span data-stu-id="952e8-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="952e8-147">Ainsi, les cellules obtenues sont `[0,1,1]`, car la première observation est comprise entre 0 et 200 000, et les autres sont supérieures à 200 000 mais inférieures à l’infini.</span><span class="sxs-lookup"><span data-stu-id="952e8-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="952e8-148">Utiliser des données de catégorie</span><span class="sxs-lookup"><span data-stu-id="952e8-148">Work with categorical data</span></span>

<span data-ttu-id="952e8-149">L’un des types de données les plus courants est celui des données catégoriques.</span><span class="sxs-lookup"><span data-stu-id="952e8-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="952e8-150">Les données catégoriques ont un nombre fini de catégories.</span><span class="sxs-lookup"><span data-stu-id="952e8-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="952e8-151">Par exemple, les États des États-Unis ou une liste des types d’animaux trouvés dans un ensemble d’images.</span><span class="sxs-lookup"><span data-stu-id="952e8-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="952e8-152">Que les données catégoriques soient des fonctionnalités ou des étiquettes, elles doivent être mappées sur une valeur numérique afin de pouvoir être utilisées pour générer un modèle de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="952e8-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="952e8-153">Il existe plusieurs façons de travailler avec des données catégoriques dans ML.NET, en fonction du problème que vous résolvez.</span><span class="sxs-lookup"><span data-stu-id="952e8-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="952e8-154">Mappage des valeurs de clé</span><span class="sxs-lookup"><span data-stu-id="952e8-154">Key value mapping</span></span>

<span data-ttu-id="952e8-155">Dans ML.NET, une clé est une valeur entière qui représente une catégorie.</span><span class="sxs-lookup"><span data-stu-id="952e8-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="952e8-156">Le mappage des valeurs de clé est le plus souvent utilisé pour mapper des étiquettes de chaîne dans des valeurs entières uniques pour l’apprentissage, puis revenir à leurs valeurs de chaîne lorsque le modèle est utilisé pour effectuer une prédiction.</span><span class="sxs-lookup"><span data-stu-id="952e8-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="952e8-157">Les transformations utilisées pour effectuer le mappage des valeurs de clé sont [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) et [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="952e8-158">`MapValueToKey` ajoute un dictionnaire de mappages dans le modèle, afin que `MapKeyToValue` puisse effectuer la transformation inverse lors de la création d’une prédiction.</span><span class="sxs-lookup"><span data-stu-id="952e8-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="952e8-159">Un encodage réactif</span><span class="sxs-lookup"><span data-stu-id="952e8-159">One hot encoding</span></span>

<span data-ttu-id="952e8-160">Un encodage réactif accepte un ensemble fini de valeurs et les mappe sur des entiers dont la représentation binaire a une seule `1` valeur dans les positions uniques de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="952e8-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="952e8-161">Un encodage réactif peut être le meilleur choix s’il n’existe aucun classement implicite des données catégoriques.</span><span class="sxs-lookup"><span data-stu-id="952e8-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="952e8-162">Le tableau suivant montre un exemple avec des codes postaux comme valeurs brutes.</span><span class="sxs-lookup"><span data-stu-id="952e8-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="952e8-163">Valeur brute</span><span class="sxs-lookup"><span data-stu-id="952e8-163">Raw value</span></span>|<span data-ttu-id="952e8-164">Une valeur encodée à chaud</span><span class="sxs-lookup"><span data-stu-id="952e8-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="952e8-165">98052</span><span class="sxs-lookup"><span data-stu-id="952e8-165">98052</span></span>|<span data-ttu-id="952e8-166">00... 01</span><span class="sxs-lookup"><span data-stu-id="952e8-166">00...01</span></span>|
|<span data-ttu-id="952e8-167">98100</span><span class="sxs-lookup"><span data-stu-id="952e8-167">98100</span></span>|<span data-ttu-id="952e8-168">00... 10</span><span class="sxs-lookup"><span data-stu-id="952e8-168">00...10</span></span>|
|<span data-ttu-id="952e8-169">...</span><span class="sxs-lookup"><span data-stu-id="952e8-169">...</span></span>|<span data-ttu-id="952e8-170">...</span><span class="sxs-lookup"><span data-stu-id="952e8-170">...</span></span>|
|<span data-ttu-id="952e8-171">98109</span><span class="sxs-lookup"><span data-stu-id="952e8-171">98109</span></span>|<span data-ttu-id="952e8-172">10... 00</span><span class="sxs-lookup"><span data-stu-id="952e8-172">10...00</span></span>|

<span data-ttu-id="952e8-173">La transformation pour convertir des données catégoriques en nombres codés à chaud est [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="952e8-174">Hachage</span><span class="sxs-lookup"><span data-stu-id="952e8-174">Hashing</span></span>

<span data-ttu-id="952e8-175">Le hachage est une autre façon de convertir des données catégoriques en nombres.</span><span class="sxs-lookup"><span data-stu-id="952e8-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="952e8-176">Une fonction de hachage mappe les données d’une taille arbitraire (une chaîne de texte par exemple) sur un nombre avec une plage fixe.</span><span class="sxs-lookup"><span data-stu-id="952e8-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="952e8-177">Le hachage peut être un moyen rapide et efficace de vectoriser des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="952e8-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="952e8-178">Un exemple notable de hachage dans Machine Learning est le filtrage de courrier indésirable par courrier électronique où, au lieu de conserver un dictionnaire de mots connus, chaque mot de l’e-mail est haché et ajouté à un vecteur de fonctionnalité de grande taille.</span><span class="sxs-lookup"><span data-stu-id="952e8-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="952e8-179">L’utilisation du hachage de cette façon évite le problème de contournement du filtrage de courrier indésirable malveillant par l’utilisation de mots qui ne sont pas dans le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="952e8-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="952e8-180">ML.NET fournit une transformation de [hachage](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) pour effectuer un hachage sur du texte, des dates et des données numériques.</span><span class="sxs-lookup"><span data-stu-id="952e8-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="952e8-181">À l’instar du mappage de clé de valeur, les sorties de la transformation de hachage sont des types de clés.</span><span class="sxs-lookup"><span data-stu-id="952e8-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="952e8-182">Utiliser des données texte</span><span class="sxs-lookup"><span data-stu-id="952e8-182">Work with text data</span></span>

<span data-ttu-id="952e8-183">Comme les données catégoriques, les données de texte doivent être transformées en fonctionnalités numériques avant de les utiliser pour générer un modèle de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="952e8-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="952e8-184">Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de texte.</span><span class="sxs-lookup"><span data-stu-id="952e8-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="952e8-185">Supposons que nous utilisons des données telles que celles ci-dessous qui ont été chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :</span><span class="sxs-lookup"><span data-stu-id="952e8-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="952e8-186">ML.NET fournit la transformation [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) qui prend la valeur de chaîne d’un texte et crée un ensemble de fonctionnalités à partir du texte, en appliquant une série de transformations individuelles.</span><span class="sxs-lookup"><span data-stu-id="952e8-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="952e8-187">La transformation résultante convertit les valeurs de texte de la colonne `Description` en un vecteur numérique ressemblant à la sortie ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="952e8-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="952e8-188">Les transformations qui composent `FeaturizeText` peuvent également être appliquées individuellement pour un contrôle plus fin de la génération de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="952e8-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="952e8-189">`textEstimator` contient un sous-ensemble des opérations effectuées par la méthode [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A).</span><span class="sxs-lookup"><span data-stu-id="952e8-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="952e8-190">L’avantage d’un pipeline plus complexe est qu’il procure une visibilité et un contrôle des transformations appliquées aux données.</span><span class="sxs-lookup"><span data-stu-id="952e8-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="952e8-191">Si, par exemple, nous utilisons la première entrée, voici une description détaillée des résultats produits par les étapes de transformation définies par `textEstimator` :</span><span class="sxs-lookup"><span data-stu-id="952e8-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="952e8-192">**Texte d’origine : il s’agit d’un bon produit**</span><span class="sxs-lookup"><span data-stu-id="952e8-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="952e8-193">Transformer</span><span class="sxs-lookup"><span data-stu-id="952e8-193">Transform</span></span> | <span data-ttu-id="952e8-194">Description</span><span class="sxs-lookup"><span data-stu-id="952e8-194">Description</span></span> | <span data-ttu-id="952e8-195">Résultats</span><span class="sxs-lookup"><span data-stu-id="952e8-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="952e8-196">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="952e8-196">1. NormalizeText</span></span> | <span data-ttu-id="952e8-197">Convertit toutes les lettres en minuscules par défaut</span><span class="sxs-lookup"><span data-stu-id="952e8-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="952e8-198">this is a good product</span><span class="sxs-lookup"><span data-stu-id="952e8-198">this is a good product</span></span>
|<span data-ttu-id="952e8-199">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="952e8-199">2. TokenizeWords</span></span> | <span data-ttu-id="952e8-200">Fractionne la chaîne en mots individuels</span><span class="sxs-lookup"><span data-stu-id="952e8-200">Splits string into individual words</span></span> | <span data-ttu-id="952e8-201">["this","is","a","good","product"]</span><span class="sxs-lookup"><span data-stu-id="952e8-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="952e8-202">3. RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="952e8-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="952e8-203">Supprime les mots vides comme *is* et *a*.</span><span class="sxs-lookup"><span data-stu-id="952e8-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="952e8-204">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="952e8-204">["good","product"]</span></span>
|<span data-ttu-id="952e8-205">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="952e8-205">4. MapValueToKey</span></span> | <span data-ttu-id="952e8-206">Mappe les valeurs sur des clés (catégories) en fonction des données d’entrée</span><span class="sxs-lookup"><span data-stu-id="952e8-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="952e8-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="952e8-207">[1,2]</span></span>
|<span data-ttu-id="952e8-208">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="952e8-208">5. ProduceNGrams</span></span> | <span data-ttu-id="952e8-209">Transforme le texte en une séquence de mots consécutifs</span><span class="sxs-lookup"><span data-stu-id="952e8-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="952e8-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="952e8-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="952e8-211">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="952e8-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="952e8-212">Applique une mise à l’échelle aux entrées d’après leur norme IP</span><span class="sxs-lookup"><span data-stu-id="952e8-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="952e8-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="952e8-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
