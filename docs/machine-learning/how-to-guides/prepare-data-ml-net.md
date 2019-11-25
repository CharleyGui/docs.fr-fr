---
title: Préparer des données pour la génération d’un modèle
description: Découvrez comment utiliser des transformations dans ML.NET pour manipuler et préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: e9bfad4724b353b0f3bfc615a40f1d72b80a2cd4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976976"
---
# <a name="prepare-data-for-building-a-model"></a>Préparer des données pour la génération d’un modèle

Découvrez comment utiliser ML.NET pour préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.

Les données sont souvent dans un format incorrect et disséminées. Les algorithmes Machine Learning ML.NET attendent que les entrées ou les fonctionnalités soient dans un vecteur numérique unique. De même, la valeur à prédire (étiquette), en particulier lorsqu’il s’agit de données catégoriques, doit être encodée. Ainsi, un des objectifs de la préparation des données consiste à obtenir les données dans le format attendu par les algorithmes ML.NET.

## <a name="filter-data"></a>Filtrer les données

Parfois, toutes les données d’un jeu de données ne sont pas appropriées pour l’analyse. Une approche pour supprimer les données non pertinentes consiste à effectuer un filtrage. Le [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) comporte un ensemble d’opérations de filtre qui acceptent un [`IDataView`](xref:Microsoft.ML.IDataView) contenant toutes les données et retournent un [IDataView](xref:Microsoft.ML.IDataView) contenant uniquement les points de données d’intérêt. Il est important de noter que les opérations de filtre, qui ne sont pas un [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) comme dans le [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), ne peuvent pas être incluses dans le cadre d’un pipeline de préparation des données [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601).

Supposons que nous utilisons les données d’entrée suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

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

Pour filtrer les données en fonction de la valeur d’une colonne, utilisez la méthode [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*).

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

L’exemple ci-dessus prend les lignes dans le jeu de données ayant un prix entre 200 000 et 1 000 000. L’application de ce filtre retourne uniquement les deux dernières lignes dans les données et exclut la première ligne, car son prix, 1 00 000, n’appartient pas à la plage spécifiée.

## <a name="replace-missing-values"></a>Remplacer les valeurs manquantes

Les valeurs manquantes sont courantes dans les jeux de données. Pour traiter les valeurs manquantes, une approche consiste à les remplacer par la valeur par défaut du type donné éventuel ou par une autre valeur significative telle que la valeur moyenne dans les données.

Supposons que nous utilisons les données d’entrée suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

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

Notez que le dernier élément dans notre liste a une valeur manquante pour `Price`. Pour remplacer la valeur manquante dans la colonne `Price`, utilisez la méthode [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) afin de remplir cette valeur manquante.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) fonctionne uniquement avec des données numériques.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET prend en charge divers [modes de remplacement](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). L’exemple ci-dessus utilise le mode de remplacement `Mean`, qui remplit la valeur manquante avec la valeur moyenne de la colonne concernée. Le remplacement se traduit par le remplissage de la propriété `Price` pour le dernier élément dans les données avec la valeur 200 000, soit la moyenne de 100 000 et 300 000.

## <a name="use-normalizers"></a>Utiliser des normaliseurs

