---
title: Charger des données depuis des fichiers et d’autres sources
description: Découvrez comment charger des données pour le traitement et la formation dans ML.NET à l’aide de l’API. Les données sont stockées dans des fichiers, des bases de données, JSON, XML ou des collections en mémoire.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344756"
---
# <a name="load-data-from-files-and-other-sources"></a>Charger des données depuis des fichiers et d’autres sources

Découvrez comment charger des données pour le traitement et la formation dans ML.NET à l’aide de l’API. Les données sont stockées à l’origine dans des fichiers ou d’autres sources de données, comme des bases de données, du JSON, du XML ou des collections en mémoire.

Si vous utilisez le générateur de modèles, consultez [charger des données d’apprentissage dans le générateur de modèles](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Création du modèle de données

ML.NET permet de définir des modèles de données par le biais de classes. Soit les données d’entrée suivantes :

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Créez un modèle de données qui représente l’extrait de code ci-dessous :

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Annotation du modèle de données avec des attributs de colonne

Les attributs donnent à ML.NET plus d’informations sur le modèle de données et la source de données.

L’attribut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) spécifie les index de colonne de vos propriétés.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) est nécessaire uniquement lors du chargement de données à partir d’un fichier.

Chargez les colonnes en tant que :

- Colonnes individuelles comme `Size` et `CurrentPrices` dans la classe `HousingData`.
- Plusieurs colonnes à la fois sous la forme d’un vecteur comme `HistoricalPrices` dans la classe `HousingData`.

Si vous avez une propriété de vecteur, appliquez-lui l’attribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) dans votre modèle de données. Il est important de noter que tous les éléments du vecteur doivent être du même type. Le fait de conserver les colonnes séparées permet de faciliter et d’assouplir l’ingénierie des caractéristiques mais, pour un très grand nombre de colonnes, le fonctionnement des colonnes individuelles a un impact sur la vitesse d’entraînement.

ML.NET fonctionne par le biais des noms de colonne. Si vous souhaitez nommer une colonne en autre chose que le nom de propriété, utilisez l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute). Quand vous créez des objets en mémoire, vous le faites toujours en utilisant le nom de propriété. Toutefois, pour le traitement des données et la génération des modèles Machine Learning, ML.NET remplace la propriété et la référence avec la valeur fournie dans l’attribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute).

## <a name="load-data-from-a-single-file"></a>Charger des données à partir d’un fichier spécifique

Pour charger des données à partir d’un fichier, utilisez la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) ainsi que le modèle de données pour les données à charger. Le paramètre `separatorChar` étant par défaut défini sur le caractère de tabulation, changez-le pour votre fichier de données si cela est nécessaire. Si votre fichier a un en-tête, définissez le paramètre `hasHeader` sur `true` pour ignorer la première ligne du fichier et commencer à charger les données à partir de la deuxième ligne.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Charger des données à partir de plusieurs fichiers

Si vos données sont stockées dans plusieurs fichiers, tant que le schéma de données est le même, ML.NET vous permet de charger les données, que les différents fichiers se trouvent dans le même répertoire ou dans plusieurs répertoires.

### <a name="load-from-files-in-a-single-directory"></a>Effectuer le chargement à partir de fichiers situés dans le même répertoire

Si tous vos fichiers de données se trouvent dans le même répertoire, utilisez des caractères génériques dans la méthode [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Effectuer le chargement à partir de fichiers situés dans plusieurs répertoires

Pour charger des données à partir de plusieurs répertoires, utilisez la méthode [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) pour créer un [`TextLoader`](xref:Microsoft.ML.Data.TextLoader). Ensuite, utilisez la méthode [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) et spécifiez les différents chemins de fichiers (vous ne pouvez pas utiliser de caractères génériques).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Charger des données à partir d’une base de données relationnelle

ML.NET prend en charge le chargement de données à partir de diverses bases de données relationnelles prises en charge par [`System.Data`](xref:System.Data) qui incluent SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 et bien d’autres encore.

> [!NOTE]
> Pour utiliser `DatabaseLoader`, référencez le package NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .

À partir d’une base de données avec une table nommée `House` et le schéma suivant :

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Les données peuvent être modélisées par une classe comme `HouseData`.

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Ensuite, à l’intérieur de votre application, créez une `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Définissez votre chaîne de connexion, ainsi que la commande SQL à exécuter sur la base de données et créez une instance `DatabaseSource`. Cet exemple utilise une base de données locale SQL Server avec un chemin d’accès de fichier. Toutefois, DatabaseLoader prend en charge toute autre chaîne de connexion valide pour les bases de données locales et dans le Cloud.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Les données numériques qui ne sont pas de type [`Real`](xref:System.Data.SqlDbType) doivent être converties en [`Real`](xref:System.Data.SqlDbType). Le type de [`Real`](xref:System.Data.SqlDbType) est représenté sous la forme d’une valeur à virgule flottante simple précision ou d’un [`Single`](xref:System.Single), le type d’entrée attendu par les algorithmes ml.net. Dans cet exemple, la colonne `NumBed` est un entier dans la base de données. À l’aide de la fonction intégrée `CAST`, elle est convertie en [`Real`](xref:System.Data.SqlDbType). Étant donné que la propriété `Price` est déjà de type [`Real`](xref:System.Data.SqlDbType) elle est chargée telle quelle.

Utilisez la méthode `Load` pour charger les données dans une [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Charger des données depuis d’autres sources

En plus du chargement de données stockées dans des fichiers, ML.NET prend en charge le chargement de données depuis des sources incluant notamment celles-ci :

- Collections en mémoire
- JSON/XML

Notez que quand vous utilisez des sources de streaming, ML.NET s’attend à ce que l’entrée se présente sous la forme d’une collection en mémoire. Ainsi, quand vous utilisez des sources telles que JSON/XML, veillez à convertir les données en une collection en mémoire.

Soit la collection en mémoire suivante :

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

Chargez la collection en mémoire dans un [`IDataView`](xref:Microsoft.ML.IDataView) avec la méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :

> [!IMPORTANT]
> La méthode [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) suppose que l’[`IEnumerable`](xref:System.Collections.IEnumerable) à partir duquel elle est chargée est thread-safe.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Étapes suivantes :

- Pour nettoyer ou traiter des données, consultez [préparer des données pour la génération d’un modèle](prepare-data-ml-net.md).
- Lorsque vous êtes prêt à créer un modèle, consultez [former et évaluer un modèle](train-machine-learning-model-ml-net.md).
