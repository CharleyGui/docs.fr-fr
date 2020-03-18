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
# <a name="prepare-data-for-building-a-model"></a>Préparer des données pour la génération d’un modèle

Découvrez comment utiliser ML.NET pour préparer des données en vue d’effectuer un traitement supplémentaire ou de générer un modèle.

Les données sont souvent dans un format incorrect et disséminées. ML.NET algorithmes d’apprentissage automatique s’attendent à ce que l’entrée ou les fonctionnalités se trouve dans un seul vecteur numérique. De même, la valeur de prévoir (l’étiquette), surtout lorsqu’il s’agit de données catégoriques, doit être codée. Ainsi, un des objectifs de la préparation des données consiste à obtenir les données dans le format attendu par les algorithmes ML.NET.

## <a name="filter-data"></a>Filtrer les données

Parfois, toutes les données d’un jeu de données ne sont pas appropriées pour l’analyse. Une approche pour supprimer les données non pertinentes consiste à effectuer un filtrage. Le [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contient un ensemble d’opérations [`IDataView`](xref:Microsoft.ML.IDataView) de filtre qui prennent dans un contenant toutes les données et de retourner un [IDataView](xref:Microsoft.ML.IDataView) contenant uniquement les points de données d’intérêt. Il est important de noter que parce [`IEstimator`](xref:Microsoft.ML.IEstimator%601) [`ITransformer`](xref:Microsoft.ML.ITransformer) que les [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)opérations de filtre ne sont [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) pas un ou comme ceux dans le , ils ne peuvent pas être inclus dans un pipeline ou de préparation de données.

Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :

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

Pour filtrer les données en fonction [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) de la valeur d’une colonne, utilisez la méthode.

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

L’exemple ci-dessus prend les lignes dans le jeu de données ayant un prix entre 200 000 et 1 000 000. L’application de ce filtre retourne uniquement les deux dernières lignes dans les données et exclut la première ligne, car son prix, 1 00 000, n’appartient pas à la plage spécifiée.

## <a name="replace-missing-values"></a>Remplacer des valeurs manquantes

Les valeurs manquantes sont courantes dans les jeux de données. Pour traiter les valeurs manquantes, une approche consiste à les remplacer par la valeur par défaut du type donné éventuel ou par une autre valeur significative telle que la valeur moyenne dans les données.

Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :

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

Notez que le dernier élément dans notre liste a une valeur manquante pour `Price`. Pour remplacer les valeurs `Price` manquantes [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) dans la colonne, utilisez la méthode pour combler cette valeur manquante.

> [!IMPORTANT]
> [`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A)ne fonctionne qu’avec des données numériques.

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

ML.NET prend en charge divers [modes de remplacement](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode). L’échantillon ci-dessus utilise le `Mean` mode de remplacement, qui remplit la valeur manquante avec la valeur moyenne de cette colonne. Le remplacement se traduit par le remplissage de la propriété `Price` pour le dernier élément dans les données avec la valeur 200 000, soit la moyenne de 100 000 et 300 000.

## <a name="use-normalizers"></a>Utiliser des normaliseurs

[La normalisation](https://en.wikipedia.org/wiki/Feature_scaling) est une technique de pré-traitement des données utilisée pour mettre à l’échelle les fonctionnalités pour être dans la même plage, généralement entre 0 et 1, de sorte qu’ils peuvent être traités avec plus de précision par un algorithme d’apprentissage automatique. Par exemple, les fourchettes d’âge et de revenu varient considérablement selon l’âge généralement de 0 à 100 ans et le revenu étant généralement de l’ordre de zéro à des milliers. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de normalisation.

### <a name="min-max-normalization"></a>Normalisation min-max

Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :

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

La normalisation peut être appliquée aux colonnes avec des valeurs numériques uniques, ainsi qu’aux vecteurs. Normalisez les `Price` données de la colonne à [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) l’aide d’une normalisation min-max avec la méthode.

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

Les valeurs `[200000,100000]` de prix `[ 1, 0.5 ]` d’origine sont converties en utilisant la `MinMax` formule de normalisation qui génère des valeurs de production de l’ordre de 0-1.

### <a name="binning"></a>Quantification

La [quantification](https://en.wikipedia.org/wiki/Data_binning) convertit des valeurs continues en une représentation discrète de l’entrée. Par exemple, supposons qu’une de vos caractéristiques est l’âge. Au lieu d’utiliser la valeur de l’âge réel, la quantification crée des plages pour cette valeur. 0-18 pourrait être une cellule, de même que 19-35, et ainsi de suite.

Prenez les données d’entrée [`IDataView`](xref:Microsoft.ML.IDataView) suivantes `data`et chargez-les dans un :

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

Normalisez les données en [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) bacs à l’aide de la méthode. Le paramètre `maximumBinCount` vous permet de spécifier le nombre de cellules nécessaires pour classifier vos données. Dans cet exemple, les données sont placées dans deux cellules.

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

L’un des types de données les plus courants est celui des données catégoriques. Les données catégories ont un nombre limité de catégories. Par exemple, les États des États-Unis, ou une liste des types d’animaux trouvés dans un ensemble d’images. Que les données catégoriques soient des caractéristiques ou des étiquettes, elles doivent être cartographiées sur une valeur numérique afin qu’elles puissent être utilisées pour générer un modèle d’apprentissage automatique. Il existe un certain nombre de façons de travailler avec des données catégoriques dans ML.NET, en fonction du problème que vous résolvez.

### <a name="key-value-mapping"></a>Cartographie de la valeur clé

Dans ML.NET, une clé est une valeur integer qui représente une catégorie. La cartographie des valeurs clés est le plus souvent utilisée pour cartographier les étiquettes de chaîne en valeurs integer uniques pour la formation, puis revenir à leurs valeurs de chaîne lorsque le modèle est utilisé pour faire une prédiction.

Les transformations utilisées pour effectuer la cartographie de valeur clé sont [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) et [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).

`MapValueToKey`ajoute un dictionnaire de cartes dans `MapKeyToValue` le modèle, de sorte que peut effectuer la transformation inverse lors de la prise d’une prédiction.

### <a name="one-hot-encoding"></a>Un codage chaud

Un codage chaud prend un ensemble fini de valeurs et les cartographie `1` sur les entiers dont la représentation binaire a une valeur unique dans des positions uniques dans la chaîne. Un codage chaud peut être le meilleur choix s’il n’y a pas de commande implicite des données catégoriques. Le tableau suivant montre un exemple avec des codes postaux comme valeurs brutes.

|Valeur brute|Une valeur codée chaude|
|---------|---------------------|
|98052|00...01|
|98100|00...10|
|...|...|
|98109|10...00|

La transformation pour convertir les données catégoriques en [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A)numéros codés à un seul chaud est .

### <a name="hashing"></a>Hashing

Le hachage est une autre façon de convertir les données catégoriques en nombres. Une fonction de hachage cartographie les données d’une taille arbitraire (une chaîne de texte par exemple) sur un nombre à portée fixe. Le hachage peut être un moyen rapide et efficace pour l’espace de vectoriser les caractéristiques. Un exemple notable de hachage dans l’apprentissage automatique est le filtrage des spams par courriel où, au lieu de maintenir un dictionnaire de mots connus, chaque mot dans l’e-mail est haché et ajouté à un vecteur de fonctionnalités grande. L’utilisation du hachage de cette façon évite le problème du contournement malveillant de filtrage de spam par l’utilisation de mots qui ne sont pas dans le dictionnaire.

ML.NET fournit la transformation [de Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) pour effectuer le hachage sur le texte, les dates et les données numériques. Comme la cartographie des clés de valeur, les sorties de la transformation du hachage sont des types clés.

## <a name="work-with-text-data"></a>Utiliser des données texte

Comme les données catégoriques, les données textuelles doivent être transformées en caractéristiques numériques avant de les utiliser pour construire un modèle d’apprentissage automatique. Consultez la [page sur les transformations](../resources/transforms.md) pour obtenir une liste et une description plus détaillées des transformations de texte.

Utilisation de données comme les données [`IDataView`](xref:Microsoft.ML.IDataView)ci-dessous qui ont été chargées dans un :

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

ML.NET fournit la [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transformation qui prend la valeur de chaîne d’un texte et crée un ensemble de fonctionnalités à partir du texte, en appliquant une série de transformations individuelles.

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

La transformation qui en résulte `Description` convertit les valeurs de texte dans la colonne en un vecteur numérique qui ressemble à la sortie ci-dessous :

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

Les transformations qui `FeaturizeText` composent peuvent également être appliquées individuellement pour un contrôle plus fin du grain sur la génération de fonctionnalités.

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

`textEstimator`contient un sous-ensemble d’opérations effectuées par la [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) méthode. L’avantage d’un pipeline plus complexe est qu’il procure une visibilité et un contrôle des transformations appliquées aux données.

Si, par exemple, nous utilisons la première entrée, voici une description détaillée des résultats produits par les étapes de transformation définies par `textEstimator` :

**Texte original: C’est un bon produit**

|Transformer | Description | Résultats
|--|--|--|
|1. NormalizeText | Convertit toutes les lettres en minuscules par défaut | this is a good product
|2. Mots symboliques | Fractionne la chaîne en mots individuels | ["this","is","a","good","product"]
|3. SupprimerDefaultStopWords | Supprime les mots vides comme *is* et *a*. | ["good","product"]
|4. MapValueToKey | Mappe les valeurs sur des clés (catégories) en fonction des données d’entrée |  [1,2]
|5. ProduceNGrams | Transforme le texte en une séquence de mots consécutifs | [1,1,1,0,0]
|6. NormalizeLpNorm | Applique une mise à l’échelle aux entrées d’après leur norme IP | [ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]
