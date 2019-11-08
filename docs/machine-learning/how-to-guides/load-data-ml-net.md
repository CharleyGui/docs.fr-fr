---
title: Charger des données depuis des fichiers et d’autres sources
description: Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET. Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 07b3e7f5302a03f5fa4c936679c8a3c00d19a7b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740549"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="a25f9-104">Charger des données depuis des fichiers et d’autres sources</span><span class="sxs-lookup"><span data-stu-id="a25f9-104">Load data from files and other sources</span></span>

<span data-ttu-id="a25f9-105">Ce guide pratique vous montre comment charger des données à des fins de traitement et d’entraînement dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a25f9-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="a25f9-106">Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a25f9-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="a25f9-107">Créer le modèle de données</span><span class="sxs-lookup"><span data-stu-id="a25f9-107">Create the data model</span></span>

<span data-ttu-id="a25f9-108">ML.NET permet de définir des modèles de données par le biais de classes.</span><span class="sxs-lookup"><span data-stu-id="a25f9-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="a25f9-109">Soit les données d’entrée suivantes :</span><span class="sxs-lookup"><span data-stu-id="a25f9-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="a25f9-110">Créez un modèle de données qui représente l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a25f9-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="a25f9-111">Annotation du modèle de données avec des attributs de colonne</span><span class="sxs-lookup"><span data-stu-id="a25f9-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="a25f9-112">Les attributs donnent à ML.NET plus d’informations sur le modèle de données et la source de données.</span><span class="sxs-lookup"><span data-stu-id="a25f9-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="a25f9-113">L’attribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) spécifie les index de colonne de vos propriétés.</span><span class="sxs-lookup"><span data-stu-id="a25f9-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a25f9-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) est nécessaire uniquement lors du chargement de données à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="a25f9-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="a25f9-115">Chargez les colonnes en tant que :</span><span class="sxs-lookup"><span data-stu-id="a25f9-115">Load columns as:</span></span>

- <span data-ttu-id="a25f9-116">Colonnes individuelles comme `Size` et `CurrentPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="a25f9-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="a25f9-117">Plusieurs colonnes à la fois sous la forme d’un vecteur comme `HistoricalPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="a25f9-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="a25f9-118">Si vous avez une propriété de vecteur, appliquez-lui l’attribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) dans votre modèle de données.</span><span class="sxs-lookup"><span data-stu-id="a25f9-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="a25f9-119">Il est important de noter que tous les éléments du vecteur doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="a25f9-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="a25f9-120">Le fait de conserver les colonnes séparées permet de faciliter et d’assouplir l’ingénierie des caractéristiques mais, pour un très grand nombre de colonnes, le fonctionnement des colonnes individuelles a un impact sur la vitesse d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="a25f9-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="a25f9-121">ML.NET fonctionne par le biais des noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="a25f9-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="a25f9-122">Si vous souhaitez nommer une colonne en autre chose que le nom de propriété, utilisez l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="a25f9-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="a25f9-123">Quand vous créez des objets en mémoire, vous le faites toujours en utilisant le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="a25f9-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="a25f9-124">Toutefois, pour le traitement des données et la génération des modèles Machine Learning, ML.NET remplace la propriété et la référence avec la valeur fournie dans l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).</span><span class="sxs-lookup"><span data-stu-id="a25f9-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="a25f9-125">Charger des données à partir d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="a25f9-125">Load data from a single file</span></span>

<span data-ttu-id="a25f9-126">Pour charger des données à partir d’un fichier, utilisez la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ainsi que le modèle de données pour les données à charger.</span><span class="sxs-lookup"><span data-stu-id="a25f9-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="a25f9-127">Le paramètre `separatorChar` étant par défaut défini sur le caractère de tabulation, changez-le pour votre fichier de données si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a25f9-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="a25f9-128">Si votre fichier a un en-tête, définissez le paramètre `hasHeader` sur `true` pour ignorer la première ligne du fichier et commencer à charger les données à partir de la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="a25f9-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="a25f9-129">Charger des données à partir de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="a25f9-129">Load data from multiple files</span></span>

<span data-ttu-id="a25f9-130">Si vos données sont stockées dans plusieurs fichiers, tant que le schéma de données est le même, ML.NET vous permet de charger les données, que les différents fichiers se trouvent dans le même répertoire ou dans plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="a25f9-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="a25f9-131">Effectuer le chargement à partir de fichiers situés dans le même répertoire</span><span class="sxs-lookup"><span data-stu-id="a25f9-131">Load from files in a single directory</span></span>

<span data-ttu-id="a25f9-132">Si tous vos fichiers de données se trouvent dans le même répertoire, utilisez des caractères génériques dans la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).</span><span class="sxs-lookup"><span data-stu-id="a25f9-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="a25f9-133">Effectuer le chargement à partir de fichiers situés dans plusieurs répertoires</span><span class="sxs-lookup"><span data-stu-id="a25f9-133">Load from files in multiple directories</span></span>