La [normalisation](https://en.wikipedia.org/wiki/Feature_scaling) est une technique de prétraitement des données utilisée pour normaliser les caractéristiques qui ne sont pas sur la même échelle, ce qui permet aux algorithmes de converger plus rapidement. Par exemple, les plages de valeurs telles que l’âge et le revenu varient de façon importante, l’âge étant généralement compris entre 0 et 100 et le revenu entre zéro et plusieurs milliers. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de normalisation.

### <a name="min-max-normalization"></a>Normalisation min-max

Supposons que nous utilisons les données d’entrée suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

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

La normalisation peut être appliquée aux colonnes avec des valeurs numériques uniques, ainsi qu’aux vecteurs. Normalisez les données dans la colonne `Price` à l’aide de la normalisation min-max avec la méthode [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*).

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Les valeurs de prix d’origine `[200000,100000]` sont converties en `[ 1, 0.5 ]` à l’aide de la formule de normalisation `MinMax`, qui génère des valeurs de sortie appartenant à la plage 0-1.

### <a name="binning"></a>Quantification

La [quantification](https://en.wikipedia.org/wiki/Data_binning) convertit des valeurs continues en une représentation discrète de l’entrée. Par exemple, supposons qu’une de vos caractéristiques est l’âge. Au lieu d’utiliser la valeur de l’âge réel, la quantification crée des plages pour cette valeur. 0-18 pourrait être une cellule, de même que 19-35, et ainsi de suite.

Supposons que nous utilisons les données d’entrée suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

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

Normalisez les données en cellules à l’aide de la méthode [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*). Le paramètre `maximumBinCount` vous permet de spécifier le nombre de cellules nécessaires pour classifier vos données. Dans cet exemple, les données sont placées dans deux cellules.

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

La quantification crée des bornes de cellule de `[0,200000,Infinity]`. Ainsi, les cellules obtenues sont `[0,1,1]`, car la première observation est comprise entre 0 et 200 000, et les autres sont supérieures à 200 000 mais inférieures à l’infini.

## <a name="work-with-categorical-data"></a>Utiliser des données de catégorie

Les données de catégorie non numériques doivent être converties en nombre avant d’être utilisées pour générer un modèle Machine Learning.

Supposons que nous utilisons les données d’entrée suivantes qui sont chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

```csharp
CarData[] cars = new CarData[]
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

La propriété `VehicleType` de catégorie peut être convertie en un nombre à l’aide de la méthode [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*).

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

La transformation qui en résulte convertit la valeur de texte de `VehicleType` en un nombre. Les entrées de la colonne `VehicleType` deviennent les suivantes quand la transformation est appliquée :

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a>Utiliser des données texte

Les données texte doivent être transformées en nombres avant d’être utilisées pour générer un modèle Machine Learning. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de texte.

Supposons que nous utilisons des données telles que celles ci-dessous qui ont été chargées dans un [`IDataView`](xref:Microsoft.ML.IDataView) :

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

L’étape minimale pour convertir du texte en une représentation sous forme de vecteur numérique consiste à utiliser la méthode [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*). À l’aide de la transformation [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*), une série de transformations est appliquée à la colonne de texte d’entrée, ce qui engendre un vecteur numérique représentant les n-grammes de mot et de caractère à la norme IP.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

La transformation qui en résulte convertit les valeurs de texte dans la colonne `Description` en un vecteur numérique qui ressemble à la sortie ci-dessous :

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Vous pouvez combiner des étapes de traitement de texte complexes en un [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pour supprimer le bruit et potentiellement réduire la quantité de ressources de traitement requises.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` contient un sous-ensemble des opérations effectuées par la méthode [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*). L’avantage d’un pipeline plus complexe est qu’il procure une visibilité et un contrôle des transformations appliquées aux données.

Si, par exemple, nous utilisons la première entrée, voici une description détaillée des résultats produits par les étapes de transformation définies par `textEstimator` :

**Texte d’origine : il s’agit d’un bon produit**

|transformation | Description | Résultat
|--|--|--|
|1. NormalizeText | Convertit toutes les lettres en minuscules par défaut | this is a good product
|2. TokenizeWords | Fractionne la chaîne en mots individuels | ["this","is","a","good","product"]
|3. RemoveDefaultStopWords | Supprime les mots vides comme *is* et *a*. | ["good","product"]
|4. MapValueToKey | Mappe les valeurs sur des clés (catégories) en fonction des données d’entrée |  [1,2]
|5. ProduceNGrams | Transforme le texte en une séquence de mots consécutifs | [1,1,1,0,0]
|6. NormalizeLpNorm | Applique une mise à l’échelle aux entrées d’après leur norme IP | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
