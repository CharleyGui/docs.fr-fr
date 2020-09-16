---
title: Charger des données depuis des fichiers et d’autres sources
description: Découvrez comment charger des données pour le traitement et la formation dans ML.NET à l’aide de l’API. Les données sont stockées dans des fichiers, des bases de données, JSON, XML ou des collections en mémoire.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: edcb1c4d00a09ba8404b08ddc3ca3447a52a81b6
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679584"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="21fa3-104">Charger des données depuis des fichiers et d’autres sources</span><span class="sxs-lookup"><span data-stu-id="21fa3-104">Load data from files and other sources</span></span>

<span data-ttu-id="21fa3-105">Découvrez comment charger des données pour le traitement et la formation dans ML.NET à l’aide de l’API.</span><span class="sxs-lookup"><span data-stu-id="21fa3-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="21fa3-106">Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.</span><span class="sxs-lookup"><span data-stu-id="21fa3-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="21fa3-107">Si vous utilisez le générateur de modèles, consultez [charger des données d’apprentissage dans le générateur de modèles](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="21fa3-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="21fa3-108">Créer le modèle de données</span><span class="sxs-lookup"><span data-stu-id="21fa3-108">Create the data model</span></span>

<span data-ttu-id="21fa3-109">ML.NET permet de définir des modèles de données par le biais de classes.</span><span class="sxs-lookup"><span data-stu-id="21fa3-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="21fa3-110">Soit les données d’entrée suivantes :</span><span class="sxs-lookup"><span data-stu-id="21fa3-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="21fa3-111">Créez un modèle de données qui représente l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="21fa3-111">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="21fa3-112">Annotation du modèle de données avec des attributs de colonne</span><span class="sxs-lookup"><span data-stu-id="21fa3-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="21fa3-113">Les attributs donnent à ML.NET plus d’informations sur le modèle de données et la source de données.</span><span class="sxs-lookup"><span data-stu-id="21fa3-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="21fa3-114">L' [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribut spécifie les index de colonne de vos propriétés.</span><span class="sxs-lookup"><span data-stu-id="21fa3-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21fa3-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) est requis uniquement lors du chargement de données à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="21fa3-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="21fa3-116">Chargez les colonnes en tant que :</span><span class="sxs-lookup"><span data-stu-id="21fa3-116">Load columns as:</span></span>

- <span data-ttu-id="21fa3-117">Colonnes individuelles comme `Size` et `CurrentPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="21fa3-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="21fa3-118">Plusieurs colonnes à la fois sous la forme d’un vecteur comme `HistoricalPrices` dans la classe `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="21fa3-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="21fa3-119">Si vous avez une propriété Vector, appliquez l' [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribut à la propriété dans votre modèle de données.</span><span class="sxs-lookup"><span data-stu-id="21fa3-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="21fa3-120">Il est important de noter que tous les éléments du vecteur doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="21fa3-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="21fa3-121">Le fait de conserver les colonnes séparées permet de faciliter et d’assouplir l’ingénierie des caractéristiques mais, pour un très grand nombre de colonnes, le fonctionnement des colonnes individuelles a un impact sur la vitesse d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="21fa3-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="21fa3-122">ML.NET fonctionne par le biais des noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="21fa3-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="21fa3-123">Si vous souhaitez remplacer le nom d’une colonne par un nom autre que le nom de la propriété, utilisez l' [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribut.</span><span class="sxs-lookup"><span data-stu-id="21fa3-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="21fa3-124">Quand vous créez des objets en mémoire, vous le faites toujours en utilisant le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="21fa3-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="21fa3-125">Toutefois, pour le traitement des données et la création de modèles Machine Learning, ML.NET Substitue et référence la propriété avec la valeur fournie dans l' [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribut.</span><span class="sxs-lookup"><span data-stu-id="21fa3-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="21fa3-126">Charger des données à partir d’un fichier spécifique</span><span class="sxs-lookup"><span data-stu-id="21fa3-126">Load data from a single file</span></span>

<span data-ttu-id="21fa3-127">Pour charger des données à partir d’un fichier, utilisez la [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) méthode avec le modèle de données pour les données à charger.</span><span class="sxs-lookup"><span data-stu-id="21fa3-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="21fa3-128">Le paramètre `separatorChar` étant par défaut défini sur le caractère de tabulation, changez-le pour votre fichier de données si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="21fa3-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="21fa3-129">Si votre fichier a un en-tête, définissez le paramètre `hasHeader` sur `true` pour ignorer la première ligne du fichier et commencer à charger les données à partir de la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="21fa3-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="21fa3-130">Charger des données à partir de plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="21fa3-130">Load data from multiple files</span></span>

<span data-ttu-id="21fa3-131">Si vos données sont stockées dans plusieurs fichiers, tant que le schéma de données est le même, ML.NET vous permet de charger les données, que les différents fichiers se trouvent dans le même répertoire ou dans plusieurs répertoires.</span><span class="sxs-lookup"><span data-stu-id="21fa3-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="21fa3-132">Effectuer le chargement à partir de fichiers situés dans le même répertoire</span><span class="sxs-lookup"><span data-stu-id="21fa3-132">Load from files in a single directory</span></span>

<span data-ttu-id="21fa3-133">Lorsque tous vos fichiers de données se trouvent dans le même répertoire, utilisez des caractères génériques dans la [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) méthode.</span><span class="sxs-lookup"><span data-stu-id="21fa3-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="21fa3-134">Effectuer le chargement à partir de fichiers situés dans plusieurs répertoires</span><span class="sxs-lookup"><span data-stu-id="21fa3-134">Load from files in multiple directories</span></span>

<span data-ttu-id="21fa3-135">Pour charger des données à partir de plusieurs répertoires, utilisez la [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) méthode pour créer un [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) .</span><span class="sxs-lookup"><span data-stu-id="21fa3-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader%2A) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="21fa3-136">Ensuite, utilisez la [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) méthode et spécifiez les chemins d’accès individuels des fichiers (les caractères génériques ne peuvent pas être utilisés).</span><span class="sxs-lookup"><span data-stu-id="21fa3-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load%2A) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="21fa3-137">Charger des données à partir d’une base de données relationnelle</span><span class="sxs-lookup"><span data-stu-id="21fa3-137">Load data from a relational database</span></span>

