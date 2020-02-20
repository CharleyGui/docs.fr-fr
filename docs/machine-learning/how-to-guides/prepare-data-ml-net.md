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
# <a name="prepare-data-for-building-a-model"></a>Préparer des données pour la génération d’un modèle

Découvrez comment utiliser ML.NET pour préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.

Les données sont souvent dans un format incorrect et disséminées. Les algorithmes Machine Learning ML.NET attendent que les entrées ou les fonctionnalités soient dans un vecteur numérique unique. De même, la valeur à prédire (étiquette), en particulier lorsqu’il s’agit de données catégoriques, doit être encodée. Ainsi, un des objectifs de la préparation des données consiste à obtenir les données dans le format attendu par les algorithmes ML.NET.

## <a name="filter-data"></a>Filtrer les données

Parfois, toutes les données d’un jeu de données ne sont pas appropriées pour l’analyse. Une approche pour supprimer les données non pertinentes consiste à effectuer un filtrage. Le [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) comporte un ensemble d’opérations de filtre qui acceptent un [`IDataView`](xref:Microsoft.ML.IDataView) contenant toutes les données et retournent un [IDataView](xref:Microsoft.ML.IDataView) contenant uniquement les points de données d’intérêt. Il est important de noter que les opérations de filtre, qui ne sont pas un [`IEstimator`](xref:Microsoft.ML.IEstimator%601) ou [`ITransformer`](xref:Microsoft.ML.ITransformer) comme dans le [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), ne peuvent pas être incluses dans le cadre d’un pipeline de préparation des données [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ou [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601).

Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:

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

Pour filtrer les données en fonction de la valeur d’une colonne, utilisez la méthode [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A).

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

L’exemple ci-dessus prend les lignes dans le jeu de données ayant un prix entre 200 000 et 1 000 000. L’application de ce filtre retourne uniquement les deux dernières lignes dans les données et exclut la première ligne, car son prix, 1 00 000, n’appartient pas à la plage spécifiée.

## <a name="replace-missing-values"></a>Remplacer des valeurs manquantes

Les valeurs manquantes sont courantes dans les jeux de données. Pour traiter les valeurs manquantes, une approche consiste à les remplacer par la valeur par défaut du type donné éventuel ou par une autre valeur significative telle que la valeur moyenne dans les données.

Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:

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

Notez que le dernier élément dans notre liste a une valeur manquante pour `Price`. Pour remplacer la valeur manquante dans la colonne `Price`, utilisez la méthode [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) afin de remplir cette valeur manquante.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) fonctionne uniquement avec des données numériques.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET prend en charge divers [modes de remplacement](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). L’exemple ci-dessus utilise le mode de remplacement `Mean`, qui remplit la valeur manquante avec la valeur moyenne de cette colonne. Le remplacement se traduit par le remplissage de la propriété `Price` pour le dernier élément dans les données avec la valeur 200 000, soit la moyenne de 100 000 et 300 000.

## <a name="use-normalizers"></a>Utiliser des normaliseurs

