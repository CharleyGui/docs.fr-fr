---
title: Charger des données depuis des fichiers et d’autres sources
description: Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET. Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.
ms.date: 08/01/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: d5f3aab14a60a8c9860dc67f1cc98f3b1b3188ed
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733363"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="0e65b-104">Charger des données depuis des fichiers et d’autres sources</span><span class="sxs-lookup"><span data-stu-id="0e65b-104">Load data from files and other sources</span></span>

<span data-ttu-id="0e65b-105">Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="0e65b-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="0e65b-106">Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e65b-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="0e65b-107">Créer le modèle de données</span><span class="sxs-lookup"><span data-stu-id="0e65b-107">Create the data model</span></span>

<span data-ttu-id="0e65b-108">ML.NET permet de définir des modèles de données par le biais de classes.</span><span class="sxs-lookup"><span data-stu-id="0e65b-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="0e65b-109">Soit les données d’entrée suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e65b-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="0e65b-110">Créez un modèle de données qui représente l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0e65b-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="0e65b-111">Annotation du modèle de données avec des attributs de colonne</span><span class="sxs-lookup"><span data-stu-id="0e65b-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="0e65b-112">Les attributs donnent à ML.NET plus d’informations sur le modèle de données et la source de données.</span><span class="sxs-lookup"><span data-stu-id="0e65b-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="0e65b-113">L’attribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) spécifie les index de colonne de vos propriétés.</span><span class="sxs-lookup"><span data-stu-id="0e65b-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e65b-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) est nécessaire uniquement lors du chargement de données à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="0e65b-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="0e65b-115">Chargez les colonnes en tant que :</span><span class="sxs-lookup"><span data-stu-id="0e65b-115">Load columns as:</span></span> 
- <span data-ttu-id="0e65b-116">Colonnes individuelles comme `Size` et `CurrentPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="0e65b-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="0e65b-117">Plusieurs colonnes à la fois sous la forme d’un vecteur comme `HistoricalPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="0e65b-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="0e65b-118">Si vous avez une propriété de vecteur, appliquez-lui l’attribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) dans votre modèle de données.</span><span class="sxs-lookup"><span data-stu-id="0e65b-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="0e65b-119">Il est important de noter que tous les éléments du vecteur doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="0e65b-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="0e65b-120">Le fait de conserver les colonnes séparées permet de faciliter et d’assouplir l’ingénierie des caractéristiques mais, pour un très grand nombre de colonnes, le fonctionnement des colonnes individuelles a un impact sur la vitesse d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="0e65b-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="0e65b-121">ML.NET fonctionne par le biais des noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="0e65b-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="0e65b-122">Si vous souhaitez nommer une colonne en autre chose que le nom de propriété, utilisez l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="0e65b-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="0e65b-123">Quand vous créez des objets en mémoire, vous le faites toujours en utilisant le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="0e65b-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="0e65b-124">Toutefois, pour le traitement des données et la génération des modèles Machine Learning, ML.NET remplace la propriété et la référence avec la valeur fournie dans l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="0e65b-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="0e65b-125">Charger des données à partir d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="0e65b-125">Load data from a single file</span></span>

<span data-ttu-id="0e65b-126">Pour charger des données à partir d’un fichier, utilisez la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ainsi que le modèle de données pour les données à charger.</span><span class="sxs-lookup"><span data-stu-id="0e65b-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="0e65b-127">Le paramètre `separatorChar` étant par défaut défini sur le caractère de tabulation, changez-le pour votre fichier de données si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0e65b-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="0e65b-128">Si votre fichier a un en-tête, définissez le paramètre `hasHeader` sur `true` pour ignorer la première ligne du fichier et commencer à charger les données à partir de la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="0e65b-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="0e65b-129">Charger des données à partir de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="0e65b-129">Load data from multiple files</span></span>

<span data-ttu-id="0e65b-130">Si vos données sont stockées dans plusieurs fichiers, tant que le schéma de données est le même, ML.NET vous permet de charger les données, que les différents fichiers se trouvent dans le même répertoire ou dans plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="0e65b-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="0e65b-131">Effectuer le chargement à partir de fichiers situés dans le même répertoire</span><span class="sxs-lookup"><span data-stu-id="0e65b-131">Load from files in a single directory</span></span>

<span data-ttu-id="0e65b-132">Si tous vos fichiers de données se trouvent dans le même répertoire, utilisez des caractères génériques dans la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).</span><span class="sxs-lookup"><span data-stu-id="0e65b-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="0e65b-133">Effectuer le chargement à partir de fichiers situés dans plusieurs répertoires</span><span class="sxs-lookup"><span data-stu-id="0e65b-133">Load from files in multiple directories</span></span>

<span data-ttu-id="0e65b-134">Pour charger des données à partir de plusieurs répertoires, utilisez la méthode [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) pour créer un [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="0e65b-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="0e65b-135">Ensuite, utilisez la méthode [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) et spécifiez les différents chemins de fichiers (vous ne pouvez pas utiliser de caractères génériques).</span><span class="sxs-lookup"><span data-stu-id="0e65b-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="0e65b-136">Charger des données depuis d’autres sources</span><span class="sxs-lookup"><span data-stu-id="0e65b-136">Load data from other sources</span></span>

<span data-ttu-id="0e65b-137">En plus du chargement de données stockées dans des fichiers, ML.NET prend en charge le chargement de données depuis des sources incluant notamment celles-ci :</span><span class="sxs-lookup"><span data-stu-id="0e65b-137">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="0e65b-138">Collections en mémoire</span><span class="sxs-lookup"><span data-stu-id="0e65b-138">In-memory collections</span></span>
- <span data-ttu-id="0e65b-139">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="0e65b-139">JSON/XML</span></span>
- <span data-ttu-id="0e65b-140">Bases de données</span><span class="sxs-lookup"><span data-stu-id="0e65b-140">Databases</span></span>

<span data-ttu-id="0e65b-141">Notez que quand vous utilisez des sources de streaming, ML.NET s’attend à ce que l’entrée se présente sous la forme d’une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e65b-141">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="0e65b-142">Ainsi, quand vous utilisez des sources telles que JSON/XML, veillez à convertir les données en une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e65b-142">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="0e65b-143">Soit la collection en mémoire suivante :</span><span class="sxs-lookup"><span data-stu-id="0e65b-143">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="0e65b-144">Chargez la collection en mémoire dans un [`IDataView`](xref:Microsoft.ML.IDataView) avec la méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :</span><span class="sxs-lookup"><span data-stu-id="0e65b-144">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e65b-145">La méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) suppose que l’[`IEnumerable`](xref:System.Collections.IEnumerable) à partir duquel elle est chargée est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="0e65b-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span> 

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