<span data-ttu-id="21fa3-138">ML.NET prend en charge le chargement de données à partir de diverses bases de données relationnelles prises en charge par, [`System.Data`](xref:System.Data) notamment SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="21fa3-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="21fa3-139">Pour utiliser `DatabaseLoader` , référencez le package NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .</span><span class="sxs-lookup"><span data-stu-id="21fa3-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="21fa3-140">À partir d’une base de données avec une table nommée `House` et le schéma suivant :</span><span class="sxs-lookup"><span data-stu-id="21fa3-140">Given a database with a table named `House` and the following schema:</span></span>

```sql
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="21fa3-141">Les données peuvent être modélisées par une classe comme `HouseData`.</span><span class="sxs-lookup"><span data-stu-id="21fa3-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="21fa3-142">Ensuite, à l’intérieur de votre application, créez un `DatabaseLoader` .</span><span class="sxs-lookup"><span data-stu-id="21fa3-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="21fa3-143">Définissez votre chaîne de connexion, ainsi que la commande SQL à exécuter sur la base de données et créez une `DatabaseSource` instance.</span><span class="sxs-lookup"><span data-stu-id="21fa3-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="21fa3-144">Cet exemple utilise une base de données locale SQL Server avec un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="21fa3-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="21fa3-145">Toutefois, DatabaseLoader prend en charge toute autre chaîne de connexion valide pour les bases de données locales et dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="21fa3-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="21fa3-146">Les données numériques qui ne sont pas de type doivent [`Real`](xref:System.Data.SqlDbType) être converties en [`Real`](xref:System.Data.SqlDbType) .</span><span class="sxs-lookup"><span data-stu-id="21fa3-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="21fa3-147">Le [`Real`](xref:System.Data.SqlDbType) type est représenté sous la forme d’une valeur à virgule flottante simple précision ou [`Single`](xref:System.Single) du type d’entrée attendu par les algorithmes ml.net.</span><span class="sxs-lookup"><span data-stu-id="21fa3-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="21fa3-148">Dans cet exemple, la `NumBed` colonne est un entier dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="21fa3-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="21fa3-149">À l’aide de la `CAST` fonction intégrée, elle est convertie en [`Real`](xref:System.Data.SqlDbType) .</span><span class="sxs-lookup"><span data-stu-id="21fa3-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="21fa3-150">Étant donné que la `Price` propriété est déjà de type, [`Real`](xref:System.Data.SqlDbType) elle est chargée telle quelle.</span><span class="sxs-lookup"><span data-stu-id="21fa3-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="21fa3-151">Utilisez la `Load` méthode pour charger les données dans un [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="21fa3-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="21fa3-152">Charger des données depuis d’autres sources</span><span class="sxs-lookup"><span data-stu-id="21fa3-152">Load data from other sources</span></span>

<span data-ttu-id="21fa3-153">En plus du chargement de données stockées dans des fichiers, ML.NET prend en charge le chargement de données depuis des sources incluant notamment celles-ci :</span><span class="sxs-lookup"><span data-stu-id="21fa3-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="21fa3-154">Collections en mémoire</span><span class="sxs-lookup"><span data-stu-id="21fa3-154">In-memory collections</span></span>
- <span data-ttu-id="21fa3-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="21fa3-155">JSON/XML</span></span>

<span data-ttu-id="21fa3-156">Notez que quand vous utilisez des sources de streaming, ML.NET s’attend à ce que l’entrée se présente sous la forme d’une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="21fa3-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="21fa3-157">Ainsi, quand vous utilisez des sources telles que JSON/XML, veillez à convertir les données en une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="21fa3-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="21fa3-158">Soit la collection en mémoire suivante :</span><span class="sxs-lookup"><span data-stu-id="21fa3-158">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="21fa3-159">Chargez la collection en mémoire dans un [`IDataView`](xref:Microsoft.ML.IDataView) avec la [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) méthode :</span><span class="sxs-lookup"><span data-stu-id="21fa3-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21fa3-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) suppose que le [`IEnumerable`](xref:System.Collections.IEnumerable) chargement à partir de est thread-safe.</span><span class="sxs-lookup"><span data-stu-id="21fa3-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable%2A) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="21fa3-161">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="21fa3-161">Next steps</span></span>

- <span data-ttu-id="21fa3-162">Pour nettoyer ou traiter des données, consultez [préparer des données pour la génération d’un modèle](prepare-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="21fa3-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="21fa3-163">Lorsque vous êtes prêt à créer un modèle, consultez [former et évaluer un modèle](train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="21fa3-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