<span data-ttu-id="a25f9-134">Pour charger des données à partir de plusieurs répertoires, utilisez la méthode [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) pour créer un [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="a25f9-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="a25f9-135">Ensuite, utilisez la méthode [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) et spécifiez les différents chemins de fichiers (vous ne pouvez pas utiliser de caractères génériques).</span><span class="sxs-lookup"><span data-stu-id="a25f9-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="a25f9-136">Charger des données à partir d’une base de données relationnelle</span><span class="sxs-lookup"><span data-stu-id="a25f9-136">Load data from a relational database</span></span>

<span data-ttu-id="a25f9-137">ML.NET prend en charge le chargement de données à partir de diverses bases de données relationnelles prises en charge par [`System.Data`](xref:System.Data) qui incluent SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 et bien d’autres encore.</span><span class="sxs-lookup"><span data-stu-id="a25f9-137">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="a25f9-138">Pour utiliser `DatabaseLoader`, référencez le package NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .</span><span class="sxs-lookup"><span data-stu-id="a25f9-138">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="a25f9-139">À partir d’une base de données avec une table nommée `House` et le schéma suivant :</span><span class="sxs-lookup"><span data-stu-id="a25f9-139">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="a25f9-140">Les données peuvent être modélisées par une classe comme `HouseData`.</span><span class="sxs-lookup"><span data-stu-id="a25f9-140">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }
    
    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="a25f9-141">Ensuite, à l’intérieur de votre application, créez une `DatabaseLoader`.</span><span class="sxs-lookup"><span data-stu-id="a25f9-141">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="a25f9-142">Définissez votre chaîne de connexion, ainsi que la commande SQL à exécuter sur la base de données et créez une instance `DatabaseSource`.</span><span class="sxs-lookup"><span data-stu-id="a25f9-142">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="a25f9-143">Cet exemple utilise une base de données locale SQL Server avec un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="a25f9-143">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="a25f9-144">Toutefois, DatabaseLoader prend en charge toute autre chaîne de connexion valide pour les bases de données locales et dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="a25f9-144">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="a25f9-145">Les données numériques qui ne sont pas de type [`Real`](xref:System.Data.SqlDbType) doivent être converties en [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="a25f9-145">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="a25f9-146">Le type de [`Real`](xref:System.Data.SqlDbType) est représenté sous la forme d’une valeur à virgule flottante simple précision ou d’un [`Single`](xref:System.Single), le type d’entrée attendu par les algorithmes ml.net.</span><span class="sxs-lookup"><span data-stu-id="a25f9-146">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="a25f9-147">Dans cet exemple, la colonne `NumBed` est un entier dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="a25f9-147">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="a25f9-148">À l’aide de la fonction intégrée `CAST`, elle est convertie en [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="a25f9-148">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="a25f9-149">Étant donné que la propriété `Price` est déjà de type [`Real`](xref:System.Data.SqlDbType) elle est chargée telle quelle.</span><span class="sxs-lookup"><span data-stu-id="a25f9-149">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="a25f9-150">Utilisez la méthode `Load` pour charger les données dans une [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="a25f9-150">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="a25f9-151">Charger des données depuis d’autres sources</span><span class="sxs-lookup"><span data-stu-id="a25f9-151">Load data from other sources</span></span>

<span data-ttu-id="a25f9-152">En plus du chargement de données stockées dans des fichiers, ML.NET prend en charge le chargement de données depuis des sources incluant notamment celles-ci :</span><span class="sxs-lookup"><span data-stu-id="a25f9-152">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="a25f9-153">Collections en mémoire</span><span class="sxs-lookup"><span data-stu-id="a25f9-153">In-memory collections</span></span>
- <span data-ttu-id="a25f9-154">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="a25f9-154">JSON/XML</span></span>

<span data-ttu-id="a25f9-155">Notez que quand vous utilisez des sources de streaming, ML.NET s’attend à ce que l’entrée se présente sous la forme d’une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a25f9-155">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="a25f9-156">Ainsi, quand vous utilisez des sources telles que JSON/XML, veillez à convertir les données en une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a25f9-156">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="a25f9-157">Soit la collection en mémoire suivante :</span><span class="sxs-lookup"><span data-stu-id="a25f9-157">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="a25f9-158">Chargez la collection en mémoire dans un [`IDataView`](xref:Microsoft.ML.IDataView) avec la méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :</span><span class="sxs-lookup"><span data-stu-id="a25f9-158">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a25f9-159">La méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) suppose que l’[`IEnumerable`](xref:System.Collections.IEnumerable) à partir duquel elle est chargée est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="a25f9-159">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="a25f9-160">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a25f9-160">Next steps</span></span>

<span data-ttu-id="a25f9-161">Si vous utilisez le générateur de modèles pour effectuer l’apprentissage du modèle de Machine Learning, consultez [charger des données d’apprentissage dans le générateur de modèles](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="a25f9-161">If you're using Model Builder to train the machine learning model, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>