La [normalisation](https://en.wikipedia.org/wiki/Feature_scaling) est une technique de prétraitement des données utilisée pour mettre à l’échelle des fonctionnalités qui se trouvent dans la même plage, généralement entre 0 et 1, afin qu’elles puissent être traitées de façon plus précise par un algorithme machine learning. Par exemple, les plages de l’âge et du revenu varient considérablement avec l’âge généralement dans la plage de 0-100 et le revenu est généralement compris entre zéro et des milliers. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de normalisation.

### <a name="min-max-normalization"></a>Normalisation min-max

Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:

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

La normalisation peut être appliquée aux colonnes avec des valeurs numériques uniques, ainsi qu’aux vecteurs. Normalisez les données dans la colonne `Price` à l’aide de la normalisation min-max avec la méthode [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A).

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Les valeurs de prix d’origine `[200000,100000]` sont converties en `[ 1, 0.5 ]` à l’aide de la formule de normalisation `MinMax` qui génère des valeurs de sortie dans la plage 0-1.

### <a name="binning"></a>Quantification

La [quantification](https://en.wikipedia.org/wiki/Data_binning) convertit des valeurs continues en une représentation discrète de l’entrée. Par exemple, supposons qu’une de vos caractéristiques est l’âge. Au lieu d’utiliser la valeur de l’âge réel, la quantification crée des plages pour cette valeur. 0-18 pourrait être une cellule, de même que 19-35, et ainsi de suite.

Prenez les données d’entrée suivantes et chargez-les dans une [`IDataView`](xref:Microsoft.ML.IDataView) appelée `data`:

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

Normalisez les données en cellules à l’aide de la méthode [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A). Le paramètre `maximumBinCount` vous permet de spécifier le nombre de cellules nécessaires pour classifier vos données. Dans cet exemple, les données sont placées dans deux cellules.

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

L’un des types de données les plus courants est celui des données catégoriques. Les données catégoriques ont un nombre fini de catégories. Par exemple, les États des États-Unis ou une liste des types d’animaux trouvés dans un ensemble d’images. Que les données catégoriques soient des fonctionnalités ou des étiquettes, elles doivent être mappées sur une valeur numérique afin de pouvoir être utilisées pour générer un modèle de Machine Learning. Il existe plusieurs façons de travailler avec des données catégoriques dans ML.NET, en fonction du problème que vous résolvez.

### <a name="key-value-mapping"></a>Mappage des valeurs de clé

Dans ML.NET, une clé est une valeur entière qui représente une catégorie. Le mappage des valeurs de clé est le plus souvent utilisé pour mapper des étiquettes de chaîne dans des valeurs entières uniques pour l’apprentissage, puis revenir à leurs valeurs de chaîne lorsque le modèle est utilisé pour effectuer une prédiction.

Les transformations utilisées pour effectuer le mappage des valeurs de clé sont [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) et [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey` ajoute un dictionnaire de mappages dans le modèle, afin que `MapKeyToValue` puisse effectuer la transformation inverse lors de la création d’une prédiction.

### <a name="one-hot-encoding"></a>Un encodage réactif

Un encodage réactif accepte un ensemble fini de valeurs et les mappe sur des entiers dont la représentation binaire a une seule `1` valeur dans les positions uniques de la chaîne. Un encodage réactif peut être le meilleur choix s’il n’existe aucun classement implicite des données catégoriques. Le tableau suivant montre un exemple avec des codes postaux comme valeurs brutes.

|Valeur brute|Une valeur encodée à chaud|
|---------|---------------------|
|98052|00... 01|
|98100|00... 10|
|...|...|
|98109|10... 00|

La transformation pour convertir des données catégoriques en nombres codés à chaud est [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).

### <a name="hashing"></a>Hachage

Le hachage est une autre façon de convertir des données catégoriques en nombres. Une fonction de hachage mappe les données d’une taille arbitraire (une chaîne de texte par exemple) sur un nombre avec une plage fixe. Le hachage peut être un moyen rapide et efficace de vectoriser des fonctionnalités. Un exemple notable de hachage dans Machine Learning est le filtrage de courrier indésirable par courrier électronique où, au lieu de conserver un dictionnaire de mots connus, chaque mot de l’e-mail est haché et ajouté à un vecteur de fonctionnalité de grande taille. L’utilisation du hachage de cette façon évite le problème de contournement du filtrage de courrier indésirable malveillant par l’utilisation de mots qui ne sont pas dans le dictionnaire.

ML.NET fournit une transformation de [hachage](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) pour effectuer un hachage sur du texte, des dates et des données numériques. À l’instar du mappage de clé de valeur, les sorties de la transformation de hachage sont des types de clés.

## <a name="work-with-text-data"></a>Utiliser des données texte

Comme les données catégoriques, les données de texte doivent être transformées en fonctionnalités numériques avant de les utiliser pour générer un modèle de Machine Learning. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de texte.

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

ML.NET fournit la transformation [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) qui prend la valeur de chaîne d’un texte et crée un ensemble de fonctionnalités à partir du texte, en appliquant une série de transformations individuelles.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

La transformation résultante convertit les valeurs de texte de la colonne `Description` en un vecteur numérique ressemblant à la sortie ci-dessous :

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Les transformations qui composent `FeaturizeText` peuvent également être appliquées individuellement pour un contrôle plus fin de la génération de fonctionnalités.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator` contient un sous-ensemble des opérations effectuées par la méthode [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A). L’avantage d’un pipeline plus complexe est qu’il procure une visibilité et un contrôle des transformations appliquées aux données.

Si, par exemple, nous utilisons la première entrée, voici une description détaillée des résultats produits par les étapes de transformation définies par `textEstimator` :

**Texte d’origine : il s’agit d’un bon produit**

|Transformer | Description | Résultats
|--|--|--|
|1. NormalizeText | Convertit toutes les lettres en minuscules par défaut | this is a good product
|2. TokenizeWords | Fractionne la chaîne en mots individuels | ["this","is","a","good","product"]
|3. RemoveDefaultStopWords | Supprime les mots vides comme *is* et *a*. | ["good","product"]
|4. MapValueToKey | Mappe les valeurs sur des clés (catégories) en fonction des données d’entrée |  [1,2]
|5. ProduceNGrams | Transforme le texte en une séquence de mots consécutifs | [1,1,1,0,0]
|6. NormalizeLpNorm | Applique une mise à l’échelle aux entrées d’après leur norme IP | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
